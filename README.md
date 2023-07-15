# esolang-analysis
1-byte command order for several esolangs used on CGCC.

## An interesting observation
An interesting thing I discovered is that Jelly, has a total of 380 builtins that are ever used on CGCC (1 or 2 bytes). 05AB1E has 415 builtins actually used in total (because there are a few random builtins for specific purposes added here or there).

That means these 2-byte builtins could be packed into a single visual unit if the encoding base of the program is larger, say, base 343 for example. Then, programs would be significantly golfier without spending an extra bit in encoding. (The base 512 approach I see in [Orst](https://github.com/cairdcoinheringaahing/Orst-Geo) is too inefficient, because a large part of the encoding is not used to pack actual commands.)

Indeed, I don't think these two bases [make much of a difference](https://tio.run/##yy9OTMpM/f/f2MT43CYjU7MLm/7/jwZydKA4FgA) in length, except for 1/2-bit bloats for edge cases where the digits in base-343 is large. This can be circumvented by making sure that the most frequent builtins are encoded with the smallest digits, and the least frequent builtins encoded with the largest digits, to ensure optimal compression. 
