# GetNextLine [![Build Status](https://travis-ci.org/dwyl/esta.svg?branch=master)](https://travis-ci.org/dwyl/esta)

## Intro

  This project will not only allow you to add a very convenient function to your collection,
but it will also allow you to learn a highly interesting new concept in C programming:
static variables.

  You will also gain a deeper understanding of allocations, whether they happen on the
stack memory or in the heap memory, the manipulation and the life cycle of a buffer, the
unexpected complexity implied in the use of one or many static variables.

  Your respect of the Norm will improve the rigor of your programming. We also suspect
that your approach to coding will change when you will discover that the initial state of
a variable in a function can vary depending on the call of that very function.

## Documentation

 1.  Function returns a line read from a file descriptor.
 2.  What we call a “line” is a succession of characters that end with ’\n’ (ascii code 0x0a) or with End Of File (EOF).
 3.  Function prototyped as follow :
     - ``` int get_next_line(const int fd, char **line); ``` 
 4.  The first parameter is the file descriptor that will be used to rea
 5.  The second parameter is the address of a pointer to a character that will be used
      to save the line read from the file descriptor
 6.  The return value can be 1, 0 or -1 depending on whether a line has been read,
      when the reading has been completed, or if an error has happened respectively.
 7.  Function *get_next_line* return its result without ’\n’.
 8.  Calling function *get_next_line* in a loop will then allow you to read the text
     available on a file descriptor one line at a time until the end of the text, no matter
     the size of either the text or one of its lines.
 9.  Function behaves well when it reads from a file, from the standard output, from a redirection etc.
 10. *get_next_line.h* have the prototype of the function get_next_line and a macro 
     that allows to choose the size of the reading buffer for the read function. This value will be modified during the defence to
     evaluate the strength of your function. That macro must be named BUFF_SIZE.
     For example:
     ``` #define BUFF_SIZE 42 ```
 11. *get_next_line* has an undefined behavior if, between two calls, the same file descriptor designs two distinct files although the reading from the first
      file was not completed.
 12. Consider also that a call to lseek(2) will never take place between two calls of
      the function get_next_line on the same file descriptor.
 13. Consider that get_next_line has an undefined behavior when reading 
     from a binary file.
 14. Global variables are forbidden.
 15. Static variables are allowed.
 
## Bonus part

  - [x]  *get_next_line* with a single static variable.
  - [X]  Able to manage multiple file descriptor with your get_next_line. For example,
         if the file descriptors 3, 4 and 5 are accessible for reading, then you can call
         *get_next_line* once on 3, once on 4, once again on 3 then once on 5 etc. without
         losing the reading thread on each of the descriptors.
         
## How to use
  
  Just include *get_next_line.h* and compile with *get_next_line.c*
