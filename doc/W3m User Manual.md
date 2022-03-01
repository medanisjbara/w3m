# W3m User Manual

**This document is a work in progress.**

## Content
1. [Introduction](#introduction)
2. [Motives](#motives)
3. [Installation](#installation)
4. [Basic usage](#basic-usage)
5. [Tips and tricks](#tips-and-tricks)
6. [Troubleshooting](#troubleshooting)
7. [Useful Sources](#useful-sources)

## Introduction
This document is not the official user manual for w3m. Instead, it is the result of collected information over the internet and from the source code. This is the case for now, until the maintainers of w3m give this document a look.
## Motives
*This section will be removed since it's not relevant*  
On the [Old README file](/doc/doc-old/doc-en/README) they pointed out in the *Current problems are* section that their online manuals are poor. Personally w3m saved me a couple of times when I had limited bandwidth or I didn't have enough money to by mobile data. And when I started reading the source code and looking online, there were a couple of things that I wished I knew when I needed them. That's why I'm creating this document.
## Installation
### Via the package manager
Since this fork isn't official, here we'll be listing the ways you can install the official [w3m](https://github.com/tats/w3m) repository.  
The official w3m is available for most distributions via the package manager. a couple of examples are listed below
#### Debian
```
sudo apt install w3m
```
#### Arch
```
sudo pacman -S w3m
```
### Compile from source
If you want to compile from source you should first install the [dependencies](/doc/README.md#dependencies). along with `make`
```
git clone https://github.com/tats/w3m
cd w3m
./configure
sudo make
```


## Basic usage
*This section needs more information*  
w3m is a pager and an HTTP browser, meaning it can open files and URLs.
```
usage: w3m [options] [URL or filename]
```
to get general information on how to use w3m, read the man page `man w3m` or the output of `w3m --help`.
You can also have a look at the [old documentation](/doc/doc-old/MANUAL.html) for more information

## Tips and tricks
### Terminal emulators
*This section needs more information*  
According to [this thread](https://www.reddit.com/r/w3m/comments/pwwizm/which_terminal_emulator_are_you_using_with_w3m/) w3m image rendering is the most stable on Xterm, And [st](https://wiki.archlinux.org/title/St) (Only in the case of applying a [patch](https://st.suckless.org/patches/w3m/)
### Open homepage when no arguments are supplied
In case of no arguments, w3m will look for the `HTTP_HOME` environment variable, If `HTTP_HOME` is not set, w3m will display the help message.
In some cases, It could be helpful to add this to your `~/.bashrc`
```
export HTTP_HOME=google.com
```
So that w3m will automatically launch to your search engine if no arguments were given.

### Combining with mpv and watching youtube.
This is one of the best tricks you can use with w3m it order to make the browsing experience richer.  
Start first by making a `keymap` file in `~/.w3m` if you haven't already. And write the following content to it.

```
keymap <key> EXTERN_LINK "(mpv --player-operation-mode=pseudo-gui --no-terminal %s &)"
```
Where *<key>* represents the key combination of your choice. You can add as many lines like these as you like.  
And combined with the `ytdl` implimentation of mpv, you can add special options to mpv to be able to customize the video player according to your needs.
#### Example:
```
# use "mn" key combination to play sound only
keymap mn EXTERN_LINK "(mpv --player-operation-mode=pseudo-gui --no-terminal --ytdl-raw-options='format=bestaudio' -ytdl %s &)"

# Use "ml" key combination to play with the most bandwidth economisation possible.
keymap ml EXTERN_LINK "(mpv --player-operation-mode=pseudo-gui --no-terminal --ytdl-raw-options='format=278+249' -ytdl %s &)"

...
```

You can add as many keymaps as you need, Not only for external video players like mpv. But also to other types of external interpretations of a link. See the [old manual](/doc/doc-old/MANUAL.html) for more details.

## Troubleshooting
### GC Memory allocation Warning
This error occurs mainly on termux on android but can occure on some other low end devices.
If you see an error that looks like this:
```
GC Warning: Repeated allocation of very large block (appr. size 110592):
	May lead to memory leak and poor performance
```
add this to your `~/.bashrc`
```
export GC_LARGE_ALLOC_WARN_INTERVAL=30000
```
## Useful sources
* [The old documentation](/doc/doc-old/MANUAL.html)
* [The old FAQ](/doc/doc-old/FAQ.html)
* [Subreddit](reddit.com/r/w3m)
* [W3M Rocks](http://w3m.rocks/) 
