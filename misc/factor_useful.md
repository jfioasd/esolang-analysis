I think golfing languages outdesign each other because some of them have better sequence processing functions than others. For example they have builtins for palindromize, center, Husk has count-by, etc.

(Not noting that number operations are not that useful in golf than sequences ... Numbers are the most common datatype in golflangs, but lists
are the most useful datatype.)

1. Blocks `[ ... ]`
2. Some way to denote lists (eg. `{ ... }`). And Strings `" ... "` which are just arrays of codepoints.
3. Numbers: `0` `1` `2` `3` `4` `5` `10` `0.0` `2.0` ... (`t` `f`) (`166` is that frequent?)
4. Some stack-shuffling operators: `dup` `drop` `swap` `over` `nip` `2drop` `2dip` `2dup`
5. Some combinators: `_cond_ [ if_t ] [ if_f ] if`, `and`, `or`, `not`, `dip`, `with` `bi`, `keep`, `when`, `map`, `each`
6. More: `call`, `bi@` (which applies 1 quotation to two values), `bi*` (which respectively applies two quotations to two values). `tri` (which applies 3 quotations to 1 value, like `bi`), `2bi` (which respectively applies two dyadic quotations over two values )
7. Other useful words: `+`, `=`, `seq` (really?), `_` (in fry sequence), `get`, `length`, `-`, `'[`, `*`, `first`, `<`, `set`, `on`, `::` (named word definition), `%` (which is more useful than `/`), `shift` (bit shifting...), `curry` (like `keep`, but uses TOS as the first value of partial application of quotation), `unless` (`when` with `not`ted argument)
8. `""` empty string. `-1`, `16`, `100`, `9`, `20` (didn't see `6` thru `8` that much here), `11`, `30`, `write`: print str. w/o a newline, `print` (print str w/ a newline)
9. `case` (is more useful than `cond`, evidently), `cond`, `values` (outputs all values in an assoc.) `nth` (indexing)
10. and then we have `>` and `/`.
