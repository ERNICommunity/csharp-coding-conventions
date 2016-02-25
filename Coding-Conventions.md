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
## Naming conventions
We follow Microsoft [Naming Guidelines](https://msdn.microsoft.com/en-us/library/ms229002.aspx).

Constants and private fields deserved to be mentioned separetely.

### Constants
Constant names should follow Pascal casing irrespective of access modifier.

```csharp
private const int TheAnswer = 42;
```

## Commenting conventions

 