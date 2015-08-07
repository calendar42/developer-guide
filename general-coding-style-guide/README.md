# General coding style guide

Language overarching style-guide

## Abstract rules

Some rules apply to all languages, although more strictly to some. 

1. Variable names should be clear and preferably short; if names need to be long to be clear, most likely the code should be moved to a more logical place,
2. Functions should be short and have a clear single purpose; this improves readability, reusability and reduces the need for extensive commentary,
3. Information should be stored in one and only one place (except for very specific purposes like caching), otherwise the information has to be kept in sync continuously to prevent invalid program states,
4. Variables, constants, attributes and the like should not be reused unless they have the same exact logical meaning, otherwise,  refactoring (when the differences become apparent) will be complicated and error prone,
5. Code should be modular and decoupled; different aspects of coding (business logic, logging, error handling, inter process communication, etc) should be separated as much as possible, 
6. Comments should explain the why of the code, not the what; the code itself is the what of the code.
