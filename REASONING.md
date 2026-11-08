# Reasoning for the Predictions Table

Write one entry under every heading below, then commit this file together with
`predictions.tsv`, before you run a case or open `tests/expected.tsv`.

Each entry names the rule that produces the four predicted fields for that
case. One to three sentences is enough. The grader checks structure only. It
does not judge quality, and it sets no word minimum.

After you run the cases, add a short correction under each case you predicted
wrongly. Say what you predicted, what CLISP printed, and which rule you
misread. Those entries belong in the correction commits.

## P01
The expression is evaluated mathematically as 1 + (2 * 3) = 7, giving the value 7 with an integer data type. Since the expression contains no list of multiple elements to determine a length, its length is none. The outer expression uses `+` which is a function, so its operator kind is function. 

## P02
When the right expression is evaluated it returns a list since the expression is nested in a quote. Inside the list there are still 3 elements. And the operator is a special-operator since a `quote` based on common lisp is a `special operator`

## P03
Based on the grader notation its written as `nil`. nil has the Common Lisp data type NULL. It represents an empty list, which has a length of zero. Under the checker's classification, the resulting value has no applicable operator so the operator is `none`

## P04
`t` is recognized as a symbol rather than a string or a function call. Therefore, its value is displayed as `t`, its kind is `symbol`, and its length and operator are `none` because it is neither a sequence nor an operation.

## P05
The symbolp function checks whether its argument is a symbol. Since nil is a valid symbol in Common Lisp, `symbolp nil` evaluates to T. Therefore, the expression returns T, with the value classified as a symbol, no length, and a function `symobolp` as its operator.

## P06
The `car` retrieves the first element of a list. Since `'()` represents an empty list, (car '()) evaluates to nil. Therefore, the expression returns nil, which is classified as a null, has 0 length, and uses a function as its operator.

## P07
The `cons` function combines an element with a list. The value 1 is added to the list (2 3), producing (1 2 3). Therefore, the expression returns a list containing three elements, with a length of 3 and a function as its operator.

## P08
The `if` special operator evaluates the condition `(null '())`, which returns `T` because the quoted empty list is `nil`. Since the condition is true, it evaluates and returns `'empty`, which is a quoted symbol. Therefore, the value is the symbol `empty`, with no length since its not a list or `nil`, and its operator is classified as a special operator because its the `if` statement.

## P09
Since the and evaluates its arguments sequentially and stops when it encounters nil, it returns `nil` without evaluating the remaining expression, otherwise it will return `t`. The resulting value is `nil`, which has no length 0 and is classified as null. According to common lisp the `and` operator is a macro.

## P10
The `let` expression creates a temporary dynamic binding of the special variable `*ps3-rate*` to `10`. When `(ps3-scale 3)` is called, the function multiplies `3` by the current dynamically bound value of `*ps3-rate*`, which is `10`, producing `30`. The result is therefore an integer (`30`), with no length value, and its operator is classified as a special operator because the expression uses `cons`/`let` special-form evaluation.


## P11
Since the right side is quoted, this evaluate the `defun` expression, and it returns `ps3-twice` since its the function name. Its kind is therefore `symbol`, its length is `none` because the return value is not a sequence, and its operator type is `macro` because `defun` is a macro in Common Lisp.


## P12
The `labels` special operator defines a local recursive function named `down`, which generates a list of numbers by repeatedly decreasing `n` until it reaches 0. The resulting value is a list containing three elements since every recursive function the n is appended at the front, hence `kind` is a `list` and `length` is `3`. The `operator` is `special-operator` because `labels` is a Common Lisp special operator. 

## P13
The mapcar function applies the length function to each element of the list '((1 2) () (3)). The sublists have lengths 2, 0 (since () is the empty list), and 1, which collects into the list (2,0,1). The result is a cons with a length of 3. The outermost operator is mapcar, which is a function.

## P14
Replace this line with the rule behind this case's four fields.

## P15
Replace this line with the rule behind this case's four fields.

## P16
Replace this line with the rule behind this case's four fields.
