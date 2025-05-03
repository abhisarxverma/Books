# **🤺 Chapter 2 - An Array of Seuquences**

## **Overview of Built-In-Sequences**

1. ***Container*** - Sequences that hold the items of different types, including the nested containers. They hold the ***references*** to the object it contains. E.g - tuple, list
2. ***flat*** - Sequences that hold items of single type. They hold the value of it's contents in it's own memory space, instead of distinct python objects. E.g - String, bytes, array.array

Another way of grouping :
1. ***Mutable*** - The contents can be changed after the initialization. E.g - List, array
2. ***Immutable*** - The contents cannot be changed after the initializaiton. E.g - String, Tuple, bytes

*Subclass hierarchy*
- Sequence (Immutable sequence) inherits from the *collection* and *reversed* super classes.
- Mutable Sequence inherits from the *Sequence* super class.

## **List Comprehension and Generator Expressions**

> *Python programmers use cool words for - List Comprehension - **listcomps** / Generator Expressions - **genexps***