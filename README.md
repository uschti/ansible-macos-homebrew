# ansible-osx-homebrew

Manages macOS app installation with [homebrew](https://brew.sh)

[![Build Status](https://travis-ci.org/feffi/ansible-macos-homebrew.svg?branch=master)](https://travis-ci.org/feffi/ansible-homebrew)

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
    path: /usr/local

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
  roles:
    - { role: feffi.macos-homebrew }
```
