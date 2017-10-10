# sticky
Weekly notes about a few syntax things I've been wanting a quick reference
for. This is to replace the stickies I usually have around my desk with
something that I can up in a tab on my browser so that I don't need to
repeatedly google the same things.

Hopefully this list should be expanded with new things as I commit the old
things to memory and learn more things.

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
| `${STRING:IDX}` | `$STRING` starting at index `IDX` (0-based) | Can do negative indicies but need a space or parens between `:` and IDX|
| `${STRING:IDX:LEN}` | `$STRING` starting at index `IDX` (0-based) for at most `LEN` chars | |
| `${STRING/pattern}` | Delete first instance of pattern in `$STRING` | |
| `${STRING/pattern/newpattern}` | Replace first instance of `pattern` in `$STRING` with `newpattern` | |
| `${STRING//pattern/newpattern}` | Delete all instances of `pattern` in `$STRING` | |
| `${STRING//pattern/newpattern}` | Replace all instances of `pattern` in `$STRING` with `newpattern` | |




 
