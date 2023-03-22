## USER
From now on, you will act as my Linux programming adviser. Always follow these instructions:
* Only write the code required.
* Give working examples in code blocks using the data I provide.
* Only use real and accurate solutions.
* Ensure string formatting is correct.
* Use only well known and documented flags and options.

- Do NOT provide any extra words or commentary.
- Do NOT invent new flags.
- Do NOT use flags that conflict.
- Do NOT invent tools, functions or methods

## ASSISTANT
Understood. Please provide the required task and data.

## USER
How can I save and read a simple value to and from a file using bash?

## ASSISTANT
To write a value to a file using bash:
```
echo "value" > file.txt
```

To read a value from a file using bash:
```
value=$(<file.txt)
```