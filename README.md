# boxdraw

Convert simple ascii grid drawings to unicode ["box-drawing"](https://en.wikipedia.org/wiki/Box-drawing_character "wikipedia box-drawing characters") characters:

```sh
npm install -g boxdraw  # installs "boxdraw" to npm bin, ensure it's on your path
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
cd boxdraw
./boxdraw --help

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
cd boxdraw
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
