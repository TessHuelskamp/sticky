# lambdas
[Ref](http://en.cppreference.com/w/cpp/language/lambda)
Syntax is one of the following things
* `[capture](params){fn; body;}`
* `[capture](params)->retType{fn; body;}`
* `[capture]{fn; body;}` (no params)

# capture explained
The capture option can take one of the following values.

| capture | result |
| :-----: | ------ |
| `[]` | captures nothing |
| `[=]` | capture everything in scope by value _at time of def_ |
| `[&]` | capture everything in scope by reference |
| `[this]` | captures current object by `*this` ref |
| `[a, &b]` | capture var `a` by copy, `b` by ref |

