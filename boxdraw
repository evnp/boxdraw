#!/usr/bin/env bash

set -euo pipefail

function boxdraw() {

	# if no stdin was provided, print help text:
	if [[ -t 0 ]]; then
		cat <<-EOF

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

		EOF

		if [[ " ${*} " == *" --help "* || " ${*} " == *" -h "* ]]; then
			exit 0
		else
			exit 1
		fi
	fi

	# first arg : margin (integer, optional) - define space around drawing
	local margin="${1:-0}"
	local marginchars=""
	local marginidx
	if (( margin > 0 )); then
		for (( marginidx=0 ; marginidx < margin ; marginidx++ )); do
			echo             # print top margin
			marginchars+=" " # calc string to be used for left margin
		done
	fi

	# second arg : style (integer or string enum [ light bold double ], optional)
	# 0 / light  - use thin-lined box-drawing characters
	# 1 / bold   - use thick-lined box-drawing characters
	# 2 / double - use double-lined box-drawing characters
	local style="${2:-0}"
	if [[ "${style}" == 'light' ]]; then
		style=0
	elif [[ "${style}" == 'bold' ]]; then
		style=1
	elif [[ "${style}" == 'double' ]]; then
		style=2
	elif [[ "${style}" =~ ^[012]$ ]]; then
		style=0
	fi

	# box-drawing character sets, indexed by cardinal directions:
	local nesw="┼╋╬"
	local nes_="├┣╠"
	local ne_w="┴┻╩"
	local ne__="└┗╚"
	local n_sw="┤┫╣"
	local n_s_="│┃║"
	local n__w="┘┛╝"
	local n___="╵╹║"
	local _esw="┬┳╦"
	local _es_="┌┏╔"
	local _e_w="─━═"
	local _e__="╶╺═"
	local __sw="┐┓╗"
	local __s_="╷╻║"
	local ___w="╴╸═"
	local ____="···"

	# other box-drawing charset management vars:
	local boxchar boxcharset boxcharsetidx boxcharsetvarname
	local boxchars="${nesw}${nes_}${ne_w}${ne__}${n_sw}${n_s_}${n__w}${n___}${_esw}${_es_}${_e_w}${_e__}${__sw}${__s_}${___w}${____}"
	local boxcharsets=(
		"${nesw}"
		"${nes_}"
		"${ne_w}"
		"${ne__}"
		"${n_sw}"
		"${n_s_}"
		"${n__w}"
		"${n___}"
		"${_esw}"
		"${_es_}"
		"${_e_w}"
		"${_e__}"
		"${__sw}"
		"${__s_}"
		"${___w}"
		"${____}"
	)

	# line vars : current line, prev line, next line, output line:
	local curr prev next dest

	# char vars : char index ; idx plus 1 ; idx minus 1 ; current char
	local charidx charip1 charim1 curchar

	# cardinal directions : north, south, east, west
	local n e s w

	while # do-while loop : iterate over lines in stdin (loop condition at end)

		prev="${curr:-}"
		curr="${next:-}"

		IFS= read -r next || true  # don't exit once we read empty line

		if [[ -n "${curr}" ]]; then
			dest=""

			for (( charidx=0 ; charidx < "${#curr}" ; charidx++ )); do
				charim1=$(( charidx - 1 ))
				charip1=$(( charidx + 1 ))
				curchar="${curr:${charidx}:1}"

				if [[ '+''-''─''|''│' == *"${curchar}"* ]]; then
					n="${prev:${charidx}:1}"
					e="${curr:${charip1}:1}"
					s="${next:${charidx}:1}"
					w="${curr:${charim1}:1}"; (( charim1 < 0 )) && w='' # don't allow negative indexing
					if [[ -n "${n}" && '+''┼''|''│''┤''├''·''┬' == *"${n}"* ]]; then n=n; else n=_; fi
					if [[ -n "${e}" && '+''┼''-''─''┤''·''┴''┬' == *"${e}"* ]]; then e=e; else e=_; fi
					if [[ -n "${s}" && '+''┼''|''│''┤''├''┴''·' == *"${s}"* ]]; then s=s; else s=_; fi
					if [[ -n "${w}" && '+''┼''-''─''·''├''┴''┬' == *"${w}"* ]]; then w=w; else w=_; fi
					boxcharsetvarname="${n}${e}${s}${w}"
					boxcharset="${!boxcharsetvarname}"
					boxchar="${boxcharset:${style}:1}"
				else
					boxchar="${curchar}"

					if (( style )) && [[ "${boxchars}" == *"${boxchar}"* ]]; then
						for (( boxcharsetidx=0 ; boxcharsetidx < ${#boxcharsets[@]} ; boxcharsetidx++ )); do
							boxcharset="${boxcharsets[${boxcharsetidx}]}"
							if [[ "${boxcharset}" == *"${boxchar}"* ]]; then
								boxchar="${boxcharset:${style}:1}"
								break
							fi
						done
					fi
				fi

				dest+="${boxchar}"
			done
			echo "${marginchars}${dest}"
		else
			echo
		fi

	# do-while condition : iterate over lines in stdin
	[[ -n "${next:-}" || -n "${curr:-}" ]]; do continue; done

	if (( margin > 0 )); then
		# print bottom margin:
		for (( marginidx=0 ; marginidx < margin ; marginidx++ )); do echo; done
	fi
}

boxdraw "$@"
