<!--

@license Apache-2.0

Copyright (c) 2021 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# rtrimN

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Trim `n` characters from the end of a string.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/string-right-trim-n
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).
-   To use as a general utility for the command line, install the corresponding [CLI package][cli-section] globally.

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var rtrimN = require( '@stdlib/string-right-trim-n' );
```

#### rtrimN( str, n\[, chars] )

Trims `n` characters from the end of a string.

```javascript
var str = '  foo  ';
var out = rtrimN( str, str.length );
// returns '  foo'

out = rtrimN( str, 1 );
// returns '  foo '
```

By default, the function trims whitespace characters. To trim a different set of characters instead, provide a string or an array of characters to trim:

```javascript
var str = '🐶🐶🐶 Animals 🐶🐶🐶';
var out = rtrimN( str, str.length, [ '🐶', ' ' ] );
// returns '🐶🐶🐶 Animals'

out = rtrimN( str, str.length, '🐶 ' );
// returns '🐶🐶🐶 Animals'
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var rtrimN = require( '@stdlib/string-right-trim-n' );

var out = rtrimN( '   Whitespace   ', 3 );
// returns '   Whitespace'

out = rtrimN( '\t\t\tTabs\t\t\t', 2 );
// returns '\t\t\tTabs\t'

out = rtrimN( '~~~CUSTOM~~~', 3, '~' );
// returns '~~~CUSTOM'
```

</section>

<!-- /.examples -->

<!-- Section for describing a command-line interface. -->

* * *

<section class="cli">

## CLI

<section class="installation">

## Installation

To use as a general utility, install the CLI package globally

```bash
npm install -g @stdlib/string-right-trim-n-cli
```

</section>
<!-- CLI usage documentation. -->


<section class="usage">

### Usage

```text
Usage: rtrimn [options] --n=<number>

Options:

  -h,    --help                Print this message.
  -V,    --version             Print the package version.
         --n number            Number of characters to trim.
         --chars str           Characters to trim. Default: whitespace.
         --split sep           Delimiter for stdin data. Default: '/\\r?\\n/'.
```

</section>

<!-- /.usage -->

<!-- CLI usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

### Notes

-   If the split separator is a [regular expression][mdn-regexp], ensure that the `split` option is either properly escaped or enclosed in quotes.

    ```bash
    # Not escaped...
    $ echo -n $'   foo   \n   bar   ' | rtrimn --n=3 --split /\r?\n/

    # Escaped...
    $ echo -n $'   foo   \n   bar   ' | rtrimn --n=3 --split /\\r?\\n/
    ```

-   The implementation ignores trailing delimiters.

</section>

<!-- /.notes -->

<!-- CLI usage examples. -->

<section class="examples">

### Examples

```bash
$ rtrimn '   Whitespace   ' --n=3
   Whitespace
```

To use as a [standard stream][standard-streams],

```bash
$ echo -n '~beep~boop~~~' | rtrimn --n=2 --chars '~'
~beep~boop~
```

By default, when used as a [standard stream][standard-streams], the implementation assumes newline-delimited data. To specify an alternative delimiter, set the `split` option.

```bash
$ echo -n '~~~foo~~~\t~~~bar~~~\t~~~baz~~~' | rtrimn --split '\t' --chars '~' --n=3
~~~foo
~~~bar
~~~baz
```

</section>

<!-- /.examples -->

</section>

<!-- /.cli -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/string-left-trim-n`][@stdlib/string/left-trim-n]</span><span class="delimiter">: </span><span class="description">trim `n` characters from the beginning of a string.</span>
-   <span class="package-name">[`@stdlib/string-trim`][@stdlib/string/trim]</span><span class="delimiter">: </span><span class="description">trim whitespace characters from the beginning and end of a string.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/string-right-trim-n.svg
[npm-url]: https://npmjs.org/package/@stdlib/string-right-trim-n

[test-image]: https://github.com/stdlib-js/string-right-trim-n/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/string-right-trim-n/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/string-right-trim-n/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/string-right-trim-n?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/string-right-trim-n.svg
[dependencies-url]: https://david-dm.org/stdlib-js/string-right-trim-n/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[cli-section]: https://github.com/stdlib-js/string-right-trim-n#cli
[cli-url]: https://github.com/stdlib-js/string-right-trim-n/tree/cli
[@stdlib/string-right-trim-n]: https://github.com/stdlib-js/string-right-trim-n/tree/main

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/string-right-trim-n/tree/deno
[deno-readme]: https://github.com/stdlib-js/string-right-trim-n/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/string-right-trim-n/tree/umd
[umd-readme]: https://github.com/stdlib-js/string-right-trim-n/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/string-right-trim-n/tree/esm
[esm-readme]: https://github.com/stdlib-js/string-right-trim-n/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/string-right-trim-n/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/string-right-trim-n/main/LICENSE

[mdn-regexp]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions

[standard-streams]: https://en.wikipedia.org/wiki/Standard_streams

<!-- <related-links> -->

[@stdlib/string/left-trim-n]: https://github.com/stdlib-js/string-left-trim-n

[@stdlib/string/trim]: https://github.com/stdlib-js/string-trim

<!-- </related-links> -->

</section>

<!-- /.links -->
