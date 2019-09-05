Why React?
==========

- "Don't access the DOM, I'll do it for you"
  - chainging the DOM is computationally expensive operation
  - declarative approach
    - instead of saying exactly what to do we just give React a blueprint (state) of *components* written with *JSX* that sometimes have properties => VirtualDOM => update DOM
- build websites like lego blocks
  - components
  - simply JS functions/classes
- unidirectional data flow
  - the *state* has to change in order to change the DOM
  - React *reacts* to that change
- "I'm just the UI, the rest is up to you"
  - React doesn't make assumptions on what technologies you use

How to be a great React developer?
==================================
1. Decide on components
2. Decide the state and where it lives
3. What changes when state changes
