# W3m Developer Manual

## Introduction
This document is the result of personal attempts to read the code and understand it. It will get updated everytime I learn something new.
Note that English is not my first language, nor my second. So if you find any mistakes in this document, please point me to it.

...

Since I (the person writing this document) am a newbie in programming with the C language. A lot of the information that I will put here might not be important to someone reading this. This is just a documentation of what I'm learning as I'm reading though the code. In the hopes of making it better, and readable by everyone. I'm attempting to add links to every resource related to what I learn so that anyone can follow along and learn. I should point out again that I myself am not an expert. But I like learning new things and I'm attempting here to share what I'm learning.

I'm not sure if it's okay to add such document to the repository. But I may move it to a blog in the future.

## Why
On the [Old README file](/doc/doc-old/doc-en/README) they pointed out in the *Current problems are* section that their online manuals are poor.
The online documents generally lack information, especially for developers who wants to contribute or use the project, these online documents that you'll find if you google w3m and look at every page generally contain information about general usage and the installation method. Those will be mentioned briefly here. But this document is meant for developers that wants to integrate their work with w3m.

## Installation
I'm yet do update [`README.md`](/README.md) to give installation instuctions.

## General notes on the code
This project is both simple and complicated at the same time. Therefore, my strategy is to read the codebase file by file and devide and reformat the code in each file into sections that I will address each one here before writing it's proper documentation (if necessary). Note that no actual changes to the code or it's functionalities will be made. Since this is just a strategy to study, understand and document the project.

## main.c
The [`main.c`](/main.c) file will be reformated slightly and comments will be added to it on [my fork of the repository](https://github.com/medanisjbara/w3m) without making changes to the code functionality.

### A list of headers and libraries used:
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

### Notes:

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


## Useful Sources
http://lxr.yanyahua.com/ident/make?_i=HAVE_WAITPID
https://www.nongnu.org/m17n/
https://www.gnu.org/software/emacs/manual/html_node/eintr/Digression-into-C.htmle