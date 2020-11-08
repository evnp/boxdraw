# boxdraw

Convert ascii grid drawings into unicode ["box-drawing"](https://en.wikipedia.org/wiki/Box-drawing_character "wikipedia box-drawing characters") characters:

[![tests](https://github.com/evnp/boxdraw/workflows/tests/badge.svg)](https://github.com/evnp/boxdraw/actions)
[![shellcheck](https://github.com/evnp/boxdraw/workflows/shellcheck/badge.svg)](https://github.com/evnp/boxdraw/actions)
[![latest release](https://img.shields.io/github/release/evnp/boxdraw.svg)](https://github.com/evnp/boxdraw/releases/latest)
[![npm package](https://img.shields.io/npm/v/boxdraw.svg)](https://www.npmjs.com/package/boxdraw)
[![license](https://img.shields.io/github/license/evnp/boxdraw.svg?color=blue)](https://github.com/evnp/boxdraw/blob/master/LICENSE.md)

**Contents** - [Install](https://github.com/evnp/boxdraw#install) | [Usage](https://github.com/evnp/boxdraw#install) | [Examples](https://github.com/evnp/boxdraw#run-on-file-input) | [Tests](https://github.com/evnp/boxdraw#tests) | [License](https://github.com/evnp/boxdraw#license)

Install
-------

```sh
npm install -g boxdraw  # installs "boxdraw" to npm bin, ensure that directory is on your path
boxdraw <<-EOF          # PRESS ENTER
> +-+                   # PASTE INPUT
> | |
> +-+
> EOF                   # ENTER "EOF"
┌─┐                     # PRESS ENTER
│ │
└─┘
```

Or,

```sh
git clone git@github.com:evnp/boxdraw.git
cd boxdraw
npm run demo
```

![boxdraw demo](https://raw.githubusercontent.com/evnp/boxdraw/main/boxdraw.png "boxdraw demo")

###  Usage

```sh
boxdraw --help

Usage:

  boxdraw <<-EOF    # PRESS ENTER
  > +-+             # PASTE INPUT
  > +-+
  > EOF             # ENTER "EOF"
  ┌─┐               # PRESS ENTER
  └─┘

  OR

  boxdraw < inputfile.txt

Options:

  boxdraw 8 < inputfile.txt         # Draw with margin of 8 lines/spaces
  boxdraw 0 bold < inputfile.txt    # Draw with bold "box-drawing" characters
  boxdraw 2 double < inputfile.txt  # Draw with double-line "box-drawing" characters AND margin

More information:

  https://github.com/evnp/boxdraw
  https://en.wikipedia.org/wiki/Box-drawing_character

```

### Run on file input

```sh
boxdraw < inputfile.txt
```

### Run on pasted input

```sh
boxdraw <<-EOF    # PRESS ENTER
> +-+---+         # PASTE INPUT
> | |   |
> +-+-+ |
> | | | |
> +-+-+-+
> EOF             # ENTER "EOF"
                  # PRESS ENTER
┌─┬───┐
│ │   │
├─┼─┐ │
│ │ │ │
└─┴─┴─┘

```

### Draw grids for input

http://asciiflow.com/

### Style options

Margins:

```sh
boxdraw 3 <<-EOF
> +-+---+
> | |   |
> +-+-+ |
> | | | |
> +-+-+-+
> EOF




   ┌─┬───┐
   │ │   │
   ├─┼─┐ │
   │ │ │ │
   └─┴─┴─┘




```

Line style:

```sh
boxdraw 0 bold <<-EOF
> +-+---+
> | |   |
> +-+-+ |
> | | | |
> +-+-+-+
> EOF

┏━┳━━━┓
┃ ┃   ┃
┣━╋━┓ ┃
┃ ┃ ┃ ┃
┗━┻━┻━┛

boxdraw 0 double <<-EOF
> +-+---+
> | |   |
> +-+-+ |
> | | | |
> +-+-+-+
> EOF

╔═╦═══╗
║ ║   ║
╠═╬═╗ ║
║ ║ ║ ║
╚═╩═╩═╝

```

Tests
-------------
Run once:
```sh
npm install
npm test
```
Use `fswatch` to re-run tests on file changes:
```sh
brew install fswatch
npm install
npm run testw
```
Non-OSX: replace `brew install fswatch` with package manager of choice (see [fswatch docs](https://github.com/emcrisostomo/fswatch#getting-fswatch))

License
-------
MIT
