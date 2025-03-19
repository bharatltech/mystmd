# Introduction to functional programming, Lesson 1 :

## DATA AND DATATYPES IN GOFER, SIMPLE TYPES

<div style="border: 1px solid black; padding: 10px; width: fit-content;">
  Your content goes here.


 When you start the Gofer interpreter, the message that you see is like this:          
 Copyright (c) Mark P Jones 1991- 1994                                                 
 Copyright (c) Rusi Mody 1995- 2012                                                    
 Gofer session for:
 pustd.pre
 ?
 The Gofer interpreter is an expression evaluator: think of it as a kind of calculator.

 Mark Jones created the original language, Gofer, and its interpreter. That was 25 or 30 years ago.  

 Rusi Mody made changes to notation of the original language to make it suited for beginners.  

 Gofer stands for “good for equational reasoning”. You already know equational reasoning
 from middle school mathematics, so the basic concept will not be new to you. We will
 soon review this notion, and you will discover the computational power of what you already
 know. Before we get there, it will help to get some practice with Gofer and its interpreter.


 The current language standard for Gofer-style “purely functional programming” is Haskell.
 As Mody put it, “Haskell is **real**; Gofer is ideal.” Decades have passed by since Gofer was first
 designed, but the ideas it contains are up to date, or we could say that the ideas are timeless.
 The file pustd.pre is the “standard prelude” which contains quite a few predefined
 functions. Think of the predefined functions as “buttons on the calculator” that you can use to
 perform calculations. Soon, you will be able to write and use your own functions too.

 The “?” is called the *interpreter prompt*. If an expression that is consistent with Gofer syntax is
 entered after the prompt, the interpreter will evaluate its value, display it on the next line, and
 show the prompt on the following line. This activity is known as the “read-execute-print loop”,
 or REPL for short. If a syntactically incorrect expression is entered at the prompt, the
 interpreter attempts to find the syntax error, and print it out for the user to read and repair.

</div>


### KMIT

```
R&D Lab
28 - 12 - 2021
```

> Your content goes here You can add more lines of text here.



 Note: In these lessons, € is the symbol for an exercise that the student to perform, R is a remark that
the student is to understand, and W is the indication of a warning that the student is supposed to heed.

€: Enter the following expressions at the interpreter prompt, one at a time. Notice that the interpreter
does indeed evaluate these expressions. (Note that **True** and **False** start with a captial letter.)

```
2          2.1           False      'a'
2+2        2.1 + 3.2     2<3       ' 2 '
2*3 + 4    True          3<2        ' '
```
Notice that after the value of each expression, thie interpreter prints out its type, e.g., **“ 2 : Int”**. 
The colon symbol “ **:** ” is to be read as “of type”, thus the interpreter response **“True : Bool”** is
read as “**True** is of type **Bool**.” (**Bool** is short for Boolean, a data type contains just two values,
**True** or ****False****). The expressions we have entered so far are of the four “simple” types: **Int**
(integer), **Float** (floating-point, explained in a paragraph below), **Char** (character) and Bool.



Definitions: A simple data type is one that cannot be expressed as a composition of simpler types,
while a compound type is made out of simpler (simple or compound) types. Informally, a simple type
is like an atom, whereas a compound type is a molecule made out of several atoms.

R: You are familiar with numbers written using a decimal point, **e.g., 3.14159**. So why do programmers
call this type floating point? Consider the following interpreter interactions:

```
? 1. 23                 ? pi
1 .23 : Float           3.14159
? 123000.0              0.000123
123000.0 : Float        0.000123 : Float
? 1230000.0             ? 0.0000123
1.23e+006 : Float       1.23e-005 : Float
? 123000000000.0        ? 0.0000000123
1.23e+011 : Float        1.23e-008 : Float
```
**Notation:** When we want to write numbers having an exponent and a mantissa, **e.g., 1.23* 10⁻⁶** 

without superscripts, we write **1.23e+0 6**. Similarly, we write **1.23* 10-^6 as 1.23e-06**

R: Mathematicians would normally call type **Float** as **real**, but that usage is not correct, e.g., we are
denoting the value of **pi** correct to only 6 digits, whereas in the exact value of **pi** the number of digits
is unbounded. Such a representation of **real** numbers is called **“finite precision.”** (The number of
digits is about 6 for 32-bit computer architectures, and is about 16 for 64-bit computer architectures.)

R (Floating point): Type **Float** is short for floating-point because, when the magintude of a number
is sufficiently large (>= 10⁶ , approx) or sufficiently small (<=10⁻⁵, approx), the decimal point “floats”
to a position immediately after the most significant non-zero digit, see examples above.

€: Verify that the types of different expressions are printed out with a capital or upper-case letter. Thus
**Int**, **Float**, **Char**, **Bool**.

W: While typing the Boolean constants **True** or **False**, be sure that the first letter is upper-case.

€: You can see for yourself what happens if you use lower-case letters and enter **True** or **False**.

(**Remark**: Terms starting with a lower-case letter have a different significance: they are the names of
variables, e.g., **pi**. When the name **pi** is entered at the prompt, its value is returned (correct to 6 places )

€: Enter expressions like **2^5** and **2.0^5**, and verify that **^** is the exponentiation (power of) operator.

€: Enter expressions like **2^5.0** and **2.0^5.0**, and verify that while the mantissa can be **Int** or
**Float**, the exponent has to be **Int** only.

€: Enter the expressions **2+2 == 4 , 2+2 == 5 , 2 /= 3 , 2 /= 4** , **True** == **False**, **True** /= **False**.

Conclude that **==** and **/=** are Boolean-valued equality and inequality operators that return the
values **True** and **False** depending on the values of their operands.

€: Enter any expression like **2+2 = 4** , or even something as simple as **2=2**, and see what happens.

R: Recall that it made sense in school mathematics it made sense to write, **e.g., 2+2 = 4**. You will soon
find that in functional programming, the **"="** symbol means “equality by definition”, e.g., **pi** is given its
value with the equation **pi = 3.14159**. (We will postpone the details for a few more Lessons.)


€: Enter the expressions **False**&&**False**, **False**&&**True**, **False**||**True**, **True**||**True**, etc., and
observe their values. Conclude that && and || are the OR and AND operators for Boolean-valued operands.

R: Defnition $\underline {(Literal)}$: In  natural  language, to be literal is to understand words in their usual or most
basic sense. In programming, a  $\underline {literal}$ is a value written exactly as it is meant to be interpreted, e.g.,
100 , 1.00, 'a' or **True**. These are literals of type **Int**, **Float**, **Char** and **Bool**, respectively.

R: Literals are the simplest expressions, i.e., you cannot get any simpler expressions, but expressions
composed out of more than one literal are not themselves literals , **e.g., 2+2** is not a literal.

R: In mathematical logic, the words $\underline {value}$ and $\underline{meaning}$  are synonymous. Now we understand well
that the value of 2+2 is 4. We need to understand likewise that “the meaning of 2+2” is 4.

W: If we enter character sequences that do not amount to “syntactically well-formed expressions”,
the interpreter will give an error message. Initially, some error messages may sometimes appear
confusing, and not indicate explicitly and clearly what exactly the error is. With practice you will
learn to decipher these messages.

€: Try entering expressions that are grammatically not correct, like **2 * 3 * , .1. and 'a** and
see the error messages for yourself. If you enter a sequence of letters like xyz, the interpreter will
state **“ERROR: Undefined variable”**. If the sequence starts with an upper-case letter, the
interpreter will respond **“ERROR: Undefined constructor function”**. (We will study
constructor functions in later lessons.)

€ (Note carefully): Observe the error message when you type two sequences of letters with a blank space
in between, e.g., **abc def**. An explanation of this error message requires a few basic concepts, so it is
postponed. It is enough to note that the word “juxtaposed” means being next to each other: the interpreter
is stating that the letter sequences **abc** and **def** are juxtaposed (which is, apparently, an error).

€: For the interpreter to indicate the type of an expression, enter :**type** followed by the expression.
(Instead of :**type** you may enter just the first letter, i.e., **:t**, followed by the expression.) The
interpreter will first print out the entire expression (not its value) and then indicate its type.

€: Enter **:t** followed by some of the expressions above, and see how the interpreter responds.

€: Enter some characters in double quotes, like **"hello, world!"** , the interpreter will print back
these characters minus the enclosing quotes, but it will not say what the type is.

€: To explicitly ask for the type of a character sequence in double quotes, enter **:t "hello"**.
The interpreter will print out the characters along with the quotes, and indicate that the type is
**String**, i.e., a string of characters.

W: Take note that a string of characters is $\underline{not}$ a simple type. A single character, denoted in single
quotes, e.g., **'a' or ',' (comma) or ' ' (blank space)** is indeed a simple type.

€: Enter a pair of single quotes (with nothing in between), i.e., **''**, and note the error.

€: Enter a pair of double quotes with nothing in between, i.e., **""**, a string of length 0. What happens?

R: One reason that the interpreter normally does not print out the type of strings (in general, string-
valued expressions) is that in the course of its work, e.g., while printing error messages, the interpreter
has to print out strings. It is not a good practice to label such messages with their type, because doing
so will only distract the user.


€: Enter the string **error. "Invalid argument"** and see how the interpreter responds. It states
**Program error: Invalid argument**. An error message is being printed, indicating the kind of
error. (The message is a string, but we don’t want its type mentioned, because that would be confusing.)

€: Enter a string with arbitary characters within double quotes, e.g., **error. " ... "** and see how the
interpreter responds.

(It appears that these two strings above are syntactically correct expressions. A further explanation,
e.g., why does the interpreter respond in this way, is postponed till you write some programs.)

R: So far, whenever the interpreter displayed the value of an expression, its type was also invariably
displayed. (Type **String** is the exception.) This is the default style of displaying expression values,
but it is possible to avoid displaying the type for all expressions.

€: Enter the interpreter command :**set –t** , or simply use the first letter, thus :**s –t**. Then enter some
expressions, and verify that their correct value is displayed, but their type is not. (To view the type of an
expression, or its calculated value, we have already seen the use of the interpreter command :**type* or :**t**.)
Enter the command :set +t , or s +t, and verify that the type of an expression is displayed with its value.

€: Assume that with :**s -t**, type information is not being displayed along with values. Now enter these
expressions, one at a time: 2:**Int**, 2.1:**Float**, '2':**Char**, 2+2: **Int**, 2 .5^2: **Float**. Verify
that the interpreter accepts the type along with the input expression, but does not display it with its value.

€: Enter an incorrect type with an input expression, e.g., **2+2:Char**, and observe the interpreter response.

R: The expression 2 .1 + 2 makes perfect sense to us.
€: Try entering it in the interpreter. You will get an error message of a few lines.

ERROR: Type error in application
*** expression : 2.1 + 2
*** term : 2.
*** type : **Float**
*** does not match : **Int**

Let us parse the multiline error message, for this kind of message is going to recur again and again.
The message indicates that **2.1** is of type **Float, 2** is of type **Int**, and the two types do not
match. The conclusion is: we cannot add two numbers, of type **Int** and **Float**, respectively.
Either they have to be both **Float** or both **Int**.

€: Enter **2 + 2 .1** and notice how the error message is different from the one above.

€: Enter **2.0 + 2.1** and see the result for yourself. Also verify that the same rule applies for other
arithmetic operators, like -, * and /.

€: Enter the expressions **2 + 3 + 4 + 5.0** and **2.0 + 3.0 + 4.0 + 5** , and note the error messages.

€: Now enter the expression **2 * 3 / 4** and see the error. The expression appears ambiguous to the
interpreter. Next enter two expressions, **(2*3)/ 4** and **2 * (3/4)**. The first causes the * to happen
first, and the other that causes the division to happen first.

R: Verify that 6/4 has the value 1 and 3/4 is 0. We conclude that when the operands are integers,
the interpreter performs integer division, i.e., only the quotient is retained as the value of the division,
and the remainder is lost. There is no such ambiguity when the operands are floating point numbers,
e.g., **2.0 * 3.0 / 4.0**. But we still get the same warning, that there is ambiguous use of the /


operator. Just be sure to put parentheses in the right place when we use the division operator along
with the multiplication operator.

Definition (Conditional expression): A conditional expression is one whose value depends on a
Boolean-valued expression. Its syntax is as follows:

```
if < expression: Bool > then < expression1 > else < expression 2 >
```

Its value depends on the value of <expression:Bool>. If it is **True**, then the value of the
expression is <expression1>, otherwise it is <expression2>.
The tokens then <expression1> are called the then clause of the conditional expression, and
else <expression 2> is the else clause.

€: Try out these examples on your interpreter:

```
? if 2+2 == 4 then 'T' else 'F'
'T' : Char
? if x<100 then 10 else 20 where x = 0
10 : Int
```
€: Verify the workings of conditional expressions by evaluating these expressions (and make your own):

```
if **True** then 100 else 200 if False then 100 else 200
if 1<2 then 3 else 4 if 2+2==5 then 3 else 4.
```
Definition (Conditional expression): A conditional expression is one that takes one of two values,
depending on the value of a “condition”, i.e., a Boolean-valued expression. Its syntax is as follows:

```
if < expression: Bool > then < expression1 > else < expression 2 >
```

Its value depends on the value of <expression:Bool>. If it is **True**, then the value of the
expression is <expression1>, otherwise it is <expression2>.


The tokens then <expression 1> are called the then clause of the conditional expression, and
else <expression 2> is the else clause.

€: Try out these examples on your interpreter:

```
? if 2+2 == 4 then 'T' else 'F'
'T' : Char
? if x<100 then 10 else 20 where x = 0
10 : Int
```
€: Verify the workings of conditional expressions by evaluating these expressions (and make your own):

```
if **True** then 100 else 200 if False then 100 else 200
if 1<2 then 3 else 4 if 2+2==5 then 3 else 4.
```
R: It is mandatory that the if- and else-clauses of a conditional expression return values of the same type.

€: What happens if the following conditional expressions are entered into the interpreter?

```
if **True** then 100 else 100 .0 if 3<2 then 100 else 'a'
```
<See the next page for a summary of this Lesson>


What we learnt in this Lesson: 1. The gofer interpreter is an expression evaluator. 2. Expressions
always have type. The types we have seen so far are: Int, **Float**, **Bool**, **Char**, **String**. 3. The
type information provided with the value of an expression, or not provided, depending on whether we
give the interpreter command :s +t or :s -t. In our system, the former is the default. 4. The
type of expressions of type **String** is not indicated. 5. The type of an expression can be explicitly
asked, using the command :t followed by the expression. 6. ++ is the string concatenation
operator. 7. Binary arithmetic operators like + and * require both operators to be either Int or
**Float**. We cannot have one Int operand and another **Float** operand. 8. Use of / along with *
results in a perceived ambiguity. Parentheses are required to resolve it. 9. Conditional expressions
take one of two values, depending on the value of a condition (i.e., Boolean-valued expression).

```
 ⬧ 
```
```
IPMF Lesson 1: date 06- 06 - 2020 , revised 1- 07 - 2020 , 15- 12 - 2020 , 25 - 02 - 2021
```




# Introduction to functional programming, Lesson 2 :

## DATA AND DATATYPES IN GOFER, COMPOUND TYPES TUPLE AND LIST

In Lesson 1, the very first introduction to functional programming with Gofer, we were introduced to
four simple types: **Int, Float, Char and Bool**. Simple types are atomic, i.e., they cannot be
broken down into constituent data or types.

In Lesson 2 we consider compound data and their types. A compound datatype is made out of constituent
data (constituent means “part of a whole”) so it may be likened to a molecule that contains several atoms.

There are three compound types, denoted by the use of 1. parentheses ( and ), 2. brackets [ and ],
and 3. arrow - >. These datatypes are called tuple, list and function, respectively. As of now, we have
no information about the internal structure of these types, but we will be able to recognize values as
being of these types because of their distinguishing symbols ( and ), [ and ] and the arrow ->.
The present Lesson, Lesson 2, is on tuples and lists, while the next Lesson will address functions.

Summary of Lesson 2: Internal structure of the datatypes tuple and list; type errors in list (not possible
in tuples); empty list and empty tuple; type variables and the values they can take; tuples having tuple
components and list components; lists having tuple components or list components; the type of a tuple
consisting only of empty lists; the type of a list consisting only of empty lists; list expressions made by
using the ellipsis symbol " ... ", infinite lists, joining lists together; strings are simply lists of Char.

R (Revision): Recall that the notation “**<<val>val> : <<type>type>**” is read as “value **<<val>val>** is of type **<<type>type>** ” ,
e.g., “ 100 : **Int**” is read as “value **100** is of type **Int**”, i.e., symbol ":" is to be read as “is of type”.

R (Revision): Recall that after the interpreter prompt “?”, we are supposed to enter syntactically correct
Gofer expressions, so that the interpreter calculates and displays their values. Instead of saying “Enter **<<expr>expr>**
after the interpreter prompt,” our shorthand is to simply say, “? **<<expr>expr>**” See the example below:

##                                          TUPLES

€: Find out the significance of a sequence of values enclosed within parentheses “(” and “)”. Example:

**?(2+2, 2.0, '2', 2<2)**

From the interpreter response, observe the resulting value and its type.  
**(4, 2.0, '2', False) : (Int,Float,Char,Bool)**

Repeat: symbol ":" is to be read as “is of type.” , i.e., the colon ":" lies between the tuple and its type.

**Definition**: A tuple is a sequence of values enclosed in parentheses ( and ), with fixed length and
heterogeneous component types. (The term $\underline{heterogeneous}$ means diverse or different.) Thus, the
number of components in a tuple is $\underline{fixed}$, and each component type can be any legal Gofer type.

$\underline{Notation (repeat)}$: Values of type tuple, as well as the type itself, are denoted using parentheses ( and ).
From the response, note the manner in which a tuple $\underline{value}$, and the tuple $\underline{type}$ itself, are written.

In other words, take any comma-separated sequence of Gofer expressions and enclose them in
parentheses, and you have a tuple. Replace the expressions by their types, and you have the tuple type.

€: Enter the following tuples into the interpreter,  $\underline{one}$ $\underline{tuple}$ $\underline{at}$ $\underline{a}$ $\underline{time}$ , and note their values and types.

**(1,2.0,3,4.0) (' 1 ', 2 , 3.0) (1, 2.0,3, 4.0) ('a ', 'A’, 2)**

**(True, False) (2<2, 2==2, 2>2) ((1, 2),(1.0,2.0)) ((1,2,(1,2, '1')))**

R: Use your imagination and make up your own tuples. To save yourself the effort of typing the tuples above,
character-by-character, copy-paste each tuple into the interpreter. You can copy a string with ctrl-C, and paste it


in the interpreter with **right-click top border > Edit > Paste.**  
(This cut-paste operation has proved to be “tricky” for some students. $\underline{Tell}$  $\underline{me}$  $\underline{if}$  $\underline{there}$  $\underline{are}$ $\underline{problems}$ .)

R: The components of a tuple need not have only simple types.. They can themselves be compound
types. The only compound type we know as of now is tuple. Below, there are a few tuples some of whose
components are themselves tuples. You can make up your own tuples-within-tuples too.

€: Find out the values and types of the following tuples by entering them into the interpreter:

**(1,2,(3,4),5,6), (1,2.0, (3,(4,5.0)), '6'), (1,(2,(3,(4, '5'))))**

## LISTS

€: Find out the significance of a sequence of values enclosed within brackets “[**” and “**]”. Example:
**?[1, 10, 10*10]**

results in the response  
**[1, 10, 100] : [Int]**

R: Read **[Int]** as list _-_ **Int**, meaning “list of integers”.

$\underline{Definition}$: A list is a sequence of values enclosed in brackets [ and ], with zero or more components of
homogeneous type, (**Homogeneous** means “all of the same type”). A list with zero components is also
known as the empty list, written []. Because the type of such a list is unclear, we postpone discussing it.

*Please note*: Interpreter experiments are the way to learn a whole variety of facts about lists (and other datatypes).

€: Find out the value and type of:  
**?[ 'A', ' 1 ', '?']**

€: Find out the value and type of this list—it is just one list (the caret **"^"** is the exponentiation operator).  
**?[( 10 ^1, 1.0, 'a' ), ( 10 ^2, 2 .0, 'b'), ( 10 ^ 3 , 4 .0, 'c')]**

R: Note that values of type list, as well as the list type itself, are denoted using brackets [ and ].
Repeat: Observe the manner in which values of type list, and the list type itself, are written using [ and ].
Note that since all components of a list are of the same type, the list type contains just a single type name,
e.g., if a list consists of integers, the list type is **[Int]**, and its component type is **Int**.

€: Observe what happens when not all components in a list are of the same type, e.g., if we enter
**?[1, 2, 3, 4, 5.0]**

the interpreter response is  
ERROR: Type error in list  
*** expression : [1,2,3,4,5.0]  
*** term : 5.  
*** type : Float  
*** does not match : Int  

R: Since tuple components can be of any legal Gofer type, this kind of error cannot happen with tuples.

€: Enter the following lists into the interpreter and note their values and types.
Cut-paste the values below into the interpreter, one at a time, or make up your own lists.

**['a','A',' 1 ']     [(1, 2.0),(3, 4.0)]       [[1,2], [3,4,5,6],    [7,8] ]**

**['?',' ','=']       [('T', True),('F',False)] [[[1,2]],[[3,4]],     [[5,6]] ]**

**[False, False&&True, False||True, True]**


R (New operator): To join two lists together, use the concatenation or append operator, written as **"++"**

€: Enter the following expressions into the interpreter, and next, make up new expressions of your own.

**[0 ... 4] ++ [5, 4 ... 0] "abcd" ++ "1234" ['a' ... 'z'] ++ ['A' ... 'Z']**

**[0.0 ... 4 .0] ++ [5.0, 4 .0 ... 0 .0] [0 ... 4] ++ [] [] ++ [0 ... 4]**

**[0 ... 3 ] ++ [ 4 ... 6 ] ++ [ 7 , 6 ... 0] [0,10,100] ++ ['a', 'b', 'c']**

**Question:** What is the type of the empty list **[ ]**? Enter **[]** into the interpreter and note its response

**? []**  
**[] : [a]**

R: *Important remark*: The component type above, a, is not a specific or fixed type, but a $\underline{type}$ $\underline{variable}$.  
$\underline{A}$ $\underline{type}$ $\underline{variable}$ $\underline{can}$ $\underline{take}$ $\underline{on}$ $\underline{any}$ $\underline{type}$ $\underline{as}$ $\underline{its}$ $\underline{value}$. In any context, **a, b, c, d, ...** will be the names of
the type variables, e.g., if a context calls for three type variables, they will $\underline{always}$ be **a, b, c**.

*Important note*: For Gofer-like languages (dialects of Haskell, to be more precise), the “world of values”
and “the world of types” are $\underline{very}$ $\underline{different}$. In the world of values, an Int variable n can be bound to
any valid integer value, say **-10, 0 , 1000 , etc.,** whereas in the world of types, a type variable like a can
be bound to any valid type like **Int, Char, (Int,Float), [[Int]] , [(Int,Float)], etc.**

(It is possible that the notion of type variables will not be clear to you. Please wait till it becomes clear.)

€: Verify that in the ex pression **[[1, 2],[]]** the type of the empty list is **[Int]**, while in
**[['1', '2'],[]]** the empty list is of type **[Char]**. In **[[[1, 2]], [[3, 4]] []]** ,
the list is of type **[[[Int]]]**, so all its components, including the empty list, are of type **[[Int]]**.

**Question:** What is the type of a list of many empty lists, e.g., [[], [], [], []]?
(Recall that the components of a list have to be all of the same type.)

**? [ [],[],[],[] ]**  
**[[], [], [], []] : [[a]]**

R: The type of the first component is **[a]**, i.e., list of any type. but in a list, the type of all components
must be the same. Hence the type of all the remaining components is **[a]** , and therefore the type of the
entire list is list-list-a or **[[a]]**.

**Question:** What is the type of a tuple of 2 empty lists, or a tuple of 3 empty lists?

Nomenclature: A tuple with 2 components is a pair, and one with 3 components is a triple.

**? ([], [])**  
**([],[]) : ([a],[b])**  
**? ([], [],[])**  
**([],[],[]) : ([a],[b],[c])**  

**Explanation:** Recall that unlike the components of a list, the components of a tuple need not be the
same. For example, the first and the second components of the pair ([], []) are each lists of any
type, and moreover, their respective component types need not be the same. Therefore, if the first
compnent type is, by convention, the type variable a, the second component type can, in general, be


another type variable, call it b. The same logic applies to a triple of empty lists: their component
types are the type variables a, b and c.

R: If we can have an empty list [], how about the empty tuple ()? What is the type of the empty tuple?

**? ()**  
**() : ()**  
**? :t ()**  
**() : ()**  

In Gofer () is the 0-tuple. The value and its type are both called $\underline{unit}$, and are written ()in Gofer or Haskell.
The type () has exactly one value, namely, (). It signifies “nothing” or “no information.” In advanced
classes, we might have use for (), but not any time soon. (This information is given just for your curiosity :)

R: We can have a singleton list, but not a singleton tuple, because of the usual semantics of parentheses:

**? [ 100 ]**  
**[ 100 ] : [Int]**  

**? (100)**  
**100 : Int**  

R: (This remark is a very general idea) In mathematical logic, $\underline{value}$ and $\underline{meaning}$ are synonyms, i.e., they
mean one and the same thing. That is, the meaning of **2+2** is the same as the value of **2+2**.

R: If the value (or meaning) of the expression **2+2** is **4**, the meaning of the list expression **[0...4]** is

**? [0...4]**  
**[0,1,2,3,4] : [Int]**

€: Find out the values of the expressions **[ 4 ... 0 ]** and **[4,3... 0 ]**. Try them out on your computer.

**? [ 4 ... 0 ]**  
**[] : [Int]**

R: Here the upper bound of the list, i.e., 0 , is lower than the lower bound, 4. Only an empty list can satisfy
this constraint. If we want the integers 4 to 0 in decreasing order, then the way to write such a list is:

**? [4,3 ... 0 ]**  
**[4,3,2,1,0] : [Int]**

€: Find the values of the expressions  
**[0,2 ... 10] [10,8 ... 0] [0.0 ... 5.0]**  

**[0.0, 10.0 ... 50.0] [0.0, 0.5 ... 5.0] [0.0, 0.1 ... 1.0]**  

€: What do you think are the values of the expressions

**[0 ...] [0, 10 ...] [0.0 ... ] [0.0, 0.1 ... ]**

R: This is how you write infinite lists!

W: You can stop the interpreter with the keyboard interrupt ctrl-C. This works with Linux, but!
On Windows, be prepared for the machine to crash—you can restart Gofer (I think it is a software bug).

R: The computer performs not decimal arithmetic but binary arithmetic. When list elements increase
in steps of 0.1, you might see a numerical error creeping in, **e.g., 38.7999** in place of **38.8**.


R: In the previous Lesson we noted an exception to the explicit display of type information when
values of expressions are displayed. This exception is for strings (enclosed in double quotes) are
entered into the interpreter. The double quotes are not displayed either. Q: What is its type?

**? "Here is a string enclosed in double quotes"**
**Here is a string enclosed in double quotes**

R: Observe that no quotes have been placed around the string.

**? :t "Here is a string."**
**"Here is a string." : String**

R: At the very end of this Lesson, you can learn an important fact about Gofer.

Important fact: A string is simply a list of characters, so the type String is a synonym for [Char].

**? "abcd" == ['a','b','c','d']**
**True : Bool**

**? ['a' ... 'z']**
**abcdefghijklmnopqrstuvwxyz**


 ⬧ 


