变量查找逻辑
- If there is a global x declaration, x comes from and is assigned to the x global variable module.4
- If there is a nonlocal x declaration, x comes from and is assigned to the x local variable of the nearest surrounding function where x is defined.
- If x is a parameter or is assigned a value in the function body, then x is the local variable.
- If x is referenced but is not assigned and is not a parameter:
    - x will be looked up in the local scopes of the surrounding function bodies
(nonlocal scopes).
    - If not found in surrounding scopes, it will be read from the module global scope.
    - If not found in the global scope, it will be read from __builtins__.__dict__.