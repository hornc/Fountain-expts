# Fountain-expts
[Fountain](https://github.com/catseye/Fountain) CSL grammar experiments.


This was probably the wrong part of the [Fountain design document](https://github.com/catseye/Fountain/blob/master/doc/Design-of-Fountain.md)
to be inspired by:

>We can thread an explicit pseudo-random number generator through a Fountain grammar currently, by passing a parameter up and down through the productions, calling a certain production with this parameter to advance the pseudorandom generation state, and selecting on this state in every relevant alternation operation.
>
>However, this is tedious.

but [prng.fountain](prng.fountain) is my attempt at implementing a Xorshift PRNG inspired by [this Z80 implementation](http://www.retroprogramming.com/2017/07/xorshift-pseudorandom-numbers-in-z80.html).

    fountain.exe generate prng.fountain seed=34

```
Seed   : Coin toss
0x3B2A : Heads
0xD37D : Tails
0xA6CB : Tails
0xE92A : Tails
0x6814 : Heads
0x4725 : Heads
0x1ACF : Heads
0x0C71 : Heads
0xDFEB : Tails
0x547E : Heads
0x204B : Heads
0xCCC9 : Tails
0xB51D : Tails
0xBB80 : Tails
0xC6BD : Tails
0xE971 : Tails
0x88D9 : Tails
...
```

[throwing-prng.fountain](throwing-prng.fountain) uses the PRNG to generate a ball throwing scenario where characters may drop the ball "randomly" given a start seed. The threshold is set within the production constraints with `<. thres = nnnnn .>`.

    fountain.exe generate throwing-prng.fountain seed=34

```
Anise has the ball.
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
    Oh no! Blaschko dropped the ball!
Blaschko fetches the ball and throws it back to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
    Oh no! Blaschko dropped the ball!
Blaschko fetches the ball and throws it back to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
    Oh no! Blaschko dropped the ball!
Blaschko fetches the ball and throws it back to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
    Oh no! Blaschko dropped the ball!
Blaschko fetches the ball and throws it back to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
Blaschko throws the ball to Anise. 
Anise throws the ball to Blaschko. 
```

Tested using Fountain 0.4. These examples may very well break in future. I haven't really thought through all the implications of this, but _parsing_ this output to verify the original seeds will be pretty neat, which seems like it is at least a theoretical possibility from Fountain's design. It's highly likely that I am abusing Fountain to use it more like a programming language than intended...

