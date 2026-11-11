# Environments and the Toy Evaluator
###
Replace this paragraph after your checks pass. Trace one form through your own
`eval-expr`, point to the line that captures the defining environment, say what
would change if application joined the arguments to the caller's environment
instead, and explain why the host CLISP needs `funcall` where the toy language
doesn't. 
###

## trace
Lets say we have this expression (let ((x 5)) (+ x 2)) evaluated in the empty environment nil. eval-expr tests if it is a number using numberp (no), a symbol using symbolp (no, it is a list), and if its a list consp (yes). 

The head is let, which is not in (+ - *), so the (eq op 'let) branch calls eval-let. 

The names is (x) and inits is (5). The inits are evaluated by eval-operands in the outer env, giving (5), and only then does extend-env build ((x . 5)) by appending the new pairs in front of env without modifying it. 

The body (+ x 2) is then passed to eval-expr with that extended environment. This time the head + matches the arithmetic branch, so eval-operands evaluates x (E1's lookup finds (x . 5) and returns 5) and 2 which just return itself. 

apply-op checks the operator and arity, calls (apply '+ '(5 2)), and returns 7. 

Evaluating the inits in env instead of the extended environment is what makes let parallel: (let ((x 1)) (let ((x 2) (y x)) y)) gives 1, not 2.

##
