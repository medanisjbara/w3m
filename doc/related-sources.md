This file contains a list of sources to anything that might be useful in this invertigation. Any source that has the potential of being useful will be mentioned here.
Unfortunately, most of the web only contains repeating instructions on "HOW DO I INSTALL IT AND BROWSE THE WEB" so those won't be mentioned here. What will be mentioned here is any source that contains information that can be helpful in understanding how this project works (dependencies, implementations .. etc)

## The new documentaion project.
This is what we're currently working on.
Comming soon.

## Currently Available online Documentation
* [W3M homepage](http://w3m.sourceforge.net/)
* [man page](https://www.mankier.com/1/w3m)
* [Wikipedia page](https://en.wikipedia.org/wiki/W3m)
* [CLI Usage message](#usage)
* [BLFS Chapter 18](https://www.linuxfromscratch.org/blfs/view/8.2/basicnet/w3m.html)

## Users tips and tricks.
* http://physino.xyz/learning/w3m/
* https://linuxconsole.net/www.html
* http://w3m.rocks/howto/

## Other related sources that might be useful
* [Subreddit](reddit.com/r/w3m)
* [Mailing list archive](https://www.mail-archive.com/w3m-dev-en@sic.med.tohoku.ac.jp/)
* [Debian package page](https://packages.debian.org/sid/w3m)
* [Gentoo package page](https://packages.gentoo.org/packages/www-client/w3m)
* [Security Vulnerability list](https://www.cvedetails.com/vulnerability-list/vendor_id-912/product_id-1573/W3M-W3M.html) (Might be relevant in identifying some of the code functionality)

## Relavent related projects
* [emacs-w3m](https://emacs-w3m.github.io/)
* [w3mme](http://pub.ks-and-ks.ne.jp/prog/w3mmee/)
* [w3l](https://git.sr.ht/~vdupras/w3l) W3m with way less (potentially the most helpful)

## CLI Usage message
Although this might not seem useful, But reading the help gives you an entry point to look at the code and see what it's doing with each flag and have a feeling of what the functions in the code do.
On my arch linux installation
```bash
$ w3m -h
```
gives

>3m version w3m/0.5.3+git20210102, options lang=en,m17n,image,color,ansi-color,mouse,gpm,menu,cookie,ssl,ssl-verify,external-uri-loader,nntp,gopher,ipv6,alarm,mark  
usage: w3m [options] [URL or filename]  
options:  
    -t tab           set tab width  
    -r               ignore backspace effect  
    -l line          # of preserved line (default 10000)  
    -I charset       document charset  
    -O charset       display/output charset  
    -B               load bookmark  
    -bookmark file   specify bookmark file  
    -T type          specify content-type  
    -m               internet message mode  
    -v               visual startup mode  
    -M               monochrome display  
    -N               open URL of command line on each new tab  
    -F               automatically render frames  
    -cols width      specify column width (used with -dump)  
    -ppc count       specify the number of pixels per character (4.0...32.0)  
    -ppl count       specify the number of pixels per line (4.0...64.0)  
    -dump            dump formatted page into stdout  
    -dump_head       dump response of HEAD request into stdout  
    -dump_source     dump page source into stdout  
    -dump_both       dump HEAD and source into stdout  
    -dump_extra      dump HEAD, source, and extra information into stdout  
    -post file       use POST method with file content  
    -header string   insert string as a header  
    +<num>           goto <num> line  
    -num             show line number  
    -no-proxy        don't use proxy  
    -4               IPv4 only (-o dns_order=4)  
    -6               IPv6 only (-o dns_order=6)  
    -no-mouse        don't use mouse  
    -cookie          use cookie (-no-cookie: don't use cookie)  
    -graph           use DEC special graphics for border of table and menu  
    -no-graph        use ASCII character for border of table and menu  
    -s               squeeze multiple blank lines  
    -W               toggle search wrap mode  
    -X               don't use termcap init/deinit  
    -title[=TERM]    set buffer name to terminal title string  
    -o opt=value     assign value to config option  
    -show-option     print all config options  
    -config file     specify config file  
    -help            print this usage message  
    -version         print w3m version  
    -reqlog          write request logfile  
    -debug           DO NOT USE
