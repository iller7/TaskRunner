<!--![alt text][logo]-->

# Front-end Development Tooling
A quick startup guide for setting up your environment from a front-end perspective in order to make the best use of your tools and automate many common tasks
> Based on the Google standards for Front-end development, which implies sass for styling and javascript module pattern for coding

> Platform agnostic. Tested on Linux and Windows.

### Version
1.1.18

> This is a _working document_. Last edited by [Faizal Sahebdin] on 05 May 2016 

## Tech
The toolset uses a number of open source projects to work properly while utilising your editor of choice. For this configuration I shall be using [Sublime Text] as my editor but [Vim], [Visual Studio] and [Atom] have all got their equivalent plugins and settings
***

### Libraries
- [node.js] - evented I/O for the backend
  - to get started with node and installing it on your platform please visit the [node docs repo]
- [Ruby] - open source programming language with a focus on simplicity
- [Gulp] - stream based build system
- [Python] - optional, but may be required for some plugins
- [.Net Framework 2 SDK] - optional, but may be required for some plugins
- [VS Update 2013.4] - optional, may be needed for [BrowserSync]
***

#### Troubleshooting
- [.Net Framework 2 SDK] - optional, but may be required for some plugins
 - set the path for VCBuild.exe
 ```
 $ set PATH=%PATH%;C:\Program Files\Microsoft Visual Studio 8\VC\vcpackages\VCBuild.exe;
 ```
 - finally update node-gyp
 ```
 $ where node
 ```
 - cd to that folder
 ```
 $ cd "C:\Program Files\nodejs\node_modules\npm"
 ```
 - and install the latest node-gyp
 ```
 $ npm install -g node-gyp@latest
 ```
- if still broken, try a free [VS IDE]
***

### Editor
#### Sublime Text/Vim/Atom/whichever editor flavour you fancy
You do not have to use Sublime as this tooling is both platform and editor agnostic. Both [Vim] & [Atom] have a gulp wrapper through [GulpVim] and [GulpAtom] 

#### Sublime Plugins & Configuration
If you're using Sublime then you may switch off some of the tasks in the Gulp file. Configuration files for the plugins may be found in the /dev/tools/Sublime/user-settings folder

* [Package Control] - package manager that finds, install and keep packages up-to-date
* [Gulp] - run your Gulp tasks from within Sublime
* [HTML-CSS-JS Prettify] - code formatter via node.js
* [Markdown Preview] - previews markdown
* [Sass] - syntax highlighting and tab/code completion for sass and scss files
* [SublimeGit] - optional, if you're using git for version control
* [SublimeGitGutter] - optional, if you're using git and to see diff in gutter
* [SublimeLinter] - optional, integrated linting engine. language specific plugins are installed separately
* [SublimeLinter-contrib-sass-lint] - optional plugin for sass, using sass-lint
  ```
  $ gem install scss-lint
  $ npm install -g sass-lint
  ```
* [SublimeLinter-jshint] - optional, [SublimeLinter] plugin for javascript, using jshint
  ```$ npm install -g jshint```
* [SideBarEnhancements] - optional, enhancements to Sublime Text sidebar
***

## Task runner
#### Uninstall older Gulp
optional, uninstall any previous Gulp installation, if any
```
$ npm uninstall gulp -g
$ cd [your_project_root]
$ npm uninstall gulp --save-dev
```

#### automated install Gulp and plugins into your project
```
$ npm install gulp --g
$ cd [your_project_root]
$ npm install
```

#### manual install Gulp and plugins into your project
```cmd
$ cd [your_project_root]
$ npm install gulp --save-dev
$ npm install --save-dev babel-core babel-preset-es2015 babel-register browser-sync del eslint eslint-config-google gulp-autoprefixer gulp-babel gulp-beautify gulp-cached gulp-clean-css gulp-concat gulp-filter gulp-eslint gulp-htmlmin gulp-if gulp-imagemin gulp-jasmine gulp-less gulp-load-plugins gulp-newer gulp-notify gulp-plumber gulp-progeny gulp-rename run-sequence gulp-sass gulp-scss-lint gulp-size gulp-sourcemaps gulp-uglify gulp-useref gulp-uncss gulp-util pagespeed psi sw-precache sw-toolbox
```

* Note: There a bug on Windows 10 which complains about a missing C++ compiler, I got around this by googling and installing the SDK
* Remove browser-sync and/or gulp-imagemin if you're not using them. And exclude ./install/here/node_modules directory from your repo

#### Create a gulp task stream using this format:
```javascript
gulp.task('NAME_OF_TASK', function() {
   gulp.src(['PATH_TO_SOURCE_FILE'])
   .pipe(**INSERT_TASK**)
   .pipe(gulp.dest('PATH_TO_DESTINATION');
});
```
#### List of tasks available

Task Name | Description
:--- | :---
default | combination of any number of the tasks defined below
greet | Hello world!
sass | compile sass/scss, generate css sourcemaps and minifies css
scsslint | sass/scss linting via lint.yml
jsmin | generate js sourcemaps and minify js
jslint | lint js using http://google.github.io/styleguide/javascriptguide.xml
images | image smushing and optimisation
jasmine | test runner
serve | browser sync
serve:dist | browser sync from the distribution build
clean | cleans the distribution build
copy | copies files to the distribution folder
concat | used for concatenating all relevant files defined within
pagespeed | runs pageSpeed insights
gsw | generates a service worker file that will provide offline functionality for local resources
copy-sw-scripts | copies over the scripts that are used in importScripts as part of the generate-service-worker task
watchers | re-runs the relavant task on file change
lint | standalone linting for js and sass/scss
build | standalone build deployment
sync | standalone browser sync
less | magento 2 specific less compiler
watchLess | magento 2 watcher for less file compilation
***

#### Keyboard bindings and shortcuts

* If you're using [Sublime Text], press ctrl+shift+p, type "gulp" and choose a task from the drop down menu, usually "Default"
* Or select "Gulp" from the Tools menu, and pick "Run default task" 
* On windows, feel free to import the Default (Windows).sublime-keymap file, the following shortcuts are enabled:

Shortcut | Command
:--- | :---
ctrl+shift+r | Show files overlay
ctrl+alt+r | Reveal in sidebar
ctrl+shift+b | Run default gulp task
ctrl+alt+b | Kill all gulp tasks
ctrl+shift+t | Run arbitrary gulp task
f12 | Show build panel
esc | Hide build panel
***

#### Configuration and settings files
File | Description
:--- | :---
.editorconfig | editor independent configuration file
.gitignore | folders and files to be ignored by git
.jshintrc | javascript linter settings, change the environment section to match yours
gulpfile.babel.js | task runner
.travis.yml | build script for magento 2
.babelrc | ES2015 support
./dev/tools/sublime/user-settings/Default (Windows).sublime-keymap | windows shortcuts
./dev/tools/sublime/user-settings/Preferences.sublime-settings | user preferences and defaults for Sublime
./dev/tools/sublime/user-settings/SublimeLinter.sublime-settings | linter settings
***

### Todos

* Unit Testing Automation, CucumberJs or Jasmine
* Test on a Mac, volunteer needed
* .travis.yml build scripts for [IBM Websphere]
* Control Apache and Database servers from Gulp
* Delete caches on both [IBM Websphere] and [Magento]

### Contributors
* [Faizal Sahebdin] - Author

License
----
MIT

[//]: #
  [logo]: https://lh4.googleusercontent.com/-xxSf0YF0_FA/UMejrwAqnnI/AAAAAAAADBc/gjDrcJJjU3oxdyFq-F0EowbuyVCB_mhmACL0B/s650-no/logo-large-no-text.png "Watercherry Logo"
  
  [node.js]: <http://nodejs.org>
  [node docs repo]: <https://docs.npmjs.com/>
  [Gulp]: <http://gulpjs.com>
  [Python]: <https://www.python.org>
  [.Net Framework 2 SDK]: <https://www.microsoft.com/en-gb/download/details.aspx?id=15354>
  [Ruby]: <https://www.ruby-lang.org>
  [AngularJS]: <http://angularjs.org>
  [jQuery]: <http://jquery.com>
  [VS Update 2013.4]: <https://www.visualstudio.com/en-us/news/vs2013-update4-rc-vs.aspx>
  
  [Sublime Text]: <https://www.sublimetext.com>
  [Vim]: <http://www.vim.org>
  [Atom]: <https://atom.io>
  [Visual Studio]: <https://code.visualstudio.com>
  [VS IDE]: <https://www.visualstudio.com/products/free-developer-offers-vs>
  
  [Gulp]: <https://github.com/NicoSantangelo/sublime-gulp>
  [GulpVim]: <https://github.com/KabbAmine/gulp-vim>
  [GulpAtom]: <https://atom.io/packages/gulp-control>
  [Package Control]: <https://packagecontrol.io>
  [SublimeGit]: <https://github.com/kemayo/sublime-text-git>
  [SublimeGitGutter]: <https://github.com/jisaacks/GitGutter>
  [HTML-CSS-JS Prettify]: <https://github.com/victorporof/Sublime-HTMLPrettify>
  [Sass]: <https://packagecontrol.io/packages/Sass>
  [SideBarEnhancements]: <https://github.com/titoBouzout/SideBarEnhancements>
  [SublimeLinter]: <http://www.sublimelinter.com>
  [SublimeLinter-contrib-sass-lint]: <https://github.com/skovhus/SublimeLinter-contrib-sass-lint>
  [SublimeLinter-jshint]: <https://github.com/SublimeLinter/SublimeLinter-jshint>
  [Markdown Preview]: <https://github.com/revolunet/sublimetext-markdown-preview>
  [BrowserSync]: <www.browsersync.io>
  
  [FaizalGit]: <https://github.com/iller7>
  [git-repo-url]: <https://github.com/iller7/tooling.git>
  
  [IBM Websphere]: <http://www-01.ibm.com/software/uk/websphere>
  [Magento]: <https://magento.com>
  
  [Faizal Sahebdin]: <mailto:iller7@gmail.com?Subject=FED-Tooling>
