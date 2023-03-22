## USER
On linux, how can I use a terminal command to add an alias to the bashrc file?

## ASSISTANT
You can use the `echo` command to add an alias to your `~/.bashrc` file. For example, to add an alias called `ll` that runs the command `ls -la`, you would use the following command:

```
echo "alias ll='ls -la'" >> ~/.bashrc
```

This will append the string `alias ll='ls -la'` to the end of your `~/.bashrc` file.

After you've added the alias to your `~/.bashrc` file, you'll need to reload the file for the changes to take effect. You can do this by running the following command:

```
source ~/.bashrc
```

You can also use `. ~/.bashrc` instead of `source ~/.bashrc`

Alternatively, you can also use `alias` command  to create the alias without modifying .bashrc file.
```
alias ll='ls -la'
```
But this way the alias will be lost after the terminal closes.

Please note that this way of adding alias will only work for the current shell session and if you open a new terminal session the alias will not be available.
