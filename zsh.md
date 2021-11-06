# Terminal

The terminal I use on a daily basis is [zsh](https://en.wikipedia.org/wiki/Z_shell). The Z Shell
is a Unix shell which is in the family of the [sh](https://en.wikipedia.org/wiki/Bourne_shell) shell (shell command line interpreter)
that has many improvements on top of [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)), [ksh](https://en.wikipedia.org/wiki/KornShell), and [tcsh](https://en.wikipedia.org/wiki/Tcsh).
I also use the default terminal that is provided by my macbook air.
I find it important to keep a minimalist setup to make sure everything is
light and efficient. Zsh is installed on all of my computers (Window and macOS).

## Brew

I strongly believe that [brew](https://brew.sh/) is mandatory for programming.
Whether you have macOS, Linux or Windows, you should familiarize yourself
with a package manager. I use brew, because I use a macbook, but it can be [chocolatey](https://chocolatey.org/) for
Windows.

If Homebrew (or brew) is not installed on your computer:
[Linux or Windows (WSL)](https://medium.com/@edwardbaeg9/using-homebrew-on-windows-10-with-windows-subsystem-for-linux-wsl-c7f1792f88b3),
[macOS](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-homebrew-on-macos)

## Oh My Zsh

The [Oh my zsh](https://ohmyz.sh/#install) is an open source project
that helps us manage the Zsh configuration with plugins, themes, alias and more.
To install it, simply run -

```zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Ps- The [Wiki](https://github.com/ohmyzsh/ohmyzsh/wiki) holds additional information
like cheatsheets and more.

Zsh comes with a configuration file called `.zshrc`. the file is located
in the user's home directory. To edit the configuration, simple run -

```zsh
code ~/.zshrc
```

### Theme

The theme I am using is called `minimal` on the [themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) available.
Simply make the environnement variable `ZSH_THEME` to equal the theme you want-

```zsh
ZSH_THEME="minimal"
```

### Zsh syntax highlighting

My terminal has syntax highlighting which helps visualize the available commands and makes
everything much more elegant. To set it up, simply add `zsh-syntax-highlighting` to your plugins array
like-

```zsh
plugins=(
  zsh-syntax-highlighting
  # ...
)
```

The default colors where not to my liking, so I changed the default colors with-

```zsh
ZSH_HIGHLIGHT_STYLES[suffix-alias]=fg=cyan,underline
ZSH_HIGHLIGHT_STYLES[precommand]=fg=cyan,underline
ZSH_HIGHLIGHT_STYLES[arg0]=fg=cyan
```

which are added in the configuration after the aliases. 

### BSD and GNU
The problem with
macOs is that it comes with the command line utility from the BSD world, which
has different (say minimal) interpretation of commands. For example,
`sed` does not accept group-

![Trying to replace every characters with *](./zsh/zsh-sed-bsd.png)

As you can see, the characters aren't replaced with *.
To fix this issue, I have found the GNU alternative package
on the brew repository and installed them.

for `sed`, simply run-

```zsh
brew install gnu-sed
```

![Installing gnu-sed](./zsh/brew-gnu-sed.png)

and add an alias to the Zsh configuration to make the gnu `sed` the default `sed`-

```zsh
alias sed="gsed"
```

And now, the `sed` command works as expected

![GNU sed works](./zsh/zsh-sed-gnu.png)

Change each characters to a *.

I did the same for `grep` and `egrep` with-

```zsh
brew install grep
```

and aliases are-

```zsh
alias egrep="gegrep --color"
alias grep="ggrep --color"
```

The `--color` is because it was not displaying the reddish color
when using grep.

![Example of GNU grep](./zsh/grep.png)

### Git

For my zsh plugins, I also use the `git` plugin. It helps with the shortcuts
when typing certain commands. Furthermore, it makes git command available on the terminal. The
shortcuts can be found [here](https://github.com/ohmyzsh/ohmyzsh/wiki/Cheatsheet). Also,
I like to add my own alias to `git push --set-upstream origin $(current_branch)`. Instead of
`gpsup`, it is `gps`. The `git status` command is `gs` with a alias. 

```zsh
plugins=(
  git
  # ...
)
alias gps="gpsup"
alias gs="git status"
```

### Zsh autosuggestions

I also get the `zsh-autosuggestions` to make sure I can keep
track of my last commands. It saves me a lot of time when writing complex (repetitive)
commands.

```zsh
plugins=(
  zsh-autosuggestions
  # ...
)
```

![Image showing the suggestion](./zsh/complete.png)

### Gitignore

A new plugin in my configuration is the `gitignore` plugin. It helps
me create ignore files. For example, I need a ignore file for node, I simply run-
```zsh
gi node >> .gitignore
```

Here is the plugins array-

```zsh
plugins=(
  gitignore
  # ...
)
```

In summary, we saw how to configure your terminal to be
minimal, whilst still having access to powerful tools such
as oh my zsh.
