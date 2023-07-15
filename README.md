# esolang-analysis
1-byte command order for several esolangs used on CGCC.

An interesting thing I discovered is that Jelly, with all its builtins ever used in CGCC answers (1 and 2 bytes), has a total of 380 builtins. 05AB1E has 415 builtins in total.

That means these 2-byte builtins could be packed into a single visual unit if the encoding base of the program is larger, say, base 343 for example. Then, programs would be significantly golfier without spending an extra bit in encoding. (The base 512 approach I see in [Orst](https://github.com/cairdcoinheringaahing/Orst-Geo) is too inefficient, because a large part of the encoding is not used to pack actual commands.)
