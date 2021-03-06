# ansible-macos-homebrew
Manages macOS app installation with [homebrew](https://brew.sh)

[![Build Status](https://img.shields.io/travis/feffi/ansible-macos-homebrew.svg)](https://travis-ci.org/feffi/ansible-macos-homebrew) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-macos-homebrew/total.svg)](https://github.com/feffi/ansible-macos-homebrew) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-macos-homebrew.svg?style=social&label=Fork)](https://github.com/feffi/ansible-macos-homebrew) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-macos-homebrew.svg?style=social&label=Star)](https://github.com/feffi/ansible-macos-homebrew) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-macos-homebrew.svg?style=social&label=Watch)](https://github.com/feffi/ansible-macos-homebrew) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1) [![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/feffi/ansible-macos-homebrew/blob/master/LICENSE)

## Requirements

* maxOS >= 10.10
* Ansible 2.3

### ansible.cfg
```
hash_behaviour = merge
```

## Install
Just add the role to your ``requirements.yml`` file:
```yaml
- src: https://github.com/feffi/ansible-macos-homebrew.git
  name: feffi.macos-homebrew
```

## Role Variables

Available variables are listed below, along with default values:

```yaml
macos_homebrew:
  install:
    # Path to install homebrew
    prefix: "/usr/local"
    path: "Homebrew"

    # Path to link homebrew's brew command
    bin: /usr/local/bin

    # Path to install homebrew casks
    cask: /Applications

  # Homebrew taps to attach to
  taps:
    - { name: "homebrew/dupes" }
    - { name: "caskroom/cask" }
    - { name: "caskroom/versions" }

  # Packages to install or uninstall.
  packages: []

  # Casks to install or uninstall.
  casks: []

  # Brewfile paths to process
  brews: []
```

## Dependencies
None.

## Example Playbook

```yaml
---
- hosts: all
  vars:
    macos_homebrew:
      packages:
        - node
      casks:
        - "google-chrome"
      brews:
        - "/Users/feffi/dotfiles/Brewfile-core"
        - "/Users/feffi/dotfiles/Brewfile-other"
  roles:
    - { role: feffi.macos-homebrew }
```
