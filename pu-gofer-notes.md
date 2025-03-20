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



# Introduction to functional programming, Lesson 3 :

## DATA AND DATATYPES IN GOFER: COMPOUND TYPE FUNCTION

Compared to tuples and lists, the third compound data type, function, initially appears to be counter-intuitive
as a data type, i.e., as a type of data. But functions are so important, so central, that they give rise to the term
“functional programing,” the style of programming and problem-solving that we are learning. First we learn
how to use already built-in functions, and at the end we note how the user can define quite-simple functions.

$\underline{Lesson}$ $\underline{3}$ $\underline{Summary}$: What is a function, type of a function vs value of a function, how to denote the type
of a function. Applying a function to its argument (i.e., evaluating a function for a given argument), implicit
vs explicit (i.e., invisible vs visible) function application operator. Built-in functions for tuples and lists.
What is a first class type, functions as first class types. Standard and non-standard notation in Gofer.

<div style="border: 1px solid black; padding: 10px; width: fit-content;">
               <b>Preliminary: What is a function?</b> </br>
The basic concepts are explained from first principles, to clarify them for learners who do not know them.
Definition: A function f: A -> B is a mapping from set A to set B such that for each element x in A,
there is a unique element y in B to which x is mapped (i.e., with which x is associated).
Example: square: Int->Int , square(x) = x*x. (We will not be using this notation, however.)
(R: The term "function" was introduced by Leibniz (1646-1716), and the idea was further formalized by
Euler (1707-1783), who introduced the commonly used notation for a function, y = f(x). )

Notation is important, e.g., the differential calculus was independently invented, or discovered, about
350 years ago, a few years before 1700 CE, by Leibniz and Newton (1643-1727). They used different
notations to express the same basic concepts, and as a result their work proceeded in quite different ways.
Our Gofer interpreter uses a non-standard notation, to make learning easy for beginners.
In mathematics notation, we write, e.g., f: A -> B, and read it as “a function named f, from
domain A to range B.” In functional programming, we think in terms of domain type and range type.

It is postulated (i.e., assumed for purposes of reasoning) that functions are a compound data type, and that
their type is fully determined by their domain type and range type. Note how a function’s type is written.
Given that cos or cosine is a built-in function of Gofer, we can query about its type with the command :t
? :t cos
cos : Float -> Float
Read the words cos : Float -> Float as “the function cos is of type Float to Float.”
If a function f is from any type to any other type, we use type variables a and b, so write f: a - > b

The mathematical concept of a function emerged in the 17th century in connection with the development
of the differential calculus; e.g., the slope of a graph at a point was regarded as a function of the
x-coordinate of the point. Mathematicians of the 18th century typically regarded a function as being
defined by an analytic expression (“formula”). Theoretical developments in the 19th century led to the
much more general modern concept of a function as a single-valued mapping from one set to another.
(Remark: It appears that Indian mathematicians had discovered these basic concepts much earlier—but
that story is for another day. Just now our focus is on the conventional approach and notation.)

</div>

R: When I enter 2+2 into the interpreter, its response is to give me its value, 4. If the expression is the list
**[0 ... 10 ]**, the interpreter prints all the list elements. If the expression is the infinite list **[0 ...]**
the interpreter attempts to print all the list elements. But even in the best case, it would not be possible to



similarly give a complete description of a function if the domain type is Float. The convention with Gofer
is that when asked for the value of a function, the interpreter merely prints out its name and type.

**? cos**  
**cos : Float -> Float**  

**Repeat**: The type of a function is fully determined by its domain type and range type. Thus all functions of
**type Float - > Float (e.g., sin, cos and tan)**, and in general of type **a - > b**, are of the same type.

**Question**: How to evaluate a function for a given argument value, **e.g., cos at π = 3.14159?**
It is important to take note of a distinguishing feature of the notation used in our version of Gofer.

**? pi**  
**3.14159 : Float**  
**? cos pi**  
**ERROR: Juxtaposition has no meaning. Use.**  
**? cos(pi)**  
**ERROR: Juxtaposition has no meaning. Use.**  

*Juxtaposition* means being side by side. The function cos and its argument **pi** are next to each other.
In our version of Gofer, that is not permitted. In the error message above, the first "." is a full stop,
while the second ".", as seen in **“Use** .” stands for something else: *the function application operator*.

**Remark**: Sometimes we will $\underline{pretend}$ that Gofer doesn’t like tokens to be juxtaposed, i.e, to be side by side, or
next to each other. (By tokens I mean function names, argument names or values, etc.) Instead, Gofer wants
these things to be nicely separated from one another by the "." symbol. For example, if I want to select the
first 10 elements out of a longer list like **[0 ... 100]** (it could even be an infinite list), then I will write
**take. 10. [0 ... 100]**, and if I want to drop the first 10 elements and take the next 5 , then I will
write **take. 5. (drop. 10. [0 ... 100])**. The dot symbol, the explicit separator between the
various tokens, does not change the apparent meaning. We can try this out in the interpreter.

€: Enter or cut-paste the two expressions above into the Gofer interpreter, and see what their values are.

R: The "." symbol is not just a convenient separator, $\underline{but}$ $\underline{a}$ $\underline{fundamental}$ $\underline{operator}$ $\underline{in}$ $\underline{functional}$ $\underline{programming}$.
I cannot overemphasise the importance of this operator—it is on the same level as the equality symbol "=".

Nomenclature: In functional programming, a function is $\underline{applied}$ $\underline{to}$ $\underline{its}$ $\underline{argument}$,” e.g., **cos** is applied to **pi**.

In conventional functional programming, **cos pi** or **cos(pi)** is syntactically correct, but not in our
version of Gofer. We have an explicit function application operator, denoted by the symbol "." or dot.
Conventionally, the application operator is implicit or invisible, but in our notation it is visible.

R: An important aspect of our learning is that when we read functional programming books and programs,
the invisible application operator has to “leap out of the page” and become visible to you, the reader. Your
seniors will tell you that yes, this has actually happened to them—the invisible operator becomes visible.

Below, there are some examples of builtin functions and their applications to appropriate arguments.

**? not**  
**not : Bool -> Bool**  
**? (not. True, not. False)**  
**(False,True) : (Bool,Bool)**  

**? even**  
**even : Int -> Bool**  
**? (even. 3, even. 4)**  
**(False,True) : (Bool,Bool)**  


**Recall:** We can explicitly query the type of an expression, using the :type interpreter command
(short form :t). Then, the value of the expression is not printed, but just the expression and its type.

**? :t odd**  
**odd : Int -> Bool**  
**? (odd. 3, odd. 4)**  
**(True,False) : (Bool,Bool)**  
**? :t (odd. 3, odd. 4)**  
**(odd.3,odd.4) : (Bool,Bool)**  

One of the most commonly used built-in function is the **length** function. Given a list of any
component type, the **length** function gives its length. (Recall that the type variable a can match any
valid Gofer type, so **[a]** is a list with any component type.)

**? :t length -- length of any list**  
**length : [a] -> Int**  

**? length. ['a' ... 'z']**  
**26 : Int**  
**? length. [0 ... 100]**  
**101 : Int**  
**? (length. ['a' ... 'z'], length. [0 ... 100])**  
**(26,101) : (Int,Int)**  
**length. [0, 2 ... 1000]**  
**501 : Int**  
**? ['a', 'c' ... 'z']**  
**acegikmoqsuwy**  
**? length. ['a', 'c' ... 'z']**  
**13 : Int**

R: When we enter builtin function names, sometimes we see their internal representations.

**? length**  
**foldl'.v64.0 : [a] -> Int**  
**? odd**  
**even ; not : Int -> Bool**  

R: You know that odd means “not even”, but you may not understand the use above of semi-colon ; ,
and likewise, of **foldl'**. If it is function type you are interested in, then a query with :t suffices.

**? :t length**  
**length : [a] -> Int**  
**? :t odd**  
**odd : Int - > Bool**  

**Fact**: A function, since it is a valid Gofer type, can be the component type of a list or a tuple, e.g., `

**? [sin, cos, tan]**  
**[sin, cos, tan] : [Float -> Float]**  
**? ((1, even), (1.0, not))**  
**((1,even),(1.0,not)) : ((Int, Int -> Bool),(Float, Bool -> Bool))**


**The Gofer Prelude contains all the builtin functions**

The standard prelude pustd.pre that we use contains the definitions of all builtin functions.
These functions are loaded into the Gofer interpreter whenever it starts executing. There are Gofer
preludes other than the standard one, e.g., the simple prelude pustd.simple.


**Builtin functions for compound data type tuple**

There are builtin functions to select individual components of pairs and triples:
```
? fst                                   ? fst
fst : (a,b) -> a                        fst3 : (a,b,c) -> a
? snd                                   ? snd
snd : (a,b) -> b                        snd3 : (a,b,c) -> b
? fst. (1, 10.0)                        ? thd
1 : Int                                 thd3 : (a,b,c) -> c
? snd. (1, 10.0)                        ? fst3. (1, 10.0, 'A')
10.0 : Float                            1 : Int`
? (snd.(1.0, 10), fst.(1.0, 10))        ? snd3. (1, 10.0, 'A')
(10,1.0) : (Int,Float)                  10.0 : Float
                                        ? thd3. (1, 10.0, 'A') 
                                        'A' : Char
```
**Builtin functions for compound data type list**

Functions head and tail, along with function length, are the most relevant functions for lists.
Function head gives the first element of a non-empty list, and function tail gives the remaining elements.
```
? head?                   tail. (tail. [0...5])
head : [a] -> a           [2, 3, 4, 5] : [Int]
? head. [0...5]           ? tail. (tail. (tail. [0...5]))
0 : Int                   [3, 4, 5] : [Int]
? tail. [0...5]           ? head. [0]
[1, 2, 3, 4, 5] : [Int]   0 : Int
? head. (tail. [0...5])   ? tail. [0]
1 : Int                   [] : [Int]

```
R: Asking for the head or tail of a non-empty list results in an error.
```
? head. []?                  tail. []

Program error: {head.[]}     Program error: {tail.[]}
```
R: Comparable to the **head** and **tail** functions are the **init** and **last** functions:

```
? init
init : [a] -> [a]
? last
last : [a] -> a
? init. [0 ... 5]
[0, 1, 2, 3, 4] : [Int]
? last. [0 ... 5]
5 : Int
? init. (init. [0 ... 5])
[0, 1, 2, 3] : [Int]
? last. (init. [0 ... 5])
4 : Int
```

**Functions as a first class type**

Definition: A *first class* type is one that can be used anywhere that other types are used, especially, if the
type can be passed as an argument to a function or returned as the result of applying a function to its
argument, i.e., if the type can be the domain type or range type of a function.


R: This terminology is derived directly from the notion of a first class citizen, i.e., a citizen that has all
the rights, privileges and duties that other citizens have.

R: Functions are a first class type. In general, the type of a function is **a - > b** (where **a** and **b** are type
variables). Now the domain type and range type can themselves be function types, i.e., **a** and **b** can be
bound to function types, e.g., **(Float - > Float) - > (Int->Bool)** can be a valid function type.
(What such a function achieves, is not the issue just now. We will see many such functions in later Lessons.)

# FUNCTION DEFINITION

In this Lesson, we spent much time on function application, i.e., function evaluation. However, we
have not spent any time on the dual operation, namely, function definition. Here, we make a brief
mention only, because we need more preparation on the student’s part before we take it up in detail.

A function definition consists of two parts: the type definition (or signature) and the function body.

Function definitions are made within a Gofer script (file extension **.gs**), and the script is saved for
later use. When the functions are to be used (applied to arguments, etc.), the script is loaded into the
Gofer interpreter using the **:load** or **:l** command.

```
succ: Int-> Int        dbl: Int-> Int    sq: Int-> Int
succ. n = n+1          dbl. n = n+n      sq. n = n*n
```

R: Once the functions are loaded into the interpreter, they can be used just like built-in functions.

Terminology: Functions are applied to their arguments. To distinguish between function definitions and
function application, the usage is “parameter of the definition” and “argument of the call.” Thus, in the
three definitions, n is the parameter, while in the three sets of applications, the integers are the arguments.
The first and foremost step of a function application is parameter-argument matching.

Caution (repeat): When you store a script with a new or changed name, say **newscr.gs**, take two precautions
under MS-Windows: (1) put double quotes around the name, like "**newscr.gs**", otherwise **newscr.gs** will
be the name and **.txt**, the file extension, and so the full file name will be **newscr.gs.txt**, and (2) store
the file in the same directory as the Gofer interpreter. If you don’t take these two precautions, you will get an
error message like **ERROR "newscr.gs": Unable to open file.**

R: Function composition means, apply functions, one after the other, to an original argument. There
is a function composition operator in Gofer, symbol semicolon or ";", see below on this page.

Interpreter interactions after the functions succ, dbl and sq are loaded into it:  

```
? succ.10
11 : Int                         Note the the function composition operator ";"
? dbl.10                         (f ; g).a means
20 : Int                         First apply f to a, thus f.a
? sq.10                          Then apply g to the result, thus g.(f.a)
100 : Int
? dbl. (sq. 10)                  ? (sq ; dbl).
200 : Int                        200 : Int
? succ. (dbl. (sq.10))           ? (sq ; dbl ; succ). 10
201 : Int                        201 : Int
```
_Date and time:_ 03 - 01 - 2020 1 1 : 10 , modified 12- 06 - 2020 , 15 - 07 - 2020 and 4- 1 - 2021



# Introduction to functional programming, Lesson 3 , Part 2:

## DATA AND DATATYPES IN GOFER, STANDARD AND NON-STANDARD NOTATION

The programming style known as functional programming is based on the lambda calculus, a formal
system of rules for defining and evaluating functions. This calculus has two operators, namely,
abstraction (for defining functions) and application (for evaluating functions, given their arguments).
We has seen examples of function application above. We will consider function abstraction in later lessons.

Functional programming almost always employs a typed lambda calculus, i.e., each value has type.
A consequence is that for type correctness, when a function is applied to an argument, the argument
type has to match the function’s domain type.

The Gofer interpreter evaluates well-formed expressions (lambda expressions, to be exact). We can
override this functionality by issuing “interpreter commands.” This is done by entering a line starting
with a colon “:” (that treats the subsequent string not as an expression but an interpreter command).
Following the colon “:” is the command name, e.g., load, reload, type, set. For succinctness,
it suffices to enter the first character of the command, thus :l, :r, :t, :s. Above, we saw the use of
:type and :set -t. Here we investigate the use of :set and its arguments t and S (uppercase-s).

Note: Every value has a type. Type information, given by the interpreter after a value is displayed, is
optional. The command :set –t causes the type information to be not displayed, while :set +t (the
default setting) causes type information to be displayed. See the interpreter responses below.

```
? 2+
4 : Int
? [0...4]
[0, 1, 2, 3, 4] : [Int]

? :set -t
? 2+
4
? [0...4]
[0, 1, 2, 3, 4]

? :s +t
? 2+
4 : Int
? [0...4]
[0, 1, 2, 3, 4] : [Int]
```

R: With our settings of the Gofer interpreter, by default the type of an expression is displayed along
with its value. In some circumstances you may not want to see the type. In that case, use **:s –t**.


Significance of the explicit function application operator

As mentioned above, function application, along with function abstraction (i.e., definition) are the basic
operations of the lambda calculus. Indeed, the lambda calculus gets its name because the Greek letter
lambda λ was used by the discoverers/inventors of this calculus to denote function abstraction.
But function application has no visible operator, so if we juxtapose two syntactically correct expressions,
i.e., write them next to each other, say **expr1 expr2**, the interpretation in the calculus is that expr1 is a
function, expr2 is its argument, and expr1 is applied to **expr2**.

In hindsight, it does not appear to be a good idea that blank space (or several spaces) denotes function
application. Our method is to write **expr1. expr2**. For beginners especially, the presence of an


explicit, i.e., visible, operator is helpful—seeing the dot “.” indicates which function-valued expression
is being applied to which argument. (For starters, it is essential that the argument be type-correct, i.e.,
its type should match the domain type of the function.) There are some advantages of an invisible
operator, but we are not in a position just now to understand and appreciate them. The use of the dot
operator for function application is non-standard notation (explained below in Part 2 of this Lesson.)

Note that functions are “first class” types in functional programming, by which we mean that that
they can be used wherever other data types, simple or compound, can be used. (First class types in
functional programming are like first class citizens in civic society: a first class citizen has all the
rights and privileges that other citizens have. Not all programming languages have functions as first
class types, e.g., C language does not.)


**Standard and non-standard notation with Haskell-style programming:**

We have already seen above the function application operator, dot or ".". It is important to note that
this is nonstandard notation in Haskell-like languages. There are some other changes in notation also:.

In conventional functional programming, as in the lambda calculus, the application operator is implicit
(or invisible). Repeat: if there are two well-formed lambda expressions A and B placed side by side, it
is assumed that A is a function-valued expression, expression B is its type-correct argument, and the
task of the interpreter is to apply A to B and display the result. This is the standard notation for Gofer too.

The command **:set +S** or **:s +S** causes non-standard notation to be used for function application,
while **:s –S** causes standard notation. Below we mention three important differences between the two.

1. In the interpreter response, the symbol ":" stands for “is of type” in the non-standard notation,
whereas in standard notation, the interpreter uses the double colon "::" symbol. See below.


2. In the nonstandard notation, three dots **...** indicate a range of values in a list, e.g.,
**[0...4]** but in standard notation, only two dots are used, thus **[0 .. 4]**.


3. As already stated, we use the explicit function application operator ".", whereas the standard
notation has an implicit or invisible operator (i.e., blank space). Accommodating both notations, our
version of the Gofer interpreter allows both the explicit and the implicit application operators.

Non-standard notation (single colon indicates the type, three dots indicate a sequence of list elements):

```
? 2+
4 : Int
? [0 ... 4]
[0, 1, 2, 3, 4] : [Int]
? cos
cos : Float -> Float
```
Standard notation (double colon indicates the type, two dots indicate a sequence of list elements):
```
? :set -S
? 2+
4 :: Int
? [0 ... 4]
ERROR: Undefined variable "..."
? [0 .. 4] – the interpreter requires two dots rather than three
[0, 1, 2, 3, 4] :: [Int]
? cos
cos :: Float -> Float

? cos pi — juxtaposition works for function application

- 1.0 :: Float
? cos. pi — the explicit application operator also works in our Gofer
- 1.0 :: Float
```
In standard notation, explicit function application operators cannot be used.  

```
? :set +S
? cos. pi -- using the explicit function application operator

- 1.0 : Float
? cos pi -- implicit operator, juxtaposition in other words
ERROR: Juxtaposition has no meaning. Use.
? cos. pi
- 1.0 : Float
? :s -S
? cos pi
- 1.0 :: Float

```


These exercises are to be moved to a later lesson, after function definitions have been covered.

€: Write functions that will extract the four individual components of a 4-tuple.

€: Write three functions, sel12, sel23 and sel13 which will respectively select the first two, the
second two, and the first-and-last components of a triple.

€: Write two functions, rev2 and rev3, that will reverse the order of components in a pair and a triple.

_Date and time_ 03 - 01 - 2020 18:55, modified 12- 06 - 2020 0 8 :1 5 and 15- 07 - 2020 18 : 00




# Introduction to Programming

## Lesson 4: WRITING AND LOADING A GOFER SCRIPT

(R: Some of the remarks, terminology and definitionsbelow were already stated in earlier Lessons.
The motive in repeating them is to reinforce unfamiliar concepts, so that students remember them.)

R: The Gofer interpreter operates $\underline{interactively}$ , i.e.,the user enters an expression at the interpreter
prompt"?" and terminates it by pressing the Enterkey. The interpreter responds by evaluating the
expression and printing its value on the next line. Then it repeats the interpreter prompt.

R: The interactive behaviour of the interpreter hasa name: _REPL_ , short for “read-evaluate-print
loop.” (If interpreters for other languages accept 
$\underline{commands}$ which are to be executed, instead of  $\underline{expressions}$ that are to be evaluated, REPL is understoodas “read-execute-print loop.” )

R: Even if an expression is very long (and occupiesmultiple lines on the monitor), it is still a single
expression. We cannot enter anything more than a single expression into the interpreter, but that
expression can be more complicated than the ones we have seen so far: we can locally define and use
variables within expressions.

## NAMES, VALUES ANDBINDINGS


R: When we speak of a variable , we have two ideasin mind: the name of the variable, and its value ,
e.g., the name **π** or **pi**, and its value **3.14159... .**(In this instance, the value is a constant, so the
term “variable” is a misnomer.) We can have a name called **height**, and it might or might not have
a value.


**Definition** _( binding , bound variable )_: A name is boundto a value with the equality symbol "=", e.g.,
**height = 178**. Variable definitions have the followingsyntax: name , followed by the equality
sign, followed by an expression , e.g.,**w = 100 orx = [1...4]** or **z = y+2**, wherey will
itself have to be defined in the script (unless it is predefined in the prelude).


(We could say that a name is bound to a value, or alternatively, that the value is bound to the name. In
my view, it is one and the same thing—there is a name, there is a value; they get bound to one another.)

Important: These definitions are 
$\underline{not}$ $\underline{at}$ $\underline{all}$ the sameas the assignment statements of languages like C.
In languages like Gofer, name-value bindings are _immutable_ ,i.e., once made, they are unchangeable.
In contrast, in C-like languages, a value can be assigned to a name, and later, another can be assigned.
We could say that a binding in Gofer is a fact, whereas an assignment in C is an action—a verb.

Equations or definitions like this one are placed in a plaintext file known as a Gofer script (file
extension.gs). The script is loaded into the interpreterfor the name to have a value. Then if we type
in the name into the interpreter, it will respond with the value.


The value of the expression containing a variable will depend on its value. If a variable has not been
bound to a value using the "=" symbol, and we attemptto evaluate an expression containing the
variable, the interpreter respond with an error message: **“undefined variable.”**

R: We can define names $\underline{locally}$ and bind them to values,with the keywords **where** and **let**.
These bindings are limited to the expression being entered, and are lost after the expression has been
evaluated.

€: Evaluate expressions into the interpreter using thelet andwhere keywords (see the examples
below) 

```
.? x+2 where x = 10? [n ... n+5] where n = 3 12 : Int [3, 4,
  5, 6, 7, 8] : [Int]


? let x = 10 in x+2? let n = 1 in [n ... n+5] 12 : Int
[1, 2, 3, 4, 5, 6] : [Int]
```

€: Evaluate tuples like **(x+1, x-1)**, after binding **x** to an integer with the **let** and **where**
keywords.

R: You might think that these examples are trivial, so the keywords are unnecessary. Their use comes
in handy when expressions get long and complicated, and we want single names for long
sub-expressions.

R: In Gofer’s interactive mode, we can only use a single **"="** symbol to create a binding. So you can
bind two or more names to values by putting the names as components of a list or tuple, thus:

```
? x+y where (x, y) = (10, 20)? let (x, y) = (10, 20) in x+y
30 : Int 30 : Int
? [x ... y] where (x,y) = (10,15)? let (x, y) = (10,15) in [x
... y] [10, 11, 12, 13, 14, 15] : [Int] [10, 11, 12, 13, 14, 15]
: [Int]

```
R: We can have variables whose bindings to valueslast beyond a single expression. For this purpose,
we need to write Gofer scripts.

# GOFER SCRIPTS

Definition (repeat) : A Gofer script is a plaintext file with extension **.gs.** It consists of a set of
definitions that bind names to values. One important use of scripts is to define functions (which we have
not learnt so far). A script file can be saved in non-volatile memory (like disk) and can be used
repeatedly whenever needed.

R: The definitions (see examples below) are communicatedto the interpreter by _loading_ the script into
the interpreter. At that time, the expression on the right hand side of each **=** symbol is evaluated,and
that becomes the value of the name on the left hand side of the **=**, i.e., the name is $\underline{bound}$ to that value.
After the script is loaded into the interpreter, we can construct expressions containing these names and
load them into the interpreter, and it will evaluate these expressions in the manner we expect.

€:Open a plaint exteditor,like **Notepad** on **MS-Windows** or **gedit** on **Linux**.(Notepad comes
bundled with MS-Windows, and is found at **Start > All Programs > Accessories**).
Enter some equations,one to aline(see below), save it as **trial04.gs** and load it in the 
interpreter.

W: Under MS-Windows (but not under Linux), you might get an error message like

```
this:? :l trial04.gs
ERROR "trial04.gs": Unable to open file
```
Explanation: Notepad has saved this file with name **trial04.gs** and extenstion **.txt**. If you put
double quotes around "**trial04.gs**", i.e., if you typein"trial04.gs" and only then save the
file, then the file will have the name **trial04** and extenstion **.gs**. Verify this in the directory
listing.

Along with this Lesson, file lsn04.gs is supplied. It contains the following bindings:
```
p = 100
q = 10.

r = [1...4]
s = (2, '2', 2<2)y = 2
z = y+
t = (hd, tl) where
hd = 100
tl = [0 ... 5]
--You have not seen the :: operator so far
--Find out the values of t and u
u = hd :: tl where
hd = 100
tl = [0 ... 5]
```

€: Suppose that lsn04.gs had not been supplied, and you had to make it yourself.

Be sure that $\underline{the}$ $\underline{starting}$ $\underline{characters}$ $\underline{of}$ $\underline{all}$ $\underline{3}$ $\underline{linesare}$ $\underline{aligned}$ $\underline{vertically}$, $\underline{i.e.,}$  $\underline{they}$ $\underline{start}$ $\underline{at}$ $\underline{the}$ $\underline{same}$ $\underline{column}$. Initially, let all lines start from column1. Save this file in the same folder as the Gofer
interpreter. Repeat: While saving the file, give its name in quotes and withgs as the extension,
like this: **"lsn04.gs"**. Repeat: If you don’t put thename in double quotes, then Notepad in
MS-Windows automatically gives the extension **.txt**.

€: (Repeat) Load the file **lsn04.gs** In the interpreter, with the command:**load lsn04.gs.**
Note: It is sufficient to use just the first letter of the command, like:**l lsn04.gs.** The
interpreter will start a new Gofer session, after loading the definitions in files **pustd.pre** and
**lsn04.gs**.

€: Make simple expressions using variables defined in **lsn04.gs**, and enter them into the interpreter.
Verify that the interpreter evaluates the expressions and displays their values in a manner that you
expect.

R: Sometimes you need to make corrections or additionsto a file you had earlier loaded. For instance,
there may be typographical errors, syntax errors or logical errors in your script, or you may want to
add some definitions or modify old ones. After you have made these changes, save the file. Then
simply enter **:reload** or **:r** , without supplying thefile name. The **reload** command loads the
file that was last loaded with the **load** command. 
$\underline{Don't}$ $\underline{forget}$ $\underline{to}$ $\underline{save}$ $\underline{the}$ $\underline{file!}$ Otherwise the
changes you have made won’t get loaded into the interpreter. (You can get the same effect as the
**reload** command by giving the **load** command and specifying the name of the file that was
saved.)

€:After loading or reloading file **lsn04.gs**,enter at the interpreter prompt any of the variables you
have defined,e.g., **p**,and it will print the value of **p** that you specified in the script.Optionally it will
print the type of **p** also,provided the type information has been enabled (by default,or after entering
the command:**s +t** ).Recall that:**t p**, causes the interpreter to explicitly tell you the type of **p**
without
giving its value. You can do the same with the other variables you defined. You can verify that the
interpreter has evaluated **z** correctly, as **y+3**, sincey is **2**. Enter expressions involving these
names.

R: The exponentiation operator in Gofer is the caret "^". Make expressions like **p+y,p*y,p^2,**
**p^3** (i.e.,p square and cube), or **q^2,q^3** and verify that the interpreter evaluates these
expressions correctly. Note especially that the type of the result can be **Int** or **Float**.


€: Change the values on the right hand side of the equations in the script, save the file (as discussed
earlier), reload the changed file into the interpreter, and verify that the values of the names and of
expressions containing the names are correctly evaluated.

€:Interchange the bindings of **y** and **z** in file **lsn04.gs,z=y+3** comes first,and **y=2** comes
later. That is, **z** is first defined in terms of **y**,and next ,**y** is defined to be **2** .Then save the file and
reload it into the interpreter. Verify that this makes no difference to the interpreter.

R: In functional programming, the equations are treatedas a $\underline{set}$ of definitions (in which the order of
their occurrence is not significant). On the other hand, in the languages with which most persons are
familiar, these lines are regarded as a $\underline{sequence}$ ofassignments (the order in which the assignments are
made is important). This issue is considered in greater depth in the next Lesson, entitled “The
Term-rewriting Model of Computation.”

€: Now let us observe what happens if all the lines of the script are not aligned. Given all the lines in
file lsn04.gs starting at column 1 (as suggested above), place a blank space before the start of any one
line, say line 2. The interpreter will generate a seemingly confusing error:

```
ERROR "lsn04.gs"(line 2): Juxtaposition has no meaning. Use.
```

In earlier lessons, we saw that this arose when the function application operator "." is absent. We
should consider that this error message is misleading, and the real issue is the lack of alignment of
line 2. It is the blank space at the start of the line that caused this error.

Moving a line to the right by adding blank spaces before its start is called _indentation_ , which has
meaning only in multi-line statements (i.e., single statements that span multiple lines), and is an error
otherwise. Remove the indentation that you had made, and the error will go away. Indent two or
more lines, and the interpreter flags only the first indented line.

€: Now place a blank space before the start of line 1. The error message you will see is **ERROR**

```
"lsn04.gs" (line 2): Syntax error in input (unexpected symbol)
```
This error is misleading too. The indentation in line 1 caused the interpreter to expect that the
subsequent line would be indented too, so that it would be vertically aligned with the first one.

Enter the same number of spaces, say 2 spaces, before each line, and save and load the file into the
interpreter. The file gets loaded because the blank spaces are not treated as indentation, i.e., no line(s)
are indented inwards or outwards with respect to other lines.

Note an important point: An indentation error gets caught in the process of loading the file into the
interpreter, and on catching it, the loading process stops.

R: You can give many commands to the Gofer interpreter.The commands that we have already
used, **:l,:r,:t** and **:s** are among them.

€: Enter:**?** to get a list of commands that you cangive to the interpreter. Go through the list before
reading the description below.

All interpreter commands except one start with a colon, symbol :. The commands that we are going
to use most often are **:l,:a,:r,:e,:t,:s,:n**.(These commands are short for **:load,:also,**
**:reload,:edit,:type,:set** and **:names**.) We have already used many of these commands.  

A few words about some of them are repeated. Whereas the:l command loads a file after erasing
all other files that have been previously loaded, the **:a** command loads additional files without
removing files that were loaded earlier. The **:e** command calls the editor from within the
interpreter—no need to go explicitly to the editor. (Notice: It appears that in the present version of
the Gofer intrpreter wor MS-Windows, this command has not been implemented, or does not work.)
The:**n** commands lists  
all the names that are known to the interpreter. These include those in the prelude file and those that
have been loaded by you.

The only command that does not start with a colon is described as **<<expr>expr>**. The angle brackets
"<" and ">" that surround the term called "expr"are to be found as part of other commands also,
e.g., **:load <<filename>filenames>**.

R: The angle brackets < and > serve as a placeholderfor the term that is enclosed in them, e.g.,
**<<expr>expr>** stands for any expression, while **<<filename>filenames>** stands for any blank-separated
sequence of file names. When we do enter a concrete expression like **2*3+4**, we do not put
angle brackets around it.

Thus,in the list of inter preter commands **<<expr>expr>** is a way to say,any expression can be entered
at the interpreter prompt, without a prefix of:.The explanation to the right of **<<expr>expr>** indicates
that the action of the interpreter when an expression is input is to evaluate the expression.


Typical examples of **<<expr>expr>** are **2*3+4,2.0+2.1,2<3,3<2, 'a', "abcdef"**. We have already
experienced entering such expressions into the interpreter, which computes their values and displays
them before producing yet another interpreter prompt. (The types of these various expressions are
different—note that currently we are not discussing types, but instances of **<<expr>expr>**.)


# Lesson 5 : Introduction to functional programming:

## THE TERM-REWRITING MODEL OF COMPUTATION

Here we consider basic concepts that describe the two main abstract models of computation we use.
(A valid “objection” can be raised: is the theoretical content of this lesson appropriate for beginners?
Answer: if you understand this content, it will be easier for you to study Gofer in parallel with C, Java, etc.)

One main difference between the two rests on the meaning of the equality symbol "=". In the model that
we are studying, it gives rise to a $\underline{fact}$: equality by definition. In the other, it causes the $\underline{action}$ of assignment.

(Note: This Lesson does not use the interpreter, but there is an exercise marked €: for you to use it.)

Gofer, the name of our programming language, is an acronym for “good for equational reasoning”.
Here we discuss the meaning of the term equational reasoning, and briefly explore how equational
reasoning is the process that drives computation in functional programming.

_Equational reasoning_ is the name for a basic idea that we are all familiar with. Simply stated, it is what
we do in basic algebra. If α and β are “syntactically well-formed sequences of symbols”, we understand
the equation **α=β** to mean that α and β have the same value e.g., **2+2=4**, or taking a more substantive example,
**sin 2x = 2 sin x cos x**. Equation reasoning proceeds as follows: whenever we see one of **α** or **β** in
a larger expression, we may replace it by the other, without changing the value of the larger expression.

In middle and high school, we manipulate expressions in this manner in order to simplify them, till
they reach an _irreducible form_, i.e., cannot be simplified any more. Schoolchildren call it the “answer.”
Essentially, this is what the Gofer interpreter does. Specifically, it always replaces the left hand side
of an equation by the right hand side. (Note: Sometimes, while writing proofs related to Gofer, we
humans may replace the right hand side of an equation by its left hand side.) The exact manner in
which the interpreter proceeds is given by an example below.

$\underline{Story}$: Imagine a ninth-standard student in the process of performing calculations. Imagine this student
has the capacity to perform the basic arithmetic operations, but that he simply does not have the
abstraction capability to comprehend how algebraic formulas arise and how they are derived. (We are
all familiar with this type of student; unfortunately, it seems that each class has a few such students.)

Suppose the teacher poses the problem of finding the interest on a certain principal P, where the
interest rate is R % and the time for which the loan is taken is N years. If the numbers are relatively
small and simple, it is easy to mentally calculate the interest and the total amount due. But not for our
hypothetical student—he has to memorize the relevant formulas (though substitution within formulas
and arithmetic computations are within his capabilities.) Suppose, for a simple example, the principal
is Rs 2000, the interest rate is 15% per annum and the time period is 3 years. The teacher
systematically writes the solution on the blackboard, as given in the column on the left:

```
Classroom exercise                      Gofer script (initial letter is always lower case)
SI = P*N*R/100                             si = p*n*(r/100.0)
Amt = P + SI                               amt = p + si
P = Rs 2000                                P = 2000.
N=3 years                                  n = 3.
R= 15% pa                                  r = 15.
```
Then our student writes the equation for simple interest, and rewrites it substituting values for **P, N** and **R**,
thus obtaining **SI = 2000 * 3 * 15 /100**. After performing the two multiplications and one division, the
student obtains the answer that **SI = Rs 900** and that the amount **Amt = P + SI = 2000 + 900 = Rs 2900**.


The column on the right is the same as that on the left, except for changes required by Gofer: the variable
names start with lower-case letters (a requirement of Gofer syntax), all the numeric constants are floating-
point (recall that with integer operands, Gofer performs integer division where any remainder is lost,
Gofer cannot perform binary operations on an integer and a floating-point) and moreover, parentheses are
introduced in the formula for simple interest (because in Gofer, using a * and a / together leads to ambiguity).

€: These equations are communicated to the Gofer interpreter by writing them in a script and then
loading the script into the interpreter. (The previous Lesson, Lesson 4, has details of how to do this.)

The Gofer interpreter performs its calculations with equational reasoning just as we do in school
mathematics. If we enter the variable name amt after the Gofer prompt, then the interpreter internally
replaces the name **amt** with **p + si**, the right hand side of the equation for **amt**, and next, **si** with
**p*n*(r/100.0)**, the right hand side of the equation for si. (Gofer is, arguably, even slower than
our student: in rewriting, only one variable name is replaced at a time by its right hand side, or only
one arithmetic operation is performed.) Next, each of the variables in this expression is replaced by
its value, i.e., the right hand side of the corresponding equation (one at a time), then the two
multiplication and one division operations are performed (one at a time), thus yielding the answer that
the value of **si is 900.0**. In this way, the Gofer interpreter performs calculations just as a maths
student would. The only difference is that integers and floating point numbers cannot be mixed in
Gofer operations. (Initially, this appears to be a limitation, but we shall find that it is turned into a
$\underline{powerful}$ $\underline{tool}$ for checking the correctness of types, and hence the correctness of our thinking.)

At each step the term or expression being evaluated is rewritten, either by replacing one variable name
with its definition on the right hand side of an equation, or by replacing an operator and its operand(s)
with the value resulting after performing the operation. This process comes to a halt when no more
such rewriting steps can take place. The resulting term is said to be in irreducible form, and is the
“answer”, the value of the expression to be evaluated. This is why the the abstract computer that the
Gofer interpreter implements is called the $\underline{term-rewriting}$ $\underline{model}$  $\underline{of}$ $\underline{computation}$. In contrast, practically all computers in use today employ the $\underline{stage-changes}$ $\underline{model}$  $\underline{of}$ $\underline{computation}$.

The question arises: in the expression **p + si**, does the interpreter replace **p** by its value first, or **si**
by its expression first? It does not matter in Gofer, just as it does not in arithmetic. Either way, the
answer is the same. (There is an important theorem in the mathematics underlying Gofer, that no
matter which way any arbitrary expression is reduced in this way, the result is the same.) Given this
fact, the exact order in which the interpreter performs the operations is not relevant for us.

If the sequence of equations above is placed in a program written in a language like C or Python, then
the system finds an error: the variable p is undefined in the statement for si. If we move the
statement **p = 1500.0** before the equation for si, then the error is changed slightly: **n** is
undefined. If we move the statement n = 3.0 to just after the equation for p, then the error is: r is
undefined. If all three statements, for **p, n** and **r**, are moved before that for **si**, then indeed the
correct value of si is determined.

What is happening in C or Python is that “**si = p * n * r/ 100** ” is $\underline{not}$ $\underline{an}$  $\underline{equation}$ $\underline{with}$ $\underline{which}$ $\underline{we}$  $\underline{can}$ $\underline{employ}$ $\underline{equational}$ $\underline{reasoning}$. That is why we have called it a _statement_ in the preceding paragraph,
not an equation. Warning: The paragraph that follows has an explanation that is brief to the extent of
being incomplete! Much later, we will be expanding upon the concepts introduced below.

In languages like C, the = symbol does not stand for $\underline{equality}$, as it does in high school mathematics.
Instead, it stands for an $\underline{action}$ called assignment. The meaning of a statement with the “**=**” symbol is:
calculate the value of the expression to the right hand side of the “**=**”, and assign it to the name on the
left hand side of the “**=**”. (The details depend on the language: in C, assignment means: _store_ it in the
memory location associated with the name on the left hand side, whereas in Python it means,
effectively, draw an arrow from the name to this newly computed value.) This is not at all the way
in which the Gofer interpreter behaves. In both C and Python, something in memory (either the
memory location associated with the name, or the arrow from the name to its value) changes. The
technical term for “content of memory” is $\underline{state}$, and hence the abstract computer performing
calculations in languages like C or Python is called the $\underline{state}$ $\underline{change}$  $\underline{model}$ $\underline{of}$  $\underline{computation}$.

The behaviour of the term-rewriting and state-change models of computation gives rise to two
corresponding programming styles: the $\underline{declarative}$ and $\underline{imperative}$  $\underline{programming}$ $\underline{paradigm}$.
(Terminology: A $\underline{paradigm}$ is a fundamental way of thinking or viewing the world.)

The origin of these two terms is in the syntax of sentences in natural languages: a declarative sentence
is merely an announcement or narration, whereas an imperative statement is a command to perform an
action.

Examples: (declarative statement) “The ground is wet.”
          (imperative stmt) “Pour some water on the ground,” or, “make the ground wet.”

The fundamental difference in these two statements is essentially the same as the different
interpretations of forms like **p=2000** and **a = p + si** in the two models of computation. In the
term-rewriting model, the forms are treated as equations, announcements of facts: **p** is **2000** and **a** is
the sum of **p** and **si**, while in the state-change model, they are $\underline{instructions}$ to assign the values of
expressions on the right hand side of the = symbol to the names on the left hand side. In other words,
the = sign refers to the narration of a fact in the term-rewriting model, whereas in the state-change
model it signifies an instruction to perform the action of assignment. For these reasons, the
programming styles for the two models of computation are called $\underline{declarative}$ and $\underline{imperative}$.

The $\underline{functional}$ $\underline{programming}$ paradigm is the dominant style of declarative programming. In
functional programming, the declarations (announcements of fact) are in the form of definitions of
mathematical functions, so that in a given instance, the value of a function can be computed for a
given argument. How the function is evaluated is not our concern: there are values—argument
values and function values—but no “mutable memory” in which they are stored. Given an argument
value, the function value is the same every time. In particular the function value does not depend on
the value of some other name. This behaviour is called $\underline{referential}$ $\underline{transparency}$. This is the style of thinking and programming that we shall be studying first, using the Gofer programming platform.

We will then study imperative programming.




# Introduction to Functional Programming: Lesson 6

## PROOF BY INDUCTION AND ITS RELATION TO RECURSIVE FUNCTIONS

Mathematical induction (or proof by mathematical induction) is a proof technique which is used to
prove that a statement (formula, theorem) is true for any “well-ordered set.” Most commonly, it is
used to establish statements for the set of natural numbers, i.e., for the integers **0, 1, 2, 3, ....**

Remark: Do the natural numbers start with 0, or with 1? In middle school mathematics, we start with 1,
whereas in computer science, we almost always start with 0. In other words, the first natural number is 0
(which might sound odd, so sometimes we may use a new, non-standard term: “zero-th”).

Remark: For our purposes, it is enough to know the meaning of “totally ordered” instead of “well-ordered:”
a totally ordered set is well-ordered and a little more. Formally, a _totally ordered set_ is one for which
there is an ordering relation like “<” or “less than” for integers. Given two distinct integers **m** and **n**,
either **m<n** or **n<m**. If we accept that the natural numbers **0 , 1 , 2 , 3 , ...** are indeed totally ordered, we
need not get into the precise meaning of “well-ordered” and “totally ordered”. We will be proving
propositions about the natural numbers or about sets whose elements are labeled by the natural numbers.

Let **P(n)** be a well-formed proposition (i.e., an expression that evaluates to **True** or **False** but not both)
that involves **n**, a natural number. We want to show that **P(n)** holds, i.e., **P(n)** is true, for all n.

Example of **P(n)**: “The sum **0+1+2+ ... +(n-1)+ n equals n*(n+1)/2**.”
In programming, **P(n)** will typically be a statement to the effect that a certain algorithm works as intended
or claimed, where **n** refers to the size of the data, e.g., an algorithm correctly sorts a set of **n** values.

There are two cases in a proof by induction:

1. Base case (for small values of **n**, like **n = 0, or n = 0** and **1 , or n = 0, 1** and **2** , etc.), and 
2. Induction case (for larger values of n beyond the base case).

The base case is often proved by inspection, e.g., for the example proposition **P(n)** above,
**P(0)** is “ **0** equals **0 * 1/ 2**”, or **P(1)** is “**0+1** equals ** 1 * 2/2,**” which are seen to be true by inspection.

The induction case has two parts: (2.1) the induction hypothesis, and (2.2) the induction step.
(Def: Here, a _hypothesis_ is a proposition made as a basis for reasoning, without any assumption of its truth.)


2.1 The induction hypothesis is that P(n) holds for some **n >= 0**.
2.2 The induction step is, given that P(n) holds, show that **P(n+1)** also holds.

Thus the induction case amounts to **P(n)=>P(n+1)** for all **n >= 0**, where **=>** means “implies.”

In our example, P(n) is “The sum 0+1+2+ ... +(n-1)+ n equals n*(n+1)/2.”
while P(n+1) is “The sum 0+1+2+ ... + n + (n+1) equals (n+1)*(n+2)/2.”

The induction hypothesis is that **P(n)** holds, i.e., “the sum **0+1+2+ ... +(n-1)+n equals n*(n+1)/2**. is true”

We need to show that **P(n+1)**, i.e., “the sum **0+1+2+...+ n +(n+1) equals (n+1)*(n+2)/2**” also holds.

 Note that the left hand side of **P(n+1)** is the sum **( 0+1+2+ ... + (n-1) + n ) + (n+1)**

which equals **n *(n+1)/2 + (n+1)**    by the induction hypothesis  
which equals **(n+1)* (n/2 + 1)**     by factorisation  
which equals **(n+1)*(n+2)/2**        by simplification  
which is the right hand side of **P(n+1)**  

Thus assuming **P(n)**, we have shown **P(n+1)**, or we have shown that **P(n) => P(n+1)**




Alternately, the induction hypothesis is to assume that **P(n-1)** holds for some **n>0**, and the induction step is,
given that **P(n- 1 )** holds for some **n>0**, to show that **P(n)** also holds, i.e., to show that **P(n-1) => P(n)**.

$\underline{Exercise}$: Assume that **P(n)** is the proposition that “the sum **0+1+2+ ... +(n-1)+n equals n*(n+1)/2**”
For the induction case, assume **P(n-1)** for **n>0** and show **P(n)**, i.e., show that **P(n-1) => P(n)**

$\underline{Exercise}$: Prove that the sum of squares from 0 to n, i.e., **02 +1^2 +2^2 + ... + n^2 = n*(n+1)*( 2 n+1)/ 6**

## SIGNIFICANCE OF PROOF BY INDUCTION

Suppose we want to show that, say, **P(283)** holds, for some proposition **P(n)**. Then:

First we show that the base case holds—in the simplest form, **P(0)** holds.

Assume we have proved the induction case, that **P(n) => P(n+1)** holds. Treat this implication as a crank
handle. Given **P(0)**, turn the handle once, twice, three times, to show **P(1), P(2), P(3)**. Keep on turning
the handle. Turning it **281 , 282 , 283** times lets us show **P(281), P(282)**, and finally, **P(283)** holds.


COMPUTING THE SUM **0+1+2 ... +n** IN GOFER

Two syntactically correct functions are given below to compute the sum. **sumupto1** uses the implication
**P(n-1) => P(n)**, while **sumupto2 uses P(n) => P(n+1)**.

Cut-paste the two functions below into a Gofer script, load them into the interpreter, and verify that both work
correctly, for the base case, i.e., argument value **0** , as well as the induction case, e.g., argument value **5**.

```
sumupto 1 : Int -> Int                      sumupto 2 : Int -> Int
sumupto 1. 0 = 0                            sumupto 2. 0 = 0
sumupto 1. n = sumupto 1. (n-1) + n         sumupto2. (n+1) = sumupto 2. n + n+

```
Remark (Strong and weak induction): To show **P(n)**, we have assumed **P(n- 1 )**. Sometimes we need a different
hypothesis: to show **P(n)**, the hypothesis will be that **P(i)** holds for all i such that **0<=i<=n- 1**.
(It can be easily proved that the two hypotheses are equivalent, i.e., the one holds whenever the other holds.)

Remark (Divide and conquer method): Computing problems are often solved by breaking them up into two
subproblems of half the size, obtaining their respective solutions using strong induction, and combining the
solutions. (Each half-size problem would itself be broken up into two quarter-size problems and solved, etc.)

Example (Algorithm to sort a list of numbers): Break the list into two halves, sort the two half-size lists (using
this same algorithm, i.e., break each half-size list into two quarter size lists, etc.), and finally, merge the half-
size solutions into a fully sorted list. Note: If the list is of odd length, one of the parts will have one more
element than the other. The basis case is that a list of size 0 or 1 (empty or singleton list) is sorted by default.

The proposition **P(n)** is that the algorithm correctly solves a problem of size n (i.e., sorts a list of size n), the
strong hypothesis is that the algorithm “recursively” sorts lists of half the size (size **n/2**), and the induction
step consists of proving that merging the two sorted lists of size **n/2** gives a fully sorted list of size **n**.

This mention of “recursive” directly leads to a discussion of the connection between recursion and induction.
The main difference is that induction goes from the small to the large, whereas it is the other way around in recursion.

Note to students: On the next page, recursive algorithms are discussed. Now it is felt, both by students and by
teachers, that recursive programs are “hard” to understand. The designers of this course do not at all agree!

To avoid this misunderstanding, you, the student, have to do two things: (1) understand the basic concept of
proof by induction, and (2) understand the connection between recursive algorithms and proof by induction.


## Induction and Recursion in programming

Inductive reasoning moves from specific observations to broad generalizations, e.g., proof by induction starts with
a base case, an induction hypothesis and an induction step, and proves some proposition for all natural numbers.

An important example of inductive generalization is the Peano axioms for defining N, the set of natural numbers:

1. 0 is a natural number
2. If n is a natural number, so is n + 1
3. Only numbers obtained from rules 1 and 2 are natural numbers.

Here we don't already have a set of natural numbers. We are describing a certain way to characterize
which numbers are “natural numbers”. Generally, induction is used more in mathematics than in computing.

It does matter that, in defining the natural numbers N, we have to start with 0 and “work up”. It doesn’t work to try
define the set N by saying that n is a natural number if n− 1 is a natural number. But once we have an inductive
definition of N we can leverage that for other purposes.

Recursion is a concept that is used in programming, and especially, in functional programming.

A _recursive_ entity, it is said, is one that is defined in terms of itself. This appears to be a contradiction in terms,
for when I give the meaning of a word in a dictionary, the description cannot itself contain the word being
described, but this seems to be the case with recursive definition. But this contradiction is only apparent, not real.

From Wikipedia: “Recursion in computer science is a method where the solution to a problem depends
on solutions to $\underline{smaller}$ $\underline{instances}$ $\underline{of}$ $\underline{the}$ $\underline{problem}$ [emphasis added]. For instance, the definition of n!
in terms of **(n-1)!** is a model example of recursion and proof by induction. The approach can be applied
to many types of problems, and is one of the central ideas of computer science.”

From Stack Exchange (one person’s view): The terms "recursive definition" and "inductive definition" are both quite
common, and the differences between the terms are usually so insignificant that either one will work. Some people
are fastidious about whether they call each definition "inductive" or "recursive", but I cannot immediately think of an
example where changing from one word to the other would change what is going on in a particular definition.

Inductive definitions are more common when we are defining a set of objects “out of nothing”, while recursive
definitions are more common when we are defining a function on an already-existing collection of objects.

The following definition of the factorial function is a recursive definition:
```
n! = 1, if n=
      n*(n−1)!, if n>
```
The correctness of recursive definitions like the one above is shown by employing proof by induction.

Inductive definitions are particularly important in computer science, mathematical logic, and related areas. One
additional aspect of them is that they usually give a set of "terms" for the objects being described. For example, we
know from the inductive definition of N that every natural number can be expressed as a finite string of the form
**0+1+1+⋯1+1+1+⋯ 1** (of the appropriate length). Using this idea, just to develop our recursive programming
skills, in practice problems in later lessons, we will define addition of two integers as repeated addition by 1, and
likewise, define multiplication of two integers as repeated addition and exponentiation as repeated multiplication.

[Note for students: Many of the descriptions here are adapted from _cseducators.stackexchange.com_. 
Stack Exchange is a network of question-and-answer (Q&A) websites on topics in diverse fields, each site
covering a specific topic, where questions, answers, and users are subject to a reputation award process. As of
August 2019, the three most actively-viewed sites in the network are Stack Overflow (for programmers), Super
User (for enthusiasts and powerusers) and Ask Ubuntu (for Ubuntu users and developers). ]


## PROOF BY STRUCTURAL INDUCTION, FOR LISTS


(Since you have not seen the $\underline{cons}$ operator :: for lists, wait for a few Lessons)  

Remark: Structural induction, a generalisation of mathematical induction, is used to prove that some
proposition **P(x)** holds for all instances x of some “recursively defined” structure, such as lists or trees.
Often, such a proof proceeds by natural induction on the size of the structure.

Let **P(s)** be a well-formed proposition that involves s, a list (in the sense of purely functional programming).
We want to show that **P(s)** holds, i.e., **P(s)** is true, for all lists s (in a given context, e.g., list type, properties).

The base case will be for small-sized lists, typically the empty list **[]**, and sometimes the singleton list **[x]**.
As with natural numbers, the base case for lists is usually shown to be correct by inspection. The induction case
will be for non-empty lists, denoted by the pattern **x::xs**, or lists with **>2** elements **x::y::ys**. The induction
hypothesis is that **P(xs)** is true, and the induction step is to do “something” with x, the list head, and the value of
the recursive call on the list tail **xs**, and conclude that **P(x::xs)** holds, i.e., show that **P(xs)=>P(x::xs)**.

```
len: [a] -> Int                    sum: Num.a => [a] - > Int–all numeric types
len. [ ] = 0                       a
len. (x::xs) = 1 + len. xs         sum. [ ] = 0
                                   sum. (x::xs) = x + sum. xs
```



Exercise: Prove by induction that **len** computes the length of a list, and sum computes the sum of list elements.

Proof: Base case is correct by inspection. The induction hypothesis is that **len.xs** is the length of the tail of
the list, and sum.xs is its sum. The length of a list is 1more than the length of its tail (induction step of **len**),
and the sum of a list is got by adding the head to the sum of the tail (induction step of **sum**).




# Introduction to Programming and its Mathematical Foundations

## Lesson 7: Syntax and Semantics of Function Definition and Application

Summary: The many ways of defining recursive functions are exhaustively described in this Lesson.

Background: There are two fundamental operators in functional programming: function application and
function abstraction (i.e., definition). In Lesson 3, we saw examples of application using built-in functions.

One important deviation from conventional practice is that we use an explicit (i.e., visible) operator for
function application, the “**Dijkstra dot**,” denoted by the symbol "**.**". Thus we write, e.g., **cos.pi** instead
of the conventional **cos pi** or even **cos(pi)**. Without the dot, the names **cos** and **pi** are juxtaposed
(i.e., are next to each other). This is a syntax error in our notation, but is allowed in the standard notation.

Function definitions can also be made using the application operator, see below. The abstraction operator,
lambda λ (denoted as backslash "\" since our keyboard does not have Greek letters) will be discussed later.

$\underline{Copied,}$ $\underline{with}$ $\underline{minor}$ $\underline{additions,}$ $\underline{from}$ $\underline{Lesson,}$ $\underline{3}$, “Data and Datatypes in Gofer: Compound Type Function”:

A function definition consists of two parts: the type definition (or signature) and the function body.
Relatively simple definitions are made in a single line (symbol "**=**" stands for $\underline{equallity,}$ $\underline{by}$ $\underline{definition}$.” )

```
succ: Int - > Int dbl: Int - > Int sq: Int - > Int
succ. n = n+1 dbl. n = n+n sq. n = n*n
```
Repeat: Function definitions are made within a Gofer script (file extension **.gs**), and the script is saved
for later use. When the functions are to be used (applied to arguments, etc.), the script is loaded into the
Gofer interpreter using the :**load** or :**l** command. Once the functions are loaded into the interpreter,
they can be used just like built-in functions.

Caution: When you store a script with a new or changed name, call it **newscr.gs**, take two precautions
under MS-Windows:  
 (1) put double quotes around the name, like "**newscr.gs**", otherwise **newscr.gs**
will be the name and **.txt**, the file extension, so the full file name will be **newscr.gs.txt**, and  
(2) store the file in the same directory as the Gofer interpreter. If you don’t take these precautions, you
will get an error message like **ERROR "newscr.gs": Unable to open file**.

Interpreter interactions below were made after the functions succ, dbl and sq were loaded into it:

```
? succ.
11 : Int                      Note the the function composition operator ";"
? dbl.10                      (f ; g).a means
20 : Int                      First apply f to a, thus f.a
? sq.10                       Then apply g to the result,
100 : Int                     thus (f ; g).a equals g.(f.a)
? dbl. (sq. 10)               ? (sq ; dbl).
200 : Int                     200 : Int
? succ. (dbl. (sq.10))        ? (sq ; dbl ; succ). 10
201 : Int                     201 : Int

```
Terminology: We have been saying that “functions are $\underline{applied}$ to their arguments”. To distinguish
between function definition and function application, our usage is “_parameter_ of the $\underline{definition}$,”
e.g., **succ. n**, and “_argument_ of the $\underline{application}$,” e.g., **succ. 10**. Thus, **n** is the parameter in
the definition **succ. n = n+1** , while in the application **succ. 10** , the integer **10** is the argument.

Alternative terminology: There are other usages too, e.g., $\underline{formal}$ $\underline{parameter}$ and $\underline{actual}$ $\underline{parameter}$ (instead of parameter and argument), or confusingly, the term $\underline{argument}$ is used in both definition and application.  
  
€: Students are to read, understand and assimilate the three steps below in the function application process.

$\underline{Function}$ $\underline{definition}$: Here are 3 cases: 1. one single-line definitions, and 2 , 3. two multiline definitions

```
succ: Int - > Int        sumupto1: Int -> Int               sumupto 2 : Int -> Int
succ. n = n+1            sumupto1.0 = 0                     sumupto 2 .0 = 0
                         sumupto1.n = sumupto 1 .(n-1)+n    sumupto2.(n+1)=sumupto 2 .n +(n+1)
```
The definition of succ is the simplest possible: it is one line long, and it has an uncomplicated expression
on the r.h.s of "=". The other two definitions involve recursive calls in the induction case.

$\underline{Steps}$ $\underline{in}$ $\underline{function}$ $\underline{application}$ $\underline{for}$ **succ**:

o (1) The $\underline{first}$ $\underline{and}$ $\underline{foremost}$ step of a function application is parameter-argument matching. If the function definition is **succ. n = n+1** and the function application to be evaluated is **succ. 10** , then parameter n in the definition is matched with argument **10** in the application.  
o (2) The $\underline{second}$ $\underline{step}$ is the substitution of the parameter by the argument in the value of the function, i.e., in the r.h.s. of the equality **succ.n = n+1, n+1** becomes **10+1** after substitution.  
o (3) The $\underline{third}$ $\underline{and}$ $\underline{last}$ step is the simplification of the resulting expression, thus **10+1** equals **11**.  

When the function definition is on multiple lines, the first step in function application is more elaborate.
$\underline{Here}$ $\underline{the}$ $\underline{parameeter-argument}$ $\underline{matching}$ $\underline{is}$.$\underline{attempted}$ $\underline{line}$ $\underline{by}$ $\underline{line,}$ $\underline{from}$ $\underline{top}$ $\underline{to}$ $\underline{bottom}$ 

$\underline{Steps}$ $\underline{in}$ $\underline{function}$ $\underline{application}$ $\underline{for}$ **sumupto1 and **sumupto2:


o (1) During parameter-argument matching in the two **sumupto** examples above, if the argument is **0** ,
then the matching succeeds on the first line itself. If the argument is greater than **0** , then it is matched
against $\underline{parameter}$ **n** in case 2, and $\underline{pattern}$ **n+1** in case 3. (Assume that the argument is **5**. Then n takes the value **5** in case **2** and **4** in case **3**.)  
o (2) Substitution of the parameter by the argument in **sumupto1** or **sumupto2** involves a recursive call.
To demonstrate correctness of these functions, you have to depend on proof by mathematical induction.
The induction hypothesis is that the recursive call of **sumupto1** or **sumupto2** returns the correct value.  
o (3) The induction step is that assuming the induction hypothesis, the addition of the argument to this
“correct value of the recursive call” correctly computes the value of the original call.    


o (1) **n** is defined to be an **Int**. If **n** is supposed to be a natural number, **n<0** does not exist—
it is an error. (Ask yourself, what does it mean to have the sum **0+1+2+... up to - 5?**)
Therefore the expressions **sumpto1.- 5** or **sumpto2.- 5** do not make sense. The computation
does not terminate—rather, it terminates with the error message “**control stack overflow**.”
(The error cases are not handled in the definitions above—more elaborate definitions are given below.)






# Introduction to Programming and its Mathematical Foundations

## Lesson 7, Part 2: Recursive function definitions

In the Lesson on proof by induction, we defined the sum of natural numbers up to some integer:

```
sumupto1: Int -> Int                 sumupto2 Int -> Int
sumupto 1. 0 = 0                     sumupto2.0 = 0
sumupto 1. n = sumupto1.(n-1)+ n     sumupto2.(n+1) = sumupto2.n + (n+1)
```
If we change the operator from + to *, and the base case value from 0 to 1 , we get the factorial function:

```
fact1: Int -> Int                fact2: Int -> Int
fact1. 0 = 1                     fact2.0 = 1
fact1. n = fact1.(n-1) * n       fact2.(n+1) = fact2.n * (n+1)
```
Repeat: In the left column, the variable **n** on the left of the = is called the parameter of the function definition,
while in the right column, **n+1** is called not a parameter, but the **n+1** pattern (permitted in Gofer).


$\underline{Another}$ $\underline{discussion}$ $\underline{on}$ $\underline{recursion}$:

Function definition is one place where recursion plays an important role, especially in functional programming.
Recursion was first discussed in the previous Lesson on Proof by Induction. Here is another discussion

We are using the functional programming style to learn about programming and problemsolving, and in
particular, we are considering recursive function definition. In this situation,

The value of function **f** for some argument **k** (i.e., the value of f when applied to **k**, i.e., the value **f.k**) is
written as an expression containing values of the same function f for arguments of smaller size,
e.g., see above, **fact1. n = fact1.(n-1) * n**

In turn, these applications to smaller-sized arguments are defined in terms of applications with arguments
of still smaller size. This cannot go on indefinitely when the initial argument n is of finite size. Soon
enough we reach arguments of smallest size which have to be defined directly instead of recursively. This is
the base case of the recursion.

In the general case, a definition might have several base cases, and several induction cases (see below).

Warning: When the argument of a recursive function definition is an infinite list, the “smaller-size
arguments” on right hand side of the equality sign may still be infinite lists, e.g., if a function f is defined
on the natural numbers, **f.[0...]** might depend on **f.[1...]** which might depend on **f.[2...]**,
and so on. In that situation a $\underline{a}$ $\underline{smallest-size}$ $\underline{base}$ $\underline{case}$ $\underline{will}$ $\underline{never}$ $\underline{be}$ $\underline{reached}$. (How the situation is resolved
is for another Lesson.)

$\underline{End}$ $\underline{of}$ $\underline{discussion}$ $\underline{on}$ $\underline{recursion}$

Definition (Conditional expression): A conditional expression is one whose value depends on a
Boolean-valued expression. Its syntax is as follows:


**if < expression: Bool > then < expression1 > else < expression 2 >**
Its value depends on the value of **<<expression:Bool>>**. If it is **True**, then the value of the
expression is <<expression 1>>, otherwise it is <<expression 2>>.


The tokens then <<expression 1>> are called the _then clause_ of the conditional expression, and
else **<<expression 2>>** is the else clause.

€: Try out these examples on your interpreter:

```
? if 2+2 == 4 then 'T' else 'F'
'T' : Char

? if x<100 then 10 else 20 where x = 0
10 : Int
```
€: Verify the workings of conditional expressions by evaluating these expressions (and make your own):

```
if True then 100 else 200        if False then 100 else 200
if 1<2 then 3 else 4             if 2+2==5 then 3 else 4.
```
The factorial function may be defined in a single line with a conditional expression, with the base case
and induction case forming the two clauses. See factorial function **fac 5** below.

```
fac 5 .n = if n==0 then 1    else n*fac 5 .(n-1)
```
If the argument is a negative integer, then all the definitions above will go into an endless rewriting
mode, without **n** taking the value **0**. We want to be able to announce an error whenever n is negative.
The built-in function named error allows us to do this. See function **facxx** below.

Concrete example of the $\underline{term-rewriting}$ $\underline{model}$ $\underline{of}$ $\underline{computation}$ (repetition of an Example from Lesson 5):

$\underline{Notation}$: In equations 1 to 5, **k!** means that the factorial function $\underline{is}$ $\underline{being}$ $\underline{applied}$ $\underline{to}$ $\underline{its}$ $\underline{parameter}$ **k***.

By the definition of the factorial function,

```
n! = n*(n-1)*(n-2)*(n-3)* ... * 2 * 1        Eq. 1
(n-1)! = (n-1)*(n-2)* ... * 2 * 1,           Eq. 2
0! = 1                                       Eq. 3
```
First we dentify the r.h.s. of Eq. 2 (i.e., the expression **(n-1)*(n-2)* ... * 2 * 1 )** in the
r.h.s. of Eq. 1, and next, we subsitute the l.h.s of Eq. 2 **( i.e., n-1)! )** in the r.h.s. of Eq. 1, thus

```
n! = n*(n-1)!   for n >= 1     (inductive case)      Eq. 4
0! = 1                         (base case)           Eq. 5

```
The term-rewriting model of computation proceeds through equational reasoning.

(Recall equational reasoning: If there is an equation  = , then any occurrence of  in an expression
may be replaced by , without changing the value of the expression.) In particular, whenever an
expression contains a function application, during the evaluation of this expression the $\underline{argument}$ of the
function application is matched against the $\underline{parameter}$ on the left hand side of the function definition, and
if the match is successful, the function application may be replaced by the right hand side of the equation.

Equational reasoning is employed to evaluate factorial for a particular value of n (n=4) as follows:

```
n! = 4!                 substitute argument 4 for parameter n
= 4*3!                  n! = n * (n-1)!,  n = 4
= 4*3*2!                n! = n * (n-1)!,  n = 3
= 4*3*2*1!              n! = n * (n-1)!,  n = 2
= 4*3*2*1*0!            n! = n * (n-1)!,  n = 1
= 4*3*2*1*1             0! = 1
```
The term-rewriting model applies the multiplication operator, one at a time, left to right
```
4*3*2*1*
= 12*2*1*
= 24*1*
= 24*
= 24
```
This expression is irreducible—- i.e., we cannot reduce it any further. In other words, this is “the answer.”



# Introduction to Programming and its Mathematical Foundations

# Lesson 7, Part 3: Different kinds of syntax for recursive function definitions

Summary: In its simplest form, the recursive definition of functions has two lines: one line for the base case
and another line for the induction case. The issue often reduces to whether the base case is written first, or
the induction case is first. Each of these two forms have advantages and disadvantages. See below.

Sometimes, using a conditional expression, both cases can be made to fit into a single line. At other times,
in somewhat more complicated definitions, there can be several base cases, or several induction cases, or
both. Commonly, in order to simplify the main definitions, auxiliary “helper functions” are defined earlier.
Examples for all these variations are provided below.

All the examples given below perform the same thing: computing the factorial function.

The Gofer definition of the factorial function can be written in many different ways. We use different
names **fac, fac1, fac2, fac3, ...** , so that these functions can be individually tested.

```
fac: Int -> Int             -- type declaration
fac.0 = 1                   -- base case, first line of definition
fac.n = n* fac.(n-1)        -- induction case, second line

fac 1 : Int -> Int          -- type declaration
fac1.n = n* fac1.(n-1)      -- induction case, first line of definition
fac1.0 = 1                  -- base case, second line
```
For function **fac**, if **n>0** there are n failed matches in the first line of the definition, for **n, n- 1 , n- 2 ,**
**..., 2 , 1** , before the base case of **n=0** is reached. We might try to avoid these failures by exchanging
the first and second lines, to obtain function **fac1**, where the induction case is matched first.

The difficulty is that the parameter n in line 1 of **fac1** matches both the induction case **(n > 0 )** and
the base case **(n = 0 )**. In trying to evaluate **fac.0**, there is a match between n and 0, so **0!** is rewritten
**0*(-1)!** which is not only incorrect but leads to an unending computation, for **n = - 1 , - 2 , - 3 , ....**
Try this in the interpreter. You will conclude that this arrangement of the lines leads to an incorrect definition.

Terminology: “Pattern matching” is the manner in which the Gofer interpreter employs multiline
definitions like the one above. (“pattern” because, in function **fac2** below, in place of the parameter
**n** we have the $\underline{expression}$ or $\underline{pattern}$ **n+1**.) We use the terms parameter and pattern interchangeably: “pattern matching” means parameter-argument matching.

Repeat: In a multiline definition, the parameter-argument matching proceeds line by line from top to
bottom. The right hand side of the first line for which the argument matches the parameter pattern,
replaces the function application.

```
fac 1 .n = n* fac 1 .(n-1)     -- induction case, first line of definition
fac 1 .0 = 1                   -- base case, second line
```
However, in trying to evaluate **fac.0**, there is a match between n and 0, so **0!** is rewritten **0*(-1)!**
which is not only incorrect but leads to an unending computation, for **n = - 1 , - 2 , - 3 , ....** Try this in
the interpreter. You will conclude that this new arrangement of the lines leads to an incorrect definition.

To avoid this kind of situation, Gofer provides the n+1 pattern, a special case of the **n+k** pattern.
The **n+ 1** pattern matches arguments **1** and above; thus the first line of function **fac2** below does not
match the base case, but the second line does, with the result that **fac2** correctly computes the factorial.


```
fac 2 .(n+1) = (n+1)* fac 2.n         -- induction case, first line of definition
fac 2 .0 = 1                          -- base case, second line
```
$\underline{The}$ $\underline{n+k}$ $\underline{pattern}$: An argument matches the n+k pattern whenever the argument is at least **k** (i.e., whenever n does not become negative). Thus, for an argument **c>0**, the **n+ 3 pattern** can match
arguments **c, c- 1 , c- 2 ,.. ., 4 , 3** but it cannot match **2 , 1 , or 0**. Verify the correctness of
function **fc** below, also.

```
fac3 : Int  -> Int
fac3.(n+3) = (n+3) * fac3.(n+2)
fac3.2 = 2
fac3.1 = 1
fac3.0 = 1
```
In functions **fac4** and **fac5** below, conditional expressions are used to calculate factorials

```
fac4, fac5 : Int -> Int

fac4. n = if n==0 then 1 else n * fac4. (n-1)

fac5.n = if n==0 then 1
   else if n>0 then n*fac5.(n-1)
   else error. "Invalid argument--negative integer "
```
If a negative argument is given to **fac4**, the **else** clause is executed, leading to infinite depth of
recursion. Function **fac5** computes the correct answer when the argument is **0** or positive, and sends an
error message when the argument is negative.

R: A long statement like the one for **fac5** can be spread over 2 or more lines, as long as the second and
subsequent lines are indented, all by the same amount.

R: The interpreter, which works in interactive mode can take a single line of arbitrary length, but it
cannot handle a multiline statement. You will have to enter a multiline in a script and then load the script
before executing the multiline statement. This is what is happening with function **fac5**.

R: In the case of a nested conditional expression, as with function **fac5** (i.e., when a clause of a
conditional statement is itself a conditional statement) each else clause matches the nearest **then** clause,
e.g., the else clause with the error message matches not the left most **“then” (...then 1 else ...)** but
the other **“then” (...then n*fac3.(n-1) ...)**.

For function definitions with multiple induction cases, there is another facility called statement guards.
Each line of the function definition is guarded by a Boolean valued expression Immediately to the right
of the guard is the equality sign followed by an expression. During pattern matching the guards are
evaluated, top to bottom. The expression to the right of the first guard that evaluates to True is the value
of the function. As before, the second and subsequent lines have to be indented, all by the same amount.
See example below:

```
fct.n
    | n>0 = n*fac4.(n-1)
    | n==0 = 1
    | n<0 = error."Negative argument"
```
You don’t have to explicitly state that the final guard is **n<0**. There is a keyword called **otherwise**,
which always evaluates to **True**.


€: Enter **otherwise** in the interpreter to determine its value.

It is important to use **otherwise** as the last guard in a multiline guarded statement, because
otherwise, control will never go past the line with the **otherwise**.

```
fct1.n
   | n>0 = n* fct1.(n-1)
   | n==0 = 1
   | otherwise = error."Negative argument"
```
Function **fct2** is identical to function **fct1** above, but the form (appearance) is reader-friendly. While
**fct1** uses the conventional notation "**|**" for guards, **fct2** uses commas and "**if**" for the same purpose.
It appears that most students prefer to use the notation below, because it is more clear for them.

```
fct2. n
   = error. "Negative number", if n<
   = 1, if n == 0
   = n * fct2. (n-1), otherwise
```
Function **fct3** uses guards below, but there is no explicit case (either **otherwise**, or **n<0**) for negative
arguments. Function **fct3** will evaluate correctly for zero or positive values of **n**, but there is no match
for negative values of **n**. This is a program error. See what happens when **fct3. (-1)**  is evaluated.

```
fct3.n
   = n* fct 3 .(n-1), if n>
   = 1, n==
```


## Problem set 7, Syntax and Semantics of Recursive Functions

Background: In Lesson 6, Proof by Induction, we extensively considered recursive solutions of different
kinds for a model problem: finding the sum of all natural numbers up to the parameter n. Specifically, we
employed parameter n, the (n+1) pattern, basis case first, induction case first, and so on. In Lesson 7,
Syntax and Semantics of Recursive Functions, we found that we could get the factorial function by
employing the multiplication operator instead of addition, and the basis case value of 1 instead of 0.

The problem set below uses the same syntactic structures as the solutions for finding sum of all the
numbers till a given number and finding the factorial of a given number.

1. Count the number of digits in the given number.

2. Add the digits of a given number

3. Check if a given number is prime.

4. Reverse sequence of digits in a given integer

5. Find out if a given number is a perfect number. (Definition: A natural number is a perfect number if
the sum of its factors adds up to the number, for example, the perfect numbers **6 = 1+2+3**, or
**28 = 1+2+4+7+14**. Perfect numbers are rare: there are only **4** perfect numbers among the first **1000**
natural numbers, and **5** perfect numbers among the next **10,000** numbers.)




# Introduction to Programming and its Mathematical Foundations

## Lesson 8 : Lists, Part 2 (Lesson 3 forms Lists, Part 1)

$\underline{Notation}$: A list in functional programming is commonly written as a sequence of elements, $\underline{all}$ $\underline{of}$ $\underline{the}$ $\underline{same}$ $\underline{type}$ e.g., **[2,18, 9 , 10 ]**. The _component type_ can be any simple or compound type that is legal in Gofer, e.g., **Int**, and the aggregate _list type_ is written as the component type in brackets, e.g., **[Int]**

This notation is "syntactic sugarcoating" that hides the true, recursive, nature of the list structure (see Figures 1 below).

(Definition): A list is either empty **[ ]**, or consists of a **head** (single element) and a _tail_   
(list of elements satisfying this recursive definition), all elements of the same type.                     
The head and tail are connected together by the cons operator, written :: in Gofer.                        
(Note: In standard Haskell notation, cons is written with a single colon, :)
                                                                                                
(Recursive) A non-empty tail has a head (single element( and a tail (itself another list),                     
till finally the tail is the empty list **[ ]**. The head and tail are connected together by the                  
cons operator, written :: , so **[ 2 , 18 ,9, 10 ]** is identically equal to      
**2::(18::( 9 ::( 1 0::[])))** , as illustrated in Figures 1a and 1b.                                                   
That is, the value of **[2,18,9, 1 0] == 2::(18::(9::( 1 0::[])))** is **True**.


```
           ::
           /\ 
          /  \
          2  ::  
             /\ 
            /  \
           18 ::  
              /\
             /  \
             9 ::  
               /\ 
              /  \
             10 []

Figure 1 a: Structure of [2, 18, 9, 1 0]

``` 
  

Lists can be represented in a natural way as lopsided trees, see Figure 1. The inverse operators
of **::** are the built-in unary functions head and **tail**, and there is a **length** function,
so that **length([2, 18, 9, 10])** is **4** , and **length([])** is **0**.

Further, just like we have the **n+1** pattern for positive integers, there is an **x::xs**
pattern for nonempty lists. There is no particular significance to the names—x stands
for one element, and **xs** stands for many elements. Just as the base case for the **n+1**
pattern is **0** , for lists it is **[]**. Note that neither the n+1 pattern nor the [ pattern can
match the base case—the **n+1** pattern matches integer arguments 1 and above,
while the **x::xs** pattern matches non-empty lists, i.e., lists of size 1 or more.

```
    tail  ::
          /\
         /  \
        18  ::
            /\
           /  \
          9   ::
              /\
             /  \
             10 []

Figure 1b: the head is 2 and the tail is [18, 9, 10]


```

```
Signatures                 Examples                            Application

head: [a] - > a           head.[2, 18 ,9,0] =              2 head.(x::xs) = x
tail: [a] - > [a]         tail.[2, 18 ,9,0] = [18,9,0]      tail.(x::xs) = xs
length: [a] - > Int       length.[2, 18 ,9,0] = 4           length.[] = 0

```
The various forms of recursive function definition for integers, as shown in file **recfuncs.gs**, can be
used in recursive function definitions for lists. Assume that s is a list, **x::xs** is a list pattern. Just as
the induction case for integers connects parameter **n** to **n- 1** , we have s connected to tail.s on the right
hand side, and as the induction case connects pattern **n+1** to **n**, we have **x::xs** connected to **x**. To
practically observe these “connections,” inspect the details of the example for **len**, given below

Assume **len** is a function that finds list length. (The name of the built-in function is not len but **length**.)
The different versions of len are structured as below. The first uses the **x::xs** pattern, the second uses
function tail, and the third uses a conditional expression. The **n+1** pattern matches integers 1 and above,
the **x::xs** pattern matches non-empty lists (of length **>= 1** ).

```
Induction case first (using pattern x::xs) Base case first (using parameter s)

len.(x::xs) = 1+len. xs len.[] = 0
len.[] = 0 len. s = 1 + len.(tail.s)

Conditional expression: len. s = if s==[] then 0 else 1 + len.(tail.s)

```


# PROOF BY STRUCTURAL INDUCTION, FOR LISTS

Remark: Structural induction, a generalisation of mathematical induction, is used to prove that some
proposition **P(x)** holds for all instances x of some “recursively defined” structure, such as lists or trees.
Often, such a proof proceeds by natural induction on the size of the structure.

Let **P(s)** be a well-formed proposition that involves s, a list in the sense of purely functional programming.
We want to show that **P(s)** holds, i.e., **P(s)** is true, for all lists s in a given context, e.g., a certain list type.

The base case will be for small-sized lists, typically the empty list **[]**, and sometimes the singleton list [x].
As with natural numbers, the base case for lists is usually shown to be correct by inspection. The induction case
will be for non-empty lists, denoted by the pattern **x::xs**, or lists with >2 elements **x::y::ys**. The induction
hypothesis is that **P(xs)** is true, and the induction step is to do “something” with x, the list head, and the value of
the recursive call on the list tail **xs**, and conclude that **P(x::xs)** holds, i.e., show that **P(xs)=>P(x::xs)**

```
len: [a] -> Int
len. [ ] = 0
len. (x::xs) = 1 + len. xs

sum: Num.a => [a] - > Int–all numeric types a
sum. [ ] = 0
sum. (x::xs) = x + sum. xs
```
Below, you will find descriptions of problems that can be
solved naively (i.e., from first principles, i.e., using the “base case first” or “induction case first” or “conditional expression” approaches, (according to your thinking or problem-solving strategy.)

To get a complete expression out of the “mention” below, you have to supply the list argument, e.g., when
the argument is list s, the complete expressions are, e.g., **len.s** or **oll.p.s** or **isin.q.s**.

```
Function        mention       description

len            len          length of a list (same as builtin length)

total          otal        sum of list elements (same as builtin sum)

produc        produc       product of list elements (same as product)

countevens    countevens    count the even numbers in the list

sumEvens      sumEvens      sum the even numbers in the list

sumalt1      sumalt1    sum of alternating elements starting from the head of the list

sumalt2     sumalt2  sum of alt elements, not counting the head, i.e., sumalt1 of the tail

anee         anee.p    does any element satisfy predicate p, same as builtin any

oll         oll.p do  all list elements satisfy predicate p, same as builtin all

```



# Introduction to Programming and its Mathematical Foundations

## Lesson 9 : Functions with multiple arguments

Note: File **script0 9 .gs**, to be loaded into the interpreter, contains the functions being discussed below.

Summary: **How to provide n> 1 arguments to a function, one at a time**

Terminology: When the number of arguments of a function is **1 , 2 , 3 ,... , n,** the function is called a
**unary, binary, ternary,... , n-ary** function. Examples: the area of a rectangle, with its length and
breadth as arguments, or the volume of a cylinder, given its radius and height, are binary functions.

How to pass multiple arguments to a function? This question arises because in the lambda calculus, the
mathematics underlying functional programming, all functions are supposed to be unary.

In the Gofer expression **f.x**, the dot "." is a binary operator whose left operand **f** is a function
and right operand **x** is the argument to which it is applied. (Therefore it appears that **f** is a unary function.)
In Gofer notation, we say in general that if **f: a->b, then x: a** and **f.x: b**. In other words, the type
of **x** has to be the same as the domain type of **f**, otherwise there is a type mismatch. Likewise, the
resulting type of **f.x** is the range type of **f**.

One way to pass multiple arguments to a unary function is to put the arguments into a tuple by placing
parentheses around them, and make this tuple the single argument to the function, like **x** in **f.x** above, e.g.,

```
area: Num.a => (a, a) -> a? area. (2, 3)
-- area of a rectangle 6 : Int
-- a can be any numerical type? area. (2.5, 2.0)
area. (len, br) = len * br 5.0 : Float
```
€: Write a binary function that computes the volume of a cylinder: **vol.(rad, ht) = pi * rad^2*ht.**

Q: What is the type of **vol?** Hint: Since **pi: Float**, the radius and height of the cylinder also have to be **Float**. (Recall: In Gofer you can perform arithmetic operations on **Int**, or on **Float**, but not on a combination.)

Rem: You can imagine the general case, when 3 or more arguments can be enclosed into a single tuple.

Using type **Num.a => (a,a)-> a** for function **area** can lead to a message (which I won’t try to explain) like:

```
ERROR "script0 8 .gs" (line 5): Unresolved top-level overloading
*** Binding : area_c
*** Inferred type : _5 -> _5 -> _
*** Outstanding context : Num._
```
So I modified **area** to **area1** and **area2**, where the sides of the rectangle are **Int** and **Float**, respectively.

```
area1: (Int, Int) -> Int?               area1. (5.0, 10.0)
area1. (len , br) = len * br            ERROR: Type error in application
? area 1. ( 5 , 10 )                    *** expression : area1.(5.0,10.0)
50 : Int                                *** term : (5.0,10.0)
                                        *** type : (Float,Float)
                                        *** does not match : (Int,Int)
area 2 : (Float, Float) -> Float        ? area 2. (5.0, 10.0)
area 2. (len , br) = len * br           50.0 : Float
```

$\underline{The}$ $\underline{curry}$ $\underline{and}$ $\underline{uncurry}$ $\underline{operator}$ $\underline{for}$ $\underline{binary}$ $\underline{function}$

We want to be able to supply arguments to a function without having to consolidate them into a tuple.
The **curry** operator does that for binary functions, and the **uncurry** operation is the inverse of **curry**.
Once we understand **curry**, its generalization can be used for arbitrary number of arguments.
(In comparison to **curry**, the **uncurry** operator is not so important.)

Given functions like **area1** and **area2** above, note how the **curry** and **uncurry** operators are applied.

```
area1c = curry.area1           -- The “curried” version of area
area1u = uncurry. area1c       -- The curried version is “uncurried” in turn
area 2 c = curry.area 2        -- The “curried” version of area
area 2 u = uncurry. area 2 c   -- The curried version is “uncurried”
```
The signature of the original **area1** is given below. Based upon it, the signatures of
**area1c** (the curried **area1**) and **area1u** (the uncurried **area1c**) are as follows:

```
? :t area1                        ? :t area1u
area1 : (Int,Int) -> Int          area1u : (Int,Int) -> Int
? :t area1c                       ? area1u -- “uncurried” area1c
area1c : Int -> Int -> Int        uncurry.area1c : (Int,Int) -> Int
? area1c -- “curried” area1       ? area1u. (8, 4)
curry.area1 : Int -> Int -> Int   32 : Int
```
€: Functions **area2, area2c** and **area2u** are defined in file **script0 9 .gs*. Find their types.

We can easily make sense of the types of functions **area1** and **area1u**, as they both have the type
**(Int, Int)->Int**. That is, if their argument is a pair of integers, they will return an integer result.

€: But what to make of the type of the curried function **area1c**, namely, **Int -> Int -> Int?**
Note that 1. there are two arrows in the type signature, rather than the usual one arrow, and further,
that 2. are no parentheses, i.e., a pair of integers are not to be provided.

Experiment 1 : Give a single integer as an argument to **area1c**, and observe what happens.

```
? area1c. 10
curry.area1.10 : Int -> Int
```
Outcome: If **area1c** is given a single integer as an argument, it returns a function of type **Int -> Int**.

Experiment 2 : Give function **area1c.10** another integer as an argument and see what happens.

```
? area1c. 10. 20
200 : Int
```
Outcome: **area1 c** computes the area of the rectangle with sides **10** and **20** , just as the original **area1** does.

The difference is that function area1 has to be given the two arguments together, in the pair **(10, 20)**
but the curried function **area1c** can take the arguments one at a time. Phrasing it in different words, we
can delay giving the second argument of **area1c**.

€: In file **script08.gs**, the function len10 has been defined as **len10 = area1c.10**. Find the
type of **len10**, give it an appropriate argument, and find out what the resulting value is.

```
? :t len10                     ? len10. 20 -- breadth 20
len10 : Int -> Int             200 : Int
? len10                        ? len10. 56
curry.area1.10 : Int -> Int    56 0 : Int
```

Rem: In an expression **f.x.y**, the dot associates to the left, i.e., **f.x.y = (f.x).y**, i.e., the dot on
the left is applied first—resulting in a unary function—and only then the dot on the right is applied next.
While **area1** is of type **Int->Int->Int**, the most general type of f is **a->b->c**, with **x:a** and **y:b**.

You would be able to argue to yourself that $\underline{if}$ $\underline{dot}$ $\underline{associate}$ $\underline{to}$ $\underline{the}$ $\underline{left,}$ $\underline{then}$ $\underline{arrow}$ $\underline{must}$ $\underline{associate}$ $\underline{to}$ $\underline{the}$ $\underline{right}$.

Just in case you cannot convince yourself about the arrow associating to the **right**, define two functions called
**left 1** and **right 1**. These functions can do something trivial, like returning the sum of the two parameters.

Place parentheses in the type definition of function right to force the arrow to associate to the right, thus:
**right: Int -> (Int -> Int)**. Similarly, place parentheses in function left to force the arrow to
associate to the left, thus **left: (Int -> Int) -> Int**. We want to see which function is type correct.

```
left: (Int -> Int) -> Int          right: Int -> (Int -> Int)
left. x. y = x+y                   right. x. y = x+y
```
We cannot even load the script into the interpreter, as there is a type error in the definition of function **left**.

```
ERROR "script08.gs" (line 14): Type error in function binding
*** term : left
*** type : a -> a -> a
*** does not match : (Int -> Int) -> Int
```
In other words, forcing left associativity of the arrow in function **left** leads to type incorrectness. SoI
commented out the definition of **left 1** so that the script can be loaded, and asked for the type of **right**.

```
? :t right
right : Int->Int->Int
? right. 10. 20
30 : Int
```
Observe: Something interesting has happened. In the type definition for function **right**, we had put
parentheses around the right arrow, thus **right 1 : Int -> (Int -> Int)**. But when we asked
for the type of **right** the interpreter removed the parentheses. This has happened because in the
interpreter’s view the parentheses are superfluous.

Conclusion: Forcing left associativity of the arrow by putting parentheses in **left** caused a type error,
but forcing right associativity of the arrow in **right** caused the interpreter to ignore the parentheses.
We have discovered an important fact: $\underline{when}$ $\underline{dot}$ $\underline{associate}$ $\underline{to}$ $\underline{the,}$ $\underline{arrow}$ $\underline{associate}$ $\underline{to}$ $\underline{the}$ $\underline{right}$.

$\underline{Problem}$ (Example of a binary function in uncurried and curried form): We want to raise an **Int** or a **Float**
to an integer power using the exponentiation operator "**^**". Below, and in file **script09.gs**, the curried form of
the function is called **power**, whereas the uncurried form carries an extra letter as a suffix, thus **poweru**.

```
power: Num.a => a - > Int -> a          poweru: Num.a => (a, Int) -> a
power. base. n = base ^ n               poweru(base, n) = base ^ n
? :t power                              ? :t poweru
power : Num.a => a -> Int -> a          poweru : Num.a => (a,Int) -> a
? :t power. 2
power.2 : Int -> Int – type variable a takes value Int
? :t power. 2.
power.2.0 : Int -> Float -- a takes value Float
? power. 2. 5
32 : Int
? power. 2.0. 5
32.0 : Float
```

Background: The builtin function exp is of type **Float->Float**. The value of **exp.x** is e (the base of
natural logarithms, value **2.71828**) raised to power **x**.

Functions **poweru** and **power** are generalizations of **exp**, in the sense that the base is not **e** but any **Int**
or **Float** value, and and they are variations of **exp**, in the sense that the base is raised to an integer power.
The values returned by **poweru** or **powerc** are of type **Num.a => a**, i.e., **Int** or **Float**, depending on
whether **base** is **Int** or **Float**.

€: Verify that function **expo**, defined in **script08.gs**, produces the same values as the builtin function **exp**.

Problem set (under construction):

Define **mult.m.n**, the multiplication of two integers **m** and **n**, without using the multiplication operator.
Hint: use a recursive function to implement multiplication as repeated addition.






