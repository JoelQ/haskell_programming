# Intermission Exercises 1

```hs
data Mood = Blah | Woot deriving Show
```

1. _What is the type constructor, or name of this type?_

   `Mood` is the **Type Constructor**

2. _If the function requires a `Mood` value, what are the values you could possibly
   use there?_

   `Blah` and `Woot` are valid `Mood` values

3. _We are trying to write a function `changeMood` to change Chris’s mood
   instantaneously. So far, we’ve written a type signature
   `changeMood :: Mood -> Woot`. What’s wrong with that?_

   Only **type constructors** are valid values in a type signature. `Woot` is a
   **data constructor**. The correct signature is `changeMood :: Mood -> Mood`.

4. _Now we want to write the function that changes his mood. Given an input
   mood, it gives us the other one. Fix any mistakes and complete the function:_

   ```hs
   changeMood Mood = Woot
   changeMood    _ = Blah
   ```
   
   ```hs
   changeMood :: Mood -> Mood
   changeMood Blah = Woot
   changeMood Woot = Blah
   ```

5. _Enter all of the above — datatype (including the “deriving Show” bit), your
   corrected type signature, and the corrected function into a source file. Load
   it and run it in GHCi to make sure you got it right._

   ```
   Prelude> :l 4-basic-datatypes/mood.hs 
   [1 of 1] Compiling Mood             ( 4-basic-datatypes/mood.hs, interpreted )
   Ok, modules loaded: Mood.
   *Mood> changeMood Blah
   Woot
   *Mood> changeMood Woot
   Blah
   ```
