# boxdraw

Convert simple ascii grid drawings to unicode 'box-drawing' characters:

```
npm install -g boxdraw
boxdraw <<-EOF
> +-+
> | |
> +-+
> EOF
┌─┐
│ │
└─┘
```

```
git clone git@github.com:evnp/boxdraw.git
cd boxdraw
npm run demo
```

![boxdraw demo](https://raw.githubusercontent.com/evnp/boxdraw/main/boxdraw.png "boxdraw demo")

### Run on file input

```
cd boxdraw
./boxdraw < inputfile.txt
```

### Run on pasted input

```
cd boxdraw
./boxdraw <<-EOF    <PRESS ENTER>
> +-+---+           <PASTE INPUT>
> | |   |
> +-+-+ |
> | | | |
> +-+-+-+
> EOF               <ENTER "EOF">
                    <PRESS ENTER>
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

```
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

```
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
