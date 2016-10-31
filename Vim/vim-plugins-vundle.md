# commands and Key Mappings

---
_It's a summary of the commands and key mappings of the plugins installed via Vundle._

---
>  Dir:
>     [Nerdtree](#1)
>     [NERDCommenter](#2)
>     [Tagbar](#3)
>     [CtrlP](#4)
>     [Python-mode](#5)
>     [Syntastic](#6)
>     [Vim-Trailing-Whitespace](#7)
>     [YCM](#8)
>     [Ultisnips](#9)
>     [Vim-Markdown](#10)
>     [TaskList](#11)
>     [BufExplorer](#12)
>     [Vim-Surround](#13)

---

<h3 id="1">Nerdtree</h3>

> - <leader>n :NERDTreeToggle<CR>
> - Inside the NERDTree window
>   - `o`   Open
>   - `t`   Open in new tab
>   - `T`   Open in new tab but focus on current tab
>   - `i`   Open in new window
>   - `O`   Recursively open
>   - `x`   Close nodes
>   - `X`   Recursively close nodes
>   - `D`   Delete bookmark
>   - `p`   Jump to current nodes parent
>   - `P`   Jump to root node
>   - `K`   Jump up
>   - `J`   Jump down
>   - `u`   Move the tree root up a dir
>   - `r`   Recursively refresh the current dir
>   - `R`   Recursively refresh the root
>   - `m`   Display the menu
>   - `cd`  Change the CWD
>   - `C`   Change the tree root to the selected dir
>   - `CD`  Change tree root to the CWD
>   - `q`   Close window
>   - `?`   Help

---

<h3 id="2">NERDCommenter</h3>

> - ' [count]<leader>cc '     Comment out
> - ' [count]<leader>c<space> '   Toggle comment state
> - ' [count]<leader>ci '     Toggle comment state,line individually
> - ' [count]<leader>cn '     Comment out but forces nesting
> - ' [count]<leader>cy '     Yank then comment out
> - ' <leader>c$ '            Comment to the end of the line
> - ' <leader>cA '            Edit comment
> - ' [count]<leader>cu '     Uncomment

---

<h3 id="3">Tagbar</h3>

> - `<F8>`    :TagbarToggle<CR>
> - General
>     - `<CR>`    Jump to definition
>     - `p`       Preview
>     - `P`       Preview in window
>     - `<C-n>`   Next top-level tag
>     - `<C-p>`   Previous top-level tag
>     - `<Space>` Tag prototype
>     - `v`       Hide non-public tags
> - Folds
>     - `zo` `+`  Open fold
>     - `zc` `-`  Close
>     - `za` `o`  Toggle
>     - `zR` `*`  Open all
>     - `zM` `=`  Close all
>     - `zj`      Next fold
>     - `zk`      Previous
> - Misc
>     - `s`       Toggle sort
>     - `x`       Zoom window in/out
>     - `q`       Close window
>     - `?`       Help

---

<h3 id="4">CtrlP</h3>

> - `<C-p>`   Open the CtrlP prompt in find file mode
> - In the prompt
>     - `<C-d>`   Toggle full-path/filename-only
>     - `<C-r>`   Toggle string/regexp
>     - `<C-f>`   Forward search mode
>     - `<C-b>`   "Backward" search mode
>     - `<Tab>`   Auto-complete dir
>     - `<S-Tab>` Toggle the match window & the prompt
>     - `<C-c>` `<Esc>`   Exit
> - Moving
>     - `<C-j>`   Move selection down
>     - `<C-k>`   Move up
>     - `<C-a>`   Move to the start
>     - `<C-e>`   Move to the end
>     - `<C-h>`   Move left
>     - `<C-l>`   Move right
> - Edit
>     - `<bs>`    Delete preceding
>     - `<del>`   Delete current
>     - `<C-w>`   Delete a preceding inner word
>     - `<C-u>`   Delete the input field
> - Browsing input history
>     - `<C-n>`   Next
>     - `<C-p>`   Previous
> - Opening/Creating a file
>     - `<cr>`    Open
>     - `<C-t>`   Open in new tab
>     - `<C-v>`   Open in a vertical split
>     - `<C-y>`   Create a new file and its parent directories
> - Opening multiple files
>     - `<C-z>`   Mark/Unmark a file to be opened with `<C-o>`
>     - `<C-o>`   Open files marked by `<C-z>`
> - Function keys
>     - `<F5>`
>         - Refresh the match window and perge the cache for the current directory
>         - Remove deleted files from MRU list
>     - `<F7>`
>         - MRU mode
>             - Wipe the list
>             - Delete entries marked by `<C-z>`
>         - Buffer mode
>             - Delete entries under the cursor
>             - Delete entries marked by `<C-z>`
> - Inside the match window  
>     Use the leading character to cycle through match lines.

---

<h3 id="5">Python-mode</h3>

> - Motion & Operation
>     - C     Class
>     - M     Method
>     - example:  
>         `[M` Jump to previous class or method  
>         `daC`   Delete the class exclude
> - Doc. show
>     - `K`   :PymodeDoc  Show documentation
> - Run code
>     - `<leader>r`
> - Breakpoints
>     - `<leader>b`
> - CodeCheck
>     - `:PymodeLint`     Check code in current buffer
>     - `:PymodeLintToggle`   Toggle code checking
>     - `:PymodeLintAuto` Fix PEP8 errors in current buffer automatically
> - Rope
>     - `<C-c>d`       Rope show doc
>     - `<C-Space>`    Toggle autocompletion
>     - `<CR>`         Insert the autocompletion entry
>     - `<C-p>/<C-n>`  Cycle through entries
>     - `<C-c>g`       Find definition
>     - `<C-c>rr`      Rename method/funtion/class/variable
>     - `<C-c>r1r`     Rename module/package
>     - `<C-c>ra`      Autoimport
>     - `<C-c>ro`      Organize imports

---

<h3 id="6">Syntastic</h3>

> - `<leader>sc`      :SyntasticCheck<CR>
> - ` :SyntasticInfo <language> `    List the checkers of specific languages

---

<h3 id="7">Vim-Trailing-Whitespace</h3>

> - `<leader>f<Space>`    :FixWhitespace<CR>

---

<h3 id="8">YCM</h3>

> - `<TAB>`       Select the first completion string and then cycle forward
> - `<S-TAB>`     Select the previous completion string.Only in GVim
> - `<C-Space>`   Invoke the completion menu for semantic completion
> - `<leader>d`   :YcmShowDetailedDiagnostic<CR>  Show the full diagnostic text

---

<h3 id="9">Ultisnips</h3>

> - `<C-Space>`   ExpandTrigger
> - `<C-tab>`     ListSnippets
> - `<C-j>`       JumpForward
> - `<C-k>`       JumpBackward

---

<h3 id="10">Vim-Markdown</h3>

> - `gx`      <Plug>Markdown_OpenUrlUnderCursor
> - `ge`      <Plug>Markdown_EditUrlUnderCursor   Useful for relative markdown links.
> - `]]`      <Plug>Markdown_MoveToNextHeader
> - `[[`      <Plug>Markdown_MoveToPreviousHeader
> - `][`      <Plug>Markdown_MoveToNextSiblingHeader
> - `[]`      <Plug>Markdown_MoveToPreviousSiblingHeader
> - `]c`      <Plug>Markdown_MoveToCurHeader
> - `]u`      <Plug>Markdown_MoveToParentHeader
> - `:HeaderIncrease`
> - `:HeaderDecrease`
> - `:SetexToAtx`
> - `:Toc`    Create a quickfix vertical window navigable table of contents with headers.
> - `:Toch`   Create horizontal
> - `:Toct`   Create in a new tab

---

<h3 id="11">TaskList</h3>

> - `<leader>t` <Plug>TaskList  Open results window
>
> - In the result window
>   - `j/k`     Select result in the list.The cursor moves as the window focus updates
>   - `q`       Quit and restore original cursor position
>   - `e`       Exit and keep results window open
>   - `<CR>`    Quit and keep current cursor position

---

<h3 id="12">BufExplorer</h3>

> - `<leader>be`    :BufExplorer        Start exploring in the current window
> - `<leader>bt`    :ToggleBufExplorer  Toggle bufexplorer
> - `<leader>bs`    :BufExplorerHorizontalSplit
> - `<leader>bv`    :BufExplorerVerticalSplit

> ---
> - Inside the buffer window
>   - `<CR>` `o`    :Open the buffer into the current window
>   - `<S-CR>` `t`  :Open the buffer into another tab
>   - `b`           Fast buffer switching with `b<bufnum>`
>   - `d`           :delete the buffer.Clear the 'buflisted'
>   - `D`           :wipeout the buffer.
>   - `q`           Quit.Close the bufexplorer.

---

<h3 id="13">Vim-Surround</h3>

> - `ds`  Delete surroundings.Take one arguement(`Surround-targets`).
> - `cs`  Change surroundings.Take two arguements(`Surround-targets`,`Surround-replacements`)
> - `ys`  Adding surroundings.Take two arguements(`Surround-targets`,`Surroundings`)
> - `yss` Adding surroundings.Take one arguement(`Surroundings`).Operate on the current line,ignoring leading whitespace.
> - `vS`  Adding surroundings in visual mode.Take one arguement(`Surround-targets`)
> - `cS`  Like `cs`,but place the surrounded text on its own line(s).
> - `yS`  Like `ys`,& the case with `cS`.
> - `ySS` Like `yss`,& the case with `yS`.

> ---
> - Surround-targets :
>     - Eight punctuation marks : `)`,`]`,`}`,`>`,& `(`,`[`,`{`,`<`.The opening mark will trim contained whitespace.
>     - Three quote marks : `'`,`"`,`` ` (`&#96;`).
>     - HTML or XML tags : `t`.
>     - Vim text-objects : `w/W`,`s`,`p`.For `ds`&`cs`,used as no-op(ignoring the include/exclude [`i`/`a`]).

> ---
> - Surround-replacements :
>     - *Seven* punctuation marks : `)`,`]`,`}`,`>`,& `(`,`[`,`{`.The opening mark will append an whitespace inside.
>     - HTML or XML tags : `t`,`<`,`<C-t>`.Default the attributes are kept.End inputting using `>` to discard the attributes.The `<C-t>` will open new lines.

---
