### Q: How to get Sublime 3 enabled with vim mode? [sublime] [vi] 
In user setting, change "ignored_packages": ["Vintage"] to ignored_packages": []
https://www.sublimetext.com/docs/2/vintage.html

### Q: Sublime on Mac is not allowing keys to be repeated. How to resolve this? [sublime] 
You can disable this feature for just Sublime Text by issuing the following command in your terminal (*not* the Sublime Text console):
defaults write com.sublimetext.3 ApplePressAndHoldEnabled -bool false
https://gist.github.com/kconragan/2510186

### Q: What is the package that needs to be installed in Sublime to get markdown support? [sublime] [markdown]
 * Download MarkDownPreview: Cmd-Shift-P - Package Control: Install Package
 * Use: Cmd-Shift-P - Markdown Preview: preview in browser

### Q: What are some basic concepts for bash shell? [bash]
command line editing (set -o vi), command history (!), shell and subshell, double quote vs single quote, startup scripts, program argument ($1, $#, $@), continuing line (\\), variable (setting a variable must not have space before and after =: test='hello')

### Q: What is the difference between double quote vs single quote in bash? [bash]
Single quotes won't interpolate anything, but double quotes will.
https://stackoverflow.com/a/6697781

### Q: What is the importance of shell vs subshell [bash]
subshell inherits environment variable (export) from parent shell, but does not inherit the shell variables defined in the parent shell

### Q: What are some key startup scripts for bash [bash]
.bash_profile gets executed when shell gets initialized (login shell), .bashrc gets executed when entering subshell, it may be a good practice to call .bashrc from .bash_profile. .bash_logout gets executed when exiting login shell.

### Q: How to have bash script read from file or from standard in [bash]
```
while read line
do
  echo "$line"
done < "${1:-/dev/stdin}"
```
https://stackoverflow.com/a/7045517

### Q: How to render markdown files in chrome? [chrome] [markdown]
Download this Chrome extension: Markdown Preview Plus

### Q: What are some basic command line to be productive in GIT [git] [open]
```
git clone <url>
git commit -a -m 'A simple msg' # stage and commit with a msg
git status # show current status
git push # push commits to current remote
git push origin # push commits to remote
git pull # get the latest from remote
git ls # if the alias is setup, git ls shows commit history: git config --global alias.ls 'log --pretty=format:"%C(yellow)%h %cd%Cblue [%cn] %Cred%d - %Creset%s" --decorate --date=format:"%Y-%m-%d %H:%M:%S"' --replace-all
git cmp "msg" # git config --global alias.cmp '!f() { git add -A && git commit -m "$@" && git push; }; f'
```
http://durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/

### Q: What is a good example of cut command? [Unix]
```
# use space as delimiter and extract first field
cut -d' ' -f1
```
### Q: What is the best technique to remember things? [memory] [open]
anki, github stackOverflow
Make a search site that uses elasticsearch
https://github.com/appbaseio/reactivesearch/blob/dev/README.md#4-live-demos

### Q: Where are the cheatsheets for common computing topics [cheatsheet] [vi] [git] [chrome] [awk] [sed]
 * [General Cheatsheets](http://overapi.com/)
 * [Git Quick Reference](https://www.dropbox.com/s/i3hzp531puvfsnc/git%20quick%20reference.pdf?dl=0), [Git Quick Reference 2](https://www.dropbox.com/s/59qpq9juxmcamou/git%20quick%20reference%202.pdf?dl=0)
 * [Vim Quick Reference](https://www.dropbox.com/s/sfdiwdhsr4whthe/vim%20quick%20reference.png?dl=0)
 * [Chrome Quick Reference](https://www.dropbox.com/s/ll1cai8kpa68gm1/chrome%20quick%20reference%20mac.pdf?dl=0)
 * [SED Quick Reference](https://www.dropbox.com/s/mj4lswzvib1baxq/sed%20quick%20reference.png?dl=0)
 * [AWK Quick Reference](https://www.dropbox.com/s/qyyfxm4kibbdx2x/awk%20quick%20reference.pdf?dl=0)
