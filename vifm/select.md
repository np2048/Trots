
# Vifm files selection commands

## Select all files

    gg v G

Select all files and move cursor to the same positon:

    mm gg v G 'm

>mm command sets mark to the m letter and 'm makes vifm go to the m mark. You can use any other letter for that temporary mark.

## Toggle file selection

    t

## Visual selection

- Enter in Visual selection mode — **v**
- Accept visual selection and back to normal mode — **<Enter\>**
- Cancel visual selection — **<Escape\>**

## Append selection

- Keep selected files and enter into visual selection mode — **av**
- Change action when in append selection mode (append / remove / invert) — **Ctrl+G**
- Restore previous visual selection — **gv**

## Key buindings

### Ctrl+A to select all files

    nnoremap <c-a> mmggvG<cr>'m

### Space to toggle secection of current file

    nnoremap <space> t
