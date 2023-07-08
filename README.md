# Set-Theoretic and Polymorphic Type System Prototype and Appendix

## Appendix
This archive contains the [appendix to the paper Set Theoretic and Polymorphic Type System](popl-submission-appendix.pdf), which includes extensions,
auxiliary definitions and proofs.

## Testing the Web version
The web version of this prototype is already built and included in this
repository. It can be tested by serving the `docs` directory with an
HTTP server. This can easily be done, e.g. with a standard install of Python 3:
```
$ cd docs
$ python3 -m http.server
```
and pointing a web browser to http://localhost:8000.

The URL of an anonymized version hosted on github has been submitted as a comment for the PC Chair.

## Native version

The easiest way to build the native version is through [opam](https://opam.ocaml.org/), the OCaml Package Manager.
This prototype has been tested on OCaml 4.14.1, that can be installed by doing `opam switch create 4.14.1`.

### Installing CDuce

The main dependency is the CDuce library. It can be installed this way:

```
opam pin add cduce-types 'git+https://gitlab.math.univ-paris-diderot.fr/cduce/cduce#dev'
opam pin add cduce 'git+https://gitlab.math.univ-paris-diderot.fr/cduce/cduce#dev'
```

### Building the prototype

Once CDuce is installed, our prototype can be built using

```
git clone git@github.com:poly-dl/poly-dl.git
cd poly-dl/src
opam install ppx_inline_test ppx_expect ppx_deriving pomap
make
```

### Running the prototype

Once compiled, the prototype can be executed with `dune exec -- ./prototype.exe [file]`.
If no file is given, the file `test.ml` from the current path is used.

## Javascript version (web editor)

The `docs/` directory already contains pre-built version of the prototype. If you wish to rebuild it, you will need [npm](https://www.npmjs.com/) to install the JavaScript dependencies.
First, build the native version, then:

```
opam install yojson js_of_ocaml-ppx
make libjs
cd ../docs
npm ci
```

Then either serve the whole content of the `./docs/` directory through a Web server or open the file `./docs/index.html` directly from a browser (**warning** : the later will not allow you to load the examples nor benefit from web-workers due to security policies).
