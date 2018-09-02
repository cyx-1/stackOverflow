### Q: How to get Sublime 3 enabled with vim mode? [sublime] [vi] 
In user setting, change "ignored_packages": ["Vintage"] to ignored_packages": []
https://www.sublimetext.com/docs/2/vintage.html

### Q: Sublime on Mac is not allowing keys to be repeated. How to resolve this? [sublime] 
You can disable this feature for just Sublime Text by issuing the following command in your terminal (*not* the Sublime Text console), restart required:
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
git fetch # get the latest info from remote
git pull # update local branch with the latest from remote
git ls # if the alias is setup, git ls shows commit history: git config --global alias.ls 'log --pretty=format:"%C(yellow)%h %cd%Cblue [%cn] %Cred%d - %Creset%s" --decorate --date=format:"%Y-%m-%d %H:%M:%S"' --replace-all
git ls origin/master # shows commit history for a remote branch
git cmp "msg" # add, commit and push, all in one! git config --global alias.cmp '!f() { git add -A && git commit -m "$@" && git push; }; f'
```
http://durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/

### Q: What is a good example of cut command? [Unix]
```
# use space as delimiter and extract first field
cut -d' ' -f1
```
### Q: What is the best technique to remember things? [memory] [open]
anki, github stackOverflow, CDN in Dropbox

Make a search site that uses elasticsearch
https://github.com/appbaseio/reactivesearch/blob/dev/README.md#4-live-demos

### Q: Where are the cheatsheets for common computing topics [cheatsheet] [vi] [git] [chrome] [awk] [sed]
 * [General Cheatsheets](http://overapi.com/)
 * [Git Quick Reference](https://www.dropbox.com/s/i3hzp531puvfsnc/git%20quick%20reference.pdf?dl=0), [Git Quick Reference 2](https://www.dropbox.com/s/59qpq9juxmcamou/git%20quick%20reference%202.pdf?dl=0)
 * [Vim Quick Reference](https://www.dropbox.com/s/sfdiwdhsr4whthe/vim%20quick%20reference.png?dl=0)
 * [Chrome Quick Reference](https://www.dropbox.com/s/ll1cai8kpa68gm1/chrome%20quick%20reference%20mac.pdf?dl=0)
 * [SED Quick Reference](https://www.dropbox.com/s/mj4lswzvib1baxq/sed%20quick%20reference.png?dl=0)
 * [AWK Quick Reference](https://www.dropbox.com/s/qyyfxm4kibbdx2x/awk%20quick%20reference.pdf?dl=0)

### Q: What is the best way to transfer information between work and home devices? [productivity]
 * Inbound Method 1: AirDrop a text file from MBP to IPhone OneDrive, put the file into a company folder (secure, not scanned)
 * Inbound Method 2: commit into github for reading consumption, clone is allowed, but commit is not, but minor modification can be done via source edit directly on github site (not secure, not scanned)
 * Inbound / Outbound Method 3: Email (not secure, scanned)
 * Company information does not leave the company intranet

### Q: What are some techniques to boost performance in Java
 * Memory mapping/binary file so that objects need not be created on heap
 * Flyweight pattern so that objects on the heap can be reused
 * Binary transfer over the network to avoid data structure translation
 * Fetch size optimization for queries to avoid latency for network roundtrips
 * Multithreading to utilize more CPU cores (individual core speed is not following Moore's law anymore)
 * Avoid putting time consuming logic in tight loops
 * Separate logic between IO-bound computation and CPU-bound computation. For example let one thread consume bytes over the wire as fast as possible, and let another thread create objects based on bytes consumed
 * String comparison is more expensive than number comparison, so creating lookup table for massive number of comparison can be much better
 * Zero buffer copy 
 * Leverage multiple core on CPU and multiple queue on NIC to transfer bytes faster in parallel streams
 * Pre-compute to get answers ready during UI input 
 * JIT processing. As soon as one independent chunk is ready for the next step, proceed
 * Use paging techniques to avoid sending full payload to the presentation layer
 * Display initial content that can be consumed rather than wait for full completion
 * Perceived performance: Type-ahead, Progress bar

### Q: What are some techniques to be more memory efficient in Java
 * use primitives
 * use certain data structure libraries
 * pull up variables into classes with fewer instances where possible. For example: something is wrong if class with large instance count contains repeated information
 * caching strategy: off-heap, MRU

### Q: What is a quick way to run ElasticSearch onto Mac
Use the unofficial Mac package manager!
Note: I had to uninstall brew to get brew working again. [HomeBrew](https://brew.sh/)
See also: https://stackoverflow.com/a/22855889
```
brew update
brew install elasticsearch
Data:    /usr/local/var/lib/elasticsearch/elasticsearch_yexinchen/
Logs:    /usr/local/var/log/elasticsearch/elasticsearch_yexinchen.log
Plugins: /usr/local/var/elasticsearch/plugins/
Config:  /usr/local/etc/elasticsearch/
/usr/local/Cellar/elasticsearch/6.2.4: 112 files, 30.8MB, built in 5 seconds

Navigate to http://localhost:9200/ and see the following:
{
  "name" : "sti_dJT",
  "cluster_name" : "elasticsearch_yexinchen",
  "cluster_uuid" : "8vk-Xh2vTBeMVIDetBjNNA",
  "version" : {
    "number" : "6.2.4",
    "build_hash" : "ccec39f",
    "build_date" : "2018-04-12T20:37:28.497551Z",
    "build_snapshot" : false,
    "lucene_version" : "7.2.1",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}
```

### Q: What is a quick way to ramp up on ElasticSearch
 * [Elastic Search 101](https://www.dropbox.com/s/4wjyhlagfd720c2/ElasticSearch%20101.pdf?dl=0)
 * [Elastic Search Cheatsheet](https://www.dropbox.com/s/0dw9q8a67j1c3u9/elasticsearch-cheatsheet.txt?dl=0)

### Q: Download a clean PDF representation of a website
 * Open up the site in Safari
 * In the view menu, choose "Show Reader". Shift-CMD-R is the shortcut
 * Export as PDF from Safari