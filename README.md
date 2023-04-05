# The physics module

Current semantic version: `0.6`. [Demo](physics-manual.pdf).

This [Typst](https://typst.app) package provides handy typesetting utilities for
physics, including:
* Braces,
* Vectors and vector fields,
* Matrices,
* Dirac braket notations,
* Common math functions,
* Differentials and derivatives, including partial derivatives of mixed orders,
* Tensor abstract index notations, isotopes.

:warning: [Typst](https://typst.app) is in beta and evolving, and this package
evolves with it. As a result, no backward compatibility is guaranteed yet. Also,
the package itself is under development and fine-tuning.

## Using phyiscs in your Typst document

* To use the `physics` package, simply insert `#import "physics.typ": *` at the
beginning of your document.
* To reduce the possibility of name collisions, you may want to import the
package under name scope `physics`:
  ```
  #import "physics.typ"

  $op("curl")(op("grad") f) = physics.curl (physics.grad f)$
  ```
* You may also import names specifically:
  ```
  #import "physics.typ": curl, grad

  $op("curl")(op("grad") f) = curl (grad f)$
  ```

## Demo & manual

See the manual [physics-manual.pdf](physics-manual.pdf) for a demo, a PDF file
generated directly with the [Typst](https://typst.app) CLI.

CLI Version:

```sh
$ typst --version # From release 28-03-32 (pre-release)
typst 0.1.0 (b3faef4b)
```

To regenerate the manual, use command

```sh
typst watch physics-manual.typ
```

## Contribution

* Bug fixes are welcome!

* New features: welcome as well. If it is small, feel free to create a pull
request. If it is large, the best first step is creating an issue and let us
explore the design together. Some features might warrant a package on its own.

* Testing: currently testing is done by closely inspecting the generated
[physics-manual.pdf](physics-manual.pdf). This does not scale well. I plan to add programmatic
testing by comparing rendered pictures with golden images.

These items seem to need Typst's language support:

1. Isotopes:
  * A better way to align the subscripts and superscripts to the right.
  Currently it uses an embedded table to achieve that, but it feels rather
  heavy weight.
2. Dirac braket notations:
  * Reduce the horizontal space of the inner divider.
  * Let the inner divider's height match the height given by `lr()` to the left
  and right angle brackets.

## License

* Code: the [MIT License](LICENSE.txt).
* Docs: the [Creative Commons BY-ND 4.0 license](https://creativecommons.org/licenses/by-nd/4.0/).