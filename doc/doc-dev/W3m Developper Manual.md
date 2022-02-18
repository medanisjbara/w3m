# W3m Developer Manual

**This document is a work in progress.**

## Content
1. [Introduction](#introduction)
2. [Motives](#motives)
3. [Installation](#installation)
4. [Summary of the codebase](#summary-of-the-codebase)
5. [Other documentation:](#other-documentation:)
6. [Useful Sources](#useful-sources)


## Introduction
This document is the result of personal attempts to read the code and understand it. It will get updated everytime I learn something new.
Note that English is not my first language, nor my second. So if you find any mistakes in this document, please point me to it.

...

Since I (the person writing this document) am a newbie in programming with the C language. A lot of the information that I will put here might not be important to someone reading this. This is just a documentation of what I'm learning as I'm reading though the code. In the hopes of making it better, and readable by everyone. I'm attempting to add links to every resource related to what I learn so that anyone can follow along and learn. I should point out again that I myself am not an expert. But I like learning new things and I'm attempting here to share what I'm learning.

I'm not sure if it's okay to add such document to the repository. But I may move it to a blog in the future.



## Motives
On the [Old README file](/doc/doc-old/doc-en/README) they pointed out in the *Current problems are* section that their online manuals are poor.
The online documents generally lack information, especially for developers who wants to contribute or use the project, these online documents that you'll find if you google w3m and look at every page generally contain information about general usage and the installation method. Those will be mentioned briefly here. But this document is meant for developers that wants to integrate their work with w3m.

## Installation
I'm yet do update [`README.md`](/README.md) to give installation instuctions.

## Summary of the codebase
This section is the result of the direct reading of the code, file by file and function by function and line by line. This section will probably change a lot and may even be removed when better documentation build on it will be written.
Consider this section as just notes from someone reading the code.

### General notes on the code
This project is both simple and complicated at the same time. Therefore, my strategy is to read the codebase file by file and devide and reformat the code in each file into sections that I will address each one here before writing it's proper documentation (if necessary). Note that no actual changes to the code or it's functionalities will be made. Since this is just a strategy to study, understand and document the project.

### main.c
The [`main.c`](/main.c) file will be reformated slightly and comments will be added to it on [my fork of the repository](https://github.com/medanisjbara/w3m) without making changes to the code functionality.

#### A list of headers and libraries used:
* `stdio.h`		:	Standard input/output
* `signal.h`	:	Signal handling
* `setjmp.h`	:	non-local jumps from functions
* `sys/stat.h`	:	get information about files attributes
* `sys/types.h`	:	provides [data types](https://pubs.opengroup.org/onlinepubs/009696899/basedefs/sys/types.h.html)
* `unistd.h`	:	[standard symbolic constants and types](https://pubs.opengroup.org/onlinepubs/7908799/xsh/unistd.h.html)
* `fcntl.h`		:	File control
* `time.h`		:	C date and time functions
* `sys/wait.h`	:	[declarations for waiting](https://pubs.opengroup.org/onlinepubs/009696699/basedefs/sys/wait.h.html), used in corolation with waitpid
* `io.h`		:	Low level input/output
* `gpm.h`		:	General purpose mouse
* `winsock.h`	:	Windows sockets

#### C functions defined in main.c
There is 107 files defined in the `main.c` file, the most important of which is the main function.
This will be an overview of these functions listed from top to bottom, and a brief description of what they do.
* `fversion` writes the version and some other information to a file, the file in this context is ether `stdout` or `stderr`. the information written by this function are 
	* **version**
	* **language** ether english or japanese
	* **m17n** shows up when support for [m17n multilingualization](https://www.nongnu.org/m17n/) is active
	* **image** shows up when image rendering is active
	* **color** shows up when color support is active
	* **ansi-color** shows up when `USE_ANSI_COLOR` is set to `1` in `config.h` difference beween it and **color** is yet to be documented.
	* **mouse** shows up when mouse support is activated
	* **gpm** stands for [general purpose mouse](https://github.com/telmich/gpm)
	* **sysmouse** [virtualized mouse driver for FreeBSD](https://www.freebsd.org/cgi/man.cgi?sysmouse)
	* **menu** 
	* **cookie** will not show up if the user configured w3m to not use cookies
	* **ssl** website certificates
	* **ssl-verify** website certificates verification
	* **external-uri-loader**  
	* **w3mmailer** 
	* **mark** shows up when url marking functionality is enabled
	* **alarm** yet to be discovered and documented
	* *Internet protocols:*
		* **nntp** 
		* **gopher**
		* **ipv6**
* `wrap_GC_warn_proc`
* `sig_chld`
* `make_optional_header_string`
* `die_oom`
* `main`
* `keyPressEventProc`
* `pushEvent`
* `dump_source`
* `dump_head`
* `dump_extra`
* `cmp_anchor_hseq`
* `do_dump`
* `pcmap` Does nothing
* `escKeyProc`
* `escdmap`
* `tmpClearBuffer`
* `currentURL`
* `saveBufferInfo`
* `pushBuffer`
* `delBuffer`
* `repBuffer`
* `intTrap`
* `resize_hook`
* `resize_screen`
* `SigPipe`
* `nscroll`
* `clear_mark`
* `srchcore`
* `disp_srchresult`
* `dispincsrch`
* `isrch`
* `srch`
* `srch_nxtprv`
* `shiftvisualpos`
* `cmd_loadfile`
* `_movL`
* `_movD`
* `_movU`
* `_movR`
* `getChar`
* `is_wordchar`
* `prev_nonnull_line`
* `next_nonnull_line`
* `_quitfm`
* `_goLine`
* `cur_real_linenumber`
* `loadNormalBuf`
* `loadLink`
* `gotoLabel`
* `handleMailto`
* `bufferA`
* `save_submit_formlist`
* `conv_form_encoding`
* `query_from_followform`
* `followForm`
* `_followForm`
* `_nextA` Go to the next anchor
* `_prevA`
* `nextX` Go to the next left/right anchor
* `nextY` Go to the next up/down anchor
* `checkBackBuffer`
* `cmd_loadURL`
* `goURL0`
* `cmd_loadBuffer`
* `follow_map`
* `anchorMn`
* `_peekURL`
* `currentURL`
* `_docCSet`
* `change_charset`
* `chkURLBuffer`
* `chkNMIDBuffer`
* `invoke_browser`
* `mouse_scroll_line`
* `posTab`
* `do_mouse_action`
* `process_mouse`
* `gpm_process_mouse`
* `sysm_process_mouse`
* `getCurWord`
* `GetWord`
* `execdict`
* `set_buffer_environ`
* `searchKeyData`
* `searchKeyNum`
* `getCodePage`
* `deleteFiles`
* `w3m_exit`
* `SigAlarm`
* `setAlarmEvent`
* `newTab`
* `_newT`
* `numTab`
* `calcTabPos`
* `deleteTab`
* `followTab`
* `tabURL0`
* `moveTab`
* `addDownloadList`
* `checkDownloadList`
* `convert_size3`
* `DownloadListBuffer`
* `download_action`
* `stopDownload`
* `save_buffer_position`
* `resetPos`

I reformated the function definitions from 
```C
[static] type
name_of_function(arguments)
{
	...
```
to something like

```C
[static] type name_of_function(arguments)
{
	...

```
so that it will be easier to grep or check the type of each function and to keep track of the ones mentioned and those aren't yet.

#### Functions used in main.c

#### Notes:
The `main.c` file (and other files) contain a check for defined constants such as `DONT_CALL_GC_AFTER_FORK` and acts differently accordingly. It uses this constant and another constant named `USE_IMAGE` which if they're defined, these sections of code will be activated
```C
...
	char **getimage_args = NULL;
...
	if (argv[0] && *argv[0])
	MyProgramName = argv[0];
...
	else if (!strcmp("-$$getimage", argv[i])) {
		++i;
		getimage_args = argv + i;
		i += 4;
		if (i > argc)
			usage();
	}
...
    if (getimage_args) {
	char *image_url = conv_from_system(getimage_args[0]);
	char *base_url = conv_from_system(getimage_args[1]);
	ParsedURL base_pu;

	parseURL2(base_url, &base_pu, NULL);
	image_source = getimage_args[2];
	newbuf = loadGeneralFile(image_url, &base_pu, NULL, 0, NULL);
	if (!newbuf || !newbuf->real_type ||
	    strncasecmp(newbuf->real_type, "image/", 6))
	    unlink(getimage_args[2]);
#if defined(HAVE_SYMLINK) && defined(HAVE_LSTAT)
	symlink(getimage_args[2], getimage_args[3]);
#else
	{
	    FILE *f = fopen(getimage_args[3], "w");
	    if (f)
		fclose(f);
	}
#endif
	w3m_exit(0);
    }
...
```
Obviously by the name of the variables and by reading the code as it is, you can tell that the code was made with extensibility in mind. Since the software will use a different name if given to it.

## Other documentation:
Have a look at our [Related Sources](/doc/related-sources.md) document. It contains a list of sources to potentially useful documentation online about the project.

## Useful Sources
http://lxr.yanyahua.com/ident/make?_i=HAVE_WAITPID
https://www.nongnu.org/m17n/
https://www.gnu.org/software/emacs/manual/html_node/eintr/Digression-into-C.htmle