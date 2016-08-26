`z3-rkt`: Racket bindings for Z3
================================

This package provides an implementation of Z3 in Typed Racket.
Although I develop this package specifically for use in my symbolic execution,
it should be usable for general-purpose Racket SMT integration.
I originally forked from [https://github.com/sid0/z3.rkt](https://github.com/sid0/z3.rkt), then:
* gave Typed Racket bindings; ported all but the ffi layer to Typed Racket
* generalized `declare-datatypes` to allow complex and recursive datatypes
* migrated from the deprecated API (which was very unresponsive to timeouts and had strange memory behavior) to the new Solver API
* ditched all deprecated functions
* ditched all hacky sort-instance functions (will generalize it later)

Old exapmles that used sort instances are not working for now.

I only use Typed Racket to prevent simple mistakes in implementing the API.
The embedded SMT language itself is untyped because expressions and commands
can be dynamically generated.
All SMT expressions have type `Z3:Ast`.


Installing
----------

`z3-rkt` has been tested with Z3 4.4.1, which you can download for your platform from [the
Microsoft Research
site](http://research.microsoft.com/en-us/um/redmond/projects/z3/download.html).
We work on Windows, Mac and Linux. You need to copy or create a symlink to `z3.dll`,
`libz3.so` or `libz3.dylib` in the `ffi/` directory.


Structure
----------

* [`ffi/`](https://github.com/philnguyen/z3.rkt/tree/master/ffi) defines low-level Z3 API
* [`smt/`](https://github.com/philnguyen/z3.rkt/tree/master/smt) defines the high-level Z3 API, close to the SMT2 language.
  This is the reccommended way to interact with Z3.
  

License
-------

Licensed under the Simplified BSD License. See the LICENSE file for more
details.

Please note that this license does not apply to Z3, only to these bindings.
