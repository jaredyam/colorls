# Color LS

[![forthebadge](http://forthebadge.com/images/badges/made-with-ruby.svg)](http://forthebadge.com)
[![forthebadge](http://forthebadge.com/images/badges/built-with-love.svg)](http://forthebadge.com)

[![Gem Version](https://badge.fury.io/rb/colorls.svg)](https://badge.fury.io/rb/colorls)
[![Build Status](https://travis-ci.org/athityakumar/colorls.svg?branch=master)](https://travis-ci.org/athityakumar/colorls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=shields)](http://makeapullrequest.com)

A Ruby script that colorizes the `ls` output with color and icons.

<p float="left" align="center">
    <img src="https://user-images.githubusercontent.com/50312506/92303657-aed61a80-efa9-11ea-882e-67fe6fd6c700.png" width="500" />
    <img src="https://user-images.githubusercontent.com/50312506/92303748-7125c180-efaa-11ea-8c3d-6186a307c2d1.png" width="295" />
</p>

---

 This repo is a fork from [athityakumar/colorls](https://github.com/athityakumar/colorls). If you are new to this command-line tool, consider reading the detailed instructions in the original repo before going ahead.

## What's NEW?

- 2020-09-05: Add a new feature for customizing the color of different kind of files
- 2020-09-05: Fix the bug which causes failure to colorize and count unrecognized files

## Installation

```bash
git clone https://github.com/jaredyam/colorls.git
cd colorls

gem build
gem install --local *.gem
```

## Add custom file type color

Suppose you use the `dark_colors.yaml` yml file as your default color scheme. To customize the color of the file types you want to highlight:

```bash
cd ~/.config/colorls
# create with the following code if you don't have one yet.
# cp $(dirname $(gem which colorls))/yaml/dark_colors.yaml ~/.config/colorls/dark_colors.yaml`
subl dark_colors.yaml

# you could open a new section with # [title] for saving the custom color assignment.
# each line is a key-value pair with the format: [file types: X11 color code]
# for example

# Custom file types
py:        gold
md:        pink
pdf:       indianred

```
## Recommended aliases

You could copy the following aliases and functions into your default shell configure file (such as `.zshrc`). Don't forget to `source` it for using these new commands.

```bash
alias ls="colorls --light --sort-dirs --report --dark"
alias lc='colorls -lA --sd'

function tree() {
  colorls --tree="${1:-1}"
}

function cd() {
  builtin cd "$1"
  tree
}
```

