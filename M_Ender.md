

https://esoteric.codes/blog/martin-ender

» Tell me more about golfing languages: how do these languages take different approaches to solving the same problem? The challenge for golfing languages to allow programmers to be concise is almost the opposite of the minimalism of, say, brainfuck, where the language is tiny but the programs huge. How do you design a language toward these ends, and are there different general approaches?

You're right, designing golfing languages is quite different from designing esolangs. While these languages are still far from production languages, they share with those that they are designed to solve a problem (in this case, expressing a variety of programs in as few bytes of code as possible). These languages normally don't try to be quirky, they just sometimes end up being quirky because everything the language can do without you explicitly saying so (but meaning to) is great.

Of course, part of making a concise language is providing a large number of built-ins, which can solve useful tasks or subtasks in a single byte. So in order to maximise the number of built-ins you can provide, modern golfing languages make use of all 256 byte values. To that end, they usually define their own code page, so that all of those bytes are printable and, if possible, represent characters that provide somewhat reasonable mnemonics.

But it seems to be a bit of a misconception among less experienced golfing language designers that just throwing together a bunch of built-ins is all it takes to create a great golfing language: it's generally not very helpful to have a "FizzBuzz" built-in, because while that lets you solve this particular problem in a single byte, it also wastes that byte for another useful command (because it's probably not going to be used in any other program). So for a start, you'd rather want to think about a good set of built-ins that combine easily to build lots of different short programs.

But even then, built-ins are only part of the language's design and probably even the less important part: the real meat of designing a golfing language is coming up with language semantics and syntax that avoid redundancy. It's especially important to avoid the need for parentheses or other characters which are only there to specify the order of operations. Ideally, you'll just want to be able to put the operators you need into the source code in some order that just makes things work, without having to specify every single operand explicitly. And this is where golfing languages have taken several very interesting (and I'd say roughly equally successful) approaches.

GolfScript, and by extension CJam, started a tradition of using stack-based semantics to avoid the need for referring to operands. And even the very popular (and successful) 05AB1E is stack-based. But stack-based languages still sometimes have the problem that you end up wasting several bytes on reordering the stack so that your arguments are in the correct order (unfortunately, I don't know 05AB1E well enough to tell whether or how it solves this problem, but it's certainly a very competitive language).

Jelly instead takes inspiration from J and defines how various combinations of nilads, monads and dyads are composed into useful functions which are applied to the inputs (similar to J's hooks and forks). Interestingly, there's a layer on top of that which lets you combine the built-in functions into others using higher-order operators which is stack-based (i.e. the parser keeps track of a stack of functions which you can combine with those operators).

And then there's Husk, which is a pure functional and strongly typed language like Haskell. Here, the strong typing is used to infer the order of operations automatically so that each function in the resulting expression tree gets a valid list of arguments.

There are other approaches out there, both explored and unexplored, but the competition and exposure these languages have received on PPCG has already led to some very impressive and varied language design (e.g. there's also Brachylog which is a declarative golfing language based on Prolog). The first generation or two of golfing languages don't normally stand a chance against any of these modern ones.

