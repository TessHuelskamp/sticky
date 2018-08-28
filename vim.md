# spell check
Vim's spell check is enabled like this: `set spell spelllang=en_us`. You can
tell vim what spell file you want to use like this: `set spellfile=~/.vim/spell/tess.utf-8.add`.
There, you can put a list of words (one per line) to tell vim that those are
spelled correctly.

I haven't figured out how to make a spell file per project (I could see where
you'd want one) but I'll figure that out later when I need one.

Once the spell file is set, you can add new words on the fly to it by pressing
`zg` on a word that the spell checker has marked as incorrectly spelled. That
will add that word to the file and then regenerate the data structure vim uses
to efficiently search for misspelled words.

>Also, note that if you make changes to the spell file, vim needs to load them
>in via `;mkspell! FILE`

`[s` and `]s` move you around to the next and previous misspelled words. `z=` on
top of a misspelled word drops you into a list of words that vim thinks are a
better fit. `1z=` picks the first choice in spell check (works most of the time).


# numbers
* `CRTL-X` decrements a number
  * (and `CRTL-A` increments a number)

# f and t
* `f`_CHAR_ brings you forward to the next _CHAR_
  * Note that it *does* work with `d` to delete things.
  * And also it only works on the current line
  * ALSO: `F` brings you _backward_ to the next char.
* `t` and `T` work similarly to `f` and `F` but they bring you to the
  character _prior_ to the character that follows the operator.
