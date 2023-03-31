# jfioasd.github.io

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

» Some of your languages are concise in their menu of commands (Hexagony) while others, like Alice, have lengthy lists, compared to many esolangs. What is your thinking in deciding what to offer, and how friendly to make a language, apart from getting its programmers to think in the topographical space and program flow rules you've constructed?

I actually often have a hard time deciding on this when designing a language. With Labyrinth and Hexagony, I just decided not to use any letters to keep the number of commands reasonable but then filled up all the characters I had. It just seemed inelegant to have a few random letters in there, because then I really would have wondered "Why these commands and no others? Where do I stop?". (The only exception is v, because it goes so well with <>^.)

For Stack Cats I was much more restricted from the start: due to the symmetry constraints which are the core of the language, I only had a limited set of characters to work with, and it was already decided which of these would be involutions and which would be mutual inverses. There aren't a whole lot of characters to work with here, and I wanted most of them to act as mnemonics, but in the end I ran out of good ideas for interesting involutions first, so I didn't even use all of the characters available.

For Alice, I made a conscious decision to go for a feature-rich 2D language (because I was already overloading them with the two different modes; why would you start overloading if you still have characters left to assign). So Alice uses all printable ASCII characters as commands. That ended up being quite a challenge, because at some point coming up with interesting new ideas for commands starts to get tricky, but I'm quite happy with the final set I ended up with. The large number of commands let me explore some fun ideas that would have been scrapped in a more concise language, and I've already found use even for a lot of the more obscure commands.

The good part about the language's design is that I could get away with some really wonky commands if they neatly corresponded to a reasonable command in the other mode. For example there's a command which lets you replace the divisors of a number, but that's completely fine because one of the language's themes is that it associates characters with prime factors and substrings with divisors. So this weird built-in is the counterpart of a fairly standard substring replacement.

Wumpus was the first time I had the confidence to pick a set of commands based on what seemed useful and thematic instead of forcing myself to fill up some predefined set of characters. While choosing commands I looked at ways of manipulating the various language concepts I provided (the stack, the grid and the icosahedron) in natural ways and designed the operators around that.

» You mention "Many esolangs are deeply complex emergent systems: I can come up with a few rules to define a language and then spend weeks discovering how programming and golfing works in this model." Could you tell us about esolangs in particular that you've had this experience with?

The first language that comes to mind is also my first esolang Labyrinth. For example, as I said, I added the grid rotation commands simply based on the boardgame Labyrinth, but without any real use case in mind. I also started out designing the language with the (in my opinion) very consistent rules of how the instruction pointer behaves at each possible junction depending on the value on top of the stack. I was left with a single case where there wasn't a natural choice where to go (paths to the left and right, but the top of the stack is zero) and decided to make this choice random, which seemed like a neat way to get randomness into the language without having to provide a specific command for it.

Now, it turns out that it's impossible for the IP to end up in this specific configuration unless you make use of the grid rotation commands. That's something I never intended but the two independent mechanics of the language ended up meshing quite neatly. Grid rotation also turns out to be quite useful for golfing and for writing busy beavers, but I feel like I haven't even scratched the surface of what's possible with these commands.

With Alice, for example, I found out some time after completing the language that it provides an idiom I wish some production languages had. Consider a case where you want to run a loop for a while but you want to alternate between two different pieces of code for each loop iteration (so even iterations do something else than odd iterations). This can be useful, e.g. to process both a list and the separators between list elements in one go. Alice's jump commands sort of separate the IP's position from its direction (the return address stack remember the position but not the direction), which lets you implement this kind of loop very neatly:

    
...number of iterations...&w...even iteration...v

                           .                    k

                           >...odd iteration...k>...end of loop...

The k jumps back to the w, and by turning the IP around before jumping back we can make sure that we alternate between the two different loop bodies.

There's also Stack Cats, where I still haven't figured out how to write concise programs effectively which make use of both halves of the code. I found a construction that lets me skip the first half of the code and only executes the second half, which circumvents the language's symmetry restrictions. All non-trivial programs I've written (including "Hello World" and a prime number test) make use of this construction, because I still don't know how to make use of both halves. But I've started writing programs that search for short programs to simple tasks and it's fascinating to see the techniques these programs use (and it also turns out that such a search can be sped up significantly by applying considerations from group theory to the program space, because Stack Cats programs do form a group).

» What other topological spaces or structures are interesting to you, in terms of code or otherwise, or that you might want to explore in other languages?

I have quite a backlog of language design ideas. I'm usually not very comfortable speaking about those until they're done, but I'll try to mention a few.

The language I'm currently working on actually has fractal topology, but that makes it sound a lot worse than it is. The fractal nature is mostly related to the fact that the language is functional and provides something akin to infinite, lazy lists and how the language handles recursion without providing named functions. The source code itself also doesn't really resemble a fractal. It's more about the language's structure.

I'm also quite fascinated by aperiodic tilings, and I'd like to make a 2D language work on one of those. I've had this idea for a long time, but I wanted to get Wumpus done first. With that out of the way, I might actually tackle this sooner than later.

Knot theory is also very interesting, and it might be fun to design a language around it where the source code is an ASCII representation of one or several knots. Looking at the esolangs wiki, I don't seem to be the first person to come up with this idea, but so far no one seems to have actually designed such a language (I'd have to learn a lot about knot theory before I do though).

There are other ideas I'd like to explore for 2D languages as well, without even going crazy on the topology. For example, I'd like to see what happens when the instruction pointer of a 2D language covers more than one grid cell at a time. Or a language based on the mechanics of match-3-type puzzle games. Or a declarative 2D language (there's a severe shortage of declarative esolangs from what I've seen).

And then there's a whole bunch of ideas that aren't even 2D at all, like a language based on juggling (particularly the Siteswap notation used for juggling patterns). The backlog is quite long, and I seem to be better at growing it than shortening it.
