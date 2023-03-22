## USER
Write an application in your preferred language, that takes a time parameter like 00:00:00, and returns the timestamp of the next i-frame in an MP4 video. Give me instructions to build, run and verify its correctness on linux.

## ASSISTANT
Here is an example of a Python application that takes a time parameter in the format of "hh:mm:ss" and returns the timestamp of the next I-frame in an MP4 video:

```
import subprocess
import sys

def get_next_iframe(time):
    # Call ffprobe to get the next I-frame after the given time
    try:
        output = subprocess.check_output(['ffprobe', '-skip_frame', 'nokey', '-select_streams', 'v:0', '-show_entries', 'frame=pkt_pts_time', '-of', 'csv=print_section=0', '-i', 'input.mp4', '-ss', time], stderr=subprocess.STDOUT)
    except subprocess.CalledProcessError as e:
        print(e.output)
        sys.exit(1)
    
    # Parse the output to get the timestamp of the next I-frame
    lines = output.decode().strip().split('\n')
    if not lines:
        return None
    return lines[0]

if __name__ == '__main__':
    # Get the time parameter from the command line
    time = sys.argv[1]
    timestamp = get_next_iframe(time)
    if timestamp:
        print(f'The timestamp of the next I-frame is {timestamp}')
    else:
        print('No I-frame found')
```

To build and run the application on Linux:

1. Make sure you have Python installed on your system. You can check the version by running the following command:
```
python3 --version
```
2. If Python is not installed, you can install it by running the following command:
```
sudo apt-get install python3
```
3. Install ffmpeg by running the following command:
```
sudo apt-get install ffmpeg
```
4. Save the Python code to a file named "next_iframe.py".
5. Run the application by passing the time parameter as an argument, like this:
```
python3 next_iframe.py 00:00:00
```

To verify the correctness of the application, you can compare the output with the expected result. For example, if you know that the next I-frame in the video is at 00:00:10, you can verify that the application returns "00:00:10" as the timestamp.