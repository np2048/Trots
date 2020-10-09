
# How to install Jekyll on an Arch-based Linux disto

>This tiny trop is based on the [installation guides](https://jekyllrb.com/docs/installation/other-linux/#archlinux) available at official Jekyll site and a GitHub artice [Creating a GitHub Pages site with Jekyll](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll).

## Install Ruby

Jekyll is a ruby gem

    $ sudo pacman -S ruby base-devel
    $ sudo pacman -S ruby-full build-essential zlib1g-dev

## Install Bundler

[Bundler](https://bundler.io) is a Ruby gems manager.

    $ gem install bundler

## Install Jekyll

    $ sudo pacman -S ruby-jekyll-sass-converter



