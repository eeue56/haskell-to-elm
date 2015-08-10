# haskell-to-elm


## Function application

Instead of using the dollar symbol `$` elm uses `<|` and `|>`  for [application in different directions](http://package.elm-lang.org/packages/elm-lang/core/2.1.0/Basics#|>). 

Example:

```
    collage (round board.width) (round board.height) $ map (genRect board) board.pieces
```
becomes
```
    collage (round board.width) (round board.height) <| List.map (genRect board) board.pieces
```

## Function composition

Instead of using the `(.)` symbol Elm uses `<<` and `>>` for [composition in different directions](http://package.elm-lang.org/packages/elm-lang/core/2.1.0/Basics#>>)

Example:
```
    isEvenSquareRoot = sqrt . isEven
```
becomes
```
    isEvenSquareRoot = sqrt << isEven
    -- or
    isEvenSquareRoot = isEven >> sqrt
```

## Zip

Elm has [no built-in zip](http://elm-lang.org/examples/zip) method - instead it provides a [map2](http://package.elm-lang.org/packages/elm-lang/core/2.1.0/List#map2) function that can be used with the tuple creator `(,)` to make a list of size 2 tuples from two lists.

Example:

```
    zip xs ys
```
becomes
```
    map2 (,) xs ys
```

## List comprenhensions

There are [no list comprehensions](https://github.com/elm-lang/elm-compiler/issues/147#issuecomment-17439271) in Elm.

## Show

Elm renamed [show](http://zvon.org/other/haskell/Outputprelude/show_f.html) to [toString](http://package.elm-lang.org/packages/elm-lang/core/2.1.0/Basics#toString). Confusingly, there is also a [method called show](http://package.elm-lang.org/packages/elm-lang/core/2.1.0/Graphics-Element#show) in Elm - this generates a HTML element containing a textual representation of the data.

Example:
```
    show [1, 2, 3]
```
becomes
```
    toString [1, 2, 3]
```

## Mod

Mod in Elm uses the [`(%`) symbol](http://package.elm-lang.org/packages/elm-lang/core/2.1.0/Basics#%).

Example:
```
    isEven x = x `mod` 2 == 0
```
becomes
```
    isEven x = x % 2 == 0
```

## Module syntax

### Importing names

Elm uses the [`exposing` keyword](http://elm-lang.org/docs/syntax#modules) to import names into the current namespace.

Example:
```
    import List (map, foldl)
```
becomes
```
    import List exposing (map, foldl)
```

### Defining exportable names

TODO: find documentation on elm site for this
Following the module declaration, you must have *no* identnation level.

Example:
```
    module Coords (pos) where
        pos x y = (x, y)
```
becomes
```
    module Coords (pos) where
    pos x y = (x, y)
```
