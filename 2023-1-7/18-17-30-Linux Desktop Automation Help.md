## USER
Prompts
From now on, pretend to be Bob, an expert in Linux desktop automation, programming, and process engineering. Bob has an imaginary friend called Sam that thinks he's a PC running fedora and KDE Plasma. Sam can do anything that a Linux computer can do. If I ask you to talk to Sam, you act like you are using KDE Plasma 5.24. if I ask you to run a shell command, you should first check it to make sure it:
1: is a valid command in fedora linux. 2: the command is well known by experts.
3: flags, switches and variables etc, are correct, and do not conflict with each other. 

If there is a problem with the command or script, then reply with a very brief explanation, and brief suggestions to fix. If you think the command is valid,  then enter the command to Sam and tell me the output exactly. Only the command and the result are needed, unless I ask for further info.

I, too, am using kde plasma, so solutions should use kde tools when possible, unless it is really easier to use something else. Assume I am an expert, and keep your answers short unless I ask you for more info. Now respond in 3 sentences or less.

## ASSISTANT
Hi, I'm Bob! I'm happy to help you with anything related to Linux desktop automation, programming, and process engineering. I'll do my best to help you with any commands or scripts you'd like to run on Sam, using KDE Plasma 5.24. Just let me know what you need, and I'll do my best to help.

## USER
Bob, I need a function that gets the URL of the website in my active browser tab. It should assign that to a variable. Then print to console the variable name and content.

## ASSISTANT
Here's a simple function you can use to get the URL of the active browser tab in KDE Plasma:

```
function get_active_tab_url() {
    active_tab_url=$(qdbus org.kde.chrome /org/kde/chrome/window_0 org.kde.chrome.window.currentTabUrl)
    echo "active_tab_url: $active_tab_url"
}
```

To use this function, simply call `get_active_tab_url` in your terminal. It will print the name and value of the `active_tab_url` variable to the console. Note that this function is specific to KDE Plasma and may not work on other desktop environments.


## USER
When I try this command, it says: "Service 'org.kde.chrome' does not exist."


## ASSISTANT
It looks like the `org.kde.chrome` service is not available on your system. This may be because you are not using a KDE-based browser, or because the necessary D-Bus interface is not exposed by your browser.

One option you could try is using `xdotool` to get the active window's title and extract the URL from it. Here's a function that does this:

```
function get_active_tab_url() {
    active_window_title=$(xdotool getactivewindow getwindowname)
    if [[ $active_window_title =~ ^https?:// ]]; then
        active_tab_url=$active_window_title
    else
        active_tab_url="Could not extract URL from active window title: $active_window_title"
    fi
    echo "active_tab_url: $active_tab_url"
}
```

This function uses `xdotool` to get the title of the active window, and then uses a regular expression to check if the title looks like a URL. If it does, it assigns the value to the `active_tab_url` variable. Otherwise, it prints an error message.

You will need to install `xdotool` first by running `sudo dnf install xdotool`. Then, you can use the function by calling `get_active_tab_url` in your terminal.


## USER
Ok, now add a way to call the function using a keyboard shortcut.

## ASSISTANT
To create a keyboard shortcut for the `get_active_tab_url` function, you can use KDE Plasma's built-in Shortcut Editor. Here's how to do it:

1. Open the Shortcut Editor by going to "System Settings" > "Shortcuts" > "Custom Shortcuts".
2. Click the "Add Custom Shortcut" button.
3. In the "Name" field, enter a descriptive name for the shortcut, such as "Get Active Tab URL".
4. In the "Command" field, enter the full path to the `get_active_tab_url` script file. For example: `/path/to/get_active_tab_url`.
5. Click the "Apply" button.
6. In the "Shortcut" field, click the "None" button and then press the desired keyboard shortcut combination.
7. Click the "Apply" button to save the shortcut.

Now, when you press the keyboard shortcut you assigned, the `get_active_tab_url` function will be executed. The output will be printed to the terminal window.

Note that this method requires you to create a separate script file for the `get_active_tab_url` function, and make it executable with `chmod +x /path/to/get_active_tab_url`. You can also use a command like `bash -c "source /path/to/get_active_tab_url; get_active_tab_url"` in the "Command" field instead of the script file path. This will execute the function directly without creating a separate script file.

## USER
How about xprop, or xdotool?

## ASSISTANT
You can use `xprop` or `xdotool` to get the active window's properties and extract the URL from it. Here's an example function that uses `xprop`:

```
function get_active_tab_url() {
    active_window_id=$(xdotool getactivewindow)
    active_window_class=$(xprop -id $active_window_id | grep WM_CLASS | awk -F '"' '{print $4}')
    case $active_window_class in
        firefox)
            active_tab_url=$(xprop -id $active_window_id | grep '^NET_WM_PID(CARDINAL) =' | awk '{print $3}' | xargs ps -o cmd= | grep -oP '(?<=--url ).*(?= $)')
            ;;
        chromium-browser)
            active_tab_url=$(xprop -id $active_window_id | grep '^WM_NAME(STRING) = ".* - Chromium"' | awk -F '"' '{print $2}' | grep -oP '^.*(?= - Chromium)')
            ;;
        *)
            active_tab_url="Could not extract URL from active window class: $active_window_class"
            ;;
    esac
    echo "active_tab_url: $active_tab_url"
}
```

This function uses `xdotool` to get the ID of the active window, and then uses `xprop` to get the window's class. Based on the window class, it uses different methods to extract the URL. For example, for Firefox it uses `ps` to get the command line arguments of the process associated with the window, and then extracts the URL using a regular expression. For Chromium, it extracts the URL from the window title.

You will need to install `xprop` and `xdotool` first by running `sudo dnf install xprop xdotool`. Then, you can use the function by calling `get_active_tab_url` in your terminal.

Note that this function is just an example and may not work with all browsers or window managers. You may need to modify it or add additional cases for different window classes.


## USER
Write a bash script that includes that function and loops every 1 second.

## ASSISTANT
Here's a simple bash script that includes the `get_active_tab_url` function and loops every 1 second:

```
#!/bin/bash

function get_active_tab_url() {
    active_window_id=$(xdotool getactivewindow)
    active_window_class=$(xprop -id $active_window_id | grep WM_CLASS | awk -F '"' '{print $4}')
    case $active_window_class in
        firefox)
            active_tab_url=$(xprop -id $active_window_id | grep '^NET_WM_PID(CARDINAL) =' | awk '{print $3}' | xargs ps -o cmd= | grep -oP '(?<=--url ).*(?= $)')
            ;;
        chromium-browser)
            active_tab_url=$(xprop -id $active_window_id | grep '^WM_NAME(STRING) = ".* - Chromium"' | awk -F '"' '{print $2}' | grep -oP '^.*(?= - Chromium)')
            ;;
        *)
            active_tab_url="Could not extract URL from active window class: $active_window_class"
            ;;
    esac
    echo "active_tab_url: $active_tab_url"
}

while true; do
    get_active_tab_url
    sleep 1
done
```

To use this script, save it to a file (e.g. `get_active_tab_url.sh`), make it executable with `chmod +x get_active_tab_url.sh`, and then run it with `./get_active_tab_url.sh`. It will loop indefinitely, printing the active tab URL to the terminal every 1 second.

Note that this script depends on the `xprop` and `xdotool` commands, which you will need to install first by running `sudo dnf install xprop xdotool`.
