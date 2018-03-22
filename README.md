# gulp-KeyListener

### Adds a `keys` function to the gulp object which can be used for listening for/reacting to keystrokes..
This package is pretty much a simple mixture of [Gulp.js](https://gulpjs.com/) and [This npm module called **keypress**](https://www.npmjs.com/package/keypress)
## Installation
### npm:
```
$ npm i gulp-keylistener --save-dev
```
## Usage:
Firstly, in order to use the `gulp.keys()` function, you must get your `gulp`
instance from the `gulp-keylistener` package, like so:
```js
const gulp = require('gulp-keylistener')
```
Then you may use it like such:

```js
// Our default task...
gulp.task('default', ()=> {
  gulp.keys((ch, key)=> {
// if you pressed `ctrl-p`
    if (key.ctrl && key.name === 'p') {
// Do amazing things!!!
    }
  })
})
```
**-NOTE** The listener does not listen system-wide. At this time, it only works
within the context of the terminal.

The `gulp.keys()` function takes a callback as it's only argument, and it
takes 2 arguments -- `ch` (for character) and `key`. `ch` will give you access
to a character value, i.e. 'a' or 'z' and `key` will give you an object that
resembles thusly:
```js
{
  name: 'x',
  ctrl: true,
  meta: false,
  shift: false,
  sequence: '\u0018'
}
```
By default, `ctrl-x` and `ctrl-c` will exit the process, which you will need to use,
because the task you use `gulp.keys()` in will not finish on it's own. `ctrl-w` will
pause the listener, so that you may exit or unpause the the process, but your
callback will not be called, even if you hit your designated keybindings.

Admittedly this package is a bit on the hacky side, but it fulfills a unique
purpose for me, and maybe it will for you as well. Happy Coding!!
