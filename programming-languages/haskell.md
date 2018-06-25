# Haskell

## Hello World

```haskell
main = putStrLn "Hello, World!"
```

## Examples

```haskell
import Data.Char -- added for isLower
--Instructions

-- Expression:
--   5 + 5
e_v1 = 5 + 5
e_v2 = (5 + 5)

-- Function call:
e_v3 = max 5 7
e_v4 = (max 5) 7
e_v5a = (max 5)
e_v5b = e_v5a 7
-- "max 5" returns a function that takes one argument and
--   returns 5 + the argument.
-- Therefore e_v3, e_v4, ev_5b all return 7, the max of 5 and 7.

-- Function definition:
e_inc = \x -> x+1
-- Syntax: <newname> = <lambda>
-- <lambda>: \<arg> -> <expression>

e_add_a = \x -> (\y -> x + y)
e_add_b = \x -> \y -> x + y

e_add_c = \x y -> x + y
-- <lambda>: \<arg1> <arg2>  ->  <expression>

e_add_d x y = x + y
-- Syntax: <newname> <args> = <expression>

e_inc' x = x + 1



--Examples:
string1 = "hello"
string2 = "world"
greeting = string1 ++ " " ++ string2

v1 = sqrt 3
v2 = max 5 7
v3 = max (5 + 2) (sqrt 17)

square x = x * x
multiMax a b x = (max a b) * x

v4 = square 4 -- 16
v5 = multiMax 1 9 5 -- 45

v6 = show v5 -- "45"

v7 = 37 == 37 -- True
v8 = 37 /= 37 -- False
v81 = v7 || v8 -- True
v82 = not v81 -- False
v83 = v81 || v7 && False -- True

v9 = negate 3.3 -- -3.3
v10 = abs(-3) -- 3
v11 = signum (-3) -- -1
v12 = 7 `div` 2 -- 3
v13 = 7 `mod` 2 -- 1
v14 = 7.0 / 2.0 -- 3.5
v15 = recip 2.0 -- 0.5

posOrNeg x =
  if x >= 0
  then "Positive"
  else "Negative"

posOrNeg' x =
  case x >= 0 of {
    True -> "Positive";
    False -> "Negative" }

-- recursion
pow2 n =
      if n == 0
      then 1
      else 2 * (pow2 (n-1))

repeatString str n =
   if n == 0
   then ""
   else str ++ (repeatString str (n-1))


sumSeq n = 
    if n == 0
    then 0
    else n + sumSeq (n-1)

-- lists
x = [1,2,3]
empty = []
y = 0 : x -- [0,1,2,3]
x' = 1 : (2 : (3 : []))
x'' = 1 : 2 : 3 : []
x''' = [1..3] -- [1,2,3]

str = "abcde"  -- "abcde"
str' = 'a' : 'b': 'c' : 'd': 'e' : []  -- "abcde"

xx1 = [1,2,3] ++ [4,5] -- [1,2,3,4,5]
xx2 = "hello " ++ "world"

-- list functions
xx3 = head [1,2,3] -- 1
xx4 = tail [1,2,3] -- [2,3]
xx5 = head (tail [1,2,3]) -- 2
xx5a = init [1,2,3] -- [1,2]
xx5b = last [1,2,3] -- 3

xx6 = null [] -- True
xx7 = null [1,2] -- False

xx8 = take 3 [1,2,3,4,5] -- [1,2,3]
xx9 = drop 3 [1,2,3,4,5] -- [4,5]
xx10 = length [1,2,3,4,5] -- 5
xx11 = sum [1,2,3,4,5] -- 15
xx12 = product [1,2,3,4,5] -- 120
xx13 = [1,2,3] ++ [4,5] -- [1,2,3,4,5]
xx14 = reverse [1,2,3,4,5] -- [5,4,3,2,1]

double nums =
  if null nums
  then []
  else (2 * (head nums)) : (double (tail nums))

removeOdd nums =
  if null nums
  then []
  else
    if (mod (head nums) 2) == 0 -- even?
    then (head nums) : (removeOdd (tail nums))
    else removeOdd (tail nums)

index_v1 = [1,2,3,4,5] !! 2 -- 3
drop_v1 = drop 3 [1,2,3,4,5] -- [4,5]
sum_v1 = sum [1,2,3,4,5] -- 15
product_v1 = product [1,2,3,4,5] -- 120
reverse_v1 = reverse [1,2,3,4,5] -- [5,4,3,2,1]

factorial n = product [1..n]
average ns = sum ns `div` length ns

-- tuples
t1 = (1, "hello")
t2 = ("pi", 3.1415, [1,2,3], "four")
t1' = (,) 1 "hello" -- (1, "hello")
t2' = (,,,) "pi" 3.1415 [1,2,3] "four"

headAndLength list = (head list, length list)

pair1 = fst (1, "Hello") -- 1
pair2 = snd (1, "Hello") -- "Hello"

-- pattern matching
fst' (a,b) = a
snd' (a,b) = b

null' [] = True
null' (x : xs) = False  -- or null' (_:_) = False

head' (x : xs) = x
head' [] = error "head of empty list"

tail' (x:xs) = xs -- or tail' (_:xs) = xs

double' [] = []
double' (x : xs) = (2 * x) : (double xs)

vx_1 = let (a:b:c:[]) = "xyz" in c  -- 'z', 3rd char.
vx_2 = let (_:_:c:[]) = "xyz" in c  -- 'z', 3rd char.
vx_3 = let (_:_:c) = "xyz" in c  -- "z", 3rd char as a string.
vx_4 = let (_,y:_) = (10,"abc") in y  -- 'a' 

-- ptest1 returns true if list starts with 'a' and contains exactly 3 characters
ptest1 ['a',_,_] = True
ptest1 _         = False

-- guards
pow2' n
  | n == 0    = 1
  | otherwise = 2 * (pow2' (n-1))

removeOdd' [] = []
removeOdd' (x : xs)
  | mod x 2 == 0 = x : (removeOdd' xs)
  | otherwise    = removeOdd' xs

-- case
double'' nums = case nums of
  []       -> []
  (x : xs) -> (2 * x) : (double'' xs)

anyEven nums = case (removeOdd nums) of
  []       -> False
  (x : xs) -> True

-- let binding
fancySeven =
  let a = 3
  in 2 * a + 1

fancyNine =
  let x = 4
      y = 5
  in x + y

numEven nums =
  let evenNums = removeOdd nums
  in length evenNums

fancySeven' = 2 * a + 1
  where a = 3

fancyNine' = x + y
  where x = 4
        y = 5

fancyTen = 2 * (let a = 4 in a + 1)

-- lazy evaluation
intsFrom n = n : (intsFrom (n+1))
ints = intsFrom 1

ints_1 = null ints
ints_2 = head ints
ints_3 = take 10 ints
ints_4 = take 10 (removeOdd ints)

-- functions as value
pass3 f = f 3
add1 x = x + 1

pass_v1 = pass3 add1 -- 4 (3 = 3 + 1)

compose f g x = f (g x)
mult2 x = x * 2

comp_v1 = compose add1 mult2 4 -- 9 (add1 (mult2 4) = (2 * 4) + 1

always7 x = 7  -- 7
always7const = const 7  -- 7
always7' x = always7const -- 7

-- partial application
foo x y z = x + y + z
foo_1_2 = foo 1 2

foo_v1 = foo_1_2 3  -- 6

pass x f = f x
pass3' = pass 3
pass'_v1 = pass3' add1  -- 4

-- operators
op_v1 = (+) 5 3  -- 8

pass_3_4 f = f 3 4
pass_v2 = pass_3_4 (+)  -- 7

-- operator definitions
(a,b) .+ (c,d) = (a + c, b + d)

-- partially applying operators
plus1 = (+) 1  -- 6
 
-- sections
plus1' = (1+)
plus1'' = (+1)

-- turning functions into operators
m_v1 = mod 10 2  -- 0
m_v2 = 10 `mod` 2  -- 0

-- map
map_v1 = map length ["hello","abc","1234"]  -- [5,3,4]
map_v2 = map (1+) [1,3,5,7] -- [2,4,6,8]

double''' = map (2*)

-- returns the first n odd integers 
odds n = map f [0..n - 1]
         where f x = x * 2 + 1

-- filter
notNull xs = not (null xs)

filter_v1 = filter notNull ["","abc","","hello",""]  -- ["abc","hello"]

isEven x = x `mod` 2 == 0
removeOdd'' = filter isEven
removeOdd''' = filter (\ x -> x `mod` 2 == 0) 

map_filt_v1 = map snd (filter fst [(True,1),(False,7),(True,11)]) -- [1,11]

-- foldl, tail-recursive
foldl_v1 = foldl (+) 0 [1,2,3,4] -- 10 (0 + 1 + 2 + 3 + 4)

showPlus s x = "(" ++ s ++ "+" ++ (show x) ++ ")"
showPlus_v1 = showPlus "(1+2)" 3 -- "((1+2)+3)"

foldl_v2 = foldl showPlus "0" [1,2,3,4] -- "((((0+1)+2)+3)+4)"

-- foldr, can work on infinite lists
foldr_v1 = foldr (+) 0 [1,2,3,4] -- 10 (1 + 2 + 3 + 4 + 0)

showPlus' x s = "(" ++ (show x) ++ "+" ++ s ++ ")"
showPlus'_v1 = showPlus' 3 "(1+2)" -- "(3+(1+2))"

-- zip
zip_v1 = zip [1, 2, 3] [4, 5, 6] -- [(1,4), (2,5), (3,6)]
zip_v2 = zip [1, 2] [3, 4, 5, 6] -- [(1,3), (2,4)]

-- zipWith
zipWith_v1 = zipWith (+) [1,2,3] [4,5,6] -- [5,7,9]

plus3 x y z = x + y + z
zipWith3_v1 = zipWith3 plus3 [1,2,3] [4,5,6] [7,8,9] -- [12,15,18]

-- lambda Expression
inc x = x+1
inc'  = \x -> x+1

add x y = x+y
add'    = \x y -> x+y

-- note that inc can be defined as: inc = (+ 1)
-- note that add can be defined as: add = (+)

zipWith3_v2 = zipWith3 (\ x y z -> x + y + z) [1,2,3] [4,5,6] [7,8,9]

map_v3 = map (\ x -> 2 * x ) [1,2,3] -- [2,4,6]

map_v4 = map (2*) [1,2,3] -- [2,4,6]

map_v5 = map (\ x-> 2 * x + 1) [1,2,3] -- [3,5,7]

-- returns the first n odd integers 
odds' n = map (\x -> x * 2 + 1)[0..n - 1]

-- function Operators (.) oper, makes function from 2 other functions
stringLength = length . show
stringLength_v1 = stringLength 120 -- 3
stringLength' x = length (show x)
stringLength'_v1 = stringLength' 120 -- 3

notNull' = not . null

funcComp f g = \x -> f (g x) -- funcComp is equivalent to (.)
notNull'' = not `funcComp` null

funcComp' f g x = f (g x) -- same as funcComp, w/e lambda

-- Function Application ($) oper, applies a function to a value 
sqrt_v1 = sqrt $ 3

-- f $ g $ h $ k x = f (g (h (k x)))

-- without $
map_v6'1 = map (\f -> f 3) [(+1), (\x -> 2*x + 3), (*2)]
-- with $
map_v6'2 = map ($3)        [(+1), (\x -> 2*x + 3), (*2)]

zipWith_v2 = zipWith ($) [(+1), (\x -> 2*x + 3), (*2)] [1,2,3] -- [2,7,6]

-- explicit type
hello :: [Char] -- declare hello to be a string.  This line is unnecessary.
hello = "hello" -- assign "hello" to hello.

-- foo is a function from int to int
foo2 :: Int -> Int -- foo2 is of type function that takes int, returns int.
foo2 x = 2 * x + 1 -- define foo function
foo2_v1 = foo2 5 -- 11

-- explicit function type
add3Int :: Int -> Int -> Int -> Int -- takes 3 ints returns an int
add3Int x y z = x + y + z
add3Int_v1 = add3Int 111 222 333 -- 666

-- type annotation
x1 = 3 :: Int -- declaring a type not stored in a variable.

foo3 = x + y
  where x = length "hello"
        y = 5
foo3_v = foo3  

foo4 = x + y
  where x :: Int
        x = length "hello"
        y :: Int
        y = 5
foo4_v = foo4  

-- x2 = show (read "123")  <-- cannot work 
x2' = show (read "123" :: Int)
x3' = read "False" :: Bool

--- qsort
product' [] = 1
product' ( x : xs ) = x * product' xs 
product'_v1 = product' [2,3,4] -- 24

qsort' [] = []
qsort' (x:xs) = qsort' smaller ++ [x] ++ qsort' larger
                where
                  smaller = filter (< x) xs
                  larger = filter (> x) xs
                  --smaller = filter (\ y -> y < x) xs
                  --larger = filter (\y -> y > x) xs

qsort'' [] = []
qsort'' (x:xs) = qsort'' smaller ++ [x] ++ qsort'' larger
                where
                  smaller = filter (<= x) xs
                  larger = filter (> x) xs


qsort''' [] = []
qsort''' (x:xs) = qsort''' smaller ++ [x] ++ qsort''' larger
                where
                  smaller = [a | a <- xs, a <= x]
                  larger = [b | b <- xs, b > x]

qsort2 [] = []
qsort2 (x:xs) = reverse (qsort''' smaller) ++ [x] ++ reverse (qsort''' larger)
                where
                  smaller = [a | a <- xs, a <= x]
                  larger = [b | b <- xs, b > x]

-- id
id_v1 = id 34 -- 34


-- conditional expressions
-- edx_abs :: Int -> Int
edx_abs n = if n >= 0 then n else -n

-- edx_signum :: Int -> Int
edx_signum n = if n < 0 then -1 else
                  if n == 0 then 0 else 1

-- guarded equations
-- right hand sides tarts with a condition
edx_abs2 n | n >= 0    = n
           | otherwise = -n

edx_signum2 n | n < 0     = -1
             | n == 0    = 0
             | otherwise = 1


-- pattern matching
-- edx_not      :: Bool -> Bool
edx_not False = True
edx_not True  = False

-- (edx_)        :: Bool -> Bool -> Bool
True  `edx_and` True  = True
True  `edx_and` False = False
False `edx_and` True  = False
False `edx_and` False = False 

True `edx_and2` True  = True
_    `edx_and2` _     = False

-- even thought this works:
True  `edx_and3` b = b
False `edx_and3` _ = False

-- this won't because b is on both sides:
-- b `edx_and4` b = b
-- _ `edx_and4` _ = False

-- but this will work using guards:
b `edx_and4` c | b == c  = b
               | otherwise = False

-- cons
-- edx_head  :: [a] -> a
edx_head (x:_) = x

-- edx_tail  :: [a] -> [a]
edx_tail (_:xs) = xs

-- curring
-- edx_add is a func that takes param x and returns a func that 
-- takes parm y, returning x + y
edx_add x y = x + y

-- Safetail 
--  a conditional expression
edx_safetail_ce x = if null x then [] else tail x 

--  a guarded equation
edx_safetail_ge x | null x   = []
                  | otherwise = tail x
--  pattern matching
edx_safetail_pm [] = []
edx_safetail_pm x  = tail x

-- exercises
-- halve [1,2,3,4,5,6] should return ([1,2,3],[4,5,6])

halve n = let l = div (length n) 2 in (take l n, drop l n)

-- show curred function definition: multi x y z = x * y * z in terms of lambda
multi x y z = x * y * z
multi_a x = (\ y z -> x * y * z)
multi_b x = (\ y -> (\z -> x * y * z))
multi_c = (\x -> (\ y -> (\z -> x * y * z)))
multi_d = \x -> \ y -> \z -> x * y * z

-- list compehension
lc_1 = [x*2 | x <- [1..5]]   -- [2,4,6,8,10] 

lc_2 = [(x,y) | x <- [1,2,3], y <- [4,5]] -- [(1,4),(1,5),(2,4),(2,5),(3,4),(3,5)]

lc_3 = [(x,y) | x <- [1..3], y <- [x..3]] -- [(1,1),(1,2),(1,3),(2,2),(2,3),(3,3)]

lc_concat xss = [x | xs <- xss, x <- xs] 

lc_4 = lc_concat [[1,2,3],[4,5],[6]] -- [1,2,3,4,5,6]

lc_5 = [x | x <- [1..10], even x] -- [2,4,6,8,10]

lc_factors n = [x | x <- [1..n], n `mod` x == 0]

lc_6 = lc_factors 15 -- [1,3,5,15]

lc_prime n = lc_factors n == [1,n]

lc_7 = lc_prime 15 -- False
lc_8 = lc_prime 7 -- True

lc_primes n = [x | x <- [2..n], lc_prime x]
lc_10 = lc_primes 40 -- [2,3,5,7,11,13,17,19,23,29,31,37]

-- more with zip
z_pairs xs = zip xs (tail xs)
z_1 = z_pairs [1,2,3,4]  --[(1,2),(2,3),(3,4)]

z_sorted xs = and [x <= y | (x,y) <- z_pairs xs]

z_2 = z_sorted [1,2,3,4] -- True
z_3 = z_sorted [1,3,2,4] -- False

z_positions x xs = 
     [i | (x',i) <- zip xs [0..n], x == x']
     where n = length xs - 1

z_4 = z_positions 0 [1,0,0,1,0,1,1,0] -- [1,2,4,7]

z_lowers xs = length [x | x <- xs, isLower x]
z_5 = z_lowers "Haskell" -- 6

z_6 = take 3 "abcde" -- "abc"

z_7 = zip "abc" [1,2,3,4] -- [('a',1),('b',2),('c',3)] 

-- more with recursion
[] `cat` ys = ys
(x:xs) `cat` ys = x : (xs `cat` ys)
r_4 = [1,2,3] `cat` [5,6] -- [1,2,3,5,6]

-- standard way to define factorial
-- r_factorial n = product [1..n]
-- factorial using recursion
r_factorial 0 = 1
r_factorial n = n * r_factorial (n-1)

r_product [] = 1
r_product (n:ns) = n * r_product ns

r_length [] = 0
r_length (_:xs) = 1 + length xs

r_reverse [] = []
r_reverse (x:xs) = reverse xs ++ [x]

r_zip [] _ = []
r_zip _ [] = []
r_zip (x:xs) (y:ys) = (x,y) : r_zip xs ys

r_drop 0 xs = xs
r_drop _ [] = []
r_drop n (_:xs) = r_drop (n-1) xs

-- r_pp is recursive version of ++
[] `pp` ys = ys
(x:xs) `pp` ys = x : (xs `pp` ys)
r_v1 = "hap" `pp` "py" -- "happy"

-- map defined using list comprehension
l_map f xs = [f x | x <- xs]

-- map defined using recursion
h_map f [] = []
h_map f (x:xs) = f x : map f xs

-- filter defined using list comprehension
h_filter p xs = [x | x <- xs, p x]

-- filter defined using recursion
r_filter p [] = []
r_filter p (x:xs)
    | p x       = x : filter p xs
    | otherwise = filter p xs

r_sum [] = 0
r_sum (x:xs) = x + r_sum xs

r_and [] = True
r_and (x:xs) = x && r_and xs

-- foldr encapsulates simple pattern of recursion
f_sum = foldr (+) 0
f_product = foldr (*) 1
f_or = foldr (||) False
f_and = foldr (&&) True

f_foldr f v [] = v
f_foldr f v (x:xs) = f x (f_foldr f v xs) 

f_length = foldr (\_ n -> 1+n) 0

f_reverse = foldr (\x xs -> xs ++ [x]) []

-- composition
c_odd = not . even

-- other
o_1 = all even [2,4,6] -- True
o_2 = any isSpace "abc def" -- True
o_3 = takeWhile isAlpha "abc def" -- "abc"
o_4 = dropWhile isSpace " def" -- "def"

-- scanr1 / scanl1
s_1 = scanr1 (+) [1,2,3,4] -- [10,9,7,4]
-- 7=3+4, 9=7+2, 10=9+1

s_2 = scanl1 (+) [1,2,3,4] -- [1,3,6,10]
-- [1, 1+2, 1+2+3, 1+2+3+4]

-- const id
c_1 = (const id) 5 6 -- 6

-- flip
f_1 = (flip (-)) 100 2 -- -98

f_2 = (flip const) 5 6 -- 6

-- curry/uncurry
cr_1 = snd (6,3) -- 3

cr_2 = (curry snd) 6 3 -- 3

cr_3 = (uncurry (+)) (6,3) -- 9

uadd = uncurry (+)
cr_4 = uadd (6,3) -- 9

--- custom types
---   type synonyms:
type Point = (Double,Double)
second_point :: Point -> Double
second_point (x,y) = y
p1_v = second_point (3.4, 4.2) -- 4.2

---   newtype -- (MkCustId, the custructor can have same name as type, CustId)
newtype CustId = MkCustId Int
custToInt (MkCustId i) = i
cust1 = MkCustId 13
cust1AsInt = custToInt cust1 -- 13

---   records
---     each field is a global function, which is a problem
--      generally the weakest point in the language
data CustomerR = MakeCustomerR
  { customerIdR  :: CustId
  , nameR        :: String
  , luckyNumberR :: Int
  }

aliceR = MakeCustomerR
  { customerIdR  = MkCustId 13
  , nameR        = "Alice"
  , luckyNumberR = 42
  }

aliceR_name = nameR aliceR -- "Alice"
aliceR_luckyNumber = luckyNumberR aliceR -- 42
aliceR_custIdAsInt = custToInt (customerIdR aliceR) -- 13

sallyR = aliceR { nameR = "Sally", luckyNumberR = 84 }
sallyR_name = nameR sallyR -- "Sally"
sallyR_luckyNumber = luckyNumberR sallyR -- 84
sallyR_custIdAsInt = custToInt (customerIdR sallyR) -- 13

---    algebriac data type
data CustomerA = MakeCustomerA CustId String Int
aliceA = MakeCustomerA (MkCustId 13) "Alice" 42
getCustomerId (MakeCustomerA cust_id name luckyNumber) = cust_id
aliceA_id = custToInt (getCustomerId aliceA) -- 13

getCustomerId' (MakeCustomerA cust_id _ _) = cust_id
aliceA_id' = custToInt (getCustomerId' aliceA) -- 13

data StringTree = StringTree String [StringTree]

hierarchy = StringTree "C:"
              [ StringTree "Program Files" []
              , StringTree "Users"
                  [ StringTree "Alice" []]
              , StringTree "Cats" []
              ]
---    algebriac data type constructors
data DialogResponse = Yes | No | Help | Quit

data Bull = Falsex | Truex
bx1 = Falsex
bx2 = Truex

negatex Truex = Falsex
negatex Falsex = Truex

data MaybeInt = NoInt | JustInt Int

defaultInt :: Int -> MaybeInt -> Int
defaultInt defaultValue NoInt = defaultValue
defaultInt _ (JustInt x) = x
d1_v = NoInt
d2_v = JustInt 42

d1_vv = defaultInt 0 d1_v -- 0
d2_vv = defaultInt 0 d2_v -- 42


data StringList = EmptyStringList | ConsStringList String StringList

lengthStringList :: StringList -> Int
lengthStringList EmptyStringList = 0
lengthStringList (ConsStringList _ xs) = 1 + lengthStringList xs







----------------
-- Haskell 99 questions
----------------
-- Quesiton 1
-- Find the last element of a list
-- myLast [1,2,3,4]
-- should return 4

myLast1 x = head (reverse x)

myLast2 x = x !! ((length x) - 1)

myLast3 [x] = x
myLast3 (x:xs) = myLast3 xs

myLast4 = foldr1 (const id)

myLast5 = foldr1 (flip const)

myLast6 = foldl1 (curry snd)


-- Question 2:
-- Find the last but one element of a list
-- myButLast [1,2,3,4]
-- should return 3

myButLast1 x = x !! ((length x) - 2)

myButLast2 [] = error "Error"
myButLast2 (x:xs)
   | length xs == 1 = x
   | otherwise      = myButLast2 xs    

myButLast3 [x,_] = x
myButLast3 (_:xs) = myButLast3 xs

myButLast3x (x:_:[]) = x
myButLast3x (_:xs) = myButLast3x xs

myButLast4 x = head (tail (reverse x))

myButLast5 x = head $ tail $ reverse x

myButLast5x = head . tail . reverse

myButLast6 = last . init

myButLast7 x = reverse x !! 1




```



