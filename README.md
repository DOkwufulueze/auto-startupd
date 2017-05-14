- Purpose: Open new tabs in terminal and excute custom commands automatically on the background that remain alive even after the terminal is exited. Send command output to either nohup.out or the /dev/null black hole.
- Author: Okwufulueze Emeka Daniel
- Date: 19/03/2017


# Install xdotool
```
  sudo apt-get install xdotool
```

# Clone this repo or start from scratch:
You can simply clone this repo and modify as necessary or you can start from scratch and create your own shell script, say background-auto-startup like I have in this repo.
```
  touch background-auto-startup
  sudo chmod +x background-auto-startup
```

# If you started from scratch with your file named 'background-auto-startup' for instance, place the script below in background-auto-startup.
```
#!/bin/bash
# The SHELL_COMMANDS variable below is an array of commands you want to execute on new tabs. I have written out some for example. Remember to separate the array values with spaces

# Make the processes background jobs with either nohup or the disown parenthesis notation in order to continue execution even after the terminal is exited.


# To send output to nohup.out. Ensure you precede each command with 'nohup ', and end them with ' &' for any command you need to survive terminal exit. For example: nohup npm run dev &
# SHELL_COMMANDS=('cdyanpals; nohup npm run dev &' 'cdwscore; nohup sh serverd.sh &' 'cdwscore; nohup php worker.php &' 'nohup mysql-workbench &');


# To send output to the /dev/null black hole. Ensure you place each command in parenthesis and end them with ' &>/dev/null &' for any command you need to survive terminal exit. For example: (npm run dev &>/dev/null &)
SHELL_COMMANDS=('cdyanpals; (npm run dev &>/dev/null &)' 'cdwscore; (sh serverd.sh &>/dev/null &)' 'cdwscore; (php worker.php &>/dev/null &)' '(mysql-workbench &>/dev/null &)');


# Loop through the array of commands and execute each one on a new tab
for ((i = 0; i < ${#SHELL_COMMANDS[@]}; i++)); do
  SHELL_COMMAND=${SHELL_COMMANDS[$i]};
  xdotool key ctrl+shift+t;
  sleep 1;
  xdotool type --delay 1 --clearmodifiers "${SHELL_COMMAND}";
  xdotool key Return;
done
```

# If you didn't start from scratch [meaning you cloned this repo], simply proceed to the next step

# Execute the script from its parent directory
On your terminal, in the directory containing background-auto-startup, simply execute the script by:
```
  ./background-auto-startup
```

# Execute the script from any directory
You can also add background-auto-startup to your PATH so you can just execute it from anywhere in your terminal by entering the following:
```
  export PATH=$PATH:~/directory-name
  # where directory-name is the name of the directory containing background-auto-startup
```
After which you can execute background-auto-startup by simply typing the command below on your terminal:
```
  background-auto-startup
```

Now, even after you close your terminal, the commands in `background-auto-startup` will keep running.
