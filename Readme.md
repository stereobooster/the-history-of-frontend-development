# The History of Frontend Development

Current state of the frontend developement is controversial. How we got here? This repository is small research to understand how we get in current state.

What do I mean by "controversial"? See those links:

- [The Great Divide](https://css-tricks.com/the-great-divide/)
- [Not An Imposter: Fighting Front-End Fatigue](https://www.smashingmagazine.com/2016/11/not-an-imposter-fighting-front-end-fatigue/)
- [Web developer roadmap](https://github.com/kamranahmedse/developer-roadmap)
- [Javascript Fatigue](https://medium.com/@ericclemmons/javascript-fatigue-48d4011b6fc4)
- [NPM & left-pad: Have We Forgotten How To Program?](https://www.davidhaney.io/npm-left-pad-have-we-forgotten-how-to-program/)
- [core-js issue](https://github.com/zloirock/core-js/issues/767)

## Idea

Idea is to show how some historical events got us to current state. What was motviation behind some libraries, technologies and practices of frontend development.

How it's gonna be done? It will be some kinf of a mix between mindmap and a [timeline](http://rigaux.org/language-study/diagram.html). Probably it will be implemented as dot file which will be converted to SVG with the help of [graphviz](https://graphviz.org/).

**For example**, at some point of time we get the problem formulated as "JavaScript is confusing" (one node in mindmap), then we got solutions to this problem (each is separate node with date, so we can put them on timeline):

- There are good and bad parts. It is better if you use only good parts. (JavaScript: The Good Parts by Douglas Crockford, 2008)
  - JSLint -> JSHint -> ESLint
- It is hard, because it misses standard library. Let's create library of reusable utilities
  - Underscore.js (October 28, 2009)
  - Momen.JS
- It is hard, because browser APIs are bugy and inconsistent. Let's abstract those APIs
  - jQuery (August 26, 2006)
- It is hard to maintain dependecies
  - let's use package manager to distribute dependenies
    - npm (12 January 2010) -> 🏆
      - but you need to publish concatenated libraries, which are not tree shakeable
    - bower -> ☠️
    - CDN (jQuery CDN etc.)
  - let's use loader and modules for js
    - require.js
    - [AMD](https://github.com/amdjs/amdjs-api/blob/master/AMD.md)
  - asynchronous module load approach creates "waterfall download issue"
    - let's use bundler to concatenate all resources
      - webpack
    - npm's `require` is not a part of standard
      - ES6 introduces new `import` instruction
- JS has bad parts, let's make a language which compiles to JS
  - With a different semantics
    - CoffeeScript (13 December 2009) -> ☠️
  - With the same semantics
    - TypeScript (1 October 2012)
- JS has bad parts, let's make a language which compiles to WA (March 2017)
- Let's make new version of specification which contains improvemnts
  - ES6 (2015)
- etc.

## Sources

- [How We Got Here - The History of Web Development - Richard Campbell](https://www.youtube.com/watch?v=41mnNyMxPOA)
- [A short history of the Web](https://home.cern/science/computing/birth-web/short-history-web)
- [The Evolution of the Web](http://www.evolutionoftheweb.com/)
- [Crockford on JavaScript](https://www.youtube.com/watch?v=JxAXlJEmNMg&list=PL7664379246A246CB)
