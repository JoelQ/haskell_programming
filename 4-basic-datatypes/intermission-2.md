# Intermission Exercises 2

_The following lines of code may have mistakes — some of them won’t compile!
You know what you need to do._

```hs
-- 1
not True && true
not True && True -- capitalize second `True`

-- 2
not (x = 6)
not (x == 6) -- use double equals, assumes `x` is defined

-- 3
(1 * 2) > 5 -- correct

-- 4
[Merry] > [Happy]
["Merry"] > ["Happy"] -- compare the strings, not the data constructors

-- 5
[1, 2, 3] ++ "look at me!"
['1', '2', '3'] ++ "look at me!"
-- can't concatenate lists of different types, convert numbers to characters
```
