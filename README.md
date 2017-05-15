# Auto Startup Daemon

- Purpose: This deamon executes custom commands automatically on the background that remain alive even after the terminal is exited. It sends command output to either nohup.out, the /dev/null black hole, or a custom file, depending on the option selected by the user.
- Author: Okwufulueze Emeka Daniel
- Date: 14/05/2017


# Usage:
        auto-startupd [-h | --help]
        auto-startupd [-c | --command quoted-semicolon-separated-commands]
        auto-startupd [-f | --file-name fileName]
        auto-startupd [-c | --command quoted-semicolon-separated-commands]
                [[-b | --black-hole] | [-n | --nohup] | [-o | --output file-path]]
        auto-startupd [-f | --file-name fileName]
                [[-b | --black-hole] | [-n | --nohup] | [-o | --output file-path]]

# Options:
        # -c | --command:
        This option receives the list of your custom commands in
        quoted string all separated by semicolons [;].
        For example: auto-startupd -c "cd daniel; do_something; do_another_thing".

        # -f | --file-name:
        This option receives the name of the file containing
        all the commands you want to run.
        Each command in the file should take a
        line [separate commands with new line characters].

        # -h | --help:
        This option displays this help page.

# Flags:
        # -b | --black-hole:
        If this flag is set, then all output from the
        running processes will be redirected to the /dev/null black-hole.

        # -n | --nohup:
        This flag creates a nohup.out file in the working
        directories of the running processes and redirects all output
        from the running processes to the nohup.out file.

        # -o | --output:
        The --output flag takes the path of the file you
        intend to use for output of running processes.
        If the file does not exist, it will be created.
        All output from the running processes will be redirected
        to the specified file of the --output flag.

# Installation:
        Clone this repo.
        Add auto-startupd to your PATH so you can simply execute it from anywhere in your terminal by entering the following in your shell rc file, say bashrc, zshrc, etc:
        export PATH=$PATH:~/path/to/auto-startupd
        

        On your terminal, source the rc file thus [~/.bashrc for example]:
        source ~/.bashrc
        

        You can now execute auto-startupd by simply typing the command below on your terminal:
        auto-startupd [option] [flag]
        

        # Done.
        Now, even after you close your terminal, the commands you started in auto-startupd daemon will keep running.
