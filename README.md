# Silvermine UnderTemplate

[![Build Status](https://travis-ci.org/silvermine/undertemplate.svg?branch=master)](https://travis-ci.org/silvermine/undertemplate)
[![Coverage Status](https://coveralls.io/repos/github/silvermine/undertemplate/badge.svg?branch=master)](https://coveralls.io/github/silvermine/undertemplate?branch=master)
[![Dependency Status](https://david-dm.org/silvermine/undertemplate.svg)](https://david-dm.org/silvermine/undertemplate)
[![Dev Dependency Status](https://david-dm.org/silvermine/undertemplate/dev-status.svg)](https://david-dm.org/silvermine/undertemplate#info=devDependencies&view=table)


## What is it?

A simple replacement for `_.template` from either [Underscore][utmpl] or [Lodash][ltmpl]
that removes the features that make those libraries incompatible with Content Security
Policy (CSP). Specifically, this implementation supports only interpolation (escaped and
unescaped) and does not support JS evaluation.


## How do I use it?

Just like you would have used `_.template`:

```
var makeTemplate = require('@silvermine/undertemplate'),
    template = makeTemplate('Hello <%= name %>');

console.log(template({ name: 'John Smith' }));
```

Of course, we only support:

   * `<%= … %>`: interpolate a value
   * `<%- … %>`: interpolate and HTML escape a value

The following are **NOT** supported:

   * `<% … %>`: JS evaluation
   * `<% print('Hello ' + epithet); %>`: JS evaluation with the `print` function

NOTE: Since string interpolation is done differently from Underscore/Lodash the error
messages thrown when a variable is not available (et cetera) will now differ from what you
had before. If you were catching errors thrown when calling the template function and
relying on the messages in those errors, your code will need to be updated.


## How do I contribute?

We genuinely appreciate external contributions. See [our extensive
documentation][contributing] on how to contribute.


## License

This software is released under the MIT license. See [the license file](LICENSE) for more
details.

[contributing]: https://github.com/silvermine/silvermine-info#contributing
[utmpl]: http://underscorejs.org/#template
[ltmpl]: https://lodash.com/docs/#template
