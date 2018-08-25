### Question: How to get Sublime 3 enabled with vim mode? [sublime] [vi] [productivity]
In user setting, change "ignored_packages": ["Vintage"] to ignored_packages": []
https://www.sublimetext.com/docs/2/vintage.html

### Question: Sublime on Mac is not allowing repeat keys. How to resolve this? [sublime] [productivity]
You can disable this feature for just Sublime Text by issuing the following command in your terminal (*not* the Sublime Text console):
defaults write com.sublimetext.3 ApplePressAndHoldEnabled -bool false
https://gist.github.com/kconragan/2510186

### Question: What is the package that needs to be installed in Sublime to get markdown support? [sublime] 
 * Download MarkDownPreview: Cmd-Shift-P - Package Control: Install Package
 * Use: Cmd-Shift-P - Markdown Preview: preview in browser