## USER
How do I concatenate 2 mp4 videos without re-encoding them on linux?

## ASSISTANT
You can use the command-line tool `ffmpeg` to concatenate two or more mp4 videos without re-encoding them. 

Here is an example command that concatenates two videos, "video1.mp4" and "video2.mp4", and saves the result as "output.mp4":

```
ffmpeg -f concat -i list.txt -c copy output.mp4
```

list.txt is a text file with following contents
```
file video1.mp4
file video2.mp4
```

This command uses the `-f concat` flag to specify that the input is a list of files, and the `-i` flag to specify the location of the list file, and `-c copy` flag to copy the input codec to output file.

You can add more videos to the list.txt file and it will concatenate them together.
