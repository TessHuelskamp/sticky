# sticky
Weekly notes about a few syntax things I've been wanting a quick reference
for. This is to replace the stickies I usually have around my desk with
something that I can up in a tab on my browser so that I don't need to
repeatedly google the same things.

Hopefully this list should be expanded with new things as I commit the old
things to memory and learn more things.

# 12/11/17 cpp lambdas
[Ref](http://en.cppreference.com/w/cpp/language/lambda)
Syntax is one of the following things
* `[capture](params){fn; body;}`
* `[capture](params)->retType{fn; body;}`
* `[capture]{fn; body;}` (no params)

## capture explained
The capture option can take one of the following values.

| capture | result |
| :-----: | ------ |
| `[]` | captures nothing |
| `[=]` | capture everything in scope by value _at time of def_ |
| `[&]` | capture everything in scope by reference |
| `[this]` | captures current object by `*this` ref |
| `[a, &b]` | capture var `a` by copy, `b` by ref |

# 11/6/17 - Bash

This eventually we be moved to be near the string manipulation section but here's
information about bash variable replacement.

> These notes are based off of [this](http://tldp.org/LDP/abs/html/parameter-substitution.html) reference.

> The `:` is optional in the following examples. Omitting it removes the check
> if the variable is null or not.

| Substitution | What it does |
|---------|--------------|
| `${param:-default}` | If `$param` is not set or is null, use `default` as the string |
| `${param:=default}` | If `$param` is not set or is null, *set* `default` to `$param` |
| `${param:+default}` | If `$param` is *set*, use `default`. Else, use the null string |
| `${param:?error_msg}` | If `$param` is set use it, if not abort the script with status=1 and display `error_msg`. |

## bash - uncategorized
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

# 10/23/17 - Gmail shortcuts
These shortcuts are directly taken from
[this](https://blog.hubspot.com/sales/gmail-keyboard-shortcuts) article.

Comments are my own.

[Here's](https://support.google.com/mail/answer/6594?co=GENIE.Platform%3DDesktop&hl=en) google's docs.

## In "inbox view"
This is the view that you enter when you first got to gmail.

  * `Shift` is supposed to be able to select a range of emails (I couldn't get this
  one to work)
  * `shift + 8 + u` grabs all of the unread messages
  * `e` (with messages selected) archives messages
  * `=` (with messages selected) marks messages as important
  * `c` drops you into compose mode
  * `/` drops you into search mode (just like vim!!)
  * and `j` and `k` move up and down your messages like you would expect them to

> I need to figure out how to select a series of messages with j and k without
> having to click anything :)


## Conversation view
This view basically isn't the inbox view and isn't when you're composing a
message.

  * `r` allows you to reply to a message
  * `a` allows you to reply all to a message
  * `f` lets your forward a message
  * `shift + u` allows you to mark a message as unread
  * `=`, `e`, `a`, `r`, `j`, and `k` work as before
  * `n` jumps you to the next message in the thread
  * `p` jumps you to the previous message in the thread
  * `m` lets you mute the thread
  * `u` allows you to go back to inbox view

## Compose view
  * `cmd + shift + k` allows you to drop in a link
  * `cmd + shift + 7/8` drops you into a numbered or ordered list, respectively
  * Tabbing works as it does with every other website :)
  * Bolding, italicizing, and underlining all work as they normally do
  * and `cmd + enter` sends things

# 10/18/17
`ctrl-l` clears the screen.

# 10/16/17
In shell scripts, you can make "comments" that only take up part of the line
like this: `` `#comment` ``. The way this works is that the backticks execute
another shell (much like `$(CMD)`) and then the "command" that gets executed is
the commented line. I'm not sure why you can't do comments like this: `$(#CMD)`.

> Note: this spawns of another process just for these types of comments so it's
> not actually that useful.

> In order to use backticks in code spans in markdown (span, I guess, is the
> word for an inline block), you can begin the span with more than one \` and
> then a space. Like this:```` `` `#comment` `` ````

# 10/10/17
## Git
To remove branches on remote `git push REPO --delete BRANCH`

## Vim
  * `CRTL-X` decrements a number
    * (and `CRTL-A` increments a number)

# 10/4/17
## Markdown
I keep forgetting how to make checkmark lists. They go like this:
```
  - [ ] This is the first bullet that isn't done yet.
  - [ ] This is the second uncompleted bullet.
  - [x] This bullet is completed.
  - [ ] And this one isn't.
```
Output
  - [ ] This is the first bullet that isn't done yet.
  - [ ] This is the second uncompleted bullet.
  - [x] This bullet is completed.
  - [ ] And this one isn't.

## Vim
  * `f`_CHAR_ brings you forward to the next _CHAR_
    * Note that it *does* work with `d` to delete things.
    * And also it only works on the current line
    * ALSO: `F` brings you _backward_ to the next char.
  * `t` and `T` work similarly to `f` and `F` but they bring you to the
    character _prior_ to the characer that follows the operator.

## Bash
These are the basic string substitutions. These examples are based from
[this](http://www.tldp.org/LDP/abs/html/string-manipulation.html) reference.

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

