# better-input
A module containing enhanced input functions for Python

### simple_input
This function is almost equivalent to Python's _input_ function. The only difference is that this one always expects a prompt to be given. Use is `answer = simple_input("Enter a number: ")`.

Returns a raw string (no casting or checkings performed)

### condition_input
This function does two different things:

1. Ask the user for input and cast it to another type. Default is `str`.
2. Optionally check if some condition is met.

If any of these fail (if the input cannot be casted, or if the condition is not met), an error message is displayed. The function won't return until the user enters a proper answer.

Use is:
```python
answer = condition_input("Enter a number: ", int, error_message="Is not a valid integer. Please retry.")
answer2 = condition_input("Enter the number of a month: ", int, condition=lambda x: 1<=x<=12, error_message="Is not a valid month. Please retry."
```

Most common use case (the asking of `int`s or `float`s) does not require a condition, since type casting is done _before_ the condition is checked. Conditions must take into account that the type is no longer `str`, i.e., don't do `lambda x: int(x)>0`, but rather `lambda x: x>0`

### choice_input
This function displays a list of possible choices and asks the user to select one of them.

`choices` is a list of `str`s. `enumeration` should be either `number` or `char`.

`number` will show the following:
>1) Option 1  
 2) Option 2  
 3) Option 3
 
but `char` will show:

>A) Option 1  
 B) Option 2  
 C) Option 3
 
`char` should only be used when there are less than 27 options (still a lot).

The prompt is shown after the options and before the user's input.

The function returns the **index** of the selected option.
