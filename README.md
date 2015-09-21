# Jekyll blog theme

Simple and nice blog theme based on Inclusion framework.

Proudly built with [Jekyll](http://jekyllrb.com/) and [Grunt](http://gruntjs.com/), hosted on [Github](https://github.com).
Compatible browsers: IE8+, Firefox, Chrome, Opera, Yandex.browser, Safari

Check out [quick demo](http://website-templates.github.io/jekyll-inclusion/) of this theme

---

##Contents
* [Requirements](#requirements)
* [Structure](#structure)
* [Development and blogging](#development-and-blogging)
	- [Editorconfig](#editorconfig)
	- [Grunt tasks](#grunt-tasks)
	- [Data driven nav](#data-driven-nav)
	- [Post creating](#post-creating)
* [Changelog](#changelog)
* [Credits](#credits)
* [License](#license)

## Requirements:

- [Ruby](http://www.ruby-lang.org/)
- [Node.js](http://nodejs.org/)
- [Grunt](http://gruntjs.com/) (`npm install -g grunt-cli`)
- [Bower](http://bower.io/) (`npm install -g bower`)
- [Python](http://www.python.org/) with [pip](http://www.pip-installer.org/)

## Structure
There are two branches: master branch and gh-pages.
Project's development based on [frontend-scaffold](https://github.com/orlovmax/front-end-scaffold) and located in master branch:
```
Gruntfile.js                     - tasks
package.json                     - npm packages
bower.json                       - bower packages
README.md                        - readme
CHANGELOG.md                     - changelog
Gemfile                          - required gems
.editorconfig                    - codestyle things
_config.yml                      - site configurations
Rakefile                         - deploy scripts
post.sh                          - script for new posts creating
`/_dev/` folder - contains source code.
	`coffee/`                    - coffeescripts
	`css/`                       - compiled css
	`devtools/`                  - livereload js
	`fonts/`                     - offline and icon fonts
	`helpers/`                   - files that will be copied to _build folder
	`html/`                      - compiled html (pages and layouts)
	`img/`                       - images
	`js/`                        - compiled coffee js, vendor js, custom js
	`ruby/`                      - jekyll plugins
	`styles/`                    - sass stylesheets
		`helpers`                  - grid and third-party stuff, mixins
		`components`               - stylsheets components (blocks)
			`general`                - general styles like reset.sass
				`inclusion`          - post content styles (Inclusion)
	`templates/`                 - jade templates
		`components`               - page blocks
		`helpers`                  - mixins
		`pages`                    - site separate pages
			`_layouts`               - page layouts (will be copied to _build folder)

`/_build/` folder - build version, generated sources ready for jekyll build
	`_data/`                     - data for jekyll generation (nav etc)
		`i18n/`                  - i18n localization *.yml files
	`_drafts`                    - drafts (will be copied to `_build/_drafts` folder)
	`_layouts/`                  - layouts for jekyll generation
	`_plugins/`                  - jekyll plugins
	`_posts/`                    - posts (*.md)
	`css/`                       - site styles
	`fonts/`                     - site fonts
	`img/`                       - images
	`js/`                        - scripts

`/_publ/` folder - site content: posts, pages and pictures
	`data/`                      - data for jekyll generation (nav etc)
		`i18n/`                  - i18n localization *.yml files
	`img/`                       - post and pages images
	`pages`                      - site posts and pages
		`_drafts`                - drafts (will be copied to `_build/_drafts` folder)
		`_posts`                 - posts (will be copied to `_build/_posts`folder)
```
gh-pages branch contains pure html/css/js site compiled by jekyll. This is for common user repository. For organization repository deploy branch should be `master` This brunch located in deploy folder:

`/_deploy/` folder - generated site, ready for deploy

You shoul  read [this article](http://www.aymerick.com/2014/07/22/jekyll-github-pages-bower-bootstrap.html) about creating dev and deploy branches for your blog. 

NOTE: this example use in _config.yml use baseurl option, so after domain there is path: /jekyll-inclusion. If you want to run this example on the local machine you should to comment or remove this line in _config.yml file.

## Development and blogging
- 
Install dependencies:
* npm install
* bower install

### Editorconfig
This project have .editorconfig file at the root that used by your code editor with editorconfig plugin. It describes codestyle like indent style, trailing whitespaces etc. See more details [here](http://editorconfig.org/) 

### Grunt tasks
* Helper tasks:
		- `grunt bower-dev` - copies bower dependencies in right folders
* Site dev tasks:
		- `grunt regen` - compiles source files, generates site with jekyll, but only once. Doesn't watch for changes. Useful for the first time project initialization to avoid broken path errors or for forced project regeneration.
		- `grunt` - default task for development, compiles source files, generates site with jekyll, watches for changes. Note that this task watches and processes only changed files, thanks to `newer` option
		- `grunt build` - minifies assets and generates site with jekyll, also processes and mififies generated markup
		- `grunt theme` - task for theme styling and scripting without site rebuild. It inclues sass compile, js concat tasks and copy task that will copy generated css and js right to the _deploy folder and you'll be able to see changes without jekyll build. Please note that after this task I suggest you to run `grunt regen` task and then - `grunt build` for final build and further deploy.
* Jekyll tasks:
		- `grunt publish` - task for blogging, generates site with jekyll, processes and minifies generated markup
		- `grunt jekyll-deploy` - task for deploy, runs `rakeJekyllDeploy` through `grunt-shell` plugin: commits deploy files and push them to the remote repo.
		- `grunt deploy` - task for deploy, runs `rakeDeploy` through `grunt-shell` plugin: commits source files, commits deploy files and push all this stuff to the remote repo.

### Data driven nav
This theme use special data from _data/nav.yml to generate navigation. It's useful when you need to create nested menu. Also each page have menu option and if it will turn to true - this page will appear in menu.

### Post creating
There is a [simple bash script](https://gist.github.com/orlovmax/f1b73a5fd01fc4b917c2) that allows us to create new posts. I've put it in the root of the website, so just execute it, like `bash post.sh your-post-name` or `post.sh your-post-name` and it will create new *.md file at `_publ/pages/_posts` with predefined draft layout from `_draft` directory and also it will create folder in `_publ/img/posts/` with name `your-post-name` for your post images. It's pretty simple and useful.

## Changelog
Youc can find full changelog [HERE](https://github.com/website-templates/jekyll-inclusion/blob/master/CHANGELOG.md)

## Credits
* [JADE bemto mixin](https://github.com/kizu/bemto)
* [Lazy load plugin](http://www.appelsiini.net/projects/lazyload)
* [Intense Image Viewer](http://tholman.com/intense-images/)
* [Prism syntax highlighter](http://prismjs.com/download.html) 
* [Detect Mobile Browsers](http://detectmobilebrowsers.com/)
* [Clean blog jekyll theme](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll)
* [Strip.rb - strip newlines after for loop](https://github.com/aucor/jekyll-plugins)
* [Tag pages generator](https://github.com/ilyakhokhryakov/jekyll-tagging-pagination)
* [Tag and Category pages pagination](https://github.com/realjenius/realjenius.com/blob/master/_plugins/cat_and_tag_generator.rb)
* [Jekyll i18n filter](https://github.com/gacha/gacha.id.lv/blob/master/_plugins/i18n_filter.rb)

## License
[MIT](http://opensource.org/licenses/MIT)
