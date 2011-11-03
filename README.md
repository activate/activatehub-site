# ActivateHub Landing Site

## One-time Host Setup

### Ruby

Install rvm 

    sudo bash < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer )

Logout, log back in to load rvm into session

    ctrl^D

Find out build requirements

    rvm requirements

Install listed build requirements

    sudo apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion

Install MRI 1.8 globally

-i makes a login shell so rvm works

    sudo -i rvm install 1.8.7

Wait awhile

Get a root login shell

    sudo su -l
    # root@host >

### Frank

    rvm use 1.8.7
    gem install frank
    logout
    
### LESS

    sudo apt-add-repository ppa:chris-lea/node.js
    sudo apt-get update
    sudo apt-get install nodejs


## Per-Working Copy Setup

Clone the repo

    git clone git@github.com:activate/activatehub-site.git
    cd cloudfeet-site

Accept local .rvmrc when prompted. Yes, rvm aliases cd.

    frank server

## Tips for working over SSH

### Run a GNU Screen session:

    screen -AD # create new or attach to existing session, disconnecting existing connections

Once inside screen:

  * ctrl-A C create new window
  * ctrl-A N/P switch windows
  * ctrl-A D detach session (leaving it running)

### Tunnel a port



    ssh test.cloudfeet.com -L 13601:localhost:3601
    cd cloudfeet-site
    frank server # runs on 0.0.0.0:3601, but external ports may be blocked by firewall

Point browser to localhost:13601, and you will be forwarded via ssh to localhost:3601 on the server (for the duration of SSH session).

## Other sources of help

The site is built using the following open source components, which each have their own documentation:

 * [Frank](https://github.com/blahed/frank)
 * [Bootstrap](http://twitter.github.com/bootstrap/)

HTML is generated from layouts and pages written in [HAML](http://haml-lang.com/). CSS is generated from [LESS](http://lesscss.org/).

The source code is managed using git. The commands you will need to be familiar with are:

    git status
    git add [PATHS ...] # to stage files
    git commit -m "commit message"
    git pull # get changes from origin, always pull before push
    git push # push changes to origin
    git reset [PATHS ...] # to unstage if you've mistakenly staged something

Here are two excellent resources for using git:

  * http://progit.org/book/
  * http://book.git-scm.com/
