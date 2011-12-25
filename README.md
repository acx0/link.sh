## About

[link.sh] allows you to easily link and manage your git-controlled dotfiles on
any machine you happen to be working on, permanently or temporarily.

## Setup

Specify the git repository containing the dotfiles by setting the `SOURCE_DIR`
variable. link.sh will look in `~/etc` by default. 

The configuration file (~/etc/.link-files` by default), contains an array of
the files to be managed. It should be set up such that index 2k is the source
file in the repository, and index 2k+1 is the destination of the link.

Example:
    # ~/etc/.link-files

    FILES=(
        bashrc          $HOME/.bashrc
        gitconfig       $HOME/.gitconfig
        inputrc         $HOME/.inputrc
        profile         $HOME/.profile
        ssh/config      $HOME/.ssh/config
        vim             $HOME/.vim
        vimrc           $HOME/.vimrc
        zshrc           $HOME/.zshrc
    )

## Usage

Run the script without any arguments to see the current status of the files
being managed:

    ./link.sh

If the script shows existing files, back them up with:

    ./link.sh -b

This will backup the existing dotfiles into `~/etc.bak` (as specified in
`BACKUP_DIR`). Useful when working on a machine temporarily.

To write the symlinks for files that don't exist, use the `-w` flag,
otherwise, overwrite them by adding the `-f` flag:

    ./link.sh -w
    ./link.sh -wf

To restore the envinronment to its original state, use:

    ./link.sh -r

Use the `-h` flag to see an overview of all available options:

    ./link.sh -h
