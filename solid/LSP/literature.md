# Literature

1. Interview, 2016, Barbara Liskov
    - https://www.youtube.com/watch?v=-Z-17h3jG0A&ab_channel=TuringAwardeeClips
    - Liskov remembers queue (lifo) and stack (fifo) confusion
    - at 3:09 reasons about that her informal rule is sorts of the backbone of reasonable subtyping.
2. "Data Abstraction and Hierarchy", Liskov, 1987
    - Liskov differentiates Implementation Hierarchy from Type Hierarchy. She explains the difference by using the terms "class" vs. "type". This though somehow raises the question what the inventors of the term "class" originally had in mind. She differentiates between implementation hierarchy and type hierarchy.
3. "The Liskov Substitution Principle", Robert C. Martin, 1996
4. "SOLID Principles: Introducing Software Architecture & Design", Sujith George, udemy.com
5. "Abstract Types Defined as Classes of Variables", Parnas, 1976
    - https://dl.acm.org/doi/pdf/10.1145/942574.807133
6. "A Behavioral Notion of Subtyping", Liskov, 1994
7. "Subtyping", Wikipedia
    - https://en.wikipedia.org/wiki/Subtyping

## 1. Interview, 2016, Barbara Liskov
---
> `Technical it's called behavioural subtyping.`

---
> `A subtype should behave like a supertype as far as you can tell by using the supertype methods. So it wasn't that it couldn't behave differently, it's just that as long as you limited your interaction with its objects to the supertype methods you would get the behaviours you expected.`


## 2. "Data Abstraction and Hierarchy", Liskov, 1987
---
> `What is wanted here is something like the following substitution property: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2, then S is a subtype of T.` (p. 25)

---
> `An inheritance mechanism can be used to implement a subtype hierarchy.` (p. 26)
**CAN** be used


## 3. "The Liskov Substitution Principle", Robert C. Martin, 1996
---
> `In statically typed languages [...] one of the key mechanisms that supports abstraction and polymorphism is inheritance.` (p. 1)

---
> `If there is a function which does not conform to the LSP, then that function uses a pointer or reference to a base class, but must know about all the derivatives of that base class. Such a function violates the Open-Closed principle because it must be modified whenever a new derivative of the base class is created.` (p. 2)


## 4. "SOLID Principles: Introducing Software Architecture & Design", Sujith George, udemy.com

It is actually not clear at all why Sujith George claims that TDA was implied by LSP. One should not have to ask for the type of an object? The program should be implemented in a way such that asking for object types is not required


## 5. "Abstract Types Defined as Classes of Variables", Parnas, 1976

Variables with identical `data representation` and `access` have the same `mode` - variables of different modes that can be substituted for another have the same `type`. Since different modes are by definition not identical, their successful substitution for another is restricted to certain contexts.

### Representation
---
> `A type is determined by the way that it has been represented in terms of more primitive types [12,14]. This is done repeatedly until one reaches some primitive data types - usually hardware (or compiler) implemented primitive types.` (p. 149)

### Mode
---
> `We refer to all variables that are identical with respect to data representation and access as being of the same mode.` (p. 150)

---
> `Mode defines an equivalence class on variables.` (p. 151)

### Type
---
> `As a result, we have chosen to consider a less restricted definition in which the concept of variable is considered primitive and types are defined as various equivalence classes of variables that may be legally and meaningfully substituted for one another.` (p. 150)

### Type vs. Mode
---
> `Each mode defines a simple class of variables, namely, variables whose substitution for each other in any context will not result in a compile-time error.` (p. 151)

---
> `We introduce the concept of type in order to define classes of variables whose substitution for each other is permitted by the compiler only in some restricted contexts.` (p. 151)

> `Since we need never distinguish between two variables of the same mode, types can be thought of as classes of modes.` (p. 151)

### Rep-Type
---
> `The above considerations lead us to the conclusion that a user should be able to declare as a type a group of modes that have the same representation and to define a Set of operations on variables of that type in terms of that representation. We call such a type a rep-type.` (p. 152)


## 6. "A Behavioral Notion of Subtyping", Liskov, 1994
---
> `What does it mean for one type to be a subtype of another? We argue that this is a semantic question having to do with the behavior of the objects of the two types: the objects of the subtype ought to behave the same as those of the supertype as far as anyone or any program using supertype objects can tell.` (p. 1811)


## 7. "Subtyping", Wikipedia
---
> `Subtyping and inheritance are independent (orthogonal) relationships. They may coincide, but none is a special case of the other.`
