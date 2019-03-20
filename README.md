# vim-cheatsheet
### save and quit
```
:e edit file (also creates file)
:e scp/ftp/ftps://user@host/path/to/file network edit
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
{,} go to start/end of paragraph/code block
CTRL-f,CTRL-b forward/backward one screen
i/I insert mode / insert at line start
a/A append mode / to line end
o/O add line after/before current
r/R replace char / enter replace mode
u, :u[ndo] undo latest changes
CTRL-r, :red[o] redo change
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
CTRL-u, CTRL-d page up/page down
CTRL-y, CTRL-e move up/down wo cursor movement
```
motions
* `w,b,e` word
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
`*,#` find word under cursor down/up
:noh disable highlight after search
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
y copy/yank text
viw selects word under cursor
p paste text
:w NEWFILE save selection to new file
SHIFT-v select line
CTRL-v select rectangle
gu to lowercase
gU to uppercase
```
to select paragraph:
* `{` go to par start
* `v` enter visual mode
* `}` go to par end
* `y` to copy `d` to paste
### read from file
```
:r FILENAME insert contents of file
:r !dir insert command output
```
### set option
```
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
:set list - show tabs and line ends
:set [no]wildmenu show variants above command line
```
### windows
```
CTRL-W CTRL-W switch windows
:sp[lit] horizontal split
:vs[plit] vertical split
CTRL-W c close window
CTRL-W +- change height
CTRL-W <> change width
CTRL-W = equal width
CTRL-W hjkl move between windows
CTRL-W o maximize current window
CTRL-w ^ close max window
```
### plugins wo vundle
```
cd ~/.vim/bundle
git clone path/to/plugin/repo
set runtimepath^=~/.vim/bundle/tslime.vim //add this to .vimrc
:helptags ~/.vim/bundle/nerdtree/doc/ //add docs to help
```
### file manager
```
:Ex
:e ./
```
when using nerdtree use ctrl-n to toggle filetree
### buffers
```
:ls,:buffers list buffers
:buffer N go to buffer N
:bn, bnext next buffer

```
### tabs
```
:tabnew [name] create tab
:tabs list tabs
:tabn, gt next tab
:tabp, Gt prev tab
Ngt go to tab N
:tabm -1/+1/N move tab back/forward/to position N

```
Setup tabs:
* add `set tabstop=8 softtabstop=0 expandtab shiftwidth=4 smarttab` to `.vimrc`
* https://stackoverflow.com/questions/1878974/redefine-tab-as-4-spaces
### commands
```
q: command history
. replay last command
```
## dbext
* leader = \
* `CTRL-w =` to make windows equal
### vimrc
```
let g:dbext_default_profile_demo = 'type=MYSQL:host=192.168.89.42:user=root:passwd=root:dbname=sndbr_17_3'
let g:dbext_default_profile = 'demo'
```
### execute ALL
```
\sea
```
### execute sql under cursor
```
\se
Sql Execute
```
### select * from table under cursor
```
\st - selects all rows
\sT - prompts row limit
\stw - prompts for where clause
\sta - prompts for table name and selects from it
```
### schema info
```
:DBListTable
:DBListProcedure
:DBListView
```
map them in vimrc
```
map <leader>l :DBListTable<CR>
```
### desc table under cursor
```
\sdt - desc table
\sdp - desc procedure
\slc - copies all table column names to unnamed register (col1, col2)
```
### results buffer commands
```
R - rerun current sql
q - close
```
### registers
`"` start working with register
```
"ay - yank to register a
"+y - yank to register +
:reg a b c - view registries a b c
```
vim has a unnamed (or default) register that can be accessed with "". Any text that you delete (with d, c, s or x) or yank (with y) will be placed there, and that’s what vim uses to paste, when no explicit register is given. A simple p is the same thing as doing ""p.
### view key mappings
```
:help index - default key mappings
:map
:map!
:nmap - Display normal mode maps
:imap - Display insert mode maps
:vmap - Display visual and select mode maps
:smap - Display select mode maps
:xmap - Display visual mode maps
:cmap - Display command-line mode maps
:omap - Display operator pending mode maps
```
### auto close brackets
* https://stackoverflow.com/questions/21316727/automatic-closing-brackets-for-vim
* add to vimrc:
```
inoremap " ""<left>
inoremap ' ''<left>
inoremap ( ()<left>
inoremap [ []<left>
inoremap { {}<left>
inoremap {<CR> {<CR>}<ESC>O
inoremap {;<CR> {<CR>};<ESC>O
```
### snippets wo plugin
save lines to files
```
:100,200w filename
```
paste file contents below
```
:r filename
```
### markers
```
ma set LOCAL marker `a`
mB set GLOBAL marker `B`
\`c go to marker c (ignore backslash)
\`0 go to position before vim close (ignore backslash)
:marks list markers
```
### visually change cursor in input mode
```
:autocmd InsertEnter,InsertLeave * set cul!
```
# links
* $ vimtutor
* https://habr.com/ru/post/442110/
* https://eax.me/vim-commands/
* http://blog.erlware.org/how-to-use-vim-for-erlang-development/
* https://www.books.ru/books/izuchaem-redaktory-vi-i-vim-7-e-izdanie-827256/
* https://mutelight.org/dbext-the-last-sql-client-youll-ever-need
* https://github.com/vim-scripts/dbext.vim

