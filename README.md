#▄▄▄  ▄• ▄▌.▄▄ · .▄▄ ·     ▄▄▄▄· ▄▄▄ . ▄· ▄▌▄▄▄ .
#▀▄ █·█▪██▌▐█ ▀. ▐█ ▀.     ▐█ ▀█▪▀▄.▀·▐█▪██▌▀▄.▀·
#▐▀▀▄ █▌▐█▌▄▀▀▀█▄▄▀▀▀█▄    ▐█▀▀█▄▐▀▀▪▄▐█▌▐█▪▐▀▀▪▄
#▐█•█▌▐█▄█▌▐█▄▪▐█▐█▄▪▐█    ██▄▪▐█▐█▄▄▌ ▐█▀·.▐█▄▄▌
#.▀  ▀ ▀▀▀  ▀▀▀▀  ▀▀▀▀     ·▀▀▀▀  ▀▀▀   ▀ •  ▀▀▀ 
# russ beye's dotfiles

I love a tight running ship, and for a while my ship was leaking. In the past I had used topical dotfiles, but after considering it more, I think I like what [Zach Holman](http://zachholman.com) and others did. So, I forked, edited, and made this mine. Maybe when I get the free time I'll start from scratch, but this was seriously a great starter pack to build from.

If you're interested in the philosophy behind why projects like these are
awesome, you might want to read [Zach's post on the
subject](http://zachholman.com/2010/08/dotfiles-are-meant-to-be-forked/).

## topical

Everything's built around topic areas. If you're adding a new area to your
forked dotfiles — say, "Java" — you can simply add a `java` directory and put
files in there. Anything with an extension of `.zsh` will get automatically
included into your shell. Anything with an extension of `.symlink` will get
symlinked without extension into `$HOME` when you run `script/bootstrap`.

## components

There's a few special files in the hierarchy.

- **bin/**: Anything in `bin/` will get added to your `$PATH` and be made
  available everywhere.
- **Brewfile**: This is a list of applications for [Homebrew Cask](http://caskroom.io) to install: things like Chrome and 1Password and Adium and stuff. Might want to edit this file before running any initial setup.
- **topic/\*.zsh**: Any files ending in `.zsh` get loaded into your
  environment.
- **topic/path.zsh**: Any file named `path.zsh` is loaded first and is
  expected to setup `$PATH` or similar.
- **topic/completion.zsh**: Any file named `completion.zsh` is loaded
  last and is expected to setup autocomplete.
- **topic/install.sh**: Any file named `install.sh` is executed when you run `script/install`. To avoid being loaded automatically, its extension is `.sh`, not `.zsh`.
- **topic/\*.symlink**: Any file ending in `*.symlink` gets symlinked into
  your `$HOME`. This is so you can keep all of those versioned in your dotfiles
  but still keep those autoloaded files in your home directory. These get
  symlinked in when you run `script/bootstrap`.

## install

Run this:

```sh
git clone https://github.com/russbeye/dotfiles.git ~/.dotfiles
cd ~/.dotfiles
script/bootstrap
```

This will symlink the appropriate files in `.dotfiles` to your home directory.
Everything is configured and tweaked within `~/.dotfiles`.

The main file you'll want to change right off the bat is `zsh/zshrc.symlink`,
which sets up a few paths that'll be different on your particular machine.

`dot` is a simple script that installs some dependencies, sets sane macOS
defaults, and so on. Tweak this script, and occasionally run `dot` from
time to time to keep your environment fresh and up-to-date. You can find
this script in `bin/`.

## thanks

I forked [Zach Holman](http://github.com/holman)'s [dotfiles](http://github.com/holman/dotfiles), which is an evolution of [Ryan Bates](http://github.com/ryanb)' excellent
[dotfiles](http://github.com/ryanb/dotfiles). These are insanely reasonable, so consider doing the same. Thanks guys!
