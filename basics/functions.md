# 🔥Language Constructs

?> **Language constructs** are not functions, and so cannot be used as a callback function. They follow rules that are different from functions when it comes to parameters and the use of parentheses. For example, echo doesn’t always need parentheses when you call it and, if you call it with more than one argument, then you should use parentheses.

| Language Construct | Purpose                                                                    |
| ------------------ | -------------------------------------------------------------------------- |
| assert             | Debug command to test a condition and do something if it is not true.      |
| echo/print         | Output value                                                               |
| exit/die           | Terminate the program.                                                     |
| return             | Terminates a function and returns control & value to the calling scope.    |
| eval               | Evaluates a string as PHP code.                                            |
| empty              | Returns a Boolean value depending on whether the variable is empty or not. |
| isset              | Returns true if the variable has been set and false otherwise.             |
| unset              | Clears a variable.                                                         |
| constant           | Used to retrieve the value of a constant.                                  |
| list               | Assigns multiple variables at one time from an array.                      |
| compact            | Creates an array from variables and their values.                          |

?> The **echo** construct does not return a value, not even null, and so is not suitable for use inside an expression. The **print** construct will however return a value
