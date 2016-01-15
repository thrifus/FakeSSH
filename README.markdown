[Click me to see edits](#edits)
# FakeSSH

FakeSSH is an SSH server which denies all login requests sent its way. It's the result of literally minutes of work.

Move your real SSH server to a different port, then run the FakeSSH server.

## Why?

In a sense, FakeSSH is based on the idea that security through obscurity is kind of like adding a single bit to your security, the value of which is widely known. It might actually prevent a targeted attack by an unskilled attacker.

Mostly, though, I just like the idea that someone is wasting time trying to log into a server which will literally never let them in.

## Requirements

* python
* paramiko

# Use

1. Create an RSA key using `ssh_keygen`. Save it to data/rsa.
1. Copy data/config.sample.json to data/config.json
1. Edit if desired.
1. Run `server.py` with python.

If you're on Ubuntu, you could create an upstart script at `/etc/init/fakessh.conf`:

    # fakessh
    description "A fake SSH server"
    author "Tyler Menezes <tylermenezes@gmail.com>"
    start on runlevel [2345]
    stop on runlevel [016]
    respawn
    exec python /opt/fakessh/server.py

## Graphing

If you enable logging, you can run `python stats.py` to get statistics about login attempts. `--today` will get you the count today, and `--hist` will produce a graph of the last week. (You can use them both together.)

<div id="edits">
# Edited by [thrifus](http://thrifus.co/)
* Why did I edit this?
    * I wanted to make it a little easier to launch
    * I wanted to be able to background it and then kill it without killing all Python processes
* How to install the files?
    * I recommend placing the FakeSSH folder in your Applications folder (if on OS X, default path is set to /Applications/FakeSSH/), otherwise you'll need to edit `FSSH` file before linking it
    * sudo ln -s /path/to/FSSH /usr/bin/FSSH
    * sudo ln -s /path/to/KFSSH /usr/bin/KFSSH
</div>
