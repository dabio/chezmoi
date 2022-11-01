# chezmoi

dotfiles with chezmoi

## New Machine

Create new Admin-User (`adm`). Login once and create normal user (`dan`). Switch to normal user.

1. Terminal:
   ~~~bash
   # switch to user with admin permissions
   $ su adm
   # do not show adm account
   $ sudo dscl . create /Users/adm IsHidden 1
   $ sudo chflags hidden /Users/adm
   # change computer name
   $ sudo scutil --set ComputerName 12inch
   $ sudo scutil --set LocalHostName 12inch
   # enable firewall with logging and stealth mode
   $ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setglobalstate on
   $ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setloggingmode on
   $ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setstealthmode on
   $ sudo pkill -HUP socketfilterfw
   ~~~

2. [Install Homebrew](https://brew.sh) as normal user:
   ~~~bash
   $ cd ~
   $ mkdir .homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C .homebrew
   $ export PATH=~/.homebrew/bin:~/.homebrew/sbin:$PATH
   $ brew analytics off
   $ brew update
   ~~~
3. Install `chezmoi` and dotfiles:
   ~~~bash
   $ brew install chezmoi
   $ chezmoi init --apply git@github.com:dabio/chezmoi.git
   ~~~
4. Install Brewfile
   ~~~bash
   $ brew bundle
   ~~~
