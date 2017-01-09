#Project Introduction 

*Lasted Updated by Pengyin Shan, Jan 2017*

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

- `main.css` - compiled directly from `main.scss`, using your favorite sass compiler. **This is the only file that supposed to be transferred `dist` folder**

###Some suggestion from previous Khourshid's article

####1

Each folder should have a single `.scss` partial file that collects the other files in the same directory – such as `_module.scss` (my preference) or `_glob.scss`. Then, you can reference each of these in the `main.scss` file

####2

Structure folder: A flexible pattern for defining component structure is to put it in a Sass `%placeholder` that is only `@extend`ed once by a real selector.

Example of Exported Selectors from Khourshid:

```scss
.scotch-button {
    @extend %button;
    @include scotch-button-theme($color-primary);

    &.secondary {
        @include scotch-button-theme($color-secondary);
    }
}
```
####3

It is highly suggested that palette colors are named semantically rather than on their appearance. A variable like `$color-blue` has little meaning (other than that the color is blue), whereas `$color-primary` defines the color’s role semantically.

The Sass function `map-get()`, or a **custom utility function** (recommended), can be used to reference individual colors:

```scss
$scotch-colors: (
  'primary': #8e3329, 
  'accent': #d98328,
  'secondary': #5a1321,
  'foreground': #191919,
  'background': #e9e9e9
);

@function scotch-color($key: 'primary') {
  @return map-get($scotch-colors, $key);
}

$button-color: scotch-color('primary'); // #8e3329
````

####4

For Modular:  The point is to choose a type scale and stick with it throughout the project

```scss
$base-font-size: 1rem;
$base-line-height: $base-font-size * 1.25;

$type-scale: (
  -1: 0.75rem,  // small text
  0: 1rem,      // body text
  1: 1.333rem,  // large text
  2: 1.777rem   // main heading
);

$line-heights: (
  -1: $base-line-height,
  0: $base-line-height,
  1: $base-line-height * 2,
  2: $base-line-height * 2
);

@function type-scale($level) {
  @return map-get($type-scale, $level);
}

@function line-height($level) {
  @return map-get($line-height, $level);
}

@mixin type-setting($level: 0) {
  font-size: type-scale($level);
  line-height: line-height($level);
}

// The main heading
.heading-1 { @include type-setting(2); }

// The smaller top heading
.heading-2 { @include type-setting(-1); }

.paragraph { @include type-setting(0); }

.recipe-value { @include type-setting(1); }

.recipe-text { @include type-setting(-1); }

.recipe-button { @include type-setting(-1); }
```

####Khourshid's SASS Articles

- Part 1: https://scotch.io/tutorials/aesthetic-sass-1-architecture-and-style-organization

- Part 2: https://scotch.io/tutorials/aesthetic-sass-2-colors

- Part 3: https://scotch.io/tutorials/aesthetic-sass-3-typography-and-vertical-rhythm

##How to Use

*Problem needs to be discussed: Unable to do subtree inside Visual Studio Code (Use Github Desktop), 60 requests limit in Github API, Do we need dist folder?*

1. *admin account*: Clone this project using `git clone https://github.com/emorycpa/sass-boilerplate.git NewProjectName`, replace `NewProjectName` with the new project name 

2. *admin account*: Add collaborators to new project

3. *personal account*: Using Github Desktop, clone new project to your local machine

4. *personal account*: Modify separate scss code. *Remember to do Import in `main.scss` if you create any new scss file.* 

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
