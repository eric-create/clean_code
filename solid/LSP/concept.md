# Liskov Substitution Principle

Barbara Liskov herself states that the Liskov Substitution Principle should actually
should be called `Behavioral Subtyping` [1].

## What Is a Type

Variables with identical `data representation` and `access` have the same `mode` -
variables of different modes that can be `substituted` for another have the same
`type` [5]. Since different modes are by definition not identical, their successful
substitution for another is restricted to certain contexts.

## What Is a Subtype

Liskov argues that this "is a semantic question having to do with the behavior" of the
objects of different types [6]. She defines that type S is a subtype of type T, if an
object of type S `behaves` like an object of type T, when accessed using type T
methods [1,4].

## Robert C. Martin's LSP

The definition of a subtype discussed above does not name inheritance as a requirement and
in fact inheritance and subtyping are two concepts that are independent of each other [7]:
Type B can be derived from type A without being a subtype of A - when B overrides a method
that it inherited from A and thereby changes its behaviour. Robert C. Martin however asks
in [3] for a strict coupling of subtyping and inheritance as according to him else the
Open-Closed Principle was likely to be violated. 

> `If there is a function which does not conform to the LSP, then that function uses a
> pointer or reference to a base class, but must know about all the derivatives of that
> base class.` (p. 2)

Martin provides an example written in C++ that is imitated in Java here:
```java
public void DrawShape(Shape shape) {
    if (shape instanceof Square)
        DrawSquare((Square) shape);
    else if (shape instanceof Circle)
        DrawCircle((Circle) shape);
}
```
> `Such a function violates the Open-Closed principle because it must be
> modified whenever a new derivative of the base class is created.` (p. 2)

Firstly it is to be said that Martin talks about the LSP (remember it should say
Behavioral Subtyping) as if it was something that could be violated. However, as discussed
above the LSP defines a relation that can be present or not, but certainly not violated.

It seems that what Martin actually wanted to say, is that a tight coupling of inheritance
and behavioural subtyping helps to prevent the need for discrimination by type. If
instances of `Square` and `Circle` could be used in the same fashion when they should be
drawn, then `DrawShape` could directly implement this process.

Concluding, Martin's intention should be phrased like:

> Class B that is derived from superclass A should be a (behavioral) subtype of A, so that
> violating the OCP is prevented.
