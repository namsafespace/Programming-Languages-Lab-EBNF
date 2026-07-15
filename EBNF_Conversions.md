# EBNF Conversions
# Programming Language Grammar
### Original (BNF)
<program>     ::= "begin" <stmt_list> "end"
<stmt_list>    ::= <stmt> | <stmt> ";" <stmt_list>
<stmt>         ::= <var> "=" <expression>
<var>          ::= "A" | "B" | "C"
<expression>   ::= <var> "+" <var> | <var> "-" <var> | <var>
```

### EBNF
```ebnf
program    = "begin" stmt_list "end" ;
stmt_list  = stmt { ";" stmt } ;
stmt       = var "=" expression ;
var        = "A" | "B" | "C" ;
expression = var ( "+" | "-" ) var | var ;
``` 

 ### Original (BNF)
<assign>   ::= <id> "=" <expr>
<id>       ::= "A" | "B" | "C"
<expr>     ::= <id> "+" <expr> | <id> "*" <expr> | "(" <expr> ")" | <id>
```

### EBNF
assign = id "=" expr ;
id     = "A" | "B" | "C" ;
expr   = id "+" expr 
       | id "*" expr 
       | "(" expr ")" 
       | id ;


## Grammar For Chemical

### Original (BNF)
<Form>    ::= <Cmp> | <Cmp> <Ion>
<Cmp>     ::= <Term> | <Term> <Num> | <Cmp> <Cmp>
<Term>    ::= <Elem> | "(" <Cmp> ")"
<Elem>    ::= "H" | "He" | "Li" | "Be" | "B" | "C" | ...
<Ion>     ::= "+" | "-" | <IonNum> "+" | <IonNum> "-"
<IonNum>  ::= "2" | "3" | "4" | ...
<Num>     ::= "1" | <IonNum>
```

 ### EBNF
Form    = Cmp [ Ion ] ;
Cmp     = Term [ Num ] { Term [ Num ] } ;
Term    = Elem | "(" Cmp ")" ;
Elem    = "H" | "He" | "Li" | "Be" | "B" | "C" | ... ;
Ion     = [ IonNum ] ( "+" | "-" ) ;
IonNum  = "2" | "3" | "4" | ... ;
Num     = "1" | IonNum ;

## Grammar For Programming Language

### Original (BNF)
<BLOCK>      ::= <STMT> | "{" <STMTS> "}"
<STMTS>      ::= | <STMT> <STMTS>
<STMT>       ::= <EXPR> ";" 
               | "if" "(" <EXPR> ")" <BLOCK> 
               | "while" "(" <EXPR> ")" <BLOCK> 
               | "do" <BLOCK> "while" "(" <EXPR> ")" ";" 
               | <BLOCK>
               | ...
<EXPR>       ::= <identifier> 
               | <constant> 
               | <EXPR> "+" <EXPR> 
               | <EXPR> "-" <EXPR> 
               | <EXPR> "*" <EXPR>
               | ...
      
 ### EBNF
BLOCK      = STMT | "{" { STMT } "}" ;

STMT       = EXPR ";"
           | "if" "(" EXPR ")" BLOCK
           | "while" "(" EXPR ")" BLOCK
           | "do" BLOCK "while" "(" EXPR ")" ";"
           | BLOCK
           | ... ;

EXPR       = identifier
           | constant
           | EXPR "+" EXPR
           | EXPR "-" EXPR
           | EXPR "*" EXPR
           | ... ;