I think golfing languages outdesign each other because some of them have better sequence processing functions than others. For example they have builtins for palindromize, center, Husk has count-by, etc.

(Not noting that number operations are not that useful in golf than sequences ... Numbers are the most common datatype in golflangs, but lists
are the most useful datatype.)

I learned a lot about the most frequently used number constants after looking at this corpus.

1. Blocks `[ ... ]`
2. Some way to denote lists (eg. `{ ... }`). And Strings `" ... "` which are just arrays of codepoints.
3. Numbers: `0` `1` `2` `3` `4` `5` `10` `0.0` `2.0` ... (`t` `f`) (`166` is that frequent?)
4. Some stack-shuffling operators: `dup` `drop` `swap` `over` `nip` `2drop` `2dip` `2dup`
5. Some combinators: `_cond_ [ if_t ] [ if_f ] if`, `and`, `or`, `not`, `dip`, `with` `bi`, `keep`, `when`, `map`, `each`
6. More: `call`, `bi@` (which applies 1 quotation to two values), `bi*` (which respectively applies two quotations to two values). `tri` (which applies 3 quotations to 1 value, like `bi`), `2bi` (which respectively applies two dyadic quotations over two values )
7. Other useful words: `+`, `=`, `seq` (really?), `_` (in fry sequence), `get`, `length`, `-`, `'[`, `*`, `first`, `<`, `set`, `on`, `::` (named word definition), `%` (which is more useful than `/`), `shift` (bit shifting...), `curry` (like `keep`, but uses TOS as the first value of partial application of quotation), `unless` (`when` with `not`ted argument), `2array` (which is just pair)
8. `""` empty string. `-1`, `16`, `100`, `9`, `20` (didn't see `6` thru `8` that much here), `11`, `30`, `write`: print str. w/o a newline, `print` (print str w/ a newline)
9. `case` (is more useful than `cond`, evidently), `cond`, `values` (outputs all values in an assoc.) `nth` (indexing)
10. and then we have `>` and `/`. `pick` (`x y z -- x y z x`), `append` (merge sequences), `if*` (preserve cond if true), `15`, `32`, `first2`, `when*`, `<iota>` (`[0..n-1]`), `index` (Which is basically `indexOf`), `member?` (Whether seq contains object), `bitand`, `cleave` (a generalized `bi` or `tri` form), `push` (append item to end of seq), `string>number`, `%`, 
11. `31`, `number>string`, `14`, `13`, `>string`, `filter` (Well, it's used so much less than `map`, so it's not in the same frequency class as map). `neg` (but I'm not going to add explicit negative numbers to my golflang because that's to costly). `1array` (wrap TOS into arr).
12. `times` (a kind of repeat-quotation-n-times function), `prepend`, `dupd` (`x y -- x x y`), `111`
13. `keys` (keys of assoc. arr), `rot` (`x y z - y z x`), `empty?`
14. `24`, `>=`, `60`, `50`, `<=`, `-2`, `21`, `2^` (i.e. `2 ** x`), `0.5`, `all?`, `bitor`, `count` (# of items quotation matches), `zero?`, `/i`, `max`
15. I'll stop here because things start to get a bit too useless from this point on.

I'll do another iteration of this later on because I feel I've missed some things.
