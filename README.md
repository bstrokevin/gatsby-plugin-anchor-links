![Banner](https://i.imgur.com/H572MIB.jpg "Banner")

# Gatsby Smooth Scroll Anchor Links

## Why? What does this do?

Many sites use a mixed navigation format in which some links route to other pages, while some anchor a smooth scroll to sections within a specific page -- but both types still need to function well regardless of what page the user is currently on. This can be a little cumbersome to accomplish elegantly. This plugin aims to provide that. You can read a little more about the evolution of the logic in the plugin on my [web development blog](https://chaseohlson.com/gatsby-link-anchor-navigation).

This plugin adds a check `onRouteUpdate` - which looks for hashes in the current pathname. If so, it uses a scrolling library to scroll to the provided hash. In addition, it provides component(s) for use in your Gatsby code to which you can provide both hashed & non-hashed `to` paths.

## Installation

Using Yarn

- `yarn add gatsby-plugin-anchor-links`

Using NPM

- `npm i gatsby-plugin-anchor-links`

### gatsby-config.js

This plugin can be used with or without a configuration object:

```javascript
module.exports = {
  plugins: [`gatsby-plugin-anchor-links`]
};
```

```javascript
module.exports = {
  plugins: [
    {
      resolve: "gatsby-plugin-anchor-links",
      options: {
        offset: -100
      }
    }
  ]
};
```

### Configuration Options

| Option |          Description | Default |   Type |
| ------ | -------------------: | ------: | -----: |
| offset | # of pixels from top |       0 | number |

## Component usage

You can provide anchor or non-anchor links to this component for ease of use. If you use it as an anchor component, be sure to include both a base path and hash in the `to` string.

```javascript
import { AnchorLink } from "gatsby-plugin-anchor-links";

export default () => (
  <AnchorLink to="/about#team" title="Our team">
    <span>Check out our team!</span>
  </AnchorLink>
);
// => <a href="/about#team" title="Our team"><span>Check out our team!</span></a>

export default () => (
  <AnchorLink to="/about#team" title="Check out our team!" />
);
// => <a href="/about#team" title="Check out our team!">Check out our team!</a>

export default () => <AnchorLink to="/about" title="About us" />;
// => <a href="/about" title="About us">About us</a>
```

### AnchorLink props

| Option   |                             Description |       Type | Required |
| -------- | --------------------------------------: | ---------: | -------: |
| to       |    path with hash to your page & anchor |     string |     true |
| title    | accessible title & fallback anchor text |     string |    false |
| children |  react node to be wrapped by AnchorLink | react node |    false |

## Sites using Gatsby Anchor Links

- [chaseohlson.com](https://chaseohlson.com/) // [source](https://github.com/brohlson/chaseohlson)

## Credits

- Anchor logo by dData via [Noun Project](https://thenounproject.com/dDara)
