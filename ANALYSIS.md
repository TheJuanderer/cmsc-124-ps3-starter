# Environments and the Toy Evaluator

## trace
Lets say we have this expression (let ((x 5)) (+ x 2)) evaluated in the empty environment nil. eval-expr tests if it is a number using numberp (no), a symbol using symbolp (no, it is a list), and if its a list consp (yes). 

The head is let, which is not in (+ - *), so the (eq op 'let) branch calls eval-let. 

The names is (x) and inits is (5). The inits are evaluated by eval-operands in the outer env, giving (5), and only then does extend-env build ((x . 5)) by appending the new pairs in front of env without modifying it. 

The body (+ x 2) is then passed to eval-expr with that extended environment. This time the head + matches the arithmetic branch, so eval-operands evaluates x (E1's lookup finds (x . 5) and returns 5) and 2 which just return itself. 

apply-op checks the operator and arity, calls (apply '+ '(5 2)), and returns 7. 

Evaluating the inits in env instead of the extended environment is what makes let parallel: (let ((x 1)) (let ((x 2) (y x)) y)) gives 1, not 2.

Consider:

(let ((x 2))
  (let ((f (lambda (y)
             (+ x y))))
    (let ((x 100))
      (funcall f 1))))

When the lambda is created, `make-closure` saves its defining environment in the closure’s `env` field and the `(:closure params body env)` return expression. When `(f 1)` is called, `apply-closure` extends that saved environment with `y` bound to `1`. The body finds `x` bound to `2`, so the result is `3`.

If application used the caller’s environment instead, the body would find the caller’s x, bound to 100, and return 101. Saving and using the defining environment gives the toy language lexical scope.

The toy language is Lisp-1: variables and functions share a namespace, so a closure stored in f can be called as (f 1). CLISP is Lisp-2, with separate variable and function namespaces, so the host uses `funcall` to invoke a function value. The evaluator can implement the toy language’s direct-call behavior itself.

##
