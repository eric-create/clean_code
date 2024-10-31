# Single-Responsibility Principle

Robert C. Martin:

> "Edsger Dijkstra [...] introduced the term: The Separation of Concerns. [...] the notions of Coupling and Cohesion were introduced [...]. I tried to consolidate these notions into a principle, which I called: The Single Responsibility Principle."

> "A module should be responsible to one, and only one, actor."

> "Every software component should have one and only one reason to change."

> "Gather together the things that change for the same reasons. Separate those things that change for different reasons."

Martin provides an [example](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html) where the CTO, CFO, and COO are **actors** that represent different **business functions**. He explains that is is to be prevented, that bugs enter the code of business function B when business function A actually requested the change - because this destroys trust.

Martin explained that SRP is based on a Separation of Concerns, respectively based on the notions Cohesion and Coupling.

## Separation of Concerns

### Cohesion

> "**Cohesion** is the degree to which the various parts of a software component are related"

> "Higher cohesion helps attain better adherence to the Single-Responsibility Principle"

### Coupling

> "**Coupling** is the degree of direct knowledge that one component has of another"

> "**Coupling** is defined as the level of interdependency between various software components"

#### Loose Coupling

- Reduces the likeliness that coupled components have to change when one component changes
    - Helps attain better adherence to the Single-Responsibility Principle
- Can help to
    - isolate problems when troubleshooting
    - simplify writing tests

## Responsibility Grouping

If you can group responsibilities in a sensible way, then do it. Else the complexity becomes unnecessary high.

## Example

```python
# app.py

class Shape: ...
class Square(Shape): ...
class Triangle(Shape): ...
def create_square(properties: dict) -> Square: ...
def create_triangle(properties: dict) -> Triangle: ...
def render(shape: Shape) -> None: ...
def rotate(shape: Shape) -> None: ...
```
---
If the contents of the files is small and they are likely not to grow, then IMO there is
nothing wrong with having the contents of `shapes_factory.py` in `shapes.py`.
```python
# shapes.py
# Responsible for defining the classes that represent shapes.
# No dependencies on (knows nothing about) other components.

class Shape: ...
class Square(Shape): ...
class Triangle(Shape): ...
```
```python
# shapes_factory.py
# Responsible for the complex creation process of the shape classes.
# Depends on (knows) the instantiation process and internals of `Square` and `Triangle`.

def create_square(properties: dict) -> Square: ...
def create_triangle(properties: dict) -> Triangle: ...
```
```python
# user_interface.py
# Responsible for displaying shapes in the UI.
# Depends on (knows) the internals of `shapes.Shape`.

def render(shape: Shape) -> None: ...
def rotate(shape: Shape) -> None: ...
```
