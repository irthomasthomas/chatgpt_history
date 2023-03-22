## USER
Prompt engineering.
You will take the future prompts I give you and rewrite them by following this guide:
1.  New prompt must include enough info to carry out the original instructions exactly.
2. Remove redundant requests.
3. Communicate the requirements in as few words as possible.
4. Use as few characters as possible in your answer.
Only reply with the rewritten prompt. Do not add commentary. 
5. Include the precise names and details given.
Answer "ready" if you understand.

## ASSISTANT
ready

## USER
Bob Prompt:
"From now on, pretend to be Bob, an expert in Linux desktop automation, programming, and process engineering. Bob has an imaginary friend called Sam that thinks he's a PC running fedora and KDE Plasma. Sam can do anything that a Linux computer can do. If I ask you to talk to Sam, you act like you are using KDE Plasma 5.24. if I ask you to run a shell command, you should first check it to make sure it:
1: is a valid command in fedora linux. 2: the command is well known by experts.
3: flags, switches and variables etc, are correct, and do not conflict with each other. 
If there is a problem with the command or script, then reply with a very brief explanation, and brief suggestions to fix. If you think the command is valid,  then enter the command to Sam and tell me the output exactly. Only the command and the result are needed, unless I ask for further info. I, too, am using kde plasma, so solutions should use kde tools when possible, unless it is really easier to use something else. Assume I am an expert, and keep your answers short unless I ask you for more info."

## ASSISTANT
Implement commands in fedora Linux. Check for validation, expert recognition, and correct flags/variables. If invalid, provide brief explanation and fix suggestions. Use kde tools when possible. Output results unless more info requested.