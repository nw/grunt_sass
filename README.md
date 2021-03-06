## Grunt / Sass basic project example

### Setup

One time setup

```bash
npm install -g grunt-cli
git clone https://github.com/nw/grunt_sass.git
cd grunt_sass
npm install
```

### Running

```
grunt
```

This will run forever. You can use `Ctrl-C` to exit. Anytime you save a change to any `scss` file in `src/sass` css will automatically be built.

There is currently an `example.scss` file to demonstrate. 

### Example

`example.scss`
```scss
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;
$bg-color: #FFF;

body {
  font: 100% $font-stack;
  color: $primary-color;

  #id {
    background: $bg-color;

    .widget {
      font: 85% $font-stack;
    }
  }

}
```

becomes `example.css`
```css
/* line 5, ../../src/sass/example.scss */
body {
  font: 100% Helvetica, sans-serif;
  color: #333333;
}
/* line 9, ../../src/sass/example.scss */
body #id {
  background: white;
}
/* line 12, ../../src/sass/example.scss */
body #id .widget {
  font: 85% Helvetica, sans-serif;
}
```

### Explanation

* To keep things clean I located all the `scss` (sass) files in `src/sass`.
* CSS is generated and put into directory `public/css`
* git ignore is added to the `public/css` directory so you don't check in your generated css code. You only check in your source code.
* `Gruntfile.js` has a few options that can be tweaked based on what you want:
   * `style`: currently set to `expanded` but `nested`, `compact` & `compressed` are valid.
   * lineNumber: `true` outputs the line number from the `sass` file that generated the css. Helpful when learning or debugging.
