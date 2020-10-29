# boxdraw

Convert simple ascii grid drawings to unicode 'box-drawing' characters:

```sh
npm install -g boxdraw
./boxdraw <<-EOF          # PRESS ENTER
> +-+                     # PASTE INPUT
> | |
> +-+
> EOF                     # ENTER "EOF"
┌─┐                       # PRESS ENTER
│ │
└─┘
```

```sh
git clone git@github.com:evnp/boxdraw.git
cd boxdraw
npm run demo
```

![boxdraw demo](https://raw.githubusercontent.com/evnp/boxdraw/main/boxdraw.png "boxdraw demo")

### Run on file input

```sh
cd boxdraw
./boxdraw < inputfile.txt
```

### Run on pasted input

```sh
cd boxdraw
./boxdraw <<-EOF          # PRESS ENTER
> +-+---+                 # PASTE INPUT
> | |   |
> +-+-+ |
> | | | |
> +-+-+-+
> EOF                     # ENTER "EOF"
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
./boxdraw 3 <<-EOF
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
./boxdraw 0 bold <<-EOF
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

./boxdraw 0 double <<-EOF
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
