# Liskov Substitution Principle

Barbara Liskov herself states that the Liskov Substitution Principle should actually should be called `Behavioral Subtyping` [1].

## What Is a Type

Variables with identical `data representation` and `access` have the same `mode` - variables of different modes that can be `substituted` for another have the same `type` [5]. Since different modes are by definition not identical, their successful substitution for another is restricted to certain contexts.

## What Is a Subtype

Liskov argues that this "is a semantic question having to do with the behavior" of the objects of different types [6]. She defines that type S is a subtype of type T, if an object of type S `behaves` like an object of type T, when accessed using type T methods [1,4].

## Robert C. Martin's LSP

The definition of a subtype discussed above does not name inheritance as a requirement and in fact inheritance and subtyping are two concepts that are independent from each other [7]: Type B can be derived from type A without being a subtype of A - when B overrides a method that it inherited from A and thereby changes its behaviour. Robert C. Martin however asks in [3] for a strict coupling of subtyping and inheritance as else the Open-Closed Principle is likely to be violated. Actually he does not explicitly state it like that, instead he mixes things up and implies this coupling, when he talks about the LSP (remember it should say Behavioral Subtyping) as if it was something that could be violated [3]. However as discussed above the LSP defines a relation that can be present or not, but certainly not violated.

It seems that Martin uses (his interpretation of the) LSP as a "side-kick" that is to support adherence to the OCP. To conclude, what Martin asks for when he talks about the LSP is:

> Class B that is derived from superclass A should be a (behavioral) subtype of A, so that violating the OCP is prevented.
