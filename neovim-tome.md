# TOME OF NEOVIM

Source: [Step up your game with Neovim](https://medium.com/life-at-moka/step-up-your-game-with-neovim-62ba814166d7)

## Install and configure Neovim (on MacOS)

1. Install NeoVim using Homebrew

```
$ brew install neovim
```

2. Create config directory

```
$ mkdir ~/.config/nvim
```

3. Install a package manager (e.g. Plug, the minimalist plugin manager)

```
$ curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

4. Add the following lines to `~/.config/nvim/init.vim` (using Neovim, ideally)

```
call plug#begin("~/.config/nvim/plugged")
  " Plugin Section
call plug#end()
" Everything after this line will be the config section
```

5. Add ALE for code linting

6. If using standardrb for linting (isntead of rubocop), disable rubocop. Add the following line to `~/.config/nvim/init.vim`:

```
" " Disable rubocop because it conflicts with standardrb
let g:ale_linters_ignore = {
 \ 'ruby': ['rubocop']
 \ }
```
