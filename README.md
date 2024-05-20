# PZmodupdaterScript
A simple Expect script to automate dedicated Project Zomboid server mods. 
After fighting with getting my dedicated server updated automatically while running as a service,
I worked up an Expect script to take care of it for me. This allows the server to run as intended,
performs clean shutdowns and restarts, and avoids having to set up a systemd service that's kinda
wonky at best. I've attempted to provide thorough comments in line with the script. Testing was done
on a system running Ubuntu server 24.04 LTS.

Automated checks are made whenever the dedicated server saves. Save frequeny can be set in your
[servername].ini file. The script allows for user terminal input except during the restart phase. It
was written with the assumption that the server was set up following the guide at
https://pzwiki.net/wiki/Dedicated_server, but should be easily adaptable to different configurations.
This is my first foray into expect scripting, so there was quite a bit of trial and error.
Hope you find it useful!

You will need to install expect before this will run. This is accomplished in Ubuntu with the following command:

sudo apt install expect

The script is intended to be run by the pzuser account that was created if you followed the wiki.
The prompts on line 43 and 64 will need to be edited to match your servers info using your preferred text editor.
The format is "*[username]@[hostname]:*"
Once this is done, place the script into the /opt/pzserver directory and run:

expect /opt/pzserver/PZmodupdater.exp

The script will send the start server command after a 10 second delay. If it does not start, double check the
edits made to the script for the shell prompt. I forgot to change the hostname the first time I ported it to
another machine.
