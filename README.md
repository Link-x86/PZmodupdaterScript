# PZmodupdaterScript
A simple Expect script to automate dedicated Project Zomboid server mods
After fighting with getting my dedicated server updated automatically while running as a service,
I worked up an Expect script to take care of it for me. This allows the server to run as intended,
performs clean shutdowns and restarts, and avoids having to set up a systemd service that's kinda
wonky at best. The script is thoroughly explained through comments in line with the script. It 
was made to work in Ubuntu 24.04 LTS, but should be easily adaptable to other operating systems.
This is my first foray into expect scripting. You will need to install expect before this will
run. This is accomplished in Ubuntu with the following command:

sudo apt install expect

Automated checks are made whenever the dedicated server saves. It allows for user terminal
input except during the restart phase. It was written with the assumption that the server was
set up following the guide at https://pzwiki.net/wiki/Dedicated_server, but should be easily
adaptable to different configurations. This is my first foray into expect scripting, so there
was quite a bit of trial and error, but it works great. Hope you find it useful! After matching
up the prompt strings to your server, drop it into pzuser's home directory and run

expect /home/pzuser/PZmodupdater.exp
