# catch-links

intercept local link clicks on a page

This is useful for doing client-side pushState UIs.

# example

Given some html:

``` html
<html>
  <body>
    <div>
      <a href="/a">aaa</a>
    </div>

    <div>
      <a href="/b">bbb</a>
    </div>

    <div>
      <a href="cc">cc</a>
    </div>
    
    <div>
      <a href="http://npmjs.org">npmjs</a>
    </div>
    
    <script src="bundle.js"></script>
  </body>
</html>
```

We'll intercept the relative links `<host>/a` and `<host>/b`, printing them.
The external link to npmjs.org will go through as usual.

``` js
var getLocalLink = require('catch-links');

window.addEventListener('click', function (e) {
  const anchor = getLocalLink(e);

  if (anchor) {
    e.preventDefault();
    console.log(anchor.href);
  }
});
```

# methods

``` js
var getLocalLink = require('catch-links')
```

## getLocalLink(event)

Returns the anchor element if the anchor element is clicked and has an in-server url.

# install

With [npm](https://npmjs.org) do:

```
npm install catch-links
```

Use [browserify](http://browserify.org) to bundle this library into your
project.

# license

MIT
