
# Vim surround plugin

[vim-surround](https://github.com/tpope/vim-surround)

## add 

    Hello World!

Wrap the entire line in parentheses:

    yss)
    (Hello World!)

    yss(
    ( Hello World! )
    
Wrap word:
    
    ysiw}
    {Hello} World!

    ysiw{
    { Hello } World!

## delete

    { Hello } World!

    ds{
    Hello World!

## change
    
    { Hello } World!
    cs{]
    [Hello] World!
