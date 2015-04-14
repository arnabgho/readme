CS335A: Compiler Design (Assignment 4: ASSEMBLY CODE GENERATOR)
===================================================================

* Source Language: *Python*
* Target Language: *MIPS Assembly*
* Implementation Language: *Python*
* Authors: Abhilash Kumar, Arnab Ghosh and Saurav Kumar

* Tool Used : PLY (Python Lex and Yacc)

### MIPS Assembly Code Representation
_____________________________________

1. Representation: ```opcode rd rs```

2. Operators:

	- ADD – Add (with overflow)
	- ADDI -- Add immediate (with overflow)
	- ADDIU -- Add immediate unsigned (no overflow)
	- ADDU -- Add unsigned (no overflow)
	- AND -- Bitwise and
	- ANDI -- Bitwise and immediate
	- BEQ -- Branch on equal
	- BGEZ -- Branch on greater than or equal to zero
	- BGTZ -- Branch on greater than zero
	- BLEZ -- Branch on less than or equal to zero
	- BLTZ -- Branch on less than zero
	- BNE -- Branch on not equal
	- DIV -- Divide
	- DIVU -- Divide unsigned
	- J -- Jump
	- JAL -- Jump and link
	- JR -- Jump register
	- LW -- Load word
	- MFHI -- Move from HI
	- MFLO -- Move from LO
	- MULT -- Multiply
	- NOOP -- no operation
	- OR -- Bitwise or
	- ORI -- Bitwise or immediate
	- SLL -- Shift left logical 
	- SUB -- Subtract
	- SW -- Store word
	- SYSCALL -- System call



### Running Instruction
_______________________
1. Run the makefile 
```
make
```
2. To run the IR Generator, pass the path of filename as argument.
```
bin/irgen test/<filename>.py
```

3. To clean the executables and other helper files, run make clean.
```
make clean
```

### Directory Structure
______________________________________________________
* bin:
	* converter.py [Python source file to convert the dump of parser into dot file: may be needed for debugging]
	* lex.py [Python source file from PLY for lexing]
	* lexer.py [Python source file to specify language lexemes]
	* irgen [Python dependent bytecode for parsing and semantic analysis]
	* parser.py [Python source file to specify grammar]
	* yacc.py [Python source file from PLY for parsing ]
	* symbolTable.py [Python source file with necessary functions related to symbol table]
	* tac.py [Python scource file with necessary functions related to Three Address Code Representation]
* src:
	* converter.py [Python source file to convert the dump of parser into dot file: may be needed for debugging]
	* lex.py [Python source file from PLY for lexing]
	* lexer.py [Python source file to specify language lexemes]
	* irgen [Python dependent bytecode for parsing and semantic analysis]
	* parser.py [Python source file to specify grammar]
	* yacc.py [Python source file from PLY for parsing ]
	* symbolTable.py [Python source file with necessary functions related to symbol table]
	* tac.py [Python scource file with necessary functions related to Three Address Code Representation]
* test:
	* 'filename'.py [Test files]
* .gitignore
* makefile [To move the source files to bin directory and compile bytecode for lexer and making it executable]
* readme.md

A Tutorial on the language features offered by the compiler 
----------------------------------------------------------------
----------------------------------------------------------------

The compiler supports the basic structures of the Programming languages such as assignment , operators , loops ans function calls.

*Note : Indentation is through tabs or spaces

Assignment 
____________________________
```
a = 10
b = 20
```
Operators
_______________________________________

```
a = 10
b = 20
print a
print b
c = a + b
print c
```
Relational & Logical Operators
_________________________________________
```
a = 4 > 3
if a == 1 :
  print 8
c = 3 > 4
if c == 0 :
  print 9
if a or c :
  print 10
if a and c :
  print 11
if a and c or a or c :
  print 12  
```
If Statement
___________________________
```
a = 10
if a == 10:
  print 1
else :
  print 2
```
For Statement
___________________________

Type 1
_______
```
a = [1, 2, 3, 9, 7, 3]
for i in a:
  c = i * i + 3 / 2
```
Type 2
____________
```
for var in [1,3,6,7]:
  print var*var
```

While Statement
_____________________________

```
a = 100
summ = 0
while a > 0:
  summ = summ + a
  a = a-1
print summ
```

Nested Looping
________________________

```

a = 100
summ = 0
while a > 0:
  b = 40
  while b >= 0:
    summ = summ +b
    b = b -1
    a = a - 2
  print summ

```


Function Without Parameters
______________________________________

```
def myfun():
  a = 10
  summ = 0
  while a > 0 :
    summ = summ + a
    a = a - 1
  print summ

myfun()
```

Function With Parameters
_________________________________

```

def myfun(c, d, e, f):
  a = 35
  b = a + c
  return c+d+e+f
a = myfun(1000, 100, 10, 1)
print a

```

Complex Assignment Statements
__________________________________

```
a = [0,1,2,3,4,5]
b = a[1] + a[a[a[0]]]
a[2] = a[ a[2] + 1 + b*1] 

```
Complex String Assignment
______________________________
```
	s = ["this",
"is",
"not",
"new",
"line"]
```

Binary , Octal & Hexadecimal
_________________________________

```
z = 0b101010
x = 0o325047324
y = 0x42BA34
print x,y,z
```

Continue Statement
__________________________

```
for i in [1,2,3]:
  if i == 2:
    continue
  else :
    i = 3
```

Complex recursive codes (8 Queens Problem)
____________________________

```
BOARD_SIZE = 8

def under_attack(col, queens):
  left = right = col

  for r, c in reversed(queens):
    left, right = left - 1, right + 1

    if c in (left, col, right):
      return True
  return False

def solve(n):
  if n == 0:
    return [[]]

  smaller_solutions = solve(n - 1)
  
  return [solution+[(n,i+1)]
  for i in xrange(BOARD_SIZE)
    for solution in smaller_solutions
      if not under_attack(i+1, solution)]


for answer in solve(BOARD_SIZE):
  print answer

```

