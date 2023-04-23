I think golfing languages outdesign each other because some of them have better sequence processing functions than others. For example they have builtins for palindromize, center, Husk has count-by, etc.

(Not noting that number operations are not that useful in golf than sequences ... Numbers are the most common datatype in golflangs, but lists
are the most useful datatype.)

1. Blocks `[ ... ]`
2. Some way to denote lists (eg. `{ ... }`). And Strings `" ... "` which are just arrays of codepoints.
3. Numbers: `0` `1` `2` `3` `4` `5` `10` `0.0` ... (`t` `f`) (`166` is that frequent?)
4. Some stack-shuffling operators: `dup` `drop` `swap` `over` `nip` `2drop` `2dip` `2dup`
5. Some combinators: `_cond_ [ if_t ] [ if_f ] if`, `and`, `or`, `not`, `dip`, `with` `bi`, `keep`, `when`, `map`, `each`
6. More: `call`, `bi@` (which applies 1 quotation to two values), `bi*` (which respectively applies two quotations to two values).
7. Other useful words: `+`, `=`, `seq` (really?), `_` (in fry sequence), `get`, `length`, `-`, `'[`, `*`, `first`, `<`, `set`, `on`, `::` (named word definition), `%` (which is more useful than `/`)
8. `""` empty string. `-1`. `write`: print str. w/o a newline
