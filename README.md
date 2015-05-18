# Ansible Role: Git

[![Ansible Galaxy](http://img.shields.io/badge/galaxy-novuso.git-000000.svg)](https://galaxy.ansible.com/list#/roles/3816)
[![MIT License](http://img.shields.io/badge/license-MIT-003399.svg)](http://opensource.org/licenses/MIT)
[![Build Status](https://travis-ci.org/novuso/ansible-role-git.svg)](https://travis-ci.org/novuso/ansible-role-git)

An Ansible role that manages Git on Ubuntu 14.04

## Requirements

None

## Role Variables

Ansible variables are listed here along with their default values:

`git_flow` flags whether or not to install `git-flow`.

    git_flow: true

`git_config_user_name` sets the global user name in git config.

    git_config_user_name: ~

`git_config_user_email` sets the global email in git config.

    git_config_user_email: ~

`git_config_core_editor` sets the default editor in git config.

    git_config_core_editor: "vim"

`git_config_core_excludesfile` sets the global gitignore file.

    git_config_core_excludesfile: "~/.gitignore_global"

`git_config_color_ui` flags whether or not to enable color UI.

    git_config_color_ui: "true"

`git_config_push_default` sets the git config push setting.

    git_config_push_default: "simple"

`git_aliases` is a list of aliases added to git config.

By default, the following aliases are used:

    git_aliases:
    - "new = flow init --showcommands"
    - "flist = flow feature list"
    - "fstart = flow feature start"
    - "fdone = flow feature finish"
    - "fpub = flow feature publish"
    - "fpull = flow feature pull"
    - "fdiff = flow feature diff"
    - "ftrack = flow feature track"
    - "fbase = flow feature rebase"
    - "fco = flow feature checkout"
    - "fdel = flow feature delete"
    - "rlist = flow release list"
    - "rstart = flow release start"
    - "rdone = flow release finish"
    - "rpub = flow release publish"
    - "rtrack = flow release track"
    - "rdel = flow release delete"
    - "hlist = flow hotfix list"
    - "hstart = flow hotfix start"
    - "hdone = flow hotfix finish"
    - "hpub = flow hotfix publish"
    - "hdel = flow hotfix delete"
    - "slist = flow support list"
    - "sstart = flow support start"
    - "fconf = flow config"
    - "ptag = push --tags"
    - "pdev = push origin develop"
    - "udev = pull origin develop"
    - "stat = status -sb"
    - "co = checkout"
    - "ec = config --global -e"
    - "cm = !git add -A && git commit -m"
    - "save = !git add -A && git commit -m 'SAVEPOINT'"
    - "wip = !git add -u && git commit -m 'WIP'"
    - "undo = reset HEAD~1 --mixed"
    - "amend = commit -a --amend"
    - "alias = !git config --get-regexp ^alias | sed -e 's/^alias.//' -e 's/\\\\ /\\\\ =\\\\ /' | less"

`git_ignore` is a list of global gitignore entries. Each entry may designate:

* **heading** *required* Human-readable comment for the section
* **entries** *required* List of gitignore patterns

By default, the following gitignore entries are included:

    git_ignore:
    - heading: "Linux"
      entries:
      - "*~"
      - ".directory"
      - ".Trash-*"
    - heading: "Sublime Text"
      entries:
      - "*.tmlanguage.cache"
      - "*.tmPreferences.cache"
      - "*.stTheme.cache"
      - "*.sublime-workspace"
      - "*.sublime-project"
      - "sftp-config.json"
    - heading: "Vim"
      entries:
      - "[._]*.s[a-w][a-z]"
      - "[._]s[a-w][a-z]"
      - "*.un~"
      - "Session.vim"
      - ".netrwhist"
    - heading: "Composer"
      entries:
      - "composer.phar"
    - heading: "Vagrant"
      entries:
      - ".vagrant/"
    - heading: "Sass"
      entries:
      - ".sass-cache"
      - "*.css.map"

## Dependencies

None

## Example Playbook

    ---
    - hosts: all
      vars:
      - git_flow: false
      - git_aliases:
        - "co = checkout"
        - "ec = config --global -e"
      - git_ignore:
        - heading: "Linux"
          entries:
          - "*~"
          - ".directory"
          - ".Trash-*"
      roles:
      - novuso.git

## License

This is released under the [MIT license](http://opensource.org/licenses/MIT).
