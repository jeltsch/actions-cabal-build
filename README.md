GitHub action for building Cabal packages
=========================================

This action builds a [Haskell][haskell] [Cabal][cabal] package with all
compilers listed in the `tested-with` property of the package
description.

[haskell]:
    https://www.haskell.org/
    "Haskell"
[cabal]:
    https://www.haskell.org/cabal/
    "Cabal"


Usage
-----

This action has neither inputs nor outputs. It just expects the Cabal
package to build in `$GITHUB_WORKSPACE`.

You need to have [GHCup][ghcup] installed. GitHub’s `ubuntu-latest`
runner contains it, but you might have to install it yourself when using
other runners or a container.

[ghcup]:
    https://www.haskell.org/ghcup/
    "GHCup"


Limitations
-----------

  * [GHC][ghc] is the only supported compiler.

  * The `tested-with` property description must be a single line that is
    matched by the following extended regular expression:

        ^tested-with: +GHC == { [^,]+(, [^,]+)* }$

    The substrings matched by the `[^,]+` subexpressions must be the
    versions of GHC with which to build the package.

    If the `tested-with` property description does not follow these
    requirements or there is no `tested-with` property description, the
    behavior is unspecified.


[ghc]:
    https://www.haskell.org/ghc/
    "The Glasgow Haskell Compiler"
