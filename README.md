#Project Introduction 

##Structure of Project

This project is forked from <a href="https://github.com/HugoGiraudel/sass-boilerplate">sass-boilerplate created by Hugo Giraudel</a>. Reference can be found <a href="https://sass-guidelin.es/#the-7-1-pattern">here</a>.

A great tutorial can be found <a href="https://scotch.io/tutorials/aesthetic-sass-1-architecture-and-style-organization">here</a>, created by David Khourshid on March 24th 2015.

Basic Structure:

- `base/` – contains global styles, such as resets, typography, colors, etc.

- `components/` – contains each self-contained component in its own .scss partial

- `layout/` – contains styling for larger layout components; e.g. nav, header, footer, etc.

- `pages/` – contains page-specific styling, if necessary

- `themes/` – contains styling for different themes

- `utils/` – contains global mixins, functions, helper selectors, etc.

- `vendors/` – contains 3rd-party styles, mixins, etc.

- `main.scss` – output file that brings together all of the above parts

- `main.css` - compiled directly from `main.scss`, using your favorite sass compiler. **This is the only file that supposed to be transferred to cascade**

##How to Use

*Lasted Updated by Pengyin Shan, Jan 2017*

*Problem needs to be discussed: Unable to do subtree inside Visual Studio Code (Use Github Desktop), 60 requests limit in Github API, Do we need dist folder?*

1. *admin account*: Clone this project using `git clone https://github.com/emorycpa/sass-boilerplate.git NewProjectName`, replace `NewProjectName` with the new project name 

2. *admin account*: Add collaborators to new project

3. *personal account*: Using Github Desktop, clone new project to your local machine

4. *personal account*: Modify separate scss code. **Remember to do Import in `main.scss` if you create any new scss file. ** 

5. *personal account*: Compile `main.scss` to `main.css`. **Make sure `main.css` is in `dist` folder**

6. *personal account*: Use Github Desktop to commit and push all code in this project to `master` branch

7. *admin account*: Check code to make sure everything is ready, then transfer **everything in dist folder** to `cascade` branch by doing `git add`, `git commit` and `./git-deploy dist`. 

8. *admin account*: Go to project in cascade server, immigrate main.css to cascade

<hr/>

###Main file

The main file (usually labelled `main.scss`) should be the only Sass file from the whole code base not to begin with an underscore. This file should not contain anything but `@import` and comments.

*Note: when using [Eyeglass](https://github.com/sass-eyeglass/eyeglass) for distribution, it might be a fine idea to name this file `index.scss` rather than `main.scss` in order to stick to [Eyeglass modules specifications](https://github.com/sass-eyeglass/eyeglass#writing-an-eyeglass-module-with-sass-files). See [#21](https://github.com/HugoGiraudel/sass-boilerplate/issues/21) for reference.*

Reference: [Sass Guidelines](http://sass-guidelin.es/) > [Architecture](http://sass-guidelin.es/#architecture) > [Main file](http://sass-guidelin.es/#main-file)

<hr/>

###Sass Boilerplate

This is a sample project using the [7-1 architecture pattern](http://sass-guidelin.es/#architecture) and sticking to [Sass Guidelines](http://sass-guidelin.es) writing conventions.

Each folder of this project has its own `README.md` file to explain the purpose and add extra information. Be sure to browse the repository to see how it works.

####Using the indented syntax

This boilerplate does not provide a `.sass` version as it would be painful to maintain both versions without an appropriate build process. However, it is very easy to convert this boilerplate to Sass indented syntax.

Clone it, head into the project and then run:

```
sass-convert -F scss -T sass -i -R ./  && find . -iname “*.scss” -exec bash -c 'mv "$0" “${0%\.scss}.sass"' {} \;
```
