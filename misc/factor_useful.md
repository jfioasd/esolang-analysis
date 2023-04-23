I think golfing languages outdesign each other simply because some of them have better 1-byte sequence processing functions than others.
(Not noting that number operations are not that useful in golf than sequences ... Numbers are the most common datatype in golflangs, but lists
are the most useful datatype.)

1. Blocks `[ ... ]`
2. Some way to denote lists (eg. `{ ... }`). And Strings `" ... "`
3. Numbers: `0` `1` `2` `3` `4` `5` `10` `0.0` ... (`t` `f`) (`166` is that frequent?)
4. Some stack-shuffling operators: `dup` `drop` `swap` `over` `nip` `2drop` `2dip` `2dup`
5. Some combinators: `cond [ if_t ] [ if_f ] if`, `.. .. and`, `.. .. or`, `.. not`, `[ .. ] dip`, `[ ... ] with` `[ .. ] [ .. ] bi`, `[ ... ] keep`, `[ .. ] when`, `[ .. ] map`, `[ .. ] each`
6. More: `[ .. ] call`, 
7. Other useful words: `+`, `=`, `seq` (really?), `_` (in fry sequence), `length`, `-`, `'[`, `*`, `first`, `<`, `set`, `on`, `::` (named word definition)
8. `""` empty string.
