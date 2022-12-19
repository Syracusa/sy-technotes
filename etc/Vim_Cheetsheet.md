#move around
hjkl

#Insert mode
i

#Insert mode -> Normal mode
<ESC><CTRL-[><CTRL-C>

#move by word
w
b
W
B

# end of word
e
ge /* previous */
E
gE

# Move to specific character
f{character}
F{character} /* previous occurence */
; /* Next match char */
, /* Previous match char*/

# Move to just before cursor to specific character 
t
T

# First/End character of a line
0
^ /* first non-blank char */
$ /* End of line*/
g_ /* non-blank eol */

# Moving paragraph
{
}

# Moving page
CTRL-D
CTRL-U

# Search
/{pattern}
?{pattern} /* backwards */
n /* go to next match */
N /* go to previous match */

# Multifly command
{count}{command}


# Find definition of this word
gd

# Find File where this word imported 
gf

# Go to Top of the file
gg

# Go to specific line
{line}gg

# End of file
G

# Find matching ({[]}) at this cursor
%


# Concat command
{operator}{count}{mothion}
 * example
d2w /* delete 2 words */
dG /* delete to eof */
ggdG /* go to start of file and delete to end */

# Undoing/Redoing
u /* Undo */
CTRL-R /* Redo */

# Delete
dd /* Delete whole line */
D /* Remove from current cursor to eol (same as d$) */

# Combine with d
dt; /* Delete until ; /*
d/hello /* delete until hello */

# Reminderer
> - d for delete
> - f for find
> - c for change
> - t for unTil


# Use c instead of d (Delete and Insert = Change?)
d + i = c
