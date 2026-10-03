# About
This repository is a RTL logic synthesis tool written in Golang that translate
Verilog (or SystemVerilog) into a gate-level netlist. The scope for this is to
build a Minimum Viable Produc (MVP) that can do the following:
* Parse a Verilog file (or multiple files) and turn it into a structure that
can be processed effectively in Golang.
* Elaborate the design structure into a data structure that can be optimized.
* Optimize the design.
* Map optimized design into a few custom primitive gates (AND and XOR).
* Generate the final netlist from the optimized and mapped design.

# Recommended workspace structure:

```
src/
├── main.go          # CLI driver, top-level synthesis pipeline
├── parser/          # Lexer, parser, and AST node definitions
├── netlist/         # Graph nodes (Cell, Net, Module, Design)
└── passes/          # Independent processing steps (Elaboration, Mapping)
```

# Plan
## Phase 1: Parse Verilog
Writing a Verilog parser that satisfies IEEE standard compliance is very time
consuming. A recommended approach to a hobby project is to implement a
Hand-Written Lexer paired with a Recursive Descent Parser.

### Lexer (Tokenization)
The lexter reads the raw Verilog string character by character and groups them
into meaningful chunks called Tokens. First, define the token types using Go's
constant `iota` (enumeration).

```
package parser

type TokenType int

const (
	TokenError TokenType = iota
	TokenEOF
	
	// Keywords
	TokenModule
	TokenEndModule
	TokenInput
	TokenOutput
	TokenWire
	TokenAssign
	
	// Literals & Identifiers
	TokenIdentifier // e.g., "clk", "u_submodule"
	TokenNumber     // e.g., "1'b1", "8"
	
	// Operators & Symbols
	TokenAssignOp   // =
	TokenSemicolon  // ;
	TokenComma      // ,
	TokenDot        // .
	TokenLParen     // (
	TokenRParen     // )
	TokenAnd        // &
	TokenOr         // |
	TokenXor        // ^
	TokenNot        // ~
)
```
```
```

