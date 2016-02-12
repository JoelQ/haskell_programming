# Chapter Exercises

_As in previous chapters, you will gain more by working out the answer before
you check what GHCi tells you, but be sure to use your REPL to check your
answers to the following exercises. Also, you will need to have the `awesome`,
`alsoAwesome`, and `allAwesome` code from above in scope for this REPL session.
For convenience of reference, here are those values again:_

```hs
awesome = ["Papuchon", "curry", "Haskell"]
alsoAwesome = ["Quake", "The Simons"]
allAwesome = [awesome, alsoAwesome]
```

_`length` is a function that takes a list and returns a result that tells how
many items are in the list._

1. _Given the definition of `length` above, what would the type signature be?
   How many arguments, of what type does it take? What is the type of the result
   it evaluates to?_

   ```hs
   length :: [a] -> Int
   ```

2. _What are the results of the following expressions?_

   ```hs
   length [1, 2, 3, 4, 5]
   -- 5
   length [(1, 2), (2, 3), (3, 4)]
   -- 3
   length allAwesome
   -- 2
   length (concat allAwesome)
   -- 5
   ```

3. _Given what we know about numeric types and the type signature of length,
   look at these two expressions. One works and one returns an error. Determine
   which will return an error and why._

   ```
   Prelude> 6 / 3
   -- and
   Prelude> 6 / length [1, 2, 3]
   ```

   `length` returns an `Int`. `Int` doesn't implement `Fractional` and therefore
   can't be used with `/`.

4. _How can you fix the broken code from the preceding exercise using a
   different division function/operator?_

   ```hs
   6 `div` length [1, 2, 3] -- use integer division
   ```

5. _What is the type of the expression `2 + 3 == 5`? What would we expect as a
   result?_

   The expression has a type of `Bool`. The result is `True`.

6. _What is the type and expected result value of the following:_
   ```
   Prelude> let x = 5
   Prelude> x + 3 == 5
   ```

   The expression has a type of `Bool`. The result is `False`.

7. _Below are some bits of code. Which will work? Why or why not? If they will
   work, what value would these reduce to?_

   ```
   Prelude> length allAwesome == 2
   ```

   Works because both sides of `==` are of the same type. It evaluates to `True`

   ```
   Prelude> length [1, 'a', 3, 'b']
   ```

   Will not work because lists must be all of the same type.

   ```
   Prelude> length allAwesome + length awesome
   ```

   Will work because both calls to `length` return a number. It evaluates to `5`

   ```
   Prelude> (8 == 8) && ('b' < 'a')
   ```

   Will work because both sides of `&&` evaluate to a `Bool`. It evaluates to
   `False`

   ```
   Prelude> (8 == 8) && 9
   ```

   Will not work because `9` is not a `Bool` and isn't a valid argument to `&&`.

8. _Write a function that tells you whether or not a given String (or list) is a
   palindrome. Here you’ll want to use a function called ’reverse,’ a predefined
   function that does just what it sounds like_

   ```hs
   isPalindrome :: (Eq a) => [a] -> Bool
   isPalindrome candidate =
     candidate == reverse candidate
   ```

9. _Write a function to return the absolute value of a number using if-
   then-else_

   ```hs
   myAbs :: Integer -> Integer
   myAbs x =
     if x < 0 then
       x - (x * 2)
     else
       x
   ```

10. _Fill in the definition of the following function, using `fst` and `snd`:_

   ```hs
   f :: (a, b) -> (c, d)->((b, d), (a, c))
   f (a, b) (c, d) = ((b, d), (a, c))
   ```

## Reading Syntax

_In the following examples, you’ll be shown syntactically incorrect code. Type
it in and try to correct it in your text editor, validating it with GHC or
GHCi._

1. _Here, we want a function that adds 1 to the length of a string argument and
   returns that result._

  ```hs
   x = (+)
   F xs = w 'x' 1
     where w = length xs
  ```

  Correct:

  ```hs
   x = (+)
   f xs = w `x` 1
     where w = length xs
  ```

2. _This is supposed to be the identity function, `id`._

   ```hs
   \X = x
   ```

   Correct:

   ```hs
   \x -> x
   ```

3. _When fixed, this function will return `1` from the value `[1, 2, 3]`. Hint:
   you may need to refer back to the section about variables conventions in
   `“Hello Haskell”` to refresh your memory of this notation._

   ```hs
   \x : xs -> x
   ```

   Correct:

   ```hs
   \(x:xs) -> x
   ```

4. _When fixed, this function will return `1` from the value `(1, 2)`_

   ```hs
   f (a b) = A
   ```

   Correct:

   ```hs
   f (a, b) = a
   ```

## Match the function names to their types

1. _Which of the following types is the type of `show`?_
   * `show a => a -> String`
   * `Show a -> a -> String`
   * `Show a => a -> String`

   The type of `show` is `show a => a -> String`

2. _Which of the following types is the type of `(==)`?_
   * `a -> a -> Bool`
   * `Eq a => a -> a -> Bool`
   * `Eq a -> a -> a -> Bool`
   * `Eq a => A -> Bool`

   The type of `(==)` is `Eq a => a -> a -> Bool`

3. _Which of the following types is the type of `fst`?_
   * `(a, b) -> a`
   * `b -> a`
   * `(a, b) -> b`

   The type of `fst` is `(a, b) -> a`

4. _Which of the following types is the type of `(+)`?_
   * `Num a -> a -> a -> Bool`
   * `Num a => a -> a -> Bool`
   * `num a => a -> a -> a`
   * `Num a => a -> a -> a`
   * `a -> a -> a`

   The type of `(+)` is `Num a => a -> a -> a`
