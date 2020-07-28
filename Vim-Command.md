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