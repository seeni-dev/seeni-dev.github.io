---
layout: post
title: "Programming With Shell for Automation"
---

Most of the programmers use programming languages such as C,C++, Python, Javascript. They use shell for many tasks . But most of them don’t know that they can program with shell for automating stuff that we find ourselves doing over and over again.

Though shell is limited in number of tokens, its power lies within the hands of the developer. He/She can write a program and install it and can use it shell just like any other command. How awesome is that ? So next time you need something like this, just make a coffee and start coding….

## Dive In

In this article , I will share some basic things about shell that is necessary to program. Before That, Lets do a quick Review of most used commands

**ls —** List the files and directories in the Current directory or in the given directory

**pwd —** Print the current working directory

**mkdir —** Make a directory with a name given in the current directory

**rm —** Remove specified files and folders

**seq —** Produce a sequence from start to stop with increment steps

**cd —** Change the current directory

**cat —** Prints the contents of the file

**echo —** Prints the string passed to it in the terminal

There are plenty of more commands and above are enough for enough to follow. If you need to learn more or study above commands in detail, Feel free to do so.

## Lets Get Started

Let’s Answer this question

> **What are things needed in a programming Language for basic stuff ?**

Answer is …

1. **Variables and Data types**
2. **Control Statements [ if, while, for ..]**
3. **Arithmetic Expressions and Boolean Expressions**

Well, above are the things needed to do basic automation But Shell has also got

1. **Arrays**
2. **Regular Expressions and related tools**
3. **I/O Functions for interacting with the user and the environment**
4. **Functions**
5. **Others**

## Start Note

shell programs are saved with .sh extension. They can be run with

```bash
#shellname program.sh
#Example
sh pro1.sh
```

There are many shells such as Z shell, C shell , bash, an lot of others. Most common is bash. Install any if you don’t have any. Ask your administrator for permission if you don’t have sufficient rights for executing programs.

> This article assumes that you are using bash and you have programming experience.

## Variables and Data types

Variables in shell can be set by simply typing `VARIABLE=VALUE`

Examples are

```bash
numberVariable=3;
realVariable=3.14;
stringVariable_1=pi;
stringVariable_2="pi";
```

---

## Control Statements [ if, while, for ..]

**If statement**

```bash
if[testCondition]
then
     #codeblock
fi

# OR

if[testCondition]
then
    #code block
else
   #codeblock
fi
```

**Examples**

```bash
if [ $a -eq $b ] # -eq tests whether left operand is equal to the right operand
then
   echo "a is equal to b"
else
   echo "a and b are not equal"
fi
```

**While Statement**

Like other programming Languages, syntax of while is shell is similar

```bash
while [ testCondition ]
do
    #code block
done
```

**Examples**

```bash
i=0
while [ $i -lt 10 ]
do
  echo $i;
  i=$((i+1));   #increment the varaible i
done
```

**For statement**

for statement syntax is

```bash
for variable in sequence
do
  #codeblock
done
```

variable is a usual variable whereas sequnce is a list of values separated by spaces.

**Example**

```bash
for i in 1 2 3 4 5 6
do
    echo $i;
done
```

---

## Arithmetic Expressions

Usual Arithmetic expressions are possible in shell which includes operators +, -, *, / and % and usual hard-cored values and variables (prefixed with $). You should enclose the arithmetic expressions in $((exp)) or any other standard formats. See the code snippet below…

```bash
i=5;
echo $((1+2));
echo $(($i-3));
echo $((7/2));
echo $((7%5));
```

## Boolean Expressions

This is the area where shell differs from most of the languages. Boolean expression is of of the form operand ***-relop*** operand

operand can be hard-core values or variables or themselves boolean expressions and relop can be one of the following:

  - **-lt** for less than operator ( “<” in other languages )
  - **-le** for less than or equal to operator ( “≤” in other languages )
  - **-gt** for greater than operator ( “>” in other languages )
  - **-ge** for greater than or equal to operator ( “≥” in other languages )
  - **-eq** for equal to operator ( “=” in other languages )
  - **-ne** for equal to operator ( “!=” in other languages )
  - **-a** for logical and operator ( “&&” in other languages )
  - **-o** for logical or operator ( “||” in other languages )
  - **! expression—** for not operator ( “! expression “ in other languages)

Look at the example below

```bash
if [ 3 -eq 3 -a 3 -ge 2 ]
then
    echo "work begins";
fi

if [ ! 3 -ge 4 ]
then 
    echo "! 3>4";
fi
```

That’s it for now. We can just take a moment and try to use it in a scenario. Next Part is my favourite. I always use that snippet for organizing Downloads Directory.

---

**Sample Program**

Lets us consider a simple scenario. Consider that you have all videos of every season of your favourite TV series in a single Folder and you want to organize them into seasons. Thanks to appropriate Naming (S0xE0x ) of episodes. Following snippet will do the job for you.

```bash
for i in `seq 5` #consider that we have 5 seasons 
do
    mkdir S$i;  # creating directory
    mv *S$i* S$i;  #moving the files
done
```

f this 4 line script can save that much work, Just think about what else you can do with it.

## End Note

So if you find yourselves typing some commands or tasks repeatedly, try to make it as a shell program.

Congratulations! You made it to the end. I hope you found this article useful.

Check out my profile to find more articles.

Thank You.

Happy Coding with Shell ………

*Originally published on [HackerNoon](https://hackernoon.com/programming-with-shell-7d3n02esk).*
