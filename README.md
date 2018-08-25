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

### Q: what are some basic concepts for bash shell? [bash]
command line editing, command history, shell and subshell, double quote vs single quote, startup scripts

### Q: difference between double quote vs single quote in bash? [bash]

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
git add .
git commit -m 'test'
git push origin
```
