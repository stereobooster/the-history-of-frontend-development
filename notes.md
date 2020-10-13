# Notes

Temproral notes - need to move them to `main.dot`

- From 1999 to 2010 DHTML Era
- From 2010 to present SPA Era
- From 2014 to present New ERA (HTML 5, polyfils, ES6 to 5 transpilation, asset graph - webpack, HTTP/2)
- https://en.wikipedia.org/wiki/Browser_wars, "dot com", Firefox, Chrome
- Svetle, web components, ReScript
- WebP, AVIF, QUIC, brotli
- http://jphpsf.github.io/setImmediate-shim-demo/, https://github.com/wilsonpage/fastdom, https://csstriggers.com/
- https://developer.yahoo.com/performance/rules.html (2007) -> YSlow -> Google PageSpeed -> Google Lighthouse
- High Performance Web Sites, by Steve Souders, 2007
- JavaScript: The Good Parts, by Douglas Crockford, 2008
- Inventing on Principle, by Bret Victor, 2012
- CSSMin -> CSSNano, HTMLMin, JSMin -> Closure -> Terser
- Death of IE6 (by DHH), Death of Flash (by Steve Jobs)
- CouchDB, https://logux.io/, GraphQL, Swagger, REST, poll strategy, WebSockets
- Layout: with tables, with divs (pseudo-grid), CSS flex, CSS grid

**Problem**: Asset loading speed is slow over HTTP 1.1
**Solution**: concatenate assets (JS, CSS, and even images with CSS sprites), minify, use never expiring cache (use unique names, so called cache busting), use other domain for assets, use CDN (but it was available only for big companies). Source: High Performance Web Sites, by Steve Souders, 2007.

As the result tools to support this task appeared: asset pipeline, grunt, gulp, webpack etc.

CDN at the moment was expensive and only available for big corporations. Alternative was to use shared CDN for JS libs, like jQuery CDN, jsdelivr etc.

**Updated solution**:

- loading of assets over HTTP2 is multistream, so no need for other domain. It is still recommended to concatenate files, but this is less an issue then before
- CDNs are cheap, for example CloudFlare and Netlify have free tiers
  - with CDN and HTTP/2 we can use always re-validate cache strategy

**Sub-problem**: because we minfiy and concatenate files it is hard to debug code.
**Solution**: generate sourcemaps
