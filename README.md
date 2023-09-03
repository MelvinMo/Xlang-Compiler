# Xlang-Compiler

This is a compiler for the Xlang programming language, developed as the final project of my undergraduate compiler course.

## Overview

The Xlang compiler follows a typical compiler design, with the following phases:

- Lexical analysis - Using flex, this phase breaks the input code into tokens 
- Syntax analysis - Using bison, this phase parses the tokens and generates a syntax tree
- Semantic analysis - This phase performs semantic checking and builds a symbol table
- Intermediate code generation - The syntax tree is traversed to generate intermediate code
- Code optimization - The intermediate code is optimized to improve performance
- Code generation - The optimized intermediate code is translated to target assembly code

The compiler targets the MIPS R2000/R3000 architecture and can generate executable code on MIPS processors.

## Language Features

Xlang is an educational programming language with C/Pascal-like syntax. Key features include:

### Syntax
- Xlang syntax is similar to Pascal/C
- Code is organized into classes and methods
- Supports nested block structures using { }
- ; required to terminate statements

### Data Types

- Built-in types are integer and boolean
- Arrays are supported for these types
- No support for strings, floating point, etc.

### Variables

- Variables must be declared before use
- Local variables within methods
- Global variables at class scope
- Call-by-value parameter passing

### Expressions

- Arithmetic operators: +, -, *, /, %
- Logical operators: &&, ||, !
- Comparison operators: ==, !=, <, >, <=, >=

### Control Flow

- if-else conditional statements 
- for loops with 3 parts: init, check, increment
- break and continue keywords

### Functions

- Functions defined with return type
- void return for procedures
- Recursion is permitted
- Parameters passed by value

### Classes

- Single inheritance model
- Program entry point is main() method
- Fields and methods defined in class

### Comments 

- // indicates line comment
- /* */ delimits block comment

### Limitations

- No object-oriented features besides classes
- No strings, floats, chars, enums, structs
- Basic type checking but no full type safety
- Limited compile-time error checking
- Small subset of features compared to C or C++

## Implementation Details

### Lexical Analysis

- Input file is broken into a stream of tokens
- Each token has a type (keyword, identifier, operator etc.) and attribute value
- Regular expressions match token patterns
- Handling of comments, whitespace, preprocessor directives

### Syntax Analysis

- Context-free grammar defines allowable syntax
- Recursive descent parsing constructs syntax tree
- Syntax tree nodes reflect grammar productions 
- Tree represents program structure based on language grammar

### Semantic Analysis

- Check types of expressions and assignments
- Resolve variable references using symbol table
- Check function arguments and return types
- Detect undeclared and redefined identifiers
- Insert implicit type conversions where needed

### Intermediate Representation

- 3-address code with temporary variables 
- Static single assignment form for optimization
- Quadruples represent operations on variables
- Symbols refer to variables and constants

### Code Optimization

- Common subexpression elimination
- Copy propagation
- Dead code elimination
- Redundant load/store elimination
- Basic block optimizations

### Code Generation

- Tree traversal generates MIPS instructions
- Register allocation using graph coloring
- Peephole optimizations combine instructions
- Add directives for data/text segments
- Insert stack management instructions

> The information provided above is an English translation of the original project description, which was written in Persian. The original Persian project description PDF can be found in this repository, along with my YACC and Bison codes.
