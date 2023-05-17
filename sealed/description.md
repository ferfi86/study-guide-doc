# description

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


{% hint style="danger" %}
**Danger hints** if the **permits** keyword is used then it is necessary to declare all the classes that we want to allow.
{% endhint %}

```java

public sealed class Vehicle permits Car{
}

final class Truck extends Vehicle{}

non-sealed class Car extends Vehicle{}

```

{% hint style="danger" %}
**Danger hints** Invalid declarate final a sealed class.
{% endhint %}

```java
final public sealed class Vehicle permits Car,Truck  {
}
```

{% hint style="danger" %}
**Danger hints** Invalid, It is necessary to declare the class as final or non-sealed,
when extends a sealed class.
{% endhint %}

```java

public sealed class Vehicle permits Car  {
}

class Car extends Vehicle{}

```



