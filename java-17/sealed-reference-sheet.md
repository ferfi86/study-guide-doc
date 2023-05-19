# 📗 Sealed

> Only classes and interfaces can be marked as sealed.
>
> Records are implicitly final, which means they cannot have any subclasses at all and so, it doesn't make sense to mark them as sealed.

### Syntax

with keyword permits

```java

public sealed class Vehicle permits Car,Truck  {
}

final class Truck extends Vehicle{}

non-sealed class Car extends Vehicle{}

```

without keyword permits

```java

public sealed class Vehicle  {
}

final class Truck extends Vehicle{}

non-sealed class Car extends Vehicle{}

```

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f6d1">🛑</span>  If the <strong>permits</strong> keyword is used then it is necessary to declare all the classes that we want to allow.</summary>

```java

public sealed class Vehicle permits Car{
}

//COmpilation Error because `Truck` 
//is not allowed in the sealed hierarchy
final class Truck extends Vehicle{}

non-sealed class Car extends Vehicle{}

```

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f6d1">🛑</span> <strong>Invalid</strong> declarate final a sealed class.</summary>

```java
final public sealed class Vehicle permits Car,Truck  {
}
```

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f6d1">🛑</span> <strong>Invalid</strong> It is necessary to declare the class as final or non-sealed, when extends a sealed class.</summary>

```java

public sealed class Vehicle permits Car  {
}

class Car extends Vehicle{}

```

</details>
