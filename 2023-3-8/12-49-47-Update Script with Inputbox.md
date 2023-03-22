## USER
Update the following script. And use code block. When New_Tag is included in the selected_indexes, display an --inputbox. Replace New_Tag in the selected_tags list with the value from the inputbox.

#!/bin/bash
function select_tags() {
  # Get the list of tags from ls /run/user/1000/kio-fuse-jlzsHx/tags
  tag_list=$(ls /run/user/1000/kio-fuse-jlzsHx/tags)
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
    selected_tags="$selected_tags,$tag"
  done
  selected_tags=${selected_tags#*,}

  # Set the selected tags with setfattr
  setfattr -n user.xdg.tags -v "$selected_tags" "$1"
}

# Call the function
select_tags $1

## ASSISTANT
```
#!/bin/bash
function select_tags() {
  # Get the list of tags from ls /run/user/1000/kio-fuse-jlzsHx/tags
  tag_list=$(ls /run/user/1000/kio-fuse-jlzsHx/tags)
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
    fi
    selected_tags="$selected_tags,$tag"
  done
  selected_tags=${selected_tags#*,}

  # Set the selected tags with setfattr
  setfattr -n user.xdg.tags -v "$selected_tags" "$1"
}

# Call the function
select_tags $1
```