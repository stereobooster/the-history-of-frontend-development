# The History of Frontend Development

Current state of the frontend developement is controversial. How we got here? This repository is small research to understand how we get in current state.

What do I mean by "controversial"? See those links:

- [The Great Divide](https://css-tricks.com/the-great-divide/)
- [Not An Imposter: Fighting Front-End Fatigue](https://www.smashingmagazine.com/2016/11/not-an-imposter-fighting-front-end-fatigue/)
- [Web developer roadmap](https://github.com/kamranahmedse/developer-roadmap)
- [Javascript Fatigue](https://medium.com/@ericclemmons/javascript-fatigue-48d4011b6fc4)
- [NPM & left-pad: Have We Forgotten How To Program?](https://www.davidhaney.io/npm-left-pad-have-we-forgotten-how-to-program/)
- [core-js issue](https://github.com/zloirock/core-js/issues/767)

## Concept

Idea is to show how some historical events got us to current state. What was motviation behind some libraries, technologies and practices of frontend development.

How it's gonna be done? It will be some kind of a mix between mindmap and a [timeline](http://rigaux.org/language-study/diagram.html). It will be implemented as dot file which will be converted to SVG with the help of [graphviz](https://graphviz.org/).

We can think of it as a history of idead evolution - the same way as philosophy works. One philospher proposes idea (or question, or describes problem) second philosopher (maybe some centuries later) writes another idea as response to the first one, then third one propses other solution to the problem etc.

## Ideas

### JavaScript is confusing

Problem: JS is confusing, probably because initial version was implemented in 10 days. Initial implementation contained bug (this is why there are both `null` and `undefined`), which were not before JS got standardized. JS meant to be as minimal glue language, so instead of providing developer tools, they went for never-fail approach (that is why we have type coercion rules and [Automatic Semicolon Insertion](http://www.ecma-international.org/ecma-262/7.0/index.html#sec-rules-of-automatic-semicolon-insertion)).

Possible solutions:

- There are good and bad parts. Use good parts and it will be easier.
  - JSlint was created in 2001 by Douglas Crockford to solve this problem, for example, it would recomend to use `===` instead of `==` to avoid coercion bugs
  - JavaScript: The Good Parts, by Douglas Crockford, 2008
  - [Type coercion rules are confusing](https://www.destroyallsoftware.com/talks/wat)`
    - use `===` instead of `==`
    - use type guards (dynamic type checks)
    - use static type checker
- It misses standard library.
  - People created libraries with most common functions, for example Underscroe.js (2009), Moment.js (2011)
  - Create another language which compiles to JS, which would contain standard library, for example CoffeeScript (2009)
- It misses static checker
  - JSlint was first static checker. It could check that there are no syntax errors and that developer avoids "bad parts"
    - JSHint meant to be more configurable JSlint
      - ESLint is like JSHint, which supports ES6 syntax
        - **New problem**: ESLint rules from hell - rules about code style, which doesn't prevent any errors and can be very annoying for developers
  - TypeScript (2012) can do limited type check for JS files
- Prototypal inheritance is confusing
  - Avoid inheritance
  - Use pseudo-classes or mixins
  - ES6 classes (2015)
- `this` keyword is confusing
  - Write functional-style code. Use closures instead of classes
    - For example, React functional components and hooks
  - ES6 arrow-functions (2015) partially solve the problem
- [Arguments about formatting](https://github.com/twbs/bootstrap/issues/3057)
  - ESLint to check formatting - I don't believe this is actually solved the problem
    - Prettier (2017) - instead of checking formatting it can fix formatting automatically
- Lack of modules (before ES6)
  - jQuery-style plugins (~2006) - load JS files as scripts in html and use one namespace
  - Common JS modules. Node.js was introduce in 2009 and it could not use script tags in html (because there is no html). When people realised they can use actual modules in JS (in backend) they wanted to use them in frontend as well
    - **New problem**: CommonJS modules are not suitable for frontend, because they create "waterfall" download
      - Require.js (2010). [Asynchronous Module Definition](https://requirejs.org/docs/whyamd.html) (2011) was propsed to speed up download of modules, so they can be downloaded independently and evaluated when everything is ready
      - Webpack (2012) proposed to build dependency graph upfront and produce single JS file for output
        - CommonJS modules are hard to analyze statically and module resolution algorithm is hard and not suitable for web
        - AMD does not have concept of pathes, rather identifiers, so it's not suitable for the backend
        - [Universal Module Definition](https://github.com/umdjs/umd) (2014?)
        - **ES6 modules** (2014-2015) was proposed to work in both environments and be statically analyzable. Webpack added support for ES6 modules with the help of Babel (2014)
          - **New problem**: Node.js doesn't support ES6 modules
            - [Experimental support added in Node.js v14](https://nodejs.org/api/esm.html#) (2020)
        - **New problem**: because Webpack wants to be swiss-knife of frontend developemnt, it tries to solve very complex problem, consequently it is very hard to configure
          - Projects, like create-react-app were created to hide webpack configuration complexity
  - It forces library authors to concatenate files and distribute libraries as one big ES5 file
    - Libraries distributed as single ES5 file and lack of standard library leads to frontend bloat, for example Underscore is 28kb, Moment.sj is 288.4kB, ReactDOM 114.6kB. See https://bundlephobia.com.
      - Solution: ES6 Modules and `module` field in `package.json`
        - **New problem**: some libraries expected to work in a browser and Node.js and Node.js didn't support ES6 modules till 2020
        - **New problem**: it can contain imports from npm, which won't work in the browser - it means if you distribute library as ES6 you assume build tool as well (Webpack and/or Babel).
        - **New problem**: not all brwoser supported ES6 at the moment, so it means if you distribute library as ES6 you assume build tool as well (Webpack and/or Babel).
          - Solution: Distribute npm package containing both ES5 (UMD) and ES6 files
- Lack of package manager (before npm). In old days to install package you would download zip-archive, copy contents to public folder and links to html file. Update were manual and tedious
  - [Bower](https://bower.io/) was introduced to simplify installation of frontend packages
    - now deprecated ☠️
  - npm (2010) initially meant to be backend package manager, but as popularity of tools written in JS grew (and it means that most developers would use npm anyway), people start to put frontend packages in npm
    - **New problem**: npm is slow, `node_modules` folder is huge, because they decide not to dedupe packages and don't check version conflicts, instead you can have many copies of the same library
      - Yarn tried to solve this problem (there are alternatives, like pnpm, etc)
        - npm starting from version 5 tried as well
        - Yarn 2 seems to be a different product
    - **New problem**: Ease of installation and lack of standard library leads to overuse of dependencies. As the result we get problems, like [left-pad](https://www.davidhaney.io/npm-left-pad-have-we-forgotten-how-to-program/)
- Browser APIs are inconcistent
  - TODO
- Mutable built-in data structures
  - TODO
- Compile other language to JS
  - TODO
- Compile other language to WA
  - TODO

## Sources

- [How We Got Here - The History of Web Development - Richard Campbell](https://www.youtube.com/watch?v=41mnNyMxPOA)
- [A short history of the Web](https://home.cern/science/computing/birth-web/short-history-web)
- [The Evolution of the Web](http://www.evolutionoftheweb.com/)
- [Crockford on JavaScript](https://www.youtube.com/watch?v=JxAXlJEmNMg&list=PL7664379246A246CB)
