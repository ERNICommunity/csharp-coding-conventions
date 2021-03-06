# About
This document describes C# Coding Conventions we are using in ERNI Service Delivery Centers for solution projects.

This work is heavily inspired by [Steve McConnell's Code Complete](http://www.stevemcconnell.com/cc.htm), [Robert C. Martin's Clean Code](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882).

# General Principles

## Readability
Code is written once but read thousand times. Therefore our first principle is to always optimize code for reading.

## Simplicity
Change on one line should not require changing other lines.

## No dogma dogma
Every principle and every rule can be broken when there is a good reason for it **and** that reason is well documented.

## Maintenability
No matter which particular coding style is, once it is selected, it should be kept throughout the same project. Rule violations shall be treated as errors. Suppressed rules shall have a meanigful justification.

# Conventions

## Indent style

### Spaces
Use spaces for indentation. 

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

### Spaces
Separate elements by blank line.
Avoid more than one empty line at any time. For example, do not have two blank lines between members of a type.

Avoid spurious free spaces. For example avoid `if (someVar == 0)...`, where the dots mark the spurious free spaces. Consider enabling "View White Space (Ctrl+E, S)" if using Visual Studio, to aid detection.

## Naming conventions
We follow Microsoft [Naming Guidelines](https://msdn.microsoft.com/en-us/library/ms229002.aspx). Since Microsoft Naming Guidelines are not very precise with naming rules for constansts and private fields, we mention them separately.

### Constants
Constant names should follow Pascal casing irrespective of access modifier.

```csharp
private const int TheUniversalAnswer = 42;
public const double Pi = 3.14;
```

### Private  fields
Private field should begin with lower case. This apply for static fields as well. Private fields start with underscore prefix.

```csharp
private int _x;
private static readonly _myLock = new Object();
```

To distinguish between local and member variables use ```this.```

## Declarations

Declaration of types, type memebers (eg fields, properties, methods), parameters, and local variables can have several keywords. Follow these rules in declarations:

1. Always specify the visibility, even if it's the default (i.e. `private string foo`  not  `string foo`).
2. Visibility should be the first modifier (i.e. `public abstract` not `abstract public`).
3. When used on static fields, `readonly` should come after `static` (i.e. `static readonly` not `readonly static`).
4. Members of enums are sorted by value.

## References
1. Use `nameof(...)` instead of `"..."` whenever possible and relevant.
2. Use `this.` whenever possible to distinguish between local and member variables use.
3. Use `var` keyword instead of specific type whenever possible.
4. Use language keywords instead of BCL types (i.e. `int, string, float` instead of `Int32, String, Single`, etc) for both type references as well as method calls (i.e. `int.Parse` instead of `Int32.Parse`).

## Namespaces
Namespace imports should be specified at the top of the file, outside of `namespace` declarations and should be sorted alphabetically, but `System` namespaces must be before any other namespaces.

## Class Organization
Order type members in following order inside file:

1. Constants
2. Fields
3. Properties
4. Events
5. Methods
6. Inner Types

Type members of the same kind should be sorted by visibility, at first public, then protected and then private members.

There are exceptions to this rule, if members are strongly related to each other. For example:
- Properties and value storage fields.
- Depencency properties and related .NET properties.
- Events and related `protected virtual` methods.
- The private utilities which are called out of a public function should stand immediately behind the public function as the step-down rule instructs.

## Regions
Do not use `#region` blocks. Regions are made for hiding the code. Our code deserves not to be hidden, we are proud of it.

## Commenting conventions
Use XML comments (eg, `///<summary>...</summary>`) for documenting methods, classes and interfaces. 

Avoid block comments (i.e. `/* ... */`).

Use single line comments (i.e. `// ...`) for general commenting.

Do not commit dead code (i.e. code that is commented out).

Unless it is explicitly required by project, do not use documentary headers stating authorship, copyright or revision.
