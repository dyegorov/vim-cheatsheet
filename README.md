# vim-cheatsheet
# basics
### save and quit
```
:w save file
:w FILENAME save current file to FILENAME
:wa save all files
:q quit
:q! discard and quit
:wq write and quit
```
### moving and editing
```
hjkl move cursor
i/I insert mode / insert at line start
a/A append mode / to line end
o/O add line after/before current
r/R replace char / enter replace mode
u, :u[ndo] undo latest changes
x delete char
dw delete word
d7w delete 7 words!
dd delete line (cuts to buffer)
7dd delete 7 lines
d$ delete to end of line
dw/de delete word
y copy selected text (###text selection)
yy copy string
p paste
7w/7e move 7 words forward
0 move to line start
$ move to line end (j$ move to end of next line)
e move to end of word
ce/c$ change to end of word/line
% move to pairing bracket
CTRL-G display your location in file
G go to end of file
number G go to line number
gg go to first line
```
motions
* `w` word
* `$` end of line
### run terminal command
```
:!
```
### search
```
/phrase search forward
?phrase search backward
n next occurence
N previous occurence
CTRL-o, CTRL-i to older/newer positions
```
### substitution
```
:s/old/new change 1st occurence
:3,7s/old/new/g change in lines from 3 to 7
:s/old/new/g everywhere
:s/old/new/gc with prompt 
```
### text selection
```
v enter visual mode
move to select text
y copy (yank) text
p paste text
:w NEWFILE save selection to new file
```
### read from file
```
:r FILENAME insert contents of file
:r !dir insert command output
```
### set option
``
:set number - show line number
:set nonumber
:syntax on
:syntax off
:set wrap
:set nowrap
:set ic - ignore case
:set noic
:set is - show partial matches
:set nois
:set hlsearch - highlight search
:set nohlsearch
```
### windows
```
CTRL-W CTRL-W switch windows
:split horizontal split
:vsplit vertical split
CTRL-W c close window
CTRL-W +- change height
CTRL-W <> change width 
CTRL-W = equal width 
CTRL-W hjkl move between windows 
```
# links
* $ vimtutor
* [https://habr.com/ru/post/442110/]
* [https://eax.me/vim-commands/]
