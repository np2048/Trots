
# Vundle bundle

[Vundle](https://github.com/VundleVim/Vundle.vim.git) is a plugin manager for [VIM](https://www.vim.org/).

## Installation

    git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle

## Configuration

Add the following lines to your [.vimrc](vimrc.md) file:

    " Vundle
    set nocompatible
    filetype off 
    set rtp+=~/.vim/bundle/Vundle.vim
    call vundle#begin()
    Plugin 'VundleVim/Vundle.vim'
    " Add plugins here
    call vundle#end()
    filetype plugin indent on
    set shell=/bin/bash

After the *" Add plugins here* line you can insert the lines for plugins that you want to use in VIM:

    Plugin 'GITHUB_USER_NAME/PLUGIN_REPOSITORY_NAME'

>Example:

    Plugin 'tpope/vim-surround'

This is for [Vim-surround](surround.md) plugin.

## Plugin sources

With *Vundle* you can manage plugins not only from GitHub, but also from almost any other sources:

    " git repos on your local machine (i.e. when working on your own plugin)
    Plugin 'file:///home/USERNAME/PATH/TO/PLUGIN'

    " Git plugin not hosted on GitHub
    Plugin 'git://git.wincent.com/command-t.git'

## Install plugins from added list

When you add plugins to your .vimrc file they are not installed immediately of VIM start. You have run a command in VIM to install the plugins:
    
    :PluginInstall

## Search and install plugin

To find and install a new plugin by name start VIM and type:

    :PluginSearch PLUGIN_NAME

>Example:

    :PluginSearch colorscheme
    ...
    <list of available VIM color schemes>

To install a plugin from the list, just move the VIM cursor to the line if search results and press ‘i’

Now copy the line:
    
    Plugin NEW_PLUGIN_NAME

And paste it in the plugins list at your .vimrc file. More detailed instruction you can find in the tutorial: https://linuxhint.com/vim-vundle-tutorial/


## List installed plugins in VIM

    :PluginList

## Remove a plugin 

You can also remove a Plugin using *Vundle* Plugin Manager.

First run ‘:PluginList’ command to list all the installed VIM plugins:

    :PluginList

Then move the cursor to the plugin that you want to delete and press 
    
    <Shift>+<D>

The plugin should be deleted.

When it's done open .vimrc file and remove the line for deleted plugin from *Vundle* plugins list save the file.


## Read more

- Official: [https://github.com/VundleVim/Vundle.vim.git](https://github.com/VundleVim/Vundle.vim.git)
- Tutorial: [https://linuxhint.com/vim-vundle-tutorial/](https://linuxhint.com/vim-vundle-tutorial/)