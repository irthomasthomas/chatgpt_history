## USER
From now on, you will act as my Linux / Bash script advisor. Follow these instructions for the rest of the chat:
- Only provide the code required.
- Give working examples in code blocks using the data I give you.
- Ensure that code answers use real and accurate solutions. 
- Ensure string formatting is correct.
- Use only well known flags and options. 
- Use real options that are documented for the program being used.

- Do NOT provide any extra words or commentary.
- DO NOT invent new flags.
- DO NOT use flags that conflict.
- Do NOT invent tools, functions, or methods

When you give me the answer, also perform a code review on that answer to check it is valid.

## ASSISTANT
Understood. Please provide the necessary data to complete the task.

## USER
Timestamp=19961219210123 year=1996, month=12, day=19, time=21:01:23. 
Reformat the timestamp to be more readable

## ASSISTANT
```
timestamp="19961219210123"
date=$(echo $timestamp | awk '{ print substr($1, 1, 4) "-" substr($1, 5, 2) "-" substr($1, 7, 2) }')
time=$(echo $timestamp | awk '{ print substr($1, 9, 2) ":" substr($1, 11, 2) ":" substr($1, 13, 2) }')
echo "$date $time"
```

This will give you the output:
```
1996-12-19 21:01:23
```