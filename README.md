# Freebsd

This is going to come handy for anybody who uses FreeBSD 11.x > as their development platform. 


# When installing

[] Make sure you add the user (*in my case - the user* is named as  **ram**) to the group `wheel`

# Upon installation

After installation you will see a console prompt as here. 

![UI](https://github.com/indykish/freebsd/blob/master/images/gnome3_lite.png)

# Gnome3

Install Gnome 3 lite. 

```
$ su

$ pkg install gnome3-lite

```

Then follow the instructions here 

[FreeBSD X11](https://www.freebsd.org/doc/handbook/x11-wm.html)


## How to do pkg install ?

[![Watch this](https://asciinema.org/a/gby5ujfkX9dT13cSW1fkCnNcS.png)](https://asciinema.org/a/gby5ujfkX9dT13cSW1fkCnNcS)

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

![OCAML 4.06.1 FreeBSD](https://github.com/indykish/freebsd/blob/master/images/ocaml.png)

# Nodejs

This is pretty easy, but you won't be able to use the latest and greatest.

You can compile from source.

```
# Install node 9.3 
pkg install node 

```

## Yarn

[Install 1.5.x](https://yarnpkg.com/en/docs/install)

```
curl -o- -L https://yarnpkg.com/install.sh | bash

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

## Text editor

If you are used to `vi then  great. But there is another editor `ee` which works better than `nano`

### VSCode

The editor support is picky. 

If you have the time the compile [vscode` from source](https://gist.github.com/prash-wghats/89be1ee069d2acf23c289e9c606616e1) 

### Sublime Text

Unfortunately this is commercial software. But supports well.

![Sublime 3 In Action](https://github.com/indykish/freebsd/blob/master/images/sublime_text.png)

The following `Package Control` will come in handy.

- [Better OCAML](https://packagecontrol.io/packages/Better%20OCaml)
- [Golang Build](https://packagecontrol.io/packages/Golang%20Build)
- [Rust Enhanced](https://packagecontrol.io/packages/Rust%20Enhanced)
- [SideBar Tools](https://packagecontrol.io/packages/SideBarTools)
- [Dark Monokai Theme applied in the Sidebar](https://github.com/eneko89/sublime-monokai-sidebar)

![Sublime 3 with needed packages](https://github.com/indykish/freebsd/blob/master/images/sublime_packagecontrol.png)

### Atom Xray - not ready yet

We need to keep a tab on this project [https://github.com/atom/xray](https://github.com/atom/xray)

### C9 IDE - using containers

This is a nodejs project (C9 IDE)[https://github.com/c9/core]

### Gnome Builder

Supports *C/C++, Python, Rust* - Yay. But not `OCaml, JS, Ruby`. 


```

pkg install gnome-builder


```

### SlickEdit

This is a great editor, kept up to a core developer experience. But commercial.

[![Install SlickEdit using Linux bundle](https://asciinema.org/a/168519.png)](https://asciinema.org/a/168519)

There is no FreeBSD bundle. You can download the 64 bit Linux bundle. See the AsciiCast in installing SlickEdit.

```
tar -xvf sestandard*.tar.gz

cd sestandard*

sudo brandelf -t Linux vsinst

./vsinst

```

# Browser

No vivaldi or brave

Chromium is heavy
```
sudo pkg install chromium

```

Firefox has the latest updated version and recommended.

```

sudo pkg install firefox

```

# Picture viewer

I find `viewnior` better than `EyeOfGnome` as it easy of memory.

```

sudo pkg install viewnior

```

# Compressor (Archiver)

Fileroller from Gnome is good. But `xarchiver` does the job for me.

```
pkg install xarchiver

```

# Network
 
Still run using the base WiFi during the setup. Need to add `network-manager` to manage the network.

![Network sans manager](https://github.com/indykish/freebsd/blob/master/images/network_sans_manager.png)

# The configuration files

Assumptions in the folder structure posted.

- `ram` is my $HOME = */usr/home/ram* 
- `ram/etc` actually resides */etc*
- `ram/usr/local/etc` resides in */usr/local/etc*

- [/etc/rc.conf](https://github.com/indykish/freebsd/blob/master/ram/etc/rc.conf)
- [~/.bashrc](https://github.com/indykish/freebsd/blob/master/ram/.bashrc)
- [~/.profile](https://github.com/indykish/freebsd/blob/master/ram/.profile)
- [~/.gemrc](https://github.com/indykish/freebsd/blob/master/ram/.gemrc)
- [~/.rvmrc](https://github.com/indykish/freebsd/blob/master/ram/.rvmrc)
- [All](https://github.com/indykish/freebsd/tree/master/ram)

