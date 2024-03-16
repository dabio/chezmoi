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
   # add to sudoers file
   $ echo 'dan ALL = (ALL) ALL' | sudo tee /etc/sudoers.d/dan > /dev/null
   ~~~

2. [Install Homebrew](https://brew.sh) as normal user:
   ~~~bash
   $ brew analytics off
   $ brew update
   ~~~
3. Generate ssh key (no password)
   ~~~bash
   $ ssh-keygen -t ed25519 -C "dabio@users.noreply.github.com"
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
5. Misc:
   - Disable Spotlight Search Categories
   - [Download Apple Fonts](https://developer.apple.com/fonts/) (SF Mono)
   - Set SF Mono as default for iTerm2
