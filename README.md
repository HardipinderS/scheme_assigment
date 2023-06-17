# Scheme Assignemnt

## Excercise 1
###  Evaluated following expressions. 
##### Write down both the expression and the result (as a comment).
1.	(car '(0))
 *0*
2.	(cdr '(0)) 
*'()*
3.	(car '((1 2 3) (4 5 6)))
*'(1 2 3)*
4.	(cdr '(1 2 3 . 4)) 
*'(2 3 . 4)*
5.	(cdr (cons 3 (cons 2 (cons 1 '()))))
*'(2 1)*

## Excercise 2
###  Make following functions (these are tricky - use and and/or or):
##### 1. A function that takes two numbers as arguments. It returns the product of these three numbers if all them is positive.

```
(define (positive-product x y)
    (if (equal? #t  (and (> x 0) (> y 0)))
        (* x y)
            "number is negative"))

(positive-product -2 3)
```

##### 2. A function that takes three numbers as arguments. It returns the product of these three numbers if at least one of them is negative.

```
(define (positive-product x y z)
    (if (equal? #t  (or (< x 0) (< y 0) (< z 0)))
        (* x y z)
            "no number is negative"))

(positive-product 2 3 4)

```

## Excercise 3
##### Make following functions.
##### 1. The grade (A – D) of exam is determined by the score (score). Write a function that takes a score as an argument and returns a grade.
- A if score ≥ 85
- B if 75 ≤ score ≤ 84
- C if 63 ≤ score ≤ 74
- D C if 45 ≤ score ≤ 62
- F if score < 44


```
(define (grading marks)
        (cond
                ((>= marks 85) "A")
                ((<= 75 marks 84) "B")
                ((<= 63 marks 74) "C")
                ((<= 45 marks 62) "D")
                ((<= marks 44) "F")
                (else "retry with different input")

        )
)
(grading 10)

```

## Excercise 4
##### Write following functions using recursion.
##### 1. A function that counts the number of list items, countlist. (there is a function length defined, do not use it.)

```
(define (countlist lst count)
        (if (equal? lst '())
        (display count)
        (countlist (cdr lst) (+ count 1)))
)

(countlist '(1 2 3 (4 5)) 0)

```

##### 2. A function that counts the number of items in the list, countlists but this time includes items in sub-lists

```
(define (countlists lst count)
        (if (and (not (equal? lst '())) (list? (car lst)))
                (countlists (car lst) count)
                null)
        (if (equal? lst '())
        (display count)
        (countlists (cdr lst) (+ count 1)))
)

(countlists '(1 2 3 (4 5)) 0)

```

## Exercise 5
##### Write following functions using recursion
##### 1.A function that sumlist numbers in a list.

```
(define (sumlist lst number)
        (if (equal? lst '())
        (display number)
        (sumlist (cdr lst) (+ (car lst) number)))
)

(sumlist '(1 2 3 4) 0)

```

##### 2. sumlists that summarizing items of a list consisting of numbers and sub-lists of numbers.

```
(define (sumlists lst number)
        (if (and (not (equal? lst '())) (list? (car lst)))
                (sumlists (car lst) number)
                null)
        (if (equal? lst '())
        (display number)
        (sumlists (cdr lst) (+ (car lst) number)))
)

(sumlists '(1 2 3 (4 5)) 0)
```

## Exercise 6
##### Write the following functions using tail recursive. *No points given if noy tail recursive.*
##### 1. myreverse that reverse the order of the items in a list. (Function reverse is pre-defined and should not be used.)

```
(myreverse ‘(1 2 3) => (3 2 1)

(define (myreverse lst)
  (myreverse-helper lst '()))

(define (myreverse-helper lst acc)
  (if (null? lst)
      acc
      (myreverse-helper (cdr lst) (cons (car lst) acc))))

(myreverse '(1 2 3 4 5))
```

## Exercise 7
##### Write followings using map.
##### 1. A function that doubles each item of a list of numbers.

```
(define lst (list 1 2 3))
(define (double x) (* x 2))
(map double lst)

```

## Exercise 8
##### Write followings using map.
##### 1. Write a single function that squares each item of a list, then sums all the items in the list, and then lastly, takes square root of the sum.
##### That is a single function that

1. squares each item of a list then
2. sums each squared value in the list and then
3. takes the square root of that number

```
(define (sq-sum-sqrt xs)
        (sqrt (apply + (map * xs xs)))
)
(sq-sum-sqrt '(1 2 3 4 5))
```

## Exercise 9
##### 1. Define list-all.
##### This function takes three arguments, a function to compare, the specified item, and a list: It returns all the items that matches the according to the ‘function to compare”


```
(list-all string=? "hello" '("hi" "guys" "bye" "hello" "hello"))
⇒ (hello hello)
(list-all string=? "ciao" '("hi" "guys" "bye" "hello" "hello"))
⇒ ()
```
