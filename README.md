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
