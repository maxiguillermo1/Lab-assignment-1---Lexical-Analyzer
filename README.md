# Lexical-Analizer: Understand how to create your programming Language

# Concept Introduction 💻

A computer program is written in a language that humans can understand. But for a computer to understand and run the program, it needs to convert the human-readable code into a format that it can process.

The first step in this conversion process is to break down the code into small pieces called tokens. Each token represents a meaningful element of the code, such as a variable name, a number, or an operator (like + or -).

Example:

```bash
Consider the following example of an assignment statement:

result = oldsum – value / 100;

Following are the tokens and lexemes of this statement:

| Token       | Lexeme  |
|-------------|---------|
| IDENT       | result  |
| ASSIGN_OP   | =       |
| IDENT       | oldsum  |
| SUB_OP      | -       |
| IDENT       | value   |
| DIV_OP      | /       |
| INT_LIT     | 100     |
| SEMICOLON   | ;       |
```

# Procedure of the Lexical Analyzer

Let's take the assignment statement from the example:

result = oldsum - value / 100;

Now, let's look at each part of this statement and identify the tokens and their corresponding lexemes (the actual written code that represents a token):

    IDENT - This stands for "identifier," which is a name given to something in the code, like a variable or a function. In this case, "result," "oldsum," and "value" are identifiers. They are names for places in the computer's memory where values can be stored.

    ASSIGN_OP - This is the assignment operator, represented by the "=" sign. It's used to assign the value of whatever is on the right side of the "=" to the variable on the left side.

    SUB_OP - This is the subtraction operator, represented by the "-" sign. It tells the computer to subtract one number from another.

    DIV_OP - This is the division operator, represented by the "/" sign. It tells the computer to divide one number by another.

    INT_LIT - This stands for "integer literal," which is a type of data that represents whole numbers. Here, "100" is an integer literal.

    SEMICOLON - This is a punctuation mark in programming that represents the end of a statement, just like a period ends a sentence in English.

So, in the statement, the computer will recognize each variable (result, oldsum, value), each operation (=, -, /), the number (100), and the end of the statement (;) as separate tokens. It's like breaking a sentence into words to understand the meaning of each word separately.

# Overview

Lexical Analyzers: These are programs or subprograms that process the code written by programmers. They read the code character by character to identify meaningful elements called tokens (like variable names, numbers, or operators).

Lexemes: These are the actual strings of characters in the code that match a particular pattern that the lexical analyzer recognizes as a token.

Tokens: These are categorized patterns that lexemes match. Each token represents a type of component in the code (like a keyword, identifier, number, etc.).

Lexical Analysis Process:

    The lexical analyzer skips over parts of the code that aren't relevant to understanding the structure, like comments and white space (spaces, tabs, new lines).
    It builds a symbol table, which is a data structure that stores information about identifiers (like variable names).
    It detects and reports errors in the use of the programming language.

# Transition Diagram - State Diagram

<img src="https://i.imgur.com/wYXi8Rn.png" alt="MLH-banner" width="80%" height="600px">

Simplifying the Transition Diagram: Instead of having a different state for each possible character that could start a name or an integer literal, the diagram uses character classes like LETTER and DIGIT to simplify transitions.

    LETTER: Represents all letters (uppercase and lowercase). A name can start with any letter, so there's a single transition from the start for any letter.
    DIGIT: Represents all digits (0-9). An integer literal can start with any digit, so there's a single transition from the start for any digit.

Utility Subprograms:

    getChar: Reads the next character from the input and determines its class (LETTER, DIGIT, etc.).
    addChar: Adds a character to the current lexeme being built.
    getNonBlank: Skips over any white space to find the start of the next lexeme.
    lookup: Determines the token code for single-character tokens.

State Diagram Explained:

    The state diagram begins at a "Start" state.
    When it reads a LETTER, it transitions to an "id" state, potentially adding characters to a lexeme and getting the next character.
    If the next characters are LETTERs or DIGITs, it stays in the "id" state, building up an identifier (like a variable name).
    If it reads a DIGIT at the start, it transitions to an "int" state, potentially adding characters to a lexeme and getting the next character.
    If it keeps reading DIGITs, it stays in the "int" state, building up an integer literal (like the number 100).
    If an unknown character is encountered after a known token pattern, it transitions to a "done" state and returns the token.


# C-Program Overview and Functionality

The folder contains  a text file with the following strings to test the program:

(sum + 47) / total
oldsum - value /100

Output:

Next token is: 25, Next lexeme is (

Next token is: 11, Next lexeme is sum

Next token is: 21, Next lexeme is +

Next token is: 10, Next lexeme is 47

Next token is: 26, Next lexeme is )

Next token is: 24, Next lexeme is /

Next token is: 11, Next lexeme is total

Next token is: 11, Next lexeme is oldsum

Next token is: 22, Next lexeme is -

Next token is: 11, Next lexeme is value

Next token is: 24, Next lexeme is /

Next token is: 10, Next lexeme is 100

Next token is: -1, Next lexeme is EOF

# How to Compile and Run the program

