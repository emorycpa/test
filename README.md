###Last Updated By Pengyin Shan, Jan 2017

This project is forked from <a href="https://github.com/HugoGiraudel/sass-boilerplate">sass-boilerplate created by Hugo Giraudel</a>. Reference can be found <a href="https://sass-guidelin.es/#the-7-1-pattern">here</a>.

A great tutorial can be found <a href="https://scotch.io/tutorials/aesthetic-sass-1-architecture-and-style-organization">here</a>, created by David Khourshid on March 24th 2015.

Structure of this project:

- `base/` – contains global styles, such as resets, typography, colors, etc.

- `components/` – contains each self-contained component in its own .scss partial

- `layout/` – contains styling for larger layout components; e.g. nav, header, footer, etc.

- `pages/` – contains page-specific styling, if necessary

- `themes/` – contains styling for different themes

- `utils/` – contains global mixins, functions, helper selectors, etc.

- `vendors/` – contains 3rd-party styles, mixins, etc.

- `main.scss` – output file that brings together all of the above parts

<hr/>

# Main file

The main file (usually labelled `main.scss`) should be the only Sass file from the whole code base not to begin with an underscore. This file should not contain anything but `@import` and comments.

*Note: when using [Eyeglass](https://github.com/sass-eyeglass/eyeglass) for distribution, it might be a fine idea to name this file `index.scss` rather than `main.scss` in order to stick to [Eyeglass modules specifications](https://github.com/sass-eyeglass/eyeglass#writing-an-eyeglass-module-with-sass-files). See [#21](https://github.com/HugoGiraudel/sass-boilerplate/issues/21) for reference.*

Reference: [Sass Guidelines](http://sass-guidelin.es/) > [Architecture](http://sass-guidelin.es/#architecture) > [Main file](http://sass-guidelin.es/#main-file)

<hr/>

# Sass Boilerplate

This is a sample project using the [7-1 architecture pattern](http://sass-guidelin.es/#architecture) and sticking to [Sass Guidelines](http://sass-guidelin.es) writing conventions.

Each folder of this project has its own `README.md` file to explain the purpose and add extra information. Be sure to browse the repository to see how it works.

## Using the indented syntax

This boilerplate does not provide a `.sass` version as it would be painful to maintain both versions without an appropriate build process. However, it is very easy to convert this boilerplate to Sass indented syntax.

Clone it, head into the project and then run:

```
sass-convert -F scss -T sass -i -R ./  && find . -iname “*.scss” -exec bash -c 'mv "$0" “${0%\.scss}.sass"' {} \;
```
