# Lexer and Parser

Project 2 CS112 University of San Francisco

Create a parser for the programming language SIMPLE. The language has only assignment statements with expressions containing only integers, variable identifiers and the (+) operator. The following program is valid for the language:
x23 = 18
y = x23+ 45  +2

The parser will consist of two major components: 
Lexer: identifies the words (tokens) in a file of text. 
Parser: Determines if a statement or statements is valid based on the expected structure of those statements, and displays an error if not.

Lexer
A Lexical Analyzer (or Lexer for short) performs the task of finding the tokens in a large set of text.
A token is a sequence of characters that have a collective meaning-- for an English sentence, words are tokens. For the SIMPLE coding language, there are a number of token types, including identifiers, “=” and “+” operators, and integers.
For instance, given the text “x23=32”, a Lexer would identify three tokens: an identifier, an assignment operator, and an integer.

Your Lexer will take a text file as input and create and display a list of the tokens  contained in the file. The Lexer will identify the following token types:
Identifier: starts with a letter followed by 0 or more letters and digits.
Integer: a sequence of digits
AssignOp: a single ‘=’
PlusOp: a single ‘+’
UnknownOp: e.g., ‘$’
EndOfFile: for every file, the last token generated by the Lexer will be this one.

If your Lexer was provided the file:
aa=34
bb=45+6

It will generate the following Tokens: 
Token Type 	Token Value
Identifier         aa
AssignOp        =
Integer           34
Identifier         bb
AssignOp       =
Integer           45
PlusOp           +
Integer            6
EndOfFile        -
Lexer: Java Specifications


Parser
The Parser’s job is to determine if a given code file is syntactically correct and report either “valid program” or a particular error message. For instance, the code:
x12=17+43
a = x12+35+1
is syntactically correct for the SIMPLE language so the parser should report, “valid program”. The code:
17=x+3
is not valid and the parser should report, “Expecting Identifier on line 1”.

The Parser should find and report the following errors:
Expecting identifier
Expecting assignment operator
Expecting identifier or integer
Expecting identifier or add operator
Identifier not defined
The Parser should not access the input stream directly, but should instead create a Lexer and call getAllTokens, then loop through those tokens.
Use a recursive descent parsing scheme: define a method ParseX method for each particular “part of speech”. For example, parseAssignOp will be called when you are expecting a token of type “AssignOp”.

Symbol Table
A symbol table tracks the identifiers within a program. When an identifier appears on the left-hand-side of an assignment statement, add it to the symbol table. When an identifier appears on the right-hand-side of an assignment statement, check the symbol table to see if the identifier has been defined (it is an error if not).

