# Open-Closed Principle

> "software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification"

> "programs that conform to the open-closed principle are changed by adding new code, rather than by changing existing code" _("The Open-Closed Principle", 1996, Robert C. Martin)_

> "It should be clear that no significant program can be 100% closed [...] no matter how “closed” a module is, there will always be some kind of change against which it is not closed" _("The Open-Closed Principle", 1996, Robert C. Martin)_

> "this principle is at the heart of object oriented design. Conformance to this principle is what yeilds the greatest benefits claimed for object oriented technology" _("The Open-Closed Principle", 1996, Robert C. Martin)_

> "The primary mechanisms behind the Open-Closed principle are abstraction and polymorphism" _("The Liskov Substitution Principle", 1996, Robert C. Martin)_

> "You should be able to extend the behavior of a system without having to modify that system." _([4], 2014, Robert C. Martin)_

## History

- Invented by Bertrand Meyer in 1988
- Adapted by Robert C. Martin in 1996

## Explanation

Martin gives an example where he replaces an switch statement by using polymorphism and remarks that having many switch/if-else statements that must he changed causes problems.

Interfaces (or abstract base classes) should be extended by concrete classes when the implementation of new functionality is required. Existing concrete classes should not be changed.

Martin claims in [4] that a plugin architecture is the perfect implementation of the OCP.

### Misunderstanding?

For example in [2] the author presents an implementation strategy where they actually make a base class method final (Java) so that it really is closed for change in child classes. At the same time they invent non-final emtpy hook methods in the base class that are to be overridden in a child class when new behaviour must be added.

This seems like some kind of self-deception: The author closed the method `Draw` for change by the use of the key word `final` and at the same time they opened the method for change by inventing hooks. The following example is to illustrate that contradiction.
```java
public class Shape {
    String name;

    final public String Draw() {
        this.name = "Alice";
        // ...
        onFinish();
        return this.name;
    }

    protected void onFinish() {
        // Does nothing.
    }
}

public class Square extends Shape {
    protected void onFinish() {
        this.name = "Bob";
    }
}
```
_An alternative explanation is that the author failed to understand that OCP is about that behaviour should not change. One could think the author instead believes that OCP means that the text that codifies the behaviour should not change._

## Experiments

### OO Approach
```python
class Shape:
    @abc.abstractmethod
    def draw(self) -> None:
        raise NotImplementedError


class Circle(Shape):
    def draw(self) -> None:
        # ...


def draw_shapes(shapes: list[Shape]) -> None:
    for shape in shapes:
        shape.draw()
```

### Procedural Approach
```python
def draw_shapes(shapes: list[dict], draw: Callable) -> None:
    for shape in shapes:
        draw(shape)

def draw_circle(shape: dict) -> None:
    # ...

# ...
```

## Links

1. https://docs.google.com/a/cleancoder.com/viewer?a=v&pid=explorer&chrome=true&srcid=0BwhCYaYDn8EgN2M5MTkwM2EtNWFkZC00ZTI3LWFjZTUtNTFhZGZiYmUzODc1&hl=en
2. https://entwickler.de/webentwicklung/sealed-classes-das-ende-des-open-closed-principle
3. https://stackify.com/solid-design-open-closed-principle/
4. https://blog.cleancoder.com/uncle-bob/2014/05/12/TheOpenClosedPrinciple.html
