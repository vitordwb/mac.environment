# My macOS Development Environment

## macOS Settings

### Dock & Mission Control
- Hide Dock automatically
- Medium size
- Genie effect
- Minimize into application icon: `on`
- Show indicators for open apps: `on`
- Show recent apps: `off`
- Double-click window title: `zoom`
- Animate app openings: `on`

### Hot Corners
![Hot Corners](https://github.com/vitordwb/mac.environment/assets/64985648/99429181-4cf4-4f84-8991-fcab15caafa7)

### Displays
![Displays](https://github.com/vitordwb/mac.environment/assets/64985648/d54e8c70-30b9-45c7-af47-3eb25122dee7)

### Security
- FileVault: `on`

### Siri & Spotlight
- Ask Siri: `off`

### Keyboard
- Double space = period: `off`
- Smart quotes/dashes: `off`
- Set `"` for double, `'` for single quotes
![Keyboard](https://github.com/vitordwb/mac.environment/assets/64985648/4fcce15a-86c5-4945-9058-97e486915504)

### Finder
- Create `~/Developer` folder (adds icon)
- Sidebar:
  - Enable all Favorites
  - Add: Library, Developer, Drive, Dropbox
- Hide all tags
- Show all filename extensions
- Auto delete Trash after 30 days
![Finder Sidebar](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iubdw3xlz4v1o9pr4rt4.png)
![Tags](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fke1msfpu67hr6jc53yx.png)
![Filename extensions](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bgy7keufnu3lglp5ehwh.png)

---

## Terminal Tweaks (macOS defaults)
```bash
defaults write com.apple.finder AppleShowAllFiles YES; killall Finder
sudo find / -name .DS_Store -delete; killall Finder
defaults write com.apple.screencapture type jpg; killall SystemUIServer
chflags nohidden ~/Library; killall Finder
defaults write com.apple.finder ShowPathbar -bool true; killall Finder
defaults write com.apple.finder ShowStatusBar -bool true; killall Finder
```

---

## App Store Setup
- Sign into Apple account
- Install: [Xcode](https://apps.apple.com/br/app/xcode/id497799835?l=en&mt=12)

```bash
xcode-select --install
sudo xcodebuild -license accept
```

---

## Homebrew
```bash
sudo spctl --master-disable
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew update
```

### Homebrew Casks
```bash
brew install --cask \
  git \
  visual-studio-code \
  docker \
  insomnia \
  jetbrains-toolbox \
  neovim \
  tmux \
  raycast \
  jesseduffield/lazydocker/lazydocker
```

---

## Git Setup
```bash
brew install git-lfs git-flow
ln -s $(pwd)/git/gitconfig ~/.gitconfig
git config --global user.name "Your Name"
git config --global user.email "you@your-domain.com"
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

### SSH
```bash
ln -s $(pwd)/ssh/config ~/.ssh/config
```

---

## Terminal & Zsh

### Fonts
```bash
brew tap homebrew/cask-fonts
brew install font-hack-nerd-font
cp -r "$(pwd)/fonts/"* ~/Library/Fonts
```

### Oh My Zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
ln -s $(pwd)/zsh/zshrc ~/.zshrc
```

#### Plugins
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
git clone https://github.com/mafredri/zsh-async ~/.oh-my-zsh/plugins/async
git clone https://github.com/lukechilds/zsh-nvm ~/.oh-my-zsh/custom/plugins/zsh-nvm
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
ln -s $(pwd)/zsh/p10k ~/.p10k.zsh
git clone https://github.com/g-plane/zsh-yarn-autocompletions ~/.oh-my-zsh/custom/plugins/zsh-yarn-autocompletions
```

### Terminal Configuration
```bash
ln -s $(pwd)/bash/bash_alias ~/.bash_alias
ln -s $(pwd)/bash/bash_profile ~/.bash_profile
ln -s $(pwd)/bash/bashrc ~/.bashrc
ln -s $(pwd)/bash/flutter ~/.flutter
ln -s $(pwd)/bash/nvm-load ~/.nvm-load
ln -s $(pwd)/bash/yarn-autocompletions.yml ~/.yarn-autocompletions.yml
```
> Edit `.nvm-load` to match installed Node version.

### Terminal Theme
1. Terminal > Settings
2. Gear icon → Import
3. Select `materialshell-dark.terminal`
4. Set as Default

![Theme Import](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/77pu4602w1cusup0rlj1.png)
![Theme Applied](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/gfk6ihhzv4nabghz4z51.png)

---

## Node.js / Yarn

### NVM (Node Version Manager)
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

#### Update to New Version
```bash
nvm install <version> --reinstall-packages-from=$(nvm current)
nvm use <version>
nvm alias default <version>
```

### Yarn
```bash
curl -o- -L https://yarnpkg.com/install.sh | bash
```
