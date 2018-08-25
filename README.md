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
command line editing (set -o vi), command history (!), shell and subshell, double quote vs single quote, startup scripts, program argument ($1, $#), continuing line (\\), variable (setting a variable must not have space before and after =: test='hello')

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

### Q: What are some basic command line to be productive in GIT [git]
```
git clone <url>
git commit -a -m 'A simple msg'
git push origin
```

### Q: What is a good example of cut command? [Unix]
```
# use space as delimiter and extract first field
cut -d' ' -f1
```
