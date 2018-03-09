# Freebsd

This is going to come handy for anybody who uses FreeBSD 11.x > as their development platform. 


# When installing

[] Make sure you add the user you the group `wheel`

# Upon installation

After installation you will see a console prompt as here. 

[UI]()

# Gnome3

Install Gnome 3 lite. 

```
$ su

$ pkg install gnome3-lite

```

Then follow the instructions here 

[FreeBSD X11](https://www.freebsd.org/doc/handbook/x11-wm.html)


## How to do pkg install ?

https://asciinema.org/a/gby5ujfkX9dT13cSW1fkCnNcS

## XOrg

Include the *i915kms* for the UI to come up. There is no `xorg.conf`, the UI automatically loads.

```

kld_list="i915kms"

```

# Sudo

```
su

pkg install sudo

```

Add the user to sudoer file

# Bash

If you come from linux land, then you will have used bash scripts.

Now that we have installed `sudo`, lets use them.

```

sudo pkg install bash

chsh -s /usr/local/bin/bash

shutdown -r now

```

The shell refreshed after doing a reboot.

# Make in linux is `gmake` here.

The `Make` that comes in freebsd is [Berkely Make](https://www.freebsd.org/doc/en/books/developers-handbook/tools-make.html)

But you can install and setup an *alias* **make** in the `.bashrc`

```

pkg install gmake

```


# Rust

This is pretty easy to [install](https://www.rust-lang.org/en-US/install.html) 


```
curl https://sh.rustup.rs -sSf | sh

rustup component add rustfmt-preview


```

It didn't pull some of the `LIB` like `SODIUM` when compiling.

So add this in your *.bashrc* file

```
export SODIUM_LIB_DIR=/usr/local/lib

```

# OCaml 4.06.1

This is pretty easy but will become difficult when `opam 2.0` is released, since it needs a better version of OCaml to perform the `switch`.  The OCaml packaged in FreeBSD is 

`4.02.3` 

```

sudo pkg install ocaml-opam

opam init

opam switch 4.06.1

```

[]()

# Nodejs

This is pretty easy, but you won't be able to use the latest and greatest.

You can compile from source.

```
# Install node 9.3 
pkg install node 

```

# Ruby

This isn't as sweet as imagined pretty easy but will become difficult when `opam 2.0` is released. 

Install RVM
```
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB


\curl -sSL https://get.rvm.io | bash -s stable

```

Install Ruby

```

rvm install ruby

```

Install bundler

```

gem install bundler

```

Install native packages 

```

sudo pkg install pkgconfig cmake libgit2

```

# Git

```
sudo pkg install git

```

# PostgreSQL 10.x

FreeBSD has the latest packaged.

```

sudo pkg install postgresql10-server-10.3 postgresql10-client-10.3 


```

# Asciinema

```

pkg install asciinema

```

# Editors 

With modern editors picking up, this has been a major hassle for folks to move. 


## VSCode

The editor support is picky. 

If you have the time the compile [vscode` from source](https://gist.github.com/prash-wghats/89be1ee069d2acf23c289e9c606616e1) 

# Sublime Text

Unfortunately this is commercial software. But supports well.

# Atom Xray - not ready yet

We need to keep a tab on this project [https://github.com/atom/xray](https://github.com/atom/xray)

# C9 IDE - using containers

This is a nodejs project (C9 IDE)[https://github.com/c9/core]

# Gnome Builder

Supports *C/C++, Python, Rust* - Yay. But not `OCaml, JS, Ruby`. 


```

pkg install gnome-builder


```

# Browser

No vivaldi or brave

```
sudo pkg install chromium

``

# Picture viewer

```

sudo pkg install viewnior

```

# The configuration files

[/etc/rc.conf]()
[~/.bashrc]()
[~/.profile]()
[~/.gemrc]()
[~/.rvmrc]()
[All File]()

