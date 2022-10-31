# chezmoi

dotfiles with chezmoi

## New Machine

1. Add user to `sudoers` file: `/etc/sudoers.d/dan`:
   ~~~
   dan	ALL = (ALL) ALL
   ~~~
2. [Install Homebrew](https://brew.sh).
3. Install `chezmoi` and dotfiles:
   ~~~bash
   $ brew install chezmoi
   $ chezmoi init --apply git@github.com:dabio/chezmoi.git
   ~~~
4. Install Brewfile
   ~~~bash
   $ brew bundle
   ~~~
