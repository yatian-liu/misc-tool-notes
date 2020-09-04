## Moving and searching quickly

fx: move to the next occurrence of character 'x' on current line. Type ; to repeat this command.
Fx: move to the previous occurrence.
tx: move to one character before the destination of the fx motion.
Tx: move to one character after the destination of the Fx motion.
^: move to the first *non empty* character on current line.

numG: move to line num.
num|: move to column num.
H: move to the top of the screen.
L: move to the bottom of the screen.

(: sentences backward.   ): sentences forward.
{: paragraphs backward.   }: paragraphs forward.

]]: jump to the next "{" in the first column (beginning of last C-style function).
[[: jump to the previous "{" in the first column.
[{: jump to the "{" at the start of the current code block.
[}: jump to the "}" at the end of the current code block.

``: go the last edited line.
g;: jump backward in changelist.
g,: jump forward in changelist.

gd: jump to the local declaration of a variable/function/... .
gD: jump to the global declaration.
CTRL-]: jump to the place corresponding to the flag under the cursor.
CTRL-O: jump to older position in the *jump list*.
CTRL-I: jump to newer position.

clear search highlight: :noh.
\*: search the word under the cursor and move to the next occurence.
\#: same as \*, but move to the previous occurence.


## Avoid repeating types

Remember to add num before actions for repetition!

.: repeat the last *change* (insert, delete, replace...).

:%s/foo/bar/g: find 'foo' and replace it with 'bar' in all lines. (%: range, all lines; g: flag, replace all the occurences in one line.)
:%s.../gc: same as above, but ask for confirmation for each replacement (the 'c' flag).
"%" can be replaced by "num1,num2", representing a range from line num1 to line num2.

CTRL-N: move to the next match of auto completion.
CTRL-P: move to the previous match.

qx: start recording macro and store it into register x (a letter). To stop recording, press q again in normal mode.
@x: playback the macro stored in register x.
@@: playback the last macro.

:reg: show recently copied contents (multiple clipboards or registers).
"x[op]: do the operation (usually yank/paste) for the register x.
CTRL-R x: paste from register x in insert mode.
:call setreg('x', []): clear the register x.
## Moving and searching quickly

fx: move to the next occurrence of character 'x' on current line. Type ; to repeat this command.
Fx: move to the previous occurrence.
tx: move to one character before the destination of the fx motion.
Tx: move to one character after the destination of the Fx motion.
^: move to the first *non empty* character on current line.

numG: move to line num.
num|: move to column num.
H: move to the top of the screen.
L: move to the bottom of the screen.

(: sentences backward.   ): sentences forward.
{: paragraphs backward.   }: paragraphs forward.

]]: jump to the next "{" in the first column (beginning of last C-style function).
[[: jump to the previous "{" in the first column.
[{: jump to the "{" at the start of the current code block.
[}: jump to the "}" at the end of the current code block.

``: go the last edited line.
g;: jump backward in changelist.
g,: jump forward in changelist.

gd: jump to the local declaration of a variable/function/... .
gD: jump to the global declaration.
CTRL-]: jump to the place corresponding to the flag under the cursor.
CTRL-O: jump to older position in the *jump list*.
CTRL-I: jump to newer position.

clear search highlight: :noh.
\*: search the word under the cursor and move to the next occurence.
\#: same as \*, but move to the previous occurence.


## Avoid repeating types

Remember to add num before actions for repetition!

.: repeat the last *change* (insert, delete, replace...).

:%s/foo/bar/g: find 'foo' and replace it with 'bar' in all lines. (%: range, all lines; g: flag, replace all the occurences in one line.)
:%s.../gc: same as above, but ask for confirmation for each replacement (the 'c' flag).
"%" can be replaced by "num1,num2", representing a range from line num1 to line num2.

CTRL-N: move to the next match of auto completion.
CTRL-P: move to the previous match.

qx: start recording macro and store it into register x (a letter). To stop recording, press q again in normal mode.
@x: playback the macro stored in register x.
@@: playback the last macro.

:reg: show recently copied contents (multiple clipboards or registers).
"x[op]: do the operation (usually yank/paste) for the register x.
CTRL-R x: paste from register x in insert mode.
:call setreg('x', []): clear the register x.
:let @x=@y: set the value of register x to the value of register y.

]p: paste, automatically adjust indentation.

q:: open the command-line window for commands.
q/: open the command-line window for searchs.
Press enter to execute the current line of command or search.

## Specific settings on vimtex

Basic:
\ -> normal mode mapping leader.
\ll: compile toggle.
\lv: view (synctex supported).
\li: info about vimtex.
\lm: show insert mode mappings.
; -> insert mode mapping leader.

Text objects:
ac/ic: for commands.           ad/id: for delimiters.
ae/ie: for environments.       a$/i$: for inline math.
aP/iP: for sections.

Motions:
[[: previous beginning of a section.
[]: previous end of a section.
][: next beginning of a section.
]]: next end of a section.
[m: previous environment '\begin'.
]m: next environment '\begin'.

Others:
cse: change surrounding environment.
tse: toggle star of the surrounding environment.
tsd: toggle the "\left"/"\right" modifier of the closest (in forward direction) surrounding delimeter.
tsD: toggle the closest (in backward direction).
]] close the current delimeter.

## Other useful commands

:earlier {N}s/m/h/d: go to older text state {N} seconds/minutes/hours/days before.
:earlier {N}f: go to older text state {N} file writes before.
:later {N}s/m/h/d: go to newer text state.

:setlocal spell spelllang=en_us: enable spell checking in the *local* buffer only.
:setlocal nospell: turn off spell checking.
]s: move to next misspelled word.
[s: move to previous misspelled word.
z=: correct the misspelled word under cursor.
zg: add the word under cursor into global dictionary.
zG: add the word under cursor into a temporary dictionary.
zw: mark the word under cursor as wrong.

echo [var_name]: print the value of a defined variable.
echo &[opt_name]: print the value of a defined editor option.

:let @x=@y: set the value of register x to the value of register y.

]p: paste, automatically adjust indentation.

q:: open the command-line window for commands.
q/: open the command-line window for searchs.
Press enter to execute the current line of command or search.

:Helptags: update documentation when a new pathogen bundle is installed.

