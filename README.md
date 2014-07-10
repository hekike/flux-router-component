# flux-router-component [![Build Status](https://travis-ci.org/yahoo/flux-router-component.svg?branch=master)](https://travis-ci.org/yahoo/flux-router-component) [![Dependency Status](https://david-dm.org/yahoo/flux-router-component.svg)](https://david-dm.org/yahoo/flux-router-component)
This package provides navigational React components and router React mixin for applications built with [Flux](http://facebook.github.io/react/docs/flux-overview.html) architecture.  Please check out [examples](https://github.com/yahoo/flux-router-component/tree/master/examples) of how to use these components.

## NavLink
`NavLink` is the a React component for navigational links.  When the link is clicked, NavLink will dispatch `NAVIGATE` action to flux dispatcher.  The dispatcher can then dispatch the action to the stores that can handle it.

### Example Usage
```js
var NavLink = require('flux-router-component').NavLink;

var Nav = React.createClass({
    render: function () {
        var pages,
            links,
            dispatcher = this.props.dispatcher;  // this is the Flux dispatcher object
        pages = [
            {
                name: 'home',
                url: '/home',
                text: 'Home'
            },
            {
                name: 'about',
                url: '/about',
                text: 'About Us'
            }
        ];
        links = pages.map(function (page) {
            return (
                <li className="navItem">
                    <NavLink href={page.url} dispatcher={dispatcher}>
                        {page.text}
                    </NavLink>
                </li>
            );
        });
        return (
            <ul className="nav">
                {links}
            </ul>
        );

    }
});
```

## RouterMixin
`RouterMixin` is a React mixin to be used by appication's top level React component to:

* manage browser history when route changes, and
* dispatch `NAVIGATE` action via flux dispatcher on window `popstate` events


### Example Usage
```js
var RouterMixin = require('flux-router-component').RouterMixin;

var Application = React.createClass({
    mixins: [RouterMixin],
    ...
});
```


## License
This software is free to use under the Yahoo! Inc. BSD license.
See the [LICENSE file][] for license text and copyright information.

[LICENSE file]: https://github.com/yahoo/flux-router-component/blob/master/LICENSE.md

Third-pary open source code used are listed in our [package.json file]( https://github.com/yahoo/flux-router-component/blob/master/package.json).
