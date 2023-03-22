## USER
You are an Linux AI programming assistant.

- Follow the user's requirements carefully & to the letter.
- First think step-by-step -- describe your plan for what to build in pseudocode, written out in great detail.
- Then output the code in a single code block.
- Minimize any other prose.
- Avoid using code, or command options that are not already popular.

Your first task: Rewrite these bash functions to be more efficient. Add a new function that extracts the metadata independent of the play_video() function. Create the following variables from the metadata and use them as required in the other functions:
- pix_fmt
- color_space
- width
- height
- profile
- frame_rate (sum of */*)

Then, in the select_tags() function, add those variables as selected tags in the kdialog:

function select_tags() {
  # Get the list of tags from ls /run/user/1000/kio-fuse-jlzsHx/tags
  tag_list=$(ls /run/user/1000/kio-fuse-fmJQUg/tags)
  print 'tag_list: %s\n' "$tag_list"
#   tag_list=$(ls /run/user/1000/kio-fuse-jlzsHx/tags)
  tag_list="New_Tag $tag_list"

  # Get the selected tags from getfattr
  selected_tags=$(getfattr -n user.xdg.tags --only-values $1)

  # Create the argument list for kdialog
  arg_list=""
  index=1
  for tag in $tag_list; do
    # Check if the tag is selected
    if echo $selected_tags | grep -q $tag; then
      # If the tag is selected, set its status to "on"
      arg_list="$arg_list $index $tag on"
    else
      # If the tag is not selected, set its status to "off"
      arg_list="$arg_list $index $tag off"
    fi
    index=$((index + 1))
  done

  # Run kdialog with the argument list
  selected_indexes=$(kdialog --checklist "Select tags:" $arg_list)
  if [[ $? = 1 ]]; then # if input is canceled kill the video and exit
    exit
  fi

  # Create a list of selected tags based on the indexes
  selected_tags=""
  for index in $selected_indexes; do
    tag=$(echo $tag_list | awk "{print \$$index}")
    if [ "$tag" == "New_Tag" ]; then
      new_tag=$(kdialog --inputbox "Enter new tag name:")
      if [[ $? = 1 ]]; then # if input is canceled kill the video and exit
        exit
      fi
      tag=$new_tag
      printf 'tag: %s\n' "$tag"
    fi
    selected_tags="$selected_tags,$tag"
  done
  selected_tags=${selected_tags#*,}

  # Set the selected tags with setfattr
  setfattr -n user.xdg.tags -v "$selected_tags" "$1"
}


play_video() {
  metadata=$(ffprobe -v quiet -print_format json -show_streams "$FILEPATH" | jq '.streams[0]')
  if [[ $(echo "$metadata" | jq '.color_space') == '"bt709"' && ( $(echo "$metadata" | jq '.pix_fmt') == '"yuv420p10le"' ) ]]; then
      mpv --input-ipc-server=/tmp/mpv1 --keep-open --hwdec=auto-copy --video-unscaled=yes --script-opts=osc-timems=yes --script-opts=osc-visibility=always --image-lut='/home/thomas/Downloads/DJI Mavic 3 D-Log to Rec.709 V1.cube' "$FILEPATH" > /dev/null 2>&1 &
      sleep 0.1
      mpv --input-ipc-server=/tmp/mpv2 --keep-open --geometry=50%+1280+0 --hwdec=auto-copy --script-opts=osc-timems=yes --script-opts=osc-visibility=always --image-lut='/home/thomas/Downloads/DJI Mavic 3 D-Log to Rec.709 V1.cube' "$FILEPATH" > /dev/null 2>&1 &
      sleep 0.1
      mpv --input-ipc-server=/tmp/mpv3 --keep-open --geometry=50%+1280+720 --hwdec=auto-copy --script-opts=osc-timems=yes --script-opts=osc-visibility=always --image-lut='/home/thomas/Downloads/DJI Mavic 3 D-Log to Rec.709 V1.cube' --speed=2 "$FILEPATH" > /dev/null 2>&1 &
      sleep 0.1
  else
      mpv --input-ipc-server=/tmp/mpv1 --keep-open --hwdec=auto-copy --video-unscaled=yes --script-opts=osc-timems=yes --script-opts=osc-visibility=always "$FILEPATH" > /dev/null 2>&1 &
      sleep 0.1
      mpv --input-ipc-server=/tmp/mpv2 --keep-open --geometry=50%+1280+0 --hwdec=auto-copy --script-opts=osc-timems=yes --script-opts=osc-visibility=always "$FILEPATH" > /dev/null 2>&1 &
      sleep 0.1
      mpv --input-ipc-server=/tmp/mpv3 --keep-open --geometry=50%+1280+720 --hwdec=auto-copy --script-opts=osc-timems=yes --script-opts=osc-visibility=always --speed=2 "$FILEPATH" > /dev/null 2>&1 &
      sleep 0.1
  fi

}


## ASSISTANT
Pseudocode:
1. Create a new function called 'extract_metadata'.
2. In 'extract_metadata', use ffprobe to extract metadata values and save them in variables.
3. Pass the metadata variables to the 'play_video' and 'select_tags' functions.
4. Modify 'play_video' to use the metadata variables.
5. Modify 'select_tags' to include the metadata variables in the kdialog.

```bash
function extract_metadata() {
  metadata=$(ffprobe -v quiet -print_format json -show_streams "$1" | jq '.streams[0]')
  pix_fmt=$(echo "$metadata" | jq -r '.pix_fmt')
  color_space=$(echo "$metadata" | jq -r '.color_space')
  width=$(echo "$metadata" | jq -r '.width')
  height=$(echo "$metadata" | jq -r '.height')
  profile=$(echo "$metadata" | jq -r '.profile')
  frame_rate=$(echo "$metadata" | jq -r '.avg_frame_rate')
}

function select_tags() {
  extract_metadata "$1"
  
  # Rest of the function remains the same
  # ...
  
  # Run kdialog with the argument list
  selected_indexes=$(kdialog --checklist "Select tags:" $arg_list --title "Metadata: Pixel Format: $pix_fmt, Color Space: $color_space, Width: $width, Height: $height, Profile: $profile, Frame Rate: $frame_rate")
  
  # Rest of the function remains the same
  # ...
}

function play_video() {
  extract_metadata "$FILEPATH"
  
  if [[ "$color_space" == "bt709" && "$pix_fmt" == "yuv420p10le" ]]; then
    options="--image-lut='/home/thomas/Downloads/DJI Mavic 3 D-Log to Rec.709 V1.cube'"
  else
    options=""
  fi

  mpv --input-ipc-server=/tmp/mpv1 --keep-open --hwdec=auto-copy --video-unscaled=yes --script-opts=osc-timems=yes --script-opts=osc-visibility=always $options "$FILEPATH" > /dev/null 2>&1 &
  sleep 0.1
  mpv --input-ipc-server=/tmp/mpv2 --keep-open --geometry=50%+1280+0 --hwdec=auto-copy --script-opts=osc-timems=yes --script-opts=osc-visibility=always $options "$FILEPATH" > /dev/null 2>&1 &
  sleep 0.1
  mpv --input-ipc-server=/tmp/mpv3 --keep-open --geometry=50%+1280+720 --hwdec=auto-copy --script-opts=osc-timems=yes --script-opts=osc-visibility=always --speed=2 $options "$FILEPATH" > /dev/null 2>&1 &
  sleep 0.1
}
```

## USER
Why extract the metadata twice?

## ASSISTANT
You're right; extracting metadata twice is inefficient. We can modify the code to extract metadata only once and pass the metadata variables to the functions. Here's the updated pseudocode and code:

Pseudocode:
1. Call 'extract_metadata' function with the file path and store the metadata values in variables.
2. Pass the metadata variables to the 'play_video' and 'select_tags' functions.
3. Modify 'play_video' and 'select_tags' to use the passed metadata variables.

```bash
function extract_metadata() {
  metadata=$(ffprobe -v quiet -print_format json -show_streams "$1" | jq '.streams[0]')
  pix_fmt=$(echo "$metadata" | jq -r '.pix_fmt')
  color_space=$(echo "$metadata" | jq -r '.color_space')
  width=$(echo "$metadata" | jq -r '.width')
  height=$(echo "$metadata" | jq -r '.height')
  profile=$(echo "$metadata" | jq -r '.profile')
  frame_rate=$(echo "$metadata" | jq -r '.avg_frame_rate')
}

function select_tags() {
  local filepath="$1"
  shift
  local pix_fmt="$1"
  shift
  local color_space="$1"
  shift
  local width="$1"
  shift
  local height="$1"
  shift
  local profile="$1"
  shift
  local frame_rate="$1"

  # Rest of the function remains the same
  # ...

  # Run kdialog with the argument list
  selected_indexes=$(kdialog --checklist "Select tags:" $arg_list --title "Metadata: Pixel Format: $pix_fmt, Color Space: $color_space, Width: $width, Height: $height, Profile: $profile, Frame Rate: $frame_rate")

  # Rest of the function remains the same
  # ...
}

function play_video() {
  local filepath="$1"
  shift
  local pix_fmt="$1"
  shift
  local color_space="$1"
  shift

  if [[ "$color_space" == "bt709" && "$pix_fmt" == "yuv420p10le" ]]; then
    options="--image-lut='/home/thomas/Downloads/DJI Mavic 3 D-Log to Rec.709 V1.cube'"
  else
    options=""
  fi

  # Rest of the function remains the same
  # ...
}

# Call extract_metadata and store values in variables
extract_metadata "$FILEPATH"
play_video "$FILEPATH" "$pix_fmt" "$color_space" "$width" "$height" "$profile" "$frame_rate"
select_tags "$FILEPATH" "$pix_fmt" "$color_space" "$width" "$height" "$profile" "$frame_rate"
```

Now, metadata is only extracted once, and the metadata variables are passed to the `play_video` and `select_tags` functions.