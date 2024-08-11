- [TL;DR](#tldr)
- [Install ZSH](#install-zsh)
- [Enable the zsh-autosuggestions Plugin](#enable-the-zsh-autosuggestions-plugin)
- [Install zsh-autosuggestions Manually](#install-zsh-autosuggestions-manually)


## TL;DR
```sh

```

## Install ZSH
```sh
sudo apt update
sudo apt install zsh
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

After installation, restart your terminal. Zsh with Oh My Zsh provides command completion and autosuggestions.

## Enable the zsh-autosuggestions Plugin
1. Open ~/.zshrc
2. Locate the plugins line and add zsh-autosuggestions to the list. It should look something like this:
```sh
plugins=(git zsh-autosuggestions)
```

## Install zsh-autosuggestions Manually
If the autosuggestions plugin is not working as expected, you may need to install it manually:
```sh
# Clone the zsh-autosuggestions Repository
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions

# Reload Your Zsh Configuration
source ~/.zshrc
```
