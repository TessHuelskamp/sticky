# general bash things

![Direction Image](https://lorenzo.mile.si/wp-content/uploads/2018/02/moving_cli.png)

# editing the command line
| cmd | description |
| --- | ---- |
| {esc,alt} . | insert last work in prev command line after point (good if you want to run multiple commands on the same file |
| `^b` | back a char |
| `^f` | forward a char |
| `alt+b` | back a word |
| `alt+^f` | forward a word |
| `^d` | delete one char forward |
| `del` | delete one char backward |
| `^a` | go to beginning of line |
| `^e` | go to end of line |
| `^u` | kill the line from beginning to point |
| `^k` | kill from the point to the end of line |

# cmd completion
it's not very likely I'll use these day to day but it's worth knowing they
exist.

| cmd | description |
| --- | ---- |
| `tab` | you know what this is |
| `esc ?` | list possible completions |
| `esc /` | attempt file name completions |
| `esc ~` | attempt user name completions |
| `esc $` | attempt variable name completions |
| `esc @` | attempt host name completions |
| `esc !` | attempt command completions |
| `esc tab` | attempt completion from prev commands in history |

### miscellaneous
| cmd | description |
| --- | ---- |
| `^j` | return |
| `^l` | clear screen |
| `^t` | transpose two chars near point |
| `esc-c` | capitalize word after point |
| `esc-u` | uppercase next word |
| `esc-l` | lowercase next word |

### ways to access history
| cmd | description |
| --- | ---- |
| `!!` | last command. Good to run with `sudo !!`. Also works well with `nohup`, `echo`, and `git`. |
| `!string` | last command _starting_ with string |
| `!?string` | last command _containing_  string |
| `^string1^string2` | repeat last command, replacing 1 with 2. This one is v useful if you make a typo. Note that the substitution only happens once |

| Substitution | What it does |
|---------|--------------|
| `${param:-default}` | If `$param` is not set or is null, use `default` as the string |
| `${param:=default}` | If `$param` is not set or is null, *set* `default` to `$param` |
| `${param:+default}` | If `$param` is *set*, use `default`. Else, use the null string |
| `${param:?error_msg}` | If `$param` is set use it, if not abort the script with status=1 and display `error_msg`. |


# uncategorized

```bash
${!prefix@} #lists all variables (names. not values) starting with prefix
${!prefix*} #lists all variables starting with prefix
# I'm not yet sure what the difference between * and @ is.
# My guess it's similar to * and @ in arrays.
```
> [This site](http://tldp.org/LDP/abs/html/ivr.html) seems to explain this. I
> don't have time to look into it now but it looks like it allows you to hack
> out pointer type things.

## Bash

# `` `#comments` ``
In shell scripts, you can make "comments" that only take up part of the line
like this: `` `#comment` ``. The way this works is that the backticks execute
another shell (much like `$(CMD)`) and then the "command" that gets executed is
the commented line. I'm not sure why you can't do comments like this: `$(#CMD)`.

> Note: this spawns of another process just for these types of comments so it's
> not actually that useful.

> In order to use backticks in code spans in markdown (span, I guess, is the
> word for an inline block), you can begin the span with more than one \` and
> then a space. Like this:```` `` `#comment` `` ````

# String subs
[reference](http://www.tldp.org/LDP/abs/html/string-manipulation.html)

| Command | What it does | Notes |
|---------|--------------| --- |
| `${STRING#pattern}` | Remove shortest matching pattern from `$STRING` starting at the front | |
| `${STRING##pattern}` | Remove longest matching pattern from `$STRING` starting at the front | |
| `${STRING%pattern}` | Remove shortest matching pattern from `$STRING` starting at the end | This one is good for modifying file suffixes |
| `${STRING%%pattern}` | Remove longest matching pattern from `$STRING` starting at the end | |
| `${#STRING}` | The number of chars in `$STRING` | |
| `${STRING:IDX}` | `$STRING` starting at index `IDX` (0-based) | Can do negative indices but need a space or parens between `:` and `IDX`|
| `${STRING:IDX:LEN}` | `$STRING` starting at index `IDX` (0-based) for at most `LEN` chars | |
| `${STRING/pattern}` | Delete _first_ instance of pattern in `$STRING` | |
| `${STRING/pattern/newpattern}` | Replace first instance of `pattern` in `$STRING` with `newpattern` | |
| `${STRING//pattern}` | Delete _all_ instances of `pattern` in `$STRING` | |
| `${STRING//pattern/newpattern}` | Replace all instances of `pattern` in `$STRING` with `newpattern` | |
| `${STRING/{#,%}pattern/newpattern}` | Replace the {front, back} of `$STRING` with `newpattern` if `pattern` matches. | |

