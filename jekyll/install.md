
# How to install Jekyll on an Arch-based Linux disto

>This tiny trop is based on the [installation guides](https://jekyllrb.com/docs/installation/other-linux/#archlinux) available at official Jekyll site and a GitHub artice [Creating a GitHub Pages site with Jekyll](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll).

## Install Ruby

Jekyll is a ruby gem

    $ sudo pacman -S ruby base-devel
    $ sudo pacman -S ruby-full build-essential zlib1g-dev

## Install Bundler

[Bundler](https://bundler.io) is a Ruby gems manager.

    $ gem install bundler

At this point you may get an error in the terminal similar to this one:

    WARNING:  You don't have /home/USERNAME/.gem/ruby/2.7.0/bin in your PATH,
	  gem executables will not run.

It this happens then [add the specified path to the PATH variable](../linux/path-add.md) of your current user profile.

## Update your PATH variable

You have to update your PATH variable in order to be able to run gems.

## Install Jekyll

    $ sudo pacman -S ruby-jekyll-sass-converter

If everything is OK you can continue and [create a new site](new.md) using Jekyll.

