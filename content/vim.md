+++
date = "2015-09-05"
title = "Helpful VIM snippets"
draft = false

+++

I've been using VIM as my primary editor for awhile now.
All of these snippets are from my vimrc dot file, which you can find in my rc github repo, [here](https://github.com/nawns/rc/). Its fairly minimal and every line is commented with a description.


{{< highlight vim >}}
set mouse=a
map <ScrollWheelUp> <C-Y>
map <ScrollWheelDown> <C-E>
{{< /highlight >}}
Enables mouse and scrollwheel support. Not sure why this isn't enabled by default, but it lets you scroll with your scroll wheel and click to reposition the cursor.

{{< highlight vim >}}
cnoreabbrev Q q
cnoreabbrev W w
cnoreabbrev WQ wq
cnoreabbrev wQ wq
cnoreabbrev Wq wq
{{< /highlight >}}
Alias Q to q, W to w, WQ to wq, etc. I put these in my config since I type erratically sometimes, mistyping while trying to save or quit vim.

{{< highlight vim >}}
inoremap jk <ESC>
{{< /highlight >}}
Map jk to switch to normal mode, from insert mode. You need to type the jk fast so it will actually register as a single command. If you want to actually type jk then type slower. This is a lot faster than repositioning your fingers off of the typing keys to escape.

{{< highlight vim >}}
nnoremap <BS> <C-^>
{{< /highlight >}}
Maps backspace to switch files (if you have multiple files open). This is useful if you want to have two files open without using tabs or splits.

{{< highlight vim >}}
set iskeyword-=_
{{< /highlight >}}
Adds _ to word boundary list. The command 'ciw' will replace the word under your cursor, and adding _ to the word boundary will count a phrase like two_dogs as two separate words, so ciw will replace just one word. This is personally preference and somewhat depends what you're working on.

{{< highlight vim >}}
set display=lastline
{{< /highlight >}}
If you have word wrapping on (:set wrap), and the wrapped line is very long, vim will hide part of it with @ characters. This command seems to fix it.

{{< highlight vim >}}
cmap w!! w !sudo tee % >/dev/null
{{< /highlight >}}
Maps the command w!! to go into sudo and save the file as root. This saves you the trouble of saving the file as something else, exiting vim, then reopening as sudo

{{< highlight vim >}}
    " Put plugins and dictionaries in this dir (also on Windows)
    let vimDir = '$HOME/.vim'
    let &runtimepath.=','.vimDir

    " Keep undo history across sessions by storing it in a file
    if has('persistent_undo')
      let myUndoDir = expand(vimDir . '/undodir')
      " Create dirs
      call system('mkdir ' . vimDir)
      call system('mkdir ' . myUndoDir)
      let &undodir = myUndoDir
      set undofile
    endif
{{< /highlight >}}
Persistant undo. This will save your undo history in a file, so whenever you close and reopen vim, your history of undos is still there.

Also, check out these links for more VIM tidbits

* [reddit.com/r/vim](http://www.reddit.com/r/vim)
* [quora.com/What-are-the-most-amazing-things-that-can-be-done-with-Vim](https://www.quora.com/What-are-the-most-amazing-things-that-can-be-done-with-Vim)
