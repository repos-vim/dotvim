# This is just a starting point...
I love vim because it is FAST, lightweight, powerful, works in the commandline, and is mostly OS independent. That being said, some of the default settings are no good, and there is a lot of missing functionality.  I have developed a set of customizations to vim that fix these problems and will allow you to sync your vim customizations across the major operating systems.

Everyone has their own tastes, and will probably want to customize their setup further, so my vimrc is just a starting point.  I hope that you will be able to fork my repository and customize your own from there!  By using my vimrc as a starting place, you will save yourself a good deal of unnecessary frustration and more quickly be able to harness the full power of vim.

Please let me know if you get stuck in the install process (make a github issue) and I will try to help out.

# Installation

### 1. Download the repository and run install script

IMPORTANT: We assume that you have bash installed and that you want your vimfiles should be installed in your $HOME folder.  If either of these isn't the case, then I suggest oppening up the install.sh script and trying to duplicate the commands by hand (it isn't complicated at all).

If you are on a Mac or Linux Machine, run

	git clone https://github.com/johndgiese/dotvim.git ~/.vim
    sh ~/.vim/install.sh

if you are on a windows machine run

	git clone https://github.com/johndgiese/dotvim.git ~/vimfiles
    sh ~/vimfiles/install.sh

### 2. Install optional programs used by plugins

My setup uses the vundle plugin manager.  If any of the plugins give you
trouble, you can comment them out in your vimrc (just look for the lines that
start with Bundle).

#### Ctags

Ctags is a program that parses your code and generates links between files.  Ctags is used by a few plugins that I have, and they will complain if you don't have them installed.  You can comment out the plugins in the vimrc file, but I reccomend trying to install ctags.  It is super useful.  You can read about it [here](http://ctags.sourceforge.net/).

On Ubuntu this is:

    sudo get-apt install ctags

On Mac OSX with homebrew:
  
    brew install ctags-exuberant

On Windows you will have to find the executable online.

#### Vipy Plugin

If you want to use the vipy plugin you will need to install ipython and pyzmq, and finally run another batch script, as described in the install instructions [here](https://github.com/johndgiese/vipy).  Basically it is:

    sudo apt-get update
    sudo apt-get install libzmq-dev
    sudo apt-get install python-zmq

#### Make Programs for various File Types

On Mac OSX with homebrew:

    brew install ptidy

# How this vim setup differs from normal vim

The most important three changes are:

* ESC in insert mode is now jk (quickly, one after another)
* Swaps the semicolon and colon, because you use colon a lot and almost never use semicolon
* ,v opens the vimrc (which auto runs upon saving)

These three shorcuts will save you a lot of time, and keep your hands more comfortable when typing.  I believe one of the main benefits of vim is that it allows you to keep your hands on the keyboard so you can type more faster.

* The new leader key is , instead of /
* ,1 lets you browse files
* ,2 lets you view the structure of your file
* ,3 lets you see all the open buffers
* ,4 lets you navigate the undo history (required vim 7.3)
* ,5 runs your make program, which is file-type dependent (see below)
* Searches (pressing / or ? in normal mode) now have \v prepended so that vim uses the verymagic mode (i.e. it uses normal python/perl regular expressions instead of its own version)
* ,/ clears search highlighting
* ,s (i.e. ,s) starts spell search
* Much better colorscheme
* ,o opens the colorscheme file for easy updating if you use different languages
* ,g will do a google search on the current selection
* ,w will highlight whitespace at the ends of lines, and ,W will delete it.
* Autocomplete uses TAB unless there is white space before the cursor
* Tabs are replaced with four spaces
* CTRL-P opens the super awesome fuzzy file browser (:h ctrlp for details)

The following other plugins are installed:
* Vundle - lets you manage plugins more easily (look in the bundle directory)
* Nerdtree - browse files inside vim
* Tagbar - view the structure of your files using ctags
* Gundo - graphical view of undo branches; see the [vimcast](http://vimcasts.org/episodes/undo-branching-and-gundo-vim/)
* Fugitive - use git inside vim!  See the [vimcasts](http://vimcasts.org/episodes/archive) about it.
* Surround - work better with parenthesis and other nesting structures.  Type :h surround
* Vipy - use ipython inside vim!  python code completion, etc. see [the repo](https://github.com/johndgiese/vipy/blob/master/README.md)
* Autoclose - autoclose parenthesis
* Snipmate - add snippets of commonly usedcode
* Session - save the window structure and files opened, for easy switching between projects
* Unimpaired - provides various mappings for operating with pairs
* Powerline - a colorful and useful statusline
* Csscolor - css color highlighting
* Tabular - for aligning stuff (see [this vimcast](http://vimcasts.org/episodes/aligning-text-with-tabular-vim/))
* Supertab - tab autocompletion
* CTRLp - lets you browse files really quickly
* Syntastic - syntax highlighting for a variety of different files
* ... a few other little ones

## Run and Debug various file types
,5 is my universal "run file" key, and "SHIFT-,5" is my debug file key.  These
are loose terms.  Not all files have an

### Running a file
* python   -- runs file (in vipy plugin)
* html     -- run tidy, filling the quickfix list with bugs in your html
* latex    -- converts to a dvi and opens it in a viewer (requires Miketex)
* c        -- compiles code with make (Linux only), 
* markdown -- generates an html file with the same name (i.e. test.mkd -- > test.html) and then opens it in chrome (linux only, need markdown filter [sudo apt-get install markdown])

### Debuggin a file
* xml      -- formats using xmllint (requires xmllint)
* c        -- runs a.out
* json     -- lint for json (requires node package manager and jsonlint package;
  sudo apt-get install npm && sudo npm install jsonlint -g)

# Maintaining your repo
The structure of this vimrc setup allows easy cross platform use and easy updating of your plugins.  This comes at a cost of it being a little more complicated to maintain (but overall much faster and stable).  Here are a few notes that may help you.

### Commiting changes
If you modify your vimrc file you will likely want to commit these changes to your repository.  Do this like you would for any git repository:

	git add .
	git commit -m "brief description of changes"

finally, if you are hosting your vim setup online you would push to the remote repository:

	git push origin master
	
Note that you may need to update the origin url for the repo (google online if you don't know how to do this)

### Managing plugins
I use Vundle to manage plugins; it is much better than the default way.  Google online if you don't believe me.  Instructions on how to use it [here](https://github.com/gmarik/vundle).

### Updating the VIMRC
You can quickly update the vimrc by pressing <leader>v in normal mode.  When you save it, it will source the changes so that you can see the effects immediatly.  Note that this doesn't always work as expected, so you may have to fully reset vim to use this.

### Updating the Colorscheme
Everyone likes a different colorscheme, so you will probably want to make some updates to mine or change it completely.  To do this you can use type <leader>o to go straight to the file to start editing.  You can use <leader>O to see what syntax groups below the cursor.

If you want to change the name of the colorscheme, you will have to go into your vimrc file and change the name in two places: one for actually loading the colorscheme, and one for enabling the ,o shortcut.

See [this vimcast](http://vimcasts.org/episodes/creating-colorschemes-for-vim/) for details about colorschemes.
