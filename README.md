## What is this fork for ?

### W3M
from the man page
> w3m - a text based web browser and pager

This is a fork of the w3m text based browser/pager that aims to achieve a couple of things listed below.

### In short term
This is an attempt to document the w3m pager/browser and make the codebase easier to understand and contribute to. This fork will only add to the [doc](/doc) folder and add a couple of comments and reformats to the code for now, But as time passes It will contain more additional development documentation and hopefully when the time comes it will have some actual code changes.
### In long term
This fork's purpose is to develop an API to w3m. That will help the w3m browser/pager be more integradable with other software.
### Far far future plans
We're eventually aiming for a gtk frontend to w3m (It is a long long term project). That will put the API being developed in use.

## Why
Becase everyone loves how amazing software becomes when there is more contribution to it.
* Having an understanding and a developer documentation of the codebase is essential for developers and contributors to help the project grow and get more mature.
* Working on the extensibility of the project will also help growing the project to the better with each update.
* What better way to support a project except using it in another project ?
Having a developer documentation to make the codebase understandable will save a lot of time for developers trying to make use of this project. FOSS is about the ability to do what you want with any software so that everyone can build upon the work of others, It is also about collective work of people who wants to contribute to a project, etc ..
But when there is poor documentation to developers, the objective becomes hard to achieve to anyone new who haven't worked on the codebase before.

## Dependencies
* gc
* gpm
* ncurses
* openssl
* imlib2 (optional) - for graphics support
* git (make)
* imlib2 (make)

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
If you want to compile from source you should first install the [dependencies](#dependencies). along with `make`
```
git clone https://github.com/tats/w3m
cd w3m
./configure
sudo make
```
## Documentation
Since this project is (for now) all about making documentation. If you think you can help, please have a look at the [W3m Developper Manual](doc/doc-dev/W3m Developper Manual.md) since it is the work in progress for now to understand and document the source code and how it works.

## Tasks

### Done

* Split the documentation from the compilation assets related to doc

### Todo

* Document the main function and it's content so that a reader can understand what it's doing

## Notes
* This project is still too small to even be even brought up to discussion with the developers of w3m. After enough future commits, We're hoping this project will become presentable so that new questions on what or why things do the way they do will be okay to ask. In the mean time, If you know anything about how this project works, or if you're willing to give some time and effort reading pieces of code and trying to make sense of it and write it down for us. Please contribute with a pull request containing whatever changes that suites you.

* The actual README has been moved to README.old

## DISCLAMER
This is no where close to being professional work (for now).

## To-Do
* Add Installation instructions.
* Add a short tutorial.
