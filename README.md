# vim-cheatsheet
# basics
### save and quit
```
:w save file
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
yy copy string
p paste
7w/7e move 7 words forward
0 move to line start
ce/c$ change to end of word/line
```
motions
* `w` word
* `$` end of line

# links
* $ vimtutor
* [https://habr.com/ru/post/442110/]
* [https://eax.me/vim-commands/]
