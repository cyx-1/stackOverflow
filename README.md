### Q: How to get Sublime 3 enabled with vim mode? {sublime} {vi}
In user setting, change "ignored_packages": ["Vintage"] to ignored_packages": []
https://www.sublimetext.com/docs/2/vintage.html

### Q: Sublime on Mac is not allowing keys to be repeated. How to resolve this? {sublime} 
You can disable this feature for just Sublime Text by issuing the following command in your terminal (*not* the Sublime Text console), restart required:
defaults write com.sublimetext.3 ApplePressAndHoldEnabled -bool false
https://gist.github.com/kconragan/2510186

### Q: What is the package that needs to be installed in Sublime to get markdown support? {sublime} {markdown}
 * Download MarkDownPreview: Cmd-Shift-P - Package Control: Install Package
 * Use: Cmd-Shift-P - Markdown Preview: preview in browser

### Q: What are some basic concepts for bash shell? {bash}
command line editing (set -o vi), command history (!), shell and subshell, double quote vs single quote, startup scripts, program argument ($1, $#, $@), continuing line (\\), variable (setting a variable must not have space before and after =: test='hello')

### Q: What is the difference between double quote vs single quote in bash? {bash}
Single quotes won't interpolate anything, but double quotes will.
https://stackoverflow.com/a/6697781

### Q: What is the importance of shell vs subshell {bash}
subshell inherits environment variable (export) from parent shell, but does not inherit the shell variables defined in the parent shell

### Q: What are some key startup scripts for bash {bash}
.bash_profile gets executed when shell gets initialized (login shell), .bashrc gets executed when entering subshell, it may be a good practice to call .bashrc from .bash_profile. .bash_logout gets executed when exiting login shell.

### Q: How to have bash script read from file or from standard in {bash}
```
while read line
do
  echo "$line"
done < "${1:-/dev/stdin}"
```
https://stackoverflow.com/a/7045517

### Q: How to render markdown files in chrome? {chrome} {markdown}
Download this Chrome extension: Markdown Preview Plus

### Q: What are some basic command line to be productive in GIT {git}
```
git clone <url>
git commit -a -m 'A simple msg' # stage and commit with a msg
git status # show current status
git push # push commits to current remote
git push origin # push commits to remote
git fetch # get the latest info from remote
git pull # update local branch with the latest from remote
git ls # if the alias is setup, git ls shows commit history: git config --global alias.ls 'log --pretty=format:"%C(yellow)%h %cd%Cblue {%cn} %Cred%d - %Creset%s" --decorate --date=format:"%Y-%m-%d %H:%M:%S"' --replace-all
git ls origin/master # shows commit history for a remote branch
git cmp "msg" # add, commit and push, all in one! git config --global alias.cmp '!f() { git add -A && git commit -m "$@" && git push; }; f'
```
http://durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/

### Q: What is needed to be productive when using git in sublime? {git} {sublime}
 * Install git and gitgutter via Cmd-Shift-P - Package Control: Install Package 
 * Cmd-Shift-P, quick commit; Cmd-Shift-P push    # push a modified file into remote

### Q: What is a good example of cut command? {unix}
```
# use space as delimiter and extract first field
cut -d' ' -f1
```
### Q: What is the best technique to remember things? {memory}
anki, github stackOverflow, CDN in Dropbox, [hello-SearchKit](https://github.com/cyx-1/hello-searchkit-elasticsearch), elasticsearch

### Q: Where are the cheatsheets for common computing topics {cheatsheet} {vi} {git} {chrome} {awk} {sed}
 * [General Cheatsheets](http://overapi.com/)
 * [Git Quick Reference](https://www.dropbox.com/s/i3hzp531puvfsnc/git%20quick%20reference.pdf?dl=0)
 * [Git Quick Reference 2](https://www.dropbox.com/s/59qpq9juxmcamou/git%20quick%20reference%202.pdf?dl=0)
 * [Vim Quick Reference](https://www.dropbox.com/s/sfdiwdhsr4whthe/vim%20quick%20reference.png?dl=0)
 * [Chrome Quick Reference](https://www.dropbox.com/s/ll1cai8kpa68gm1/chrome%20quick%20reference%20mac.pdf?dl=0)
 * [SED Quick Reference](https://www.dropbox.com/s/mj4lswzvib1baxq/sed%20quick%20reference.png?dl=0)
 * [AWK Quick Reference](https://www.dropbox.com/s/qyyfxm4kibbdx2x/awk%20quick%20reference.pdf?dl=0)

### Q: What is the best way to transfer information between work and home devices? {productivity}
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
Use HomeBrew for component that runs as software.

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

### Q: How to change ElasticSearch server to avoid CORS issues for development logic on localhost
Error seen in Chrome console when launching a web application on localhost that connects to elasticsearch runningn locally: No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://localhost:3000' is therefore not allowed access. Solution is to add the following into elasticsearch.yml configuration and then restart elasticsearch
```
http.cors:
   enabled: true
   allow-origin: /https?:\/\/localhost(:{0-9}+)?/
```

### Q: How to download a clean PDF representation of a website
 * Open up the site in Safari
 * In the view menu, choose "Show Reader". Shift-CMD-R is the shortcut
 * Export as PDF from Safari

### Q: What are key milestones in the software engineering industry
 * Sep 2016 Facebook introduces YARN to improve on NPM: ~5x speed over NPM v4 and package determinism
 * May 2017 NPM v5 released to narrow the gap with YARN 

### Q: How do you use various software package managers? (npm, yarn, homebrew)
 * Use homebrew for software you install and run: elasticsearch, yarn
 * Use npm for javascript packages that is used in the code 
 * Don't use YARN because it splits community and NPM v5 has mostly [caught up](https://iamturns.com/yarn-vs-npm-2018/)

### Q: Is there a way to swap between different versions of node and npm? 
 * Yes, use nvm
```
nvm alias default v8.4.0
nvm use v8.4.0
nvm ls
# display all nvm commands
nvm 
```

### Q: What are questions to develop a growth mindset in children
1. What did you do today that made you think hard?
2. What happened today that made you keep on going?
3. What can you learn from this?
4. What mistake did you make that taught you something?
5. What did you try hard at today?
6. What strategy are you going to try now?
7. What will you do to chalenge yourself today?
8. What will you do to improve your work?
9. What wil you do to improve your talent?
10. What will you do to solve this problem?

### Q: What are some good reading comprehension questions
1. Inferring - to arrive at a decision or opinion using your own knowledge and clues from text
   1. Can you predict what is going to happen next
   2. Why did the character do that?
   3. What did the author mean by ___?
   4. What's going to happen next?
   5. (Character) must be feeling ___. Are there any clues that help us know that?
2. Summarizing - to put into your own words, a shortened version of the spoken or written material
   1. In general, what is the story about?
   2. What is the problem to be solved in this story? Is there a solution?
   3. What has happened so far?
3. Synthesizing - A process where students merge new information with prior knowledge to form a new idea, perspective, or opinion
   1. Is there anything that you understand in a new way from reading this story?
   2. What idea's are most interesting to you? why?
   3. Does a historical event or personal experience make more sense after reading this?
4. Analyzing
   1. What things would make everyone like this book?
   2. In what ways does teh autoor make you feel as if you were there?
   3. What are some examples of rich, colorful or great language that makes this a good passage to read?
5. Critiquing
   1. Would people in your life act this way?
   2. What is unbelievable about this text?
   3. Should other kids read this? Why or why not?
   4. What would have made this story more interesting to read?
6. Basic recall explicit questioning
   1. Who is the main character in the story? 
   2. Who are the other characters in the story?
   3. What is your favorite part of the chapter or book?

### Q: What is a good resource to find home improvement contractors?
www.bestpickreports.com

### Q: What are the CPU specs for different computing devices used in the past within the family?
1. Dell machine ~2010: Intel Core2 Duo E6400 2.13 GHz with the benchmark rating of 803:1289, 65nm, 2 cores, 2MB L2 Cache, 1066 MHz bus speed
2. Mac Mini (Late 2012) Intel Core i7-3615QM 2.3 GHz with benchmark rating of 1644:7371, 22nm, 4 cores, 8 threads, 6MB L2 Cache, Hyper Threading
3. Mac Book Pro (Late 2012) Intel Core i5-3210M 2.5 GHz with benchmark rating of 1521:3821, 32nm, 4 cores, 4 threads, 6MB L2 Cache, no Hyper Threading
4. IPhone 6 A1549 (Sep 2014 model) CPU A8, Mobile passmark rating of 5174
5. IPhone 7 A1661 (Sep 2016 model) CPU A10 Mobile passmark rating of 8748

### Q: What is the difference between old and new cutting board {houseRules}
 * New chopping board is for working with food that goes into mouth: cooked food, fruits
 * Old chopping board is for working with food that is raw meat, onion or food that requires cooking

### Q: What is the difference between old and new sponge {houseRules}
  * Clean sponge is for dish washing, old sponge is for sink washing

### Q: What are good habits to follow after returning home from work? {houseRules}
  * put bag where it belongs: corner next to TV or put underneath the console table 
  * put air purifier into sneaker 
  * hang up dress shirts / pants into closet

### Q: What is the difference between big and small butcher knife {houseRules}
  * big butcher knife is for raw stuff, and if clean, water melon or cooked chicken as well. 
  * Smaller black knife is for cutting cookied meat

### Q: What happened with Boeing 737 Max? {engineeringFailure}
  * Bigger engine leads to more efficiency (less fuel per power produced)
  * When competing against new Airbus, larger engine was added to older aircraft like 737
  * Larger engine needs to be placed in a position closer to front of airplane, in order to have enough clearance between the bottom of engine and tWhe ground
  * The new engine position creates propensity for airplane to pitch up when applying thrust
  * Too much pitch up leads to aerodynamic stall
  * Angle of attack sensor could prevent stall when working with Boeing's software system called MCAS (Maneuvering Characteristics Augmentation System), which automatically tells the airplane to point nose down if angle of attack is too close to aerodynamic stall conditions
  * MCAS works independently on both side of plane's computer and sensors. The pilot and co-pilot are supposed to be tie breakers when computer is in disagreement
  * MCAS doesn't allow pilot to override, and this is catastropic when the sensor is mal-functioning
  * Airbus airplane, in comparison, has 3 different sensors, which is more reliable by reaching quorum based decision making
  * Goal of MCAS to keep 737 pilots familiar with existing 737 procedures, and thus reduce cost

### Q: What is a good temperature for baking chicken drumstick {recipe}
  * 400 degree, 40-45 minutes

### Q: How did global finals go for DI 2019
  * 15+ countries
  * 8000 students
  * 17000 attendees
  * 350K square feet of props showcase

### Q: What needs to be done to change minecraft player name? {minecraft}
  * Modify ~/Library/Application Support/minecraft/launcher_profiles.json
  * Change the username in the file

### Q: Where can I see the content of this file on github? {memory}
  * https://raw.githubusercontent.com/cyx-1/stackOverflow/master/README.md
  * https://github.com/cyx-1/stackOverflow

### Q: What is the inventory of electronics {tinkering}
  * Digital Multimeter: https://www.amazon.com/gp/product/B07FDZHRB8
  * Soldering iron kit: https://www.amazon.com/gp/product/B06XZ31W3M
  * Arduino starter kit: https://www.amazon.com/Arduino-Starter-Kit-English-Official/dp/B009UKZV0A