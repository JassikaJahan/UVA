# EOF
EOF indicates "end of file". A newline (which is what happens when you press enter) isn't the end of a file, it's the end of a line, so a newline doesn't terminate this loop.

The code isn't wrong[*], it just doesn't do what you seem to expect. It reads to the end of the input, but you seem to want to read only to the end of a line.

The value of EOF is -1 because it has to be different from any return value from getchar that is an actual character. So getchar returns any character value as an unsigned char, converted to int, which will therefore be non-negative.

If you're typing at the terminal and you want to provoke an end-of-file, use CTRL-D (unix-style systems) or CTRL-Z (Windows). Then after all the input has been read, getchar() will return EOF, and hence getchar() != EOF will be false, and the loop will terminate.

[*] well, it has undefined behavior if the input is more than LONG_MAX characters due to integer overflow, but we can probably forgive that in a simple example.


