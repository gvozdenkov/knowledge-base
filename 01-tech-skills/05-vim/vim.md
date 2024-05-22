# Vim language

## Verbs

`d` - delete
`w` - word
`c` - change
`>` - indent
`v` - visual select
`y` - yank (copy)

`.` - repeat last change

## Motions

`w` - word
`b` - back

## Text objects

Operate in body of text

`iw` - inner word
`it` - inner tag (html, xml)
`i"` - inner quotes
`ip` - inner paragraph
`as` - a sentence

---

`2j` - down 2 lines
`dw` - delete word
`cw` - change word (replace word in insert mode)

## Tricks

- Autocomplatioin file names

```.vimrc
" Enable auto completion menu after pressing TAB.
set wildmenu

" Make wildmenu behave like similar to Bash completion.
set wildmode=list:longest

" There are certain files that we would never want to edit with Vim.
" Wildmenu will ignore files with these extensions.
set wildignore=*.docx,*.jpg,*.png,*.gif,*.pdf,*.pyc,*.exe,*.flv,*.img,*.xlsx
```

`:<some char/ or path> TAB` to show autocomplition
