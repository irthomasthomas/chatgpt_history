## USER
You are an AI programming assistant.

- Follow the user's requirements carefully & to the letter.
- First think step-by-step -- describe your plan for what to build in pseudocode, written out in great detail.
- Then output the code in a single code block.
- Minimize any other prose.

## ASSISTANT
User requirements:
1. Read a list of names from a text file.
2. Sort the list alphabetically.
3. Output the sorted list to a new text file.

Pseudocode:
1. Open the input file
2. Read the names into a list
3. Close

## USER
I am going to give you 5 json files about videos along with the Camera and Colour profile. Write a bash script to identify future video files Camera type and Colour profiles.

DJI_0796.MP4
Camera: Zoom
Color: Normal

{
    "streams": [
        {
            "index": 0,
            "codec_name": "hevc",
            "codec_long_name": "H.265 / HEVC (High Efficiency Video Coding)",
            "profile": "Main",
            "codec_type": "video",
            "codec_tag_string": "hvc1",
            "codec_tag": "0x31637668",
            "width": 3840,
            "height": 2160,
            "coded_width": 3840,
            "coded_height": 2160,
            "closed_captions": 0,
            "has_b_frames": 1,
            "pix_fmt": "yuv420p",
            "level": 180,
            "color_range": "tv",
            "color_space": "bt709",
            "color_transfer": "bt709",
            "color_primaries": "bt709",
            "chroma_location": "left",
            "refs": 1,
            "r_frame_rate": "50/1",
            "avg_frame_rate": "50/1",
            "time_base": "1/5000",
            "start_pts": 0,
            "start_time": "0.000000",
            "duration_ts": 51600,
            "duration": "10.320000",
            "bit_rate": "120813189",
            "nb_frames": "516",
            "disposition": {
                "default": 1,
                "dub": 0,
                "original": 0,
                "comment": 0,
                "lyrics": 0,
                "karaoke": 0,
                "forced": 0,
                "hearing_impaired": 0,
                "visual_impaired": 0,
                "clean_effects": 0,
                "attached_pic": 0,
                "timed_thumbnails": 0
            },
            "tags": {
                "creation_time": "2023-03-15T15:31:17.000000Z",
                "language": "und",
                "handler_name": "VideoHandler",
                "vendor_id": "[0][0][0][0]"
            }
        }
    ],
    "format": {
        "filename": "/media/thomas/c126dcc9-37b2-4a2c-b0c0-37ff409f39ec/test/DJI_0796.MP4",
        "nb_streams": 4,
        "nb_programs": 0,
        "format_name": "mov,mp4,m4a,3gp,3g2,mj2",
        "format_long_name": "QuickTime / MOV",
        "start_time": "0.000000",
        "duration": "10.320000",
        "size": "160934430",
        "bit_rate": "124755372",
        "probe_score": 100,
        "tags": {
            "major_brand": "isom",
            "minor_version": "512",
            "compatible_brands": "isomiso2mp41",
            "creation_time": "2023-03-15T15:31:17.000000Z",
            "encoder": "DJIMavic3"
        }
    }
}

DJI_0795.MP4
Camera: Zoom
Color: Normal

{
    "streams": [
        {
            "index": 0,
            "codec_name": "h264",
            "codec_long_name": "H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10",
            "profile": "High",
            "codec_type": "video",
            "codec_tag_string": "avc1",
            "codec_tag": "0x31637661",
            "width": 3840,
            "height": 2160,
            "coded_width": 3840,
            "coded_height": 2160,
            "closed_captions": 0,
            "has_b_frames": 2,
            "pix_fmt": "yuv420p",
            "level": 51,
            "color_range": "tv",
            "color_space": "bt709",
            "color_transfer": "bt709",
            "color_primaries": "bt709",
            "chroma_location": "left",
            "refs": 1,
            "is_avc": "true",
            "nal_length_size": "4",
            "r_frame_rate": "50/1",
            "avg_frame_rate": "50/1",
            "time_base": "1/5000",
            "start_pts": 0,
            "start_time": "0.000000",
            "duration_ts": 51800,
            "duration": "10.360000",
            "bit_rate": "160909592",
            "bits_per_raw_sample": "8",
            "nb_frames": "518",
            "disposition": {
                "default": 1,
                "dub": 0,
                "original": 0,
                "comment": 0,
                "lyrics": 0,
                "karaoke": 0,
                "forced": 0,
                "hearing_impaired": 0,
                "visual_impaired": 0,
                "clean_effects": 0,
                "attached_pic": 0,
                "timed_thumbnails": 0
            },
            "tags": {
                "creation_time": "2023-03-15T15:30:42.000000Z",
                "language": "und",
                "handler_name": "VideoHandler",
                "vendor_id": "[0][0][0][0]"
            }
        }
    ],
    "format": {
        "filename": "/media/thomas/c126dcc9-37b2-4a2c-b0c0-37ff409f39ec/test/DJI_0795.MP4",
        "nb_streams": 4,
        "nb_programs": 0,
        "format_name": "mov,mp4,m4a,3gp,3g2,mj2",
        "format_long_name": "QuickTime / MOV",
        "start_time": "0.000000",
        "duration": "10.360000",
        "size": "213475487",
        "bit_rate": "164845935",
        "probe_score": 100,
        "tags": {
            "major_brand": "isom",
            "minor_version": "512",
            "compatible_brands": "isomiso2avc1mp41",
            "creation_time": "2023-03-15T15:30:42.000000Z",
            "encoder": "DJIMavic3"
        }
    }
}

DJI_0794.MP4
Camera: Wide
Colour: HLG

{
    "streams": [
        {
            "index": 0,
            "codec_name": "hevc",
            "codec_long_name": "H.265 / HEVC (High Efficiency Video Coding)",
            "profile": "Main 10",
            "codec_type": "video",
            "codec_tag_string": "hvc1",
            "codec_tag": "0x31637668",
            "width": 5120,
            "height": 2700,
            "coded_width": 5120,
            "coded_height": 2704,
            "closed_captions": 0,
            "has_b_frames": 1,
            "pix_fmt": "yuv420p10le",
            "level": 180,
            "color_range": "tv",
            "color_space": "bt2020nc",
            "color_transfer": "arib-std-b67",
            "color_primaries": "bt2020",
            "chroma_location": "left",
            "refs": 1,
            "r_frame_rate": "30000/1001",
            "avg_frame_rate": "30000/1001",
            "time_base": "1/30000",
            "start_pts": 0,
            "start_time": "0.000000",
            "duration_ts": 358358,
            "duration": "11.945267",
            "bit_rate": "140457424",
            "nb_frames": "358",
            "disposition": {
                "default": 1,
                "dub": 0,
                "original": 0,
                "comment": 0,
                "lyrics": 0,
                "karaoke": 0,
                "forced": 0,
                "hearing_impaired": 0,
                "visual_impaired": 0,
                "clean_effects": 0,
                "attached_pic": 0,
                "timed_thumbnails": 0
            },
            "tags": {
                "creation_time": "2023-03-15T15:23:33.000000Z",
                "language": "und",
                "handler_name": "VideoHandler",
                "vendor_id": "[0][0][0][0]"
            }
        }
    ],
    "format": {
        "filename": "/media/thomas/c126dcc9-37b2-4a2c-b0c0-37ff409f39ec/test/DJI_0794.MP4",
        "nb_streams": 4,
        "nb_programs": 0,
        "format_name": "mov,mp4,m4a,3gp,3g2,mj2",
        "format_long_name": "QuickTime / MOV",
        "start_time": "0.000000",
        "duration": "11.946000",
        "size": "213980119",
        "bit_rate": "143298254",
        "probe_score": 100,
        "tags": {
            "major_brand": "isom",
            "minor_version": "512",
            "compatible_brands": "isomiso2mp41",
            "creation_time": "2023-03-15T15:23:33.000000Z",
            "encoder": "DJIMavic3"
        }
    }
}

DJI_0793.MP4
Camera: Wide
Colour: Normal

{
    "streams": [
        {
            "index": 0,
            "codec_name": "hevc",
            "codec_long_name": "H.265 / HEVC (High Efficiency Video Coding)",
            "profile": "Main",
            "codec_type": "video",
            "codec_tag_string": "hvc1",
            "codec_tag": "0x31637668",
            "width": 5120,
            "height": 2700,
            "coded_width": 5120,
            "coded_height": 2704,
            "closed_captions": 0,
            "has_b_frames": 1,
            "pix_fmt": "yuv420p",
            "level": 180,
            "color_range": "tv",
            "color_space": "bt709",
            "color_transfer": "bt709",
            "color_primaries": "bt709",
            "chroma_location": "left",
            "refs": 1,
            "r_frame_rate": "30000/1001",
            "avg_frame_rate": "30000/1001",
            "time_base": "1/30000",
            "start_pts": 0,
            "start_time": "0.000000",
            "duration_ts": 397397,
            "duration": "13.246567",
            "bit_rate": "140913617",
            "nb_frames": "397",
            "disposition": {
                "default": 1,
                "dub": 0,
                "original": 0,
                "comment": 0,
                "lyrics": 0,
                "karaoke": 0,
                "forced": 0,
                "hearing_impaired": 0,
                "visual_impaired": 0,
                "clean_effects": 0,
                "attached_pic": 0,
                "timed_thumbnails": 0
            },
            "tags": {
                "creation_time": "2023-03-15T15:22:45.000000Z",
                "language": "und",
                "handler_name": "VideoHandler",
                "vendor_id": "[0][0][0][0]"
            }
        }
    ],
    "format": {
        "filename": "/media/thomas/c126dcc9-37b2-4a2c-b0c0-37ff409f39ec/test/DJI_0793.MP4",
        "nb_streams": 4,
        "nb_programs": 0,
        "format_name": "mov,mp4,m4a,3gp,3g2,mj2",
        "format_long_name": "QuickTime / MOV",
        "start_time": "0.000000",
        "duration": "13.248000",
        "size": "238119274",
        "bit_rate": "143791832",
        "probe_score": 100,
        "tags": {
            "major_brand": "isom",
            "minor_version": "512",
            "compatible_brands": "isomiso2mp41",
            "creation_time": "2023-03-15T15:22:45.000000Z",
            "encoder": "DJIMavic3"
        }
    }
}

DJI_0792.MP4
Camera: Wide
Colour: D-Log

{
    "streams": [
        {
            "index": 0,
            "codec_name": "hevc",
            "codec_long_name": "H.265 / HEVC (High Efficiency Video Coding)",
            "profile": "Main 10",
            "codec_type": "video",
            "codec_tag_string": "hvc1",
            "codec_tag": "0x31637668",
            "width": 5120,
            "height": 2700,
            "coded_width": 5120,
            "coded_height": 2704,
            "closed_captions": 0,
            "has_b_frames": 1,
            "pix_fmt": "yuv420p10le",
            "level": 180,
            "color_range": "tv",
            "color_space": "bt709",
            "color_transfer": "bt709",
            "color_primaries": "bt709",
            "chroma_location": "left",
            "refs": 1,
            "r_frame_rate": "30000/1001",
            "avg_frame_rate": "30000/1001",
            "time_base": "1/30000",
            "start_pts": 0,
            "start_time": "0.000000",
            "duration_ts": 2329327,
            "duration": "77.644233",
            "bit_rate": "140108678",
            "nb_frames": "2327",
            "disposition": {
                "default": 1,
                "dub": 0,
                "original": 0,
                "comment": 0,
                "lyrics": 0,
                "karaoke": 0,
                "forced": 0,
                "hearing_impaired": 0,
                "visual_impaired": 0,
                "clean_effects": 0,
                "attached_pic": 0,
                "timed_thumbnails": 0
            },
            "tags": {
                "creation_time": "2023-03-15T15:19:24.000000Z",
                "language": "und",
                "handler_name": "VideoHandler",
                "vendor_id": "[0][0][0][0]"
            }
        }
    ],
    "format": {
        "filename": "/media/thomas/c126dcc9-37b2-4a2c-b0c0-37ff409f39ec/test/DJI_0792.MP4",
        "nb_streams": 4,
        "nb_programs": 0,
        "format_name": "mov,mp4,m4a,3gp,3g2,mj2",
        "format_long_name": "QuickTime / MOV",
        "start_time": "0.000000",
        "duration": "77.645000",
        "size": "1381936693",
        "bit_rate": "142385131",
        "probe_score": 100,
        "tags": {
            "major_brand": "isom",
            "minor_version": "512",
            "compatible_brands": "isomiso2mp41",
            "creation_time": "2023-03-15T15:19:24.000000Z",
            "encoder": "DJIMavic3"
        }
    }
}

## ASSISTANT
Here's a bash script that can be used to identify the camera type and color profile of future video files based on the provided JSON files.

```bash
#!/bin/bash

# Install ffprobe if not installed
if ! command -v ffprobe &> /dev/null; then
    echo "ffprobe could not be found. Please install it and try again."
    exit 1
fi

# Analyze a video file
analyze_video() {
    video_file="$1"
    json_file="$(mktemp)"
    ffprobe -v quiet -print_format json -show_streams -show_format "${video_file}" > "${json_file}"

    width=$(jq -r '.streams[0].width' "${json_file}")
    height=$(jq -r '.streams[0].height' "${json_file}")
    codec_name=$(jq -r '.streams[0].codec_name' "${json_file}")
    color_space=$(jq -r '.streams[0].color_space' "${json_file}")
    color_transfer=$(jq -r '.streams[0].color_transfer' "${json_file}")
    color_primaries=$(jq -r '.streams[0].color_primaries' "${json_file}")

    rm "${json_file}"

    # Determine camera type
    if [ "${width}" -eq 3840 ] && [ "${height}" -eq 2160 ]; then
        camera_type="Zoom"
    elif [ "${width}" -eq 5120 ] && [ "${height}" -eq 2700 ]; then
        camera_type="Wide"
    else
        camera_type="Unknown"
    fi

    # Determine color profile
    if [ "${color_space}" == "bt709" ] && [ "${color_transfer}" == "bt709" ] && [ "${color_primaries}" == "bt709" ]; then
        color_profile="Normal"
    elif [ "${color_space}" == "bt2020nc" ] && [ "${color_transfer}" == "arib-std-b67" ] && [ "${color_primaries}" == "bt2020" ]; then
        color_profile="HLG"
    elif [ "${color_space}" == "bt709" ] && [ "${color_transfer}" == "bt709" ] && [ "${color_primaries}" == "bt709" ] && [ "${codec_name}" == "hevc" ]; then
        color_profile="D-Log"
    else
        color_profile="Unknown"
    fi

    echo "File: ${video_file}"
    echo "Camera Type: ${camera_type}"
    echo "Color Profile: ${color_profile}"
    echo ""
}

# Analyze all video files in the current directory
for video_file in *.MP4; do
    analyze_video "${video_file}"
done
```

Save this script as `video_analysis.sh` and make it executable with `chmod +x video_analysis.sh`. Then, run the script in the directory containing the video files (e.g., `./video_analysis.sh`). The script will analyze all `.MP4` files in the current directory and print the camera type and color profile for each file.

Please note that this script requires `ffprobe`, which is part of the FFmpeg suite, and `jq` for JSON processing. If you don't have these tools installed, please install them before running the script.

## USER
This classifies the D-Log as Normal.

## ASSISTANT
I apologize for the mistake in my previous script. I have updated the script to properly classify D-Log color profiles as well. Here's the revised script:

```bash
#!/bin/bash

for file in *.MP4; do
  ffprobe_output=$(ffprobe -v quiet -print_format json -show_streams -show_format "$file")
  color_transfer=$(echo "$ffprobe_output" | jq -r '.streams[] | select(.codec_type=="video") | .color_transfer')
  width=$(echo "$ffprobe_output" | jq -r '.streams[] | select(.codec_type=="video") | .width')
  height=$(echo "$ffprobe_output" | jq -r '.streams[] | select(.codec_type=="video") | .height')
  
  camera_type=""
  color_profile=""
  
  if [ "$width" -eq 5120 ] && [ "$height" -eq 2700 ]; then
    camera_type="Wide"
  elif [ "$width" -eq 3840 ] && [ "$height" -eq 2160 ]; then
    camera_type="Zoom"
  else
    camera_type="Unknown"
  fi
  
  if [ "$color_transfer" == "arib-std-b67" ]; then
    color_profile="HLG"
  elif [ "$color_transfer" == "bt709" ]; then
    if [ "$(echo "$ffprobe_output" | jq -r '.streams[] | select(.codec_type=="video") | .pix_fmt')" == "yuv420p10le" ]; then
      color_profile="D-Log"
    else
      color_profile="Normal"
    fi
  else
    color_profile="Unknown"
  fi
  
  echo "File: $file"
  echo "Camera: $camera_type"
  echo "Color: $color_profile"
  echo ""
done
```

This script now checks the pixel format to determine if the color profile is D-Log or Normal. If the pixel format is `yuv420p10le` and the color transfer is `bt709`, the color profile is classified as D-Log.

## USER
Display stream section from "ffprobe -v quiet -print_format json -show_format -show_streams -select_streams v:0 $FILE" in a kdialog.