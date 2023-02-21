# Command-line argument conventions

```
Code: conv/cli-args
Version: 1.0.0
Author: Muthu Kumar <muthukumar@thefeathers.in>
Org: Feathers Studio
```

## Introduction

The POSIX standard is often cited when designing command line interfaces. However, the most recent version published as IEEE Std 1003.1-2017 (also published as [The Open Group Base Specifications](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap12.html)) still falls woefully short of modern requirements. The [GNU extensions](https://www.gnu.org/software/libc/manual/html_node/Argument-Syntax.html) to POSIX are the most widely used. However, there is still room for disambiguation. This specification addresses them.

## Specification

A command MAY accept sub-commands, options, and operands.

##### Note: This specification is available as a [formal grammar](#formal-grammar), or as a [railroad diagram](./assets/cli-railroad/index.md).

### Sub-commands

-   A sub-command is a part of the command that acts as a command by itself. In other words, a sub-command is a recursive command.
-   Commands (or sub-commands) with sub-commands MUST NOT accept operands. They MAY accept options.
-   Any arguments after a sub-command MUST be accepted literally without parsing, even if they start with `-`, `--`, or `=`. They MUST be parsed by the sub-command's own arg parser, following this specification.

### Options

-   Options are arguments that MAY modify the behaviour of the command.
-   Options MAY be supplied in any order.

#### Boolean options

-   Boolean options MUST NOT accept any value. They are boolean in nature and their presence MUST be inferred as true.
-   Boolean options MAY be referred to as "flags".

#### Non-boolean options

-   A non-boolean option MUST accept a single value. An option MAY be repeated several times to pass multiple values.
-   A non-boolean option MUST be separated from their value by a space or "=".

#### Long-form options

-   Every option MUST have a long-form. This is denoted by the delimiter `--` followed by the option name without spaces.
-   Long-form options MUST be at least two characters, and consist of alphanumeric characters, `-`, or `_`.
-   Long-form options MUST begin with an alphanumeric character.

#### Short-form options

-   Options MAY have a short-form. This is denoted by the delimiter `-` and MUST be followed by a single alphanumeric character.
-   Every short-form option MUST correspond to a long-form option. The inverse is not required.

### Operands

-   Operands are any values passed as input to the utility for its primary function.
-   Operands MUST be passed after all options.

### Strict-mode

-   "Strict-mode" MAY be specified by the application developer via the parser library or their own implementation of this specification.
-   "Strict-mode" MAY be specified by the application user via the environment variable `ARG_PARSER_STRICT_MODE`.
-   In "strict-mode", non-boolean options MUST be separated from their value by "=" only.

### Special-cases

-   Any arguments after the delimiter `--` followed by space MUST be accepted literally without parsing, even if they start with `-`, `--`, or `=`.
-   A single `-` MUST be interpreted as a regular operand. By convention, this MAY represent input from or output to the standard input/output streams.

## Formal Grammar

```C
Command ::= CmdIdentifier
Command ::= CmdIdentifier Operand*
Command ::= CmdIdentifier Option* Operand*
Command ::= CmdIdentifier Command*
Command ::= CmdIdentifier Option* Command*
CmdIdentifier ::= AlphanumericAnd*
Option ::= ShortOption | LongOption
ShortOption ::= ShortFlagOption | ShortValueOption
LongOption ::= LongFlagOption | LongValueOption
ShortFlagOption ::= '-' Alphanumeric
ShortValueOption ::= '-' Alphanumeric OptionValueDelimiter Value
LongFlagOption ::= '--' Alphanumeric AlphanumericAnd*
LongValueOption ::= '--' Alphanumeric AlphanumericAnd* OptionValueDelimiter Value
OptionValueDelimiter ::= Space | '='
Alphanumeric ::= [0-9a-zA-Z]
AlphanumericAnd ::= [0-9a-zA-Z-_]
Value ::= Char* | '"' ( Char | Space )* '"'
Char ::= ( UnicodeExceptDoubleQuotes | '\"' )
Space ::= ( U+0020 )*
Operand ::= Value
```

This grammar is also available as a [railroad diagram](./assets/cli-railroad/index.md).
