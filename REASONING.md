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
The cons function creates a pair containing the string "P01" and the quoted expression (+ 1 (* 2 3)). The expression is evaluated mathematically as 1 + (2 * 3) = 7, giving the value 7 with an integer data type. Since the expression contains no list of multiple elements to determine a length, its length is none. The outer expression uses `+` which is a function, so its operator kind is function. 

## P02
This creates a pair containing the string "P02" and the right expression has nested quoting (there are two quotes) and this prevents evaluation of the inner quoted expression. When the right expression is evaluated it returns a list since the expression is nested in a quote. Inside the list there are still 3 elements. And the operator is a special-operator since a `quote` based on common lisp is a `special operator`

## P03
Replace this line with the rule behind this case's four fields.

## P04
Replace this line with the rule behind this case's four fields.

## P05
Replace this line with the rule behind this case's four fields.

## P06
Replace this line with the rule behind this case's four fields.

## P07
Replace this line with the rule behind this case's four fields.

## P08
Replace this line with the rule behind this case's four fields.

## P09
Replace this line with the rule behind this case's four fields.

## P10
Replace this line with the rule behind this case's four fields.

## P11
Replace this line with the rule behind this case's four fields.

## P12
Replace this line with the rule behind this case's four fields.

## P13
Replace this line with the rule behind this case's four fields.

## P14
Replace this line with the rule behind this case's four fields.

## P15
Replace this line with the rule behind this case's four fields.

## P16
Replace this line with the rule behind this case's four fields.
