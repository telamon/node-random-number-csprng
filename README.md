# pure-random-number

> Hostile fork-over in progress, come back later :-)

A module for generating cryptographically secure pseudo-random numbers.

- backed by CSPRNG
- no dependencies
- no transpilation
- minimalistic repository footprint
- [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
- browser support via (Webpack/Rollup/Browserify)


This module is based on code [originally written](https://gist.github.com/sarciszewski/88a7ed143204d17c3e42) by [Scott Arciszewski](https://github.com/sarciszewski), released under the WTFPL / CC0 / ZAP.

## Usage

```js
const generate = require('pure-random-number')

generate(10, 30)
  .then(number => console.log.bind('Your number is:', number)
  .catch(err => console.error(err))
```

## API

### randomNumber(minimum, maximum, callback = null)

Returns a Promise that resolves to a random number within the specified range.

Note that the range is __inclusive__, and both numbers __must be integer values__. It is not possible to securely generate a random value for floating point numbers, so if you are working with fractional numbers (eg. `1.24`), you will have to decide on a fixed 'precision' and turn them into integer values (eg. `124`).

* __minimum__: The lowest possible value in the range.
* __maximum__: The highest possible value in the range. Inclusive.

Optionally also accepts a nodeback as `cb`, but seriously, you should be using [Promises](https://gist.github.com/joepie91/791640557e3e5fd80861).

### randomNumber.RandomGenerationError

Any errors that occur during the random number generation process will be of this type. The error object will also have a `code` property, set to the string `"RandomGenerationError"`.

The error message will provide more information, but this kind of error will generally mean that the arguments you've specified are somehow invalid.

## Changelog
* __2.0.0__ (May 3, 2020): Purified repository
* __1.0.2__ (March 8, 2016): __*Security release!*__ Patched handling of large numbers; input values are now checked for `MIN_SAFE_INTEGER` and `MAX_SAFE_INTEGER`, and the correct bitwise operator is used (`>>>` rather than `>>`).
* __1.0.1__ (March 8, 2016): Unimportant file cleanup.
* __1.0.0__ (March 8, 2016): Initial release.

## Contributing

Be aware that by making a pull request, you agree to release your modifications under the license stated below.

## License

Parent license(s) permit change of terms for derivative works.
Thus I now proclaim the license for this repository to be limited to
`GNU AGPL version 3`

(AGPL prevents Bigcorp from doing what I just did)


#### Parent licenses:

~~[WTFPL](http://www.wtfpl.net/txt/copying/) or [CC0](https://creativecommons.org/publicdomain/zero/1.0/), whichever you prefer. A donation and/or attribution are appreciated, but not required.~~

