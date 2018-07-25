# Cracking Hashes
## Goal
The goal of this project is to crack the hashes contained in the file
puzzle.txt

## Solving the puzzle
Taking a look at puzzle.txt, we can see that the file contains 100072 hashed
lines. Due to the file containing this many number of lines, brute forcing is
really not a viable solution. Examining the file more closely, we can see that
each line contains 32 hexadecimal digits (128 bits), which probably means its
an MD5 hash.

Let us see if the website crackstation.net can crack the hashes for us.
Entering the first 20 lines in puzzle.txt on crackstation.net:

Unfortunately, the website is only able to crack the first 4 lines. But,
observing more closely, we can see that the plaintext of the 4th line is the
plaintext of the 3rd line plus an additional character. The same holds true
for the 3rd and 2nd line, and for the 2nd and 1st line.

Knowing this, we can write a python script cracking_hashes.py to solve the
puzzle. The script takes in 3 command line arguments (file name of puzzle,
hashing algorithm used by the puzzle file, and the name of the output file),
and uses the fact that the plaintext of a line is the plaintext of the
previous line plus an additional character to crack the hashes.