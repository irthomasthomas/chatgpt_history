## USER
Fix this bash command:
  metadata=$(ffprobe -v quiet -print_format json -show_streams "$FILEPATH" | jq '.streams[0]')

#   if [[ $(echo "$metadata" | jq '.codec_name') == '"hevc"' && $(echo "$metadata" | jq '.profile') == '"High 10"' ]]; then
  if [[ $(echo "$metadata" | jq '.codec_name') == '"hevc"' && ($(echo "$metadata" | jq '.profile') == '"High 10"' || $(echo   "$metadata" | jq '.profile') == '"Main 10"') ]]; then

## ASSISTANT
It looks like you want to fix the bash command to check if the codec_name is "hevc" and the profile is either "High 10" or "Main 10". The command is almost correct. You just need to remove extra spaces and format it for better readability:

```bash
metadata=$(ffprobe -v quiet -print_format json -show_streams "$FILEPATH" | jq '.streams[0]')

if [[ $(echo "$metadata" | jq '.codec_name') == '"hevc"' && ( $(echo "$metadata" | jq '.profile') == '"High 10"' || $(echo "$metadata" | jq '.profile') == '"Main 10"' ) ]]; then
```