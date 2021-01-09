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
 * [Sublime3 OSX Reference](https://www.dropbox.com/s/hledclezbpp5trf/sublime3-osx.pdf?dl=0)
 * [Sublime3 Windows Reference](https://www.dropbox.com/s/rq9nd6la6ekinlm/sublime3-windows.pdf?dl=0)

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

# check what are all the node versions available
nvm ls-remote

# install a version (typically the latest LTS, long term support, version)
nvm install 10.16.0
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

### Q: What is my inventory of electronics {electronics}
  * Digital Multimeter: https://www.amazon.com/gp/product/B07FDZHRB8
  * Soldering iron kit: https://www.amazon.com/gp/product/B06XZ31W3M
  * Arduino starter kit: https://www.amazon.com/Arduino-Starter-Kit-English-Official/dp/B009UKZV0A

### Q: What are examples of electronics parts that are useful for tinkering? {electronics}

### Q: What are some important shortcuts that should be remembered {shortcuts}
  * Enter / Exit full screen on Mac: Ctrl-Cmd-F
  * Launch application via keyboard on Mac: Ctrl-Space (Spotlight)
  * Edit the address bar in chrome window: Cmd-L
  * Switch between different programs in Mac: Ctrl-Left/Right arrow

### Q: What has been done to learn programming
  * 08-02-2019: 
    * Install Typescript via this command: npm install -g typescript
    * Check the Typescript version: tsc --version
    * If VS Code npm version doesn't match with the npm/node installed in shell, use this command: nvm alias default <version> See: https://stackoverflow.com/a/44707192
    * Nice quick start: https://code.visualstudio.com/docs/typescript/typescript-tutorial
    * Nice playground: https://www.typescriptlang.org/play/index.html
    * ESLint rules: https://eslint.org/docs/rules/ 
    * VS Code plugin: ESLint, Vim
    * Stopped using VS Code plugin: prettier
    * Prefer ESLint over TSLint because that's MSFT's direction: https://github.com/Microsoft/TypeScript/issues/29288
    * Don't bother with naming files with es6 extension, since ECMAScript standard changes quickly
  * 08-03-2019:
    * Started to use SSH key on MBP to avoid annoying popups https://help.github.com/en/articles/connecting-to-github-with-ssh
    * Ran into an issue with ESLint when trying to also lint Typescript: looks like ESLint v6 broke something. Holding off on this for now
    * Started to think about the merit of using nodejs express Lambda for server-side logic, S3 for reactjs client side logic, interface to testing logic outside of the serverless environment. The flashcard could be a great proving ground for this idea
    * ClaudiaJS and AWS Lambda works really well!
    * Tried out Local DynamoDB via Node https://medium.com/@Keithweaver_/using-aws-dynamodb-using-node-js-fd17cf1724e0
    * Express and Lambda work really well! https://www.freecodecamp.org/news/express-js-and-aws-lambda-a-serverless-love-story-7c77ba0eaa35/
    * When it comes to testing software bound for serverless production environment, it is important to be able test locally, allowing the component to have options to simulate or control dependencies. Leverage the control over local dynamodb for unit tests prior to deployment, leverage the control over aws dynamodb for service tests prior to reaching the end of determinism, leverage contract testing to check that all components are communicating without stubs, prior to reaching end of automation, leverage adhoc manual testing to spot check automation prior to unlocking real value of software. https://www.freecodecamp.org/news/the-best-ways-to-test-your-serverless-applications-40b88d6ee31e/
    * Looked into service virtualization software such as Mountebank, but found it to be not so attractive, since service test would require a separate mock server. Why create a separate server, if each component can build a debug mode? Every microservice should offer an API to enable debug mode, where the responses can be carefully orchestrated for deterministic testing. Once in the debug mode, stored in dynamoDB if deployed, hard-coded if local, the behavior would be driven by a series of orchestrated simulations, not using real data or the real dependencies.
    * If an application has a S3 dependency, let's say to work with video or image, then the application should have ability to have debug mode switch to file system that serves up a much smaller media file. Or the application should have ability to use S3 in a testing partition but with a smaller data set that is handcrafted. Here, I would choose to use file system because it would be the same as local testing, since there is no local S3 yet
    * It might make sense to create separate Lambda to control the data that goes into the debug partition of dynamoDB, since multiple microservice may need dynamoDB orchestration.
    * Working with nodemon now to auto-restart express server when there is a change detected, beautiful. https://alligator.io/workflow/nodemon/
    * Install NVM via homebrew on Desktop, ran into an error "missing xcrun". Fixed via https://apple.stackexchange.com/questions/254380/why-am-i-getting-an-invalid-active-developer-path-when-attempting-to-use-git-a
    * Created a home repo to store common config files
    * On desktop: Installed NVM 0.34.0, and then installed node 10.16.0 and along with it npm 6.9.0
    * On desktop: Started to look into react again, using create react app using typescript
```
Cannot use import React from 'react';
Use this instead, since React is exported as CommonJS module which does not use a default export 
import * as React from 'react';
import * as ReactDOM from 'react-dom';
```
* 08-04-2019
  * Deployed a reactjs application to s3. Reference: https://medium.com/serverlessguru/deploy-reactjs-app-with-s3-static-hosting-f640cb49d7e6
    * create a s3 bucket with public access
    * upload build content from a react project
    * create an IAM user with permissions
    * incorporate deploy to S3 and open browser to package.json
  * Connected the S3-based ReactJS app to the scalable Lambda-based Flashcard-API!!!
    * bypassed CORS issue for now by setting permissive headers from Express
    * Express app needed to respond to method OPTION as well, app.all works very well
    * Chrome sends OPTION requests because of CORS
* 08-11-2019
    * Variable hoisting, IIFE, High-order components, class and prototypes, commonjs vs es modules
* 08-17-2019
    * installed gitlens, cloned git repo from Tyler's react
* Cool things to check out next
  * What is export default? What is async-await (alligator.io axios tutorial talks about this)??
  * What are generators? 
  * Nice tutorial site: https://alligator.io/
  * Is there a way to not make Chrome check method OPTION so often
  * Comprehensive list of ES6, 7, 8 features https://www.freecodecamp.org/news/here-are-examples-of-everything-new-in-ecmascript-2016-2017-and-2018-d52fa3b5a70e/, https://medium.com/@dupski/what-major-new-features-were-in-each-javascript-version-what-version-should-i-target-25526c498687, https://github.com/lukehoban/es6features#arrows, https://node.university/blog/7297/es7-es8-post
  * Tell express to configure a fav icon
  * SAM, ClaudiaJS, Serverless framework are all trying to solve similar problems
  * Design ideas: some examples of debug situations
    * Return a test file: http://localhost:3000/api/getFlashcards?debug=true&debugContentFrom=file&debugContent=test.json
    * Return response with a delay (30s): http://localhost:3000/api/getFlashcards?debug=true&debugResponseTime=30&debugContentFrom=file&debugContent=test.json
    * Return a malformed result: http://localhost:3000/api/getFlashcards?debug=true&debugContentFrom=file&debugContent=test-partial.txt
    * All APIs should support the debug functionality
    * All APIs that handles POST with a request under debug may need to consider response template capabilities

### Q: What is the history of JavaScript, ECMAScript and TypeScript
  * Source PDF for archived standard: https://www.ecma-international.org/publications/standards/Ecma-262-arch.htm
  * 1995 Javascript invented by Brendan Eich in 1995 in Netscape. Original name was Mocha, then LiveScript, named to JavaScript in 1995 after license purchase from Sun Microsystems. Other vendors had similar implementations: ActionScript (Macromedia), JScript (Microsoft). EcmaScript is to unite vendors implementations into a single standard
  * 1997 ES1/ES1997: first edition of ECMS-262 standard
  * 1998 ES2/ES1998: minimal change
  * 1999 ES3/ES1999: Supported by all browsers. introduced triple equal operator, try-catch, regular expression
  * ES4: abandonded, due to disagreement on scope of change
  * 2005 AJAX Asynchronous Javascript And XML https://en.wikipedia.org/wiki/Ajax_(programming), leading to Gmail, Google Map
  * 2009 ES5/ES2009: Supported by all modern browers. introduced strict mode, more Arrays function, JSON parse and stringify, property getter/setter, and Object methods such as to list properties
  * 2011 ES5.1: ISO approved standard, same as ES5
  * 2014 TypeScript 1.0 Super set of ES6. See History: https://en.wikipedia.org/wiki/Microsoft_TypeScript
  * 2015 ES6/ES2015: promise, template literals, let and const, destructuring, arrow fn, for-of
  * 2016 ES7/ES2016: array includes, expoentials
  * 2017 ES8/ES2017: async-await, string padding
  * 2018 ES9/ES2018: rest and spread operators
  * 2018 TypeScript 3.0
  * 2019 ES10/ES2019:
  * Reference: browser support for different standards: https://www.w3schools.com/js/js_versions.asp

### Q: What does Typescript have that Javascript does not? 
  * any, void, never, enum, interface (with inheritance), optional, readonly, type alias
  * Ability to detect type-related issues, ie assigning value of wrong type into a typed variable

### Q: What are some similaries between TypeScript and Java?
  * Use of static keyword
  * Access modifier such as private, public and protected
  * Extends one class, Implements multiple interfaces

### Q: Check what version of package has been installed globally via npm
  * npm list -g | grep <something>

### Q: What has been your workout activities
  * 08-03-2019 25 pound barbell plate exercise + Flat dumbbell bench press + Resistance band till muscle exhaustion
  * 08-04-2019 Ran 2.4 miles to and back from Stop & Shop
  * 08-03-2019 25 pound barbell plate composite exercise + 3 sets of Flat dumbbell bench press + Resistance band till muscle exhaustion
  * 08-04-2019 Ran 2.4 miles to and back from Stop & Shop, almost 5 pull ups
  * 08-05-2019 Almost 5 pull ups, 3 sets of 40lb dumbbell incline press, followed by resistance band raise to exhaust upper chest muscle, 1 set of overhead tricep, 1 set (6 reps) of 45lb barbell plate bicep curl, followed by 1 set (7 recps) of 25lb barbell plate bicep curl, and legs were sore from yesterday
  * 08-06-2019 25lb barbell plate side pull ups, 25lb barbell plate overhead raise for triceps
  * 08-07-2019 Skipped
  * 08-08-2019 Assembled power rack
  * 08-09-2019 10 reps of 45lb squat, 6 reps of 95lb squat in the morning, 4 pull ups
  * 08-10-2019 3 sets of 10 reps of 95lb flat bench press, 3 sets of 10, 8, 7 reps of 95lb inclined bench press, 5 pull-ups
  * 08-11-2019 2.4 miles in ~30 minutes, swimming with kids
  * 08-12-2019 5.5 pull-ups
  * 08-13-2019 rest
  * 08-14-2019 3 sets of 10 reps 95lb bench press and 3 sets of 45lb barbell plate chin raise
  * 08-15-2019 3 sets of 10 reps 105lb bench press and 10 reps 45lb barbell plate curl
  * 08-16-2019 3 pull-ups in the park (grip is not same at home), 2 sets of 10 reps resistance band

### Q: What has been done to nurture Adrian and Jaydin?
  * 08-04-2019 Looked into TinkerCAD
  * 08-04-2019 Looked into 3d capture of human face https://www.instructables.com/id/3D-Printing-your-own-full-color-bobblehead-using-1/
  * 08-09-2019 Showed Adrian the concept of source code repository, how VS code could be used to upload changes to code
  * 08-10-2019 Showed Adrian brief introduction to S3 storage, and how inexpensive it is. Showed Adrian the sandbox-ts-react program, and how it could be uplaoded to S3 as a website. Showed Adrian the concept of StackOverflow (Question and Answering website), and how I am using my own personal StackOverflow-like project to remember things like cooking recipe, programming techniques and workout routines. 
  * 08-11-2018 Took Adrian and Jaydin to swimming by walking to center count, good conversation along the way, talked about dealing with failures, getting exposures more quickly, reversible decisions, and also played a game of math concepts. Separately, spoke to Adrian about allocation of time, programmer depending on each other's work, and the entertainment vs enslaving attention paid to video games. 

### Q: What makes Adrian happy?
  * ALWAYS- NEED VIDEO GAMES
  * Likes writing on google docs
  * likes typing

### Q: What would be a concept map for Modern UI programming
  * NPM - node package manager
    * versioning symbol: ^ vs ~
  * Popular NPM Packages
    * lodash
    * moment
  * Modules systems
    * CommonJS (useful on the server-side Node development)
    * RequireJS (useful more on the browser-side)
    * Browserify (module bundler that works in conjunction with RequireJS)
    * SystemJS (yet another way to manage modules within browsers)
    * ES Module (official standard)
    * Webpack - transformation manager and module bundler (which is easier than the script tag whose order is hard to work with)
      * entry point
      * loader - allows Webpack to process more than js files (babel-loader, style-loader, css-loader, svg-inline-loader)
      * output
      * plugins - allows task execution after bundle creation (HtmlWebpackPLugin, webpack.EnvironmentPlugin)
      * mode
      * webpack-dev-server - enables hot code replace
  * React gotchas
    * JSX
      * use of curly braces for expression (this means a js object already using braces need to be wrapped again using braces)
      * use of JS to give flow control to reduce API complexity, unlike Angular or Vue that uses special syntax such as ngif or v-if
      * div vs React.Fragment
      * capitalization of react component to differentiate from built-in html element
