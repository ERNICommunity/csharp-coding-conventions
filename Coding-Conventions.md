# About
This document describes C# coding conventions we are using in ERNI Service Delivery Centers for solution projects.

This work is heavily inspired by [Steve McConnell's Code Complete](http://www.stevemcconnell.com/cc.htm), [Robert C. Martin's Clean Code](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882).

# General Principles

## Readability
Code is written once but read thousand times. Therefore our first principle is to always optimize code for reading.

## Simplicity
Change on one line should not require changing other lines.

## No dogma dogma
Every principle and every rule can be broken when there is a good reason for it **and** that reason is well documented.

# Conventions

## Indent style

### Tabs
Use tabs for indentation. Do not use spaces. Recommended tab size is 4, but always format code in a way that is compatible with arbitrary tab size.

### { Curly Braces } 
We are using [Allman style](https://en.wikipedia.org/wiki/Indent_style#Allman_style) of bracket placement.

> This style puts the brace associated with a control statement on the next line, indented to the same level as the control statement. Statements within the braces are indented to the next level.

**Never omit braces after control statement.**

```csharp
if (condition)
{ // this brace should be never omitted
    DoSomething();
}

DoSomethingElse();
```

Notable exception is nesting multiple using statements in a row. In that case, it is recommended to format code as follows:

```csharp
using (var sr = new StringReader(str))
using (var xtr = new XmlTextReader(sr))
{
    // ...
}
```

## Naming conventions
We follow Microsoft [Naming Guidelines](https://msdn.microsoft.com/en-us/library/ms229002.aspx). Since Microsoft Naming Guidelines are not very precise with nameing rules for constansts and private fields, we mention them separately.

### Constants
Constant names should follow Pascal casing irrespective of access modifier.

```csharp
private const int TheUniversalAnswer = 42;
public const double Pi = 3.14;
```

### Private  fields
Private filed should begin with lower case. This apply for static fields as well. Private fields should not start with underscore or any other prefix.

```csharp
private int x;
private static readonly myLock = new Object();
```

## Regions
Do not use `#region` blocks. Regions are made for hiding the code. Our code deserves not to be hidden, we are proud of it.

## Commenting conventions
Use XML comments (eg, `///<summary>...</summary>`) for documenting methods, classes and interfaces. 

Avoid block comments (i.e. `/* ... */`).

Use single line comments (i.e. `// ...`) for general commenting.

Do not commit dead code (i.e. code that is commented out).

Unless it is explicitly required by project, do not use documentary headers stating authorship, copyright or revision.
