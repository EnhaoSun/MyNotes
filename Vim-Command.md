## Search and replace
ref: https://vim.fandom.com/wiki/Search_and_replace

* :%s/foo/bar/g : 
  * Find each occurrence of 'foo' (in all lines), and replace it with 'bar'.
* :s/foo/bar/g : 
  * Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'.
* :%s/foo/bar/gc : 
  * Change each 'foo' to 'bar', but ask for confirmation first.
* :%s/\<foo\>/bar/gc : 
  * Change only whole words exactly matching 'foo' to 'bar'; ask for confirmation.
* :%s/foo/bar/gci : 
  * Change each 'foo' (case insensitive due to the i flag) to 'bar'; ask for confirmation.
* :%s/foo\c/bar/gc:
  * is the same because \c makes the search case insensitive.
  * This may be wanted after using :set noignorecase to make searches case sensitive (the default).
* :%s/foo/bar/gcI : 
  * Change each 'foo' (case sensitive due to the I flag) to 'bar'; ask for confirmation.
* :%s/foo\C/bar/gc 
  * is the same because \C makes the search case sensitive.
  * This may be wanted after using :set ignorecase to make searches case insensitive.
  * The g flag means global – each occurrence in the line is changed, rather than just the first.
* :5,12s/foo/bar/g	
  * Change each 'foo' to 'bar' for all lines from line 5 to line 12 (inclusive).

## Search selected

1. Yank the text you want to search for
2. q/p
3. Enter

**Explanation**

`q/` works similarly to vanilla search `/` except you're in command mode so `p` actually does "paste" instead of typing the character `p`. So the above will copy the text you're searching for and paste it into a search.

For more details type `:help q/`





**Vimrc**
```bash
"------------------ Basics ----------------------
set tabstop=4
set shiftwidth=4
syntax on
set nu
"------------------ Basics ----------------------

"------------------- NERDTREE --------------------
let NERDTreeShowHidden=1
let NERDTreeMinimalUI = 1
let NERDTreeDirArrows = 1
let NERDTreeShowLineNumbers=1
map <C-n> :NERDTreeToggle<CR>
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l
"------------------- NERDTREE --------------------


"------------------- vundle setting -----------------------
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}
Plugin 'preservim/nerdtree'

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
"------------------- vundle setting -----------------------
```
