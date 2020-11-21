# vim-cheatsheet

## modes
- normal: use it whenever not typing
- insert: insert text. `- INSERT -` indication
- command: runs command e.g. `:ex` and returns to normal
- visual: highlight text when moving cursor. `-VISUAL-` indicator
- insert normal: when in insert mode press `Ctrl-o`. One command in normal mode and back to insert

## working with files

### Open file with `:e`
```
$ vim
:e /etc/passwd
```

### Add file contents to current buffer
```
:read file.txt
:r file.txt // inserts file.txt below cursor in current buffer
:0r file.txt // insert before first line
:r!sed -n 2,8p file.txt // insert lines 2-8 from file.txt below cursor
:r !ls // insert dir listing below cursor
```

### Open file or link
```
gf // open filename under cursor
gx // open link in default browser
```

### Close file
```
:wq // save and quit vim
:x // exit vim and write if changes made
ZZ // = :x
:q! // quit without saving
:qa // exit all open files in current vim session
```

### Save file
```
:w // save opened buffer
:w file.txt // save as file.txt
:w! file.txt // save as and rewrite
:sav file.txt // wtf is this
:up[date] file.txt // save if buffer was modified
```

### Navigate words
```
hjkl // left down up right

w // go to start of next word
W // go to start of next WORD
e // go to end of current word
E // go to end of current WORD
b // go to prev (before - b) word
B // go to prev WORD
3w // go to start of 3rd word
6j // go 6 lines below
```

Vim "navigation" is not-so difficult!
`WORD` is delimited by white space
`word` is delimited by non-keyword characters

### Scroll pages
```
Ctrl-d // scroll down half page
Ctrl-u // scroll up half page
Ctrl-f // page down (forwards)
Ctrl-b // page up (backwards)
```

### Jump file
```
gg // go to top of file
G // bottom of file
{ // beginning of current paragraph
} // end of current paragraph
% // matching pair of (), [], {}
50% // line at 50% of file
:28 // to line 28
```

### Navigate window
```
H // first line in current window (High)
L // lowest line of window
M // middle of window 
```

### Search
```
/  // search forward
n  // next occurence
N  // prev occurence
ggn // go to top of file and find next
GN  // go to end and find last
?   // search backwards
```

### File manager
```
:Ex  // Explore current dir
:Ex <dir>
:Sex  // explore in horizontal split
:Vex  // in vertical
:Tex  // in new tab
:Lexplore // vertical split on the left
:40vs +Ex
let g:netrw_liststyle = 3 // set .vimrc list style
let g:newrw_browse_split = 4 // open file in previous window
let g:netrw_winsize = 20 // file manager 20% of vim window
<Enter> // open file under cursor
D // delete file
R // rename
X // execute
% // create new
```

### Edit file via SSH
```
vim scp://user@myserver[:port]//pat/to/file.txt
vim ftp://hostname/path/to/file
```

## Personalizing
```
:set number
:set nonumber
:set number! // toggle numbers on/off
:set number relativenumber // view numbers from current line. use :.+8t. to copy 8th line from current
:echo $HOME  // view vim home dir and find .vimrc
colorscheme  scheme_name
set cursorline
set cursorcolumn
```

General options
```
set nocompatible - Use Vim settings, rather then Vi settings. It’s important to have this on
the top of your file, as it influences other options.
set backspace=indent,eol,start - Allow backspacing over indention, line breaks and insertion
start.
set history=1000 - Set bigger history of executed commands.
set showcmd - Show incomplete commands at the bottom.
set showmode - Show current mode at the bottom.
set autoread - Automatically re-read files if unmodified inside Vim.
set hidden - Manage multiple buffers effectively: the current buffer can be “sent” to the
background without writing to disk. When a background buffer becomes current again,
marks and undo-history are remembered. See chapter Buffers to understand this better.
```

User interface
```
set laststatus=2 - Always display the status bar.
set ruler - Always show cursor position.
set wildmenu - Display command line’s tab complete options as a menu.
set tabpagemax=40 - Maximum number of tab pages that can be opened from the command
line.
colorscheme desert - Change color scheme.
set cursorline - Highlight the line currently under cursor.
set number - Show line numbers on the sidebar.
set relativenumber - Show line number on the current line and relative numbers on all other
lines. Works only if the option above ( number ) is enabled.
set noerrorbells - Disable beep on errors.
set visualbell - Flash the screen instead of beeping on errors.
set mouse=a - Enable mouse for scrolling and resizing.
set background=dark - Use colors that suit a dark background.
set title - Set the window’s title, reflecting the file currently being edited.
```

Indentation
```
set autoindent - New lines inherit the indentation of previous lines.
filetype plugin indent on - Smart auto indentation (instead of old smartindent option).
set tabstop=4 - Show existing tab with 4 spaces width.
set shiftwidth=2 - When indenting with ‘>’, use 2 spaces width.
set expandtab - On pressing tab, insert 4 spaces.
set nowrap - Don’t wrap lines.
```

Text rendering
```ignorelang
set encoding=utf-8 - Use an encoding that supports Unicode.
set linebreak - Wrap lines at convenient points, avoid wrapping a line in the middle of a
word.
set scrolloff=3 - The number of screen lines to keep above and below the cursor.
set sidescrolloff=5 - The number of screen columns to keep to the left and right of the
cursor.
syntax enable - Enable syntax highlighting
```

### Swap and backup
Swap files
```ignorelang
set noswapfile // disable all
set nobackup
set nowb
// or move
$ mkdir ~/.vim/swp
set directory=$HOME/.vim/swp//
set backupdir=~/.vim/.backup//
```

### Enable project specific vimrc
ATTENTION. This is dangerous!
```ignorelang
set exrc
```

### Basic vimrc
```ignorelang
set nocompatible
" Use Vim settings, rather than Vi settings
set softtabstop=2 " Indent by 2 spaces when hitting tab
set shiftwidth=2 " Indent by 4 spaces when auto-indenting
set tabstop=2 " Show existing tab with 4 spaces width
syntax on " Enable syntax highlighting
filetype indent on " Enable indenting for files
set autoindent " Enable auto indenting
set number " Enable line numbers
colorscheme desert " Set nice looking colorscheme
set nobackup " Disable backup files
set laststatus=2 "show status line
set statusline=%F%m%r%h%w%=(%{&ff}/%Y)\ (line\ %l\/%L,\ col\ %c)\
set wildmenu " Display command line's tab complete options as a menu.
```

### Undo and redo
```ignorelang
u // in normal mode
:u[ndo]
:red[o]
Ctrl-r // in normal mode
:5u // undo 5 changes
:ea[rlier]
:lat[er]
:earlier 2 // undo 2 changes
:earlier 10m // undo last 10 minutes
:ea 2d
:ea 3h
:later 5m
:lat 15s
:ea 3f // undo last 3 file writes/saves
```

Undo branches
```ignorelang
g- // prev branch
g+ // next branch
```

Persistent undo
```ignorelang
set undofile
mkdir ~/.vim/undodir
set undodir=~/.vim/undodir
```

### Buffers
Buffer is a piece of memory for opened file.
* Buffer = in-memory text of a file
* Window = viewport on a buffer
* Tab = collection of windows

```ignorelang
:ls // list buffers
:buffers // also list buffers
:5b // open 5th buffer
:buffer 5 // open 5th buffer
:ball // open all buffers
:bn[ext] // open next
:bp[revious] // open previous
:bd // buffer delete - close current buffer
map <C-K> :pbrev<CR>
map <C-J> :bnext<CR> // ctrl-k go to next buffer, ctrl-j to previous
Ctrl-6  // switch current and prev buffers
```

### Windows and Tabs
Window is a viewport on buffer.
```ignorelang
vim -O file1 file2 file3 // opens with vertical split
vim -o file1 file2 // opens with horizontal split
vim -o5 // open 5 windows
```

A window can be split
```ignorelang
:sp[lit] file.txt // opens file as horizontal split
:vs[plit] file.txt // opens file as vertical split
:20sp file.txt // horizontal split for 20 lines
:25vs file.txt // vertical for 25 chars
```

Switching windows
```ignorelang
Ctrl-w h // switch window to the left
Ctrl-w j // switch window below
Ctrl-w k // switch window above
Ctrl-w l // switch window to the right

vimrc:
nnoremap <C-H> <C-W><C-H>
nnoremap <C-J> <C-W><C-J>
nnoremap <C-K> <C-W><C-K>
nnoremap <C-L> <C-W><C-L>
```

Moving windows
```ignorelang
Ctrl-w r // Rotate vertical windows left->right
Ctrl-w R // ... right->left
Ctrl-w H // move curr window left and full height
Ctrl-w J // move curr window bot and full width
```

Resizing windows
```ignorelang
Ctrl-w = // resize equally
Ctrl-w > // increase window to right
Ctrl-w < // increase window to left
Ctrl-w 10 <
Ctrl-w - // decrease height
Ctrl-w 5 - 
Ctrl-w + // increase height
Ctrl-w 5 +

:on[ly] // close other splits
```

Sessions
```ignorelang
:mksession ~/mysession.vim // save current windows and tabs
vim -S ~/mysession.vim // restore session
:source ~/mysession.vim
```

#########################
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
f<char> jumps to char occurence in string
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
### view full path of current file `1,ctrl-g`
### disable swap files
```
set noundofile
set nobackup
set noswapfile
```
# links
* $ vimtutor
* https://habr.com/ru/post/442110/
* https://eax.me/vim-commands/
* http://blog.erlware.org/how-to-use-vim-for-erlang-development/
* https://www.books.ru/books/izuchaem-redaktory-vi-i-vim-7-e-izdanie-827256/
* https://mutelight.org/dbext-the-last-sql-client-youll-ever-need
* https://github.com/vim-scripts/dbext.vim

