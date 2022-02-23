# W3m Developer Manual

**This document is a work in progress.**

## Content
1. [Introduction](#introduction)
2. [Motives](#motives)
3. [Installation](#installation)
4. [Summary of the codebase](#summary-of-the-codebase)
5. [Interpreting the issues](#interpreting-the-issues)
6. [Other documentation:](#other-documentation:)
7. [Useful Sources](#useful-sources)


## Introduction
This document is the result of personal attempts to read the code and other valuble resources and understand it. It contains the various techniques used to understand the source code and the conclusions and sources neccecairy to understand it yourself.
It will also get updated everytime I learn something new.
Note that English is not my first language, nor my second. So if you find any mistakes in this document, please point me to it.

...
Resources used to write this manual:
* The source code itself
* Issues and pull requests
* The changelog included with it
* The old documentation
* Information available in mailing lists
* Other available online information (will be linked below)
* Hopefully revisions and corrections from the current developers and from contributors who are interested
...

Since I (the person writing this document) am a newbie in programming with the C language. A lot of the information that I will put here might not be important to someone reading this. This is just a documentation of what I'm learning as I'm reading though the code. In the hopes of making it better, and readable by everyone. I'm attempting to add links to every resource related to what I learn so that anyone can follow along and learn. I should point out again that I myself am not an expert. But I like learning new things and I'm attempting here to share what I'm learning.

I'm not sure if it's okay to add such document to the repository. But I may move it to a blog in the future.



## Motives
On the [Old README file](/doc/doc-old/doc-en/README) they pointed out in the *Current problems are* section that their online manuals are poor.
The online documents generally lack information, especially for developers who wants to contribute or use the project, these online documents that you'll find if you google w3m and look at every page generally contain information about general usage and the installation method. Those will be mentioned briefly here. But this document is meant for developers that wants to integrate their work with w3m.

## Installation
Check the [`README.md`](/README.md) for installation instuctions.

## Summary of the codebase
This section is the result of the direct reading of the code, file by file and function by function and line by line. This section will probably change a lot and may even be removed when better documentation build on it will be written.
Consider this section as just notes from someone reading the code.

### General notes on the code
This project is both simple and complicated at the same time. Therefore, my strategy is to read the codebase file by file and devide and reformat the code in each file into sections that I will address each one here before writing it's proper documentation (if necessary). Note that no actual changes to the code or it's functionalities will be made. Since this is just a strategy to study, understand and document the project.

### main.c
The [`main.c`](/main.c) file will be reformated slightly and comments will be added to it on [my fork of the repository](https://github.com/medanisjbara/w3m) without making changes to the code functionality.

#### A list of headers and libraries used:

Path headers:
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

Headers files:
* `"fm.h"`		:	*// yet to be documented*
* `"terms.h"`	:	*// yet to be documented*
* `"myctype.h"`	:	*// yet to be documented*
* `"regex.h"`	:	*// yet to be documented*
* `"wc.h"`		:	*// yet to be documented*
* `"wtf.h"`		:	*// yet to be documented*
* `"ucs.h"`		:	*// yet to be documented*



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
* `wrap_GC_warn_proc` 				*// yet to be documented* 
* `sig_chld` 						*// yet to be documented*
* `make_optional_header_string` 	*// yet to be documented*
* `die_oom` 						*// yet to be documented*
* `main` 							*// yet to be documented*
* `keyPressEventProc` 				*// yet to be documented*
* `pushEvent` 						*// yet to be documented*
* `dump_source` 					*// yet to be documented*
* `dump_head` 						*// yet to be documented*
* `dump_extra` 						*// yet to be documented*
* `cmp_anchor_hseq` 				*// yet to be documented*
* `do_dump` 						*// yet to be documented*
* `pcmap` Does nothing
* `escKeyProc` 						*// yet to be documented*
* `escdmap` 						*// yet to be documented*
* `tmpClearBuffer` 					*// yet to be documented*
* `currentURL` 						*// yet to be documented*
* `saveBufferInfo` 					*// yet to be documented*
* `pushBuffer` 						*// yet to be documented*
* `delBuffer` 						*// yet to be documented*
* `repBuffer` 						*// yet to be documented*
* `intTrap` 						*// yet to be documented*
* `resize_hook` 					*// yet to be documented*
* `resize_screen` 					*// yet to be documented*
* `SigPipe` 						*// yet to be documented*
* `nscroll` 						*// yet to be documented*
* `clear_mark` 						*// yet to be documented*
* `srchcore` 						*// yet to be documented*
* `disp_srchresult` 				*// yet to be documented*
* `dispincsrch` 					*// yet to be documented*
* `isrch` 							*// yet to be documented*
* `srch` 							*// yet to be documented*
* `srch_nxtprv` 					*// yet to be documented*
* `shiftvisualpos` 					*// yet to be documented*
* `cmd_loadfile` 					*// yet to be documented*
* `_movL` 							*// yet to be documented*
* `_movD` 							*// yet to be documented*
* `_movU` 							*// yet to be documented*
* `_movR` 							*// yet to be documented*
* `getChar` 						*// yet to be documented*
* `is_wordchar` 					*// yet to be documented*
* `prev_nonnull_line` 				*// yet to be documented*
* `next_nonnull_line` 				*// yet to be documented*
* `_quitfm` 						*// yet to be documented*
* `_goLine` 						*// yet to be documented*
* `cur_real_linenumber` 			*// yet to be documented*
* `loadNormalBuf` 					*// yet to be documented*
* `loadLink` 						*// yet to be documented*
* `gotoLabel` 						*// yet to be documented*
* `handleMailto` 					*// yet to be documented*
* `bufferA` 						*// yet to be documented*
* `save_submit_formlist` 			*// yet to be documented*
* `conv_form_encoding` 				*// yet to be documented*
* `query_from_followform` 			*// yet to be documented*
* `followForm` 						*// yet to be documented*
* `_followForm` 					*// yet to be documented*
* `_nextA` Go to the next anchor
* `_prevA` 						
* `nextX` Go to the next left/right anchor
* `nextY` Go to the next up/down anchor
* `checkBackBuffer` 				*// yet to be documented*
* `cmd_loadURL` 					*// yet to be documented*
* `goURL0` 							*// yet to be documented*
* `cmd_loadBuffer` 					*// yet to be documented*
* `follow_map` 						*// yet to be documented*
* `anchorMn` 						*// yet to be documented*
* `_peekURL` 						*// yet to be documented*
* `currentURL` 						*// yet to be documented*
* `_docCSet` 						*// yet to be documented*
* `change_charset` 					*// yet to be documented*
* `chkURLBuffer` 					*// yet to be documented*
* `chkNMIDBuffer` 					*// yet to be documented*
* `invoke_browser` 					*// yet to be documented*
* `mouse_scroll_line` 				*// yet to be documented*
* `posTab` 							*// yet to be documented*
* `do_mouse_action` 				*// yet to be documented*
* `process_mouse` 					*// yet to be documented*
* `gpm_process_mouse` 				*// yet to be documented*
* `sysm_process_mouse` 				*// yet to be documented*
* `getCurWord` 						*// yet to be documented*
* `GetWord` 						*// yet to be documented*
* `execdict` 						*// yet to be documented*
* `set_buffer_environ` 				*// yet to be documented*
* `searchKeyData` 					*// yet to be documented*
* `searchKeyNum` 					*// yet to be documented*
* `getCodePage` 					*// yet to be documented*
* `deleteFiles` 					*// yet to be documented*
* `w3m_exit` 						*// yet to be documented*
* `SigAlarm` 						*// yet to be documented*
* `setAlarmEvent` 					*// yet to be documented*
* `newTab` 							*// yet to be documented*
* `_newT` 							*// yet to be documented*
* `numTab` 							*// yet to be documented*
* `calcTabPos` 						*// yet to be documented*
* `deleteTab` 						*// yet to be documented*
* `followTab` 						*// yet to be documented*
* `tabURL0` 						*// yet to be documented*
* `moveTab` 						*// yet to be documented*
* `addDownloadList` 				*// yet to be documented*
* `checkDownloadList` 				*// yet to be documented*
* `convert_size3` 					*// yet to be documented*
* `DownloadListBuffer` 				*// yet to be documented*
* `download_action` 				*// yet to be documented*
* `stopDownload` 					*// yet to be documented*
* `save_buffer_position` 			*// yet to be documented*
* `resetPos` 						*// yet to be documented*

I reformated the function definitions in the code from 
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

#### Other C Functions used in main.c
*// yet to be documented*
#### DEFUN
As far as I understand, these are macros that are defined from [Functions](/doc/doc-dev/Functions.md). Each have it's functionality in the browser itself and each are directly associated with one of the C functions mentioned above. In the code, 


|  Funciton                            |  Macro                             |  Comment associated in the code                                                |
|:-------------------------------------|:---------------------------------- |:-------------------------------------------------------------------------------|
| `nulcmd`                             | NOTHING NULL @@@                   | "Do nothing"                                                                   |
| `pcmap`                              | PCMAP                              | "pcmap"                                                                        |
| `escmap`                             | ESCMAP                             | "ESC map"                                                                      |
| `escbmap`                            | ESCBMAP                            | "ESC [ map"                                                                    |
| `multimap`                           | MULTIMAP                           | "multimap"                                                                     |
| `pgFore`                             | NEXT_PAGE                          | "Scroll down one page"                                                         |
| `pgBack`                             | PREV_PAGE                          | "Scroll up one page"                                                           |
| `hpgFore`                            | NEXT_HALF_PAGE                     | "Scroll down half a page"                                                      |
| `hpgBack`                            | PREV_HALF_PAGE                     | "Scroll up half a page"                                                        |
| `lup1`                               | UP                                 | "Scroll the screen up one line"                                                |
| `ldown1`                             | DOWN                               | "Scroll the screen down one line"                                              |
| `ctrCsrV`                            | CENTER_V                           | "Center on cursor line"                                                        |
| `ctrCsrH`                            | CENTER_H                           | "Center on cursor column"                                                      |
| `rdrwSc`                             | REDRAW                             | "Draw the screen anew"                                                         |
| `srchfor`                            | SEARCH SEARCH_FORE WHEREIS         | "Search forward"                                                               |
| `isrchfor`                           | ISEARCH                            | "Incremental search forward"                                                   |
| `srchbak`                            | SEARCH_BACK                        | "Search backward"                                                              |
| `isrchbak`                           | ISEARCH_BACK                       | "Incremental search backward"                                                  |
| `srchnxt`                            | SEARCH_NEXT                        | "Continue search forward"                                                      |
| `srchprv`                            | SEARCH_PREV                        | "Continue search backward"                                                     |
| `shiftl`                             | SHIFT_LEFT                         | "Shift screen left"                                                            |
| `shiftr`                             | SHIFT_RIGHT                        | "Shift screen right"                                                           |
| `col1R`                              | RIGHT                              | "Shift screen one column right"                                                |
| `col1L`                              | LEFT                               | "Shift screen one column left"                                                 |
| `setEnv`                             | SETENV                             | "Set environment variable"                                                     |
| `pipeBuf`                            | PIPE_BUF                           | "Pipe current buffer through a shell command and display output"               |
| `pipesh`                             | PIPE_SHELL                         | "Execute shell command and display output"                                     |
| `readsh`                             | READ_SHELL                         | "Execute shell command and display output"                                     |
| `execsh`                             | EXEC_SHELL SHELL                   | "Execute shell command and display output"                                     |
| `ldfile`                             | LOAD                               | "Open local file in a new buffer"                                              |
| `ldhelp`                             | HELP                               | "Show help panel"                                                              |
| `movL`                               | MOVE_LEFT                          | "Cursor left"                                                                  |
| `movL1`                              | MOVE_LEFT1                         | "Cursor left. With edge touched slide"                                         |
| `movD`                               | MOVE_DOWN                          | "Cursor down"                                                                  |
| `movD1`                              | MOVE_DOWN1                         | "Cursor down. With edge touched slide"                                         |
| `movU`                               | MOVE_UP                            | "Cursor up"                                                                    |
| `movU1`                              | MOVE_UP1                           | "Cursor up. With edge touched slide"                                           |
| `movR`                               | MOVE_RIGHT                         | "Cursor right"                                                                 |
| `movR1`                              | MOVE_RIGHT1                        | "Cursor right. With edge touched slide"                                        |
| `movLW`                              | PREV_WORD                          | "Move to the previous word"                                                    |
| `movRW`                              | NEXT_WORD                          | "Move to the next word"                                                        |
| `quitfm`                             | ABORT EXIT                         | "Quit at once"                                                                 |
| `qquitfm`                            | QUIT                               | "Quit with confirmation request"                                               |
| `selBuf`                             | SELECT                             | "Display buffer-stack panel"                                                   |
| `susp`                               | INTERRUPT SUSPEND                  | "Suspend w3m to background"                                                    |
| `goLine`                             | GOTO_LINE                          | "Go to the specified line"                                                     |
| `goLineF`                            | BEGIN                              | "Go to the first line"                                                         |
| `goLineL`                            | END                                | "Go to the last line"                                                          |
| `linbeg`                             | LINE_BEGIN                         | "Go to the beginning of the line"                                              |
| `linend`                             | LINE_END                           | "Go to the end of the line"                                                    |
| `editBf`                             | EDIT                               | "Edit local source"                                                            |
| `editScr`                            | EDIT_SCREEN                        | "Edit rendered copy of document"                                               |
| `_mark`                              | MARK                               | "Set/unset mark"                                                               |
| `nextMk`                             | NEXT_MARK                          | "Go to the next mark"                                                          |
| `prevMk`                             | PREV_MARK                          | "Go to the previous mark"                                                      |
| `reMark`                             | REG_MARK                           | "Mark all occurences of a pattern"                                             |
| `followA`                            | GOTO_LINK                          | "Follow current hyperlink in a new buffer"                                     |
| `followI`                            | VIEW_IMAGE                         | "Display image in viewer"                                                      |
| `submitForm`                         | SUBMIT                             | "Submit form"                                                                  |
| `topA`                               | LINK_BEGIN                         | "Move to the first hyperlink"                                                  |
| `lastA`                              | LINK_END                           | "Move to the last hyperlink"                                                   |
| `nthA`                               | LINK_N                             | "Go to the nth link"                                                           |
| `nextA`                              | NEXT_LINK                          | "Move to the next hyperlink"                                                   |
| `prevA`                              | PREV_LINK                          | "Move to the previous hyperlink"                                               |
| `nextVA`                             | NEXT_VISITED                       | "Move to the next visited hyperlink"                                           |
| `prevVA`                             | PREV_VISITED                       | "Move to the previous visited hyperlink"                                       |
| `nextL`                              | NEXT_LEFT                          | "Move left to the next hyperlink"                                              |
| `nextLU`                             | NEXT_LEFT_UP                       | "Move left or upward to the next hyperlink"                                    |
| `nextR`                              | NEXT_RIGHT                         | "Move right to the next hyperlink"                                             |
| `nextRD`                             | NEXT_RIGHT_DOWN                    | "Move right or downward to the next hyperlink"                                 |
| `nextD`                              | NEXT_DOWN                          | "Move downward to the next hyperlink"                                          |
| `nextU`                              | NEXT_UP                            | "Move upward to the next hyperlink"                                            |
| `nextBf`                             | NEXT                               | "Switch to the next buffer"                                                    |
| `prevBf`                             | PREV                               | "Switch to the previous buffer"                                                |
| `backBf`                             | BACK                               | "Close current buffer and return to the one below in stack"                    |
| `deletePrevBuf`                      | DELETE_PREVBUF                     | "Delete previous buffer (mainly for local CGI-scripts)"                        |
| `goURL`                              | GOTO                               | "Open specified document in a new buffer"                                      |
| `goHome`                             | GOTO_HOME                          | "Open home page in a new buffer"                                               |
| `gorURL`                             | GOTO_RELATIVE                      | "Go to relative address"                                                       |
| `ldBmark`                            | BOOKMARK VIEW_BOOKMARK             | "View bookmarks"                                                               |
| `adBmark`                            | ADD_BOOKMARK                       | "Add current page to bookmarks"                                                |
| `ldOpt`                              | OPTIONS                            | "Display options setting panel"                                                |
| `setOpt`                             | SET_OPTION                         | "Set option"                                                                   |
| `msgs`                               | MSGS                               | "Display error messages"                                                       |
| `pginfo`                             | INFO                               | "Display information about the current document"                               |
| `linkMn`                             | LINK_MENU                          | "Pop up link element menu"                                                     |
| `accessKey`                          | ACCESSKEY                          | "Pop up accesskey menu"                                                        |
| `listMn`                             | LIST_MENU                          | "Pop up menu for hyperlinks to browse to"                                      |
| `movlistMn`                          | MOVE_LIST_MENU                     | "Pop up menu to navigate between hyperlinks"                                   |
| `linkLst`                            | LIST                               | "Show all URLs referenced"                                                     |
| `cooLst`                             | COOKIE                             | "View cookie list"                                                             |
| `ldHist`                             | HISTORY                            | "Show browsing history"                                                        |
| `svA`                                | SAVE_LINK                          | "Save hyperlink target"                                                        |
| `svI`                                | SAVE_IMAGE                         | "Save inline image"                                                            |
| `svBuf`                              | PRINT SAVE_SCREEN                  | "Save rendered document"                                                       |
| `svSrc`                              | DOWNLOAD SAVE                      | "Save document source"                                                         |
| `peekURL`                            | PEEK_LINK                          | "Show target address"                                                          |
| `peekIMG`                            | PEEK_IMG                           | "Show image address"                                                           |
| `curURL`                             | PEEK                               | "Show current address"                                                         |
| `vwSrc`                              | SOURCE VIEW                        | "Toggle between HTML shown or processed"                                       |
| `reload`                             | RELOAD                             | "Load current document anew"                                                   |
| `reshape`                            | RESHAPE                            | "Re-render document"                                                           |
| `docCSet`                            | CHARSET                            | "Change the character encoding for the current document"                       |
| `defCSet`                            | DEFAULT_CHARSET                    | "Change the default character encoding"                                        |
| `chkURL`                             | MARK_URL                           | "Turn URL-like strings into hyperlinks"                                        |
| `chkWORD`                            | MARK_WORD                          | "Turn current word into hyperlink"                                             |
| `chkNMID`                            | MARK_MID                           | "Turn Message-ID-like strings into hyperlinks"                                 |
| `rFrame`                             | FRAME                              | "Toggle rendering HTML frames"                                                 |
| `extbrz`                             | EXTERN                             | "Display using an external browser"                                            |
| `linkbrz`                            | EXTERN_LINK                        | "Display target using an external browser"                                     |
| `curlno`                             | LINE_INFO                          | "Display current position in document"                                         |
| `dispI`                              | DISPLAY_IMAGE                      | "Restart loading and drawing of images"                                        |
| `stopI`                              | STOP_IMAGE                         | "Stop loading and drawing of images"                                           |
| `msToggle`                           | MOUSE_TOGGLE                       | "Toggle mouse support"                                                         |
| `mouse`                              | MOUSE                              | "mouse operation"                                                              |
| `sgrmouse`                           | SGRMOUSE                           | "SGR 1006 mouse operation"                                                     |
| `movMs`                              | MOVE_MOUSE                         | "Move cursor to mouse pointer"                                                 |
| `menuMs`                             | MENU_MOUSE                         | "Pop up menu at mouse pointer"                                                 |
| `tabMs`                              | TAB_MOUSE                          | "Select tab by mouse action"                                                   |
| `closeTMs`                           | CLOSE_TAB_MOUSE                    | "Close tab at mouse pointer"                                                   |
| `dispVer`                            | VERSION                            | "Display the version of w3m"                                                   |
| `wrapToggle`                         | WRAP_TOGGLE                        | "Toggle wrapping mode in searches"                                             |
| `dictword`                           | DICT_WORD                          | "Execute dictionary command (see README.dict)"                                 |
| `dictwordat`                         | DICT_WORD_AT                       |  "Execute dictionary command for word at cursor"                               |
| `execCmd`                            | COMMAND                            | "Invoke w3m function(s)"                                                       |
| `setAlarm`                           | ALARM                              | "Set alarm"                                                                    |
| `reinit`                             | REINIT                             | "Reload configuration file"                                                    |
| `defKey`                             | DEFINE_KEY                         | "Define a binding between a key stroke combination and a command"              |
| `newT`                               | NEW_TAB                            | "Open a new tab (with current document)"                                       |
| `closeT`                             | CLOSE_TAB                          | "Close tab"                                                                    |
| `nextT`                              | NEXT_TAB                           | "Switch to the next tab"                                                       |
| `prevT`                              | PREV_TAB                           | "Switch to the previous tab"                                                   |
| `tabA`                               | TAB_LINK                           | "Follow current hyperlink in a new tab"                                        |
| `tabURL`                             | TAB_GOTO                           | "Open specified document in a new tab"                                         |
| `tabrURL`                            | TAB_GOTO_RELATIVE                  | "Open relative address in a new tab"                                           |
| `tabR`                               | TAB_RIGHT                          | "Move right along the tab bar"                                                 |
| `tabL`                               | TAB_LEFT                           | "Move left along the tab bar"                                                  |
| `ldDL`                               | DOWNLOAD_LIST                      | "Display downloads panel"                                                      |
| `undoPos`                            | UNDO                               | "Cancel the last cursor movement"                                              |
| `redoPos`                            | REDO                               | "Cancel the last undo"                                                         |
| `cursorTop`                          | CURSOR_TOP                         | "Move cursor to the top of the screen"                                         |
| `cursorMiddle`                       | CURSOR_MIDDLE                      | "Move cursor to the middle of the screen"                                      |
| `cursorBottom`                       | CURSOR_BOTTOM                      | "Move cursor to the bottom of the screen"                                      |
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

## Interpreting the issues
A valuble resource when you're trying to learn a codebase is to read the issues and pull requests and look up the code associated to fix them.
Issues can be found [here](https://github.com/tats/w3m/issues).
Here , we'll go over the each issue posted in github and the way it was fixed.

* PR [#1](https://github.com/tats/w3m/pull/1)

This fix enabled compilation by older versions of gcc to be successful. 
```C
#if (GC_VERSION_MAJOR>=7) && (GC_VERSION_MINOR>=2)
    GC_set_oom_fn(die_oom);
#else
    GC_oom_fn = die_oom;
#endif
```
the `GC_set_oom_fn` function 

## Other documentation
Have a look at our [Related Sources](/doc/related-sources.md) document. It contains a list of sources to potentially useful documentation online about the project.

## Useful Sources
http://lxr.yanyahua.com/ident/make?_i=HAVE_WAITPID
https://www.nongnu.org/m17n/
https://www.gnu.org/software/emacs/manual/html_node/eintr/Digression-into-C.htmle