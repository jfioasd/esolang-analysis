# esolang-analysis
This repository holds the 1-byte and 2-byte command frequencies for several esolangs used on CGCC.

## An interesting observation
Jelly has a total of 380 builtins that are ever used on CGCC (1 or 2 bytes). 05AB1E has 415 builtins actually used in total (because there are a few random builtins for specific purposes).

That means these 2-byte builtins could be packed into a single visual unit if the encoding base of the program is larger, say, base 343 (or maybe base 361) for example. (You don't need large bases at all to encode all of your builtins.) Then, programs would be significantly golfier without spending an extra bit in encoding. (The base 512 approach I see in [Orst](https://github.com/cairdcoinheringaahing/Orst-Geo) is too inefficient, because a large part of the encoding is not used to pack actual commands.)

Indeed, I don't think these two bases [make much of a difference](https://tio.run/##yy9OTMpM/f/f2MT43CYjU7MLm/7/jwZydKA4FgA) in length, except for 1/2-bit bloats for edge cases where the digits in base-343 is large. This can be circumvented by making sure that the most frequent builtins are encoded with the smallest digits, and the least frequent builtins encoded with the largest digits, to ensure optimal compression. 

---

P. S. Vyxal uses range encoding, and Nibbles uses an approximation to range encoding. So it would be good to pass this base-343 format to a range encoder for compressing the most frequent character sequences to a shorter format.

Also, if it's possible to train a neural network to insert the highly common builtins at the correct positions (so that they don't have to be written explicitly), that would be a great advantage. Neural networks can be quite accurate. ;P

P. P. S. Though the commands are very common, their digraph combinations are highly specific (since they often pair with a lot of different builtins).

## Defining a core set of builtins & semantics
Even though the encoding space is enlarged, it's useless if the builtins encoded inside aren't general / useful builtins that can combine easily to form a lot of programs. Therefore, the actual choices of the builtins provided in the language needs to be worked on as well.

TODO: talk about datatypes, short constant optimization (including blocks), higher-order-functions, operations, choosing builtins, ...

to be continued...
