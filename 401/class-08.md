# Reading Notes 08 -- OO Design

Wikipedia Sources:
[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
[Rule of 3](https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming))
[YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it)
[MVP](https://en.wikipedia.org/wiki/Minimum_viable_product)


**Don’t Repeat Yourself** is a software development principle originating from *The Pragmatic Programmer* by Andy Hunt and Dave Thomas (not that one).
The idea is in the name, don't repeat yourself, an aim to reduce redundant and repetitious code. The method to reduce repetitious code is through following data normalization by using a canonical form. If DRY successfully used it can make it easier to modify a single part of a program -- it shouldn't effect other areas that are not logically connected.

**The Rule of Three** is a design rule that aims at reducing duplicate code as well. The design allows for two duplicate bits of code, but if there are three, then you've got to re-factor. After using two similar code blocks adding a third would add too much cost to maintenance.

**You Aren’t Gonna Need It** comes from "extreme programming" which warns not to add functionality that is unnecessary. YAGNI comes from the practice in extreme programming to "do the simplest thing that could possibly work".

**Minimum Viable Product** is a product that fulfills the minimum requirements for a usable product. Focusing on getting something, even something small, in a usable state will allow for user feedback. Shorter update cycles can reduce unnecessary work.

