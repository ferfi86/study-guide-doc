# Record reference sheet

## constructor

{% hint style="success" %}
**Success hints** Valid cases.
{% endhint %}

#### Simple declaration

```java
public record Student(int id, String name ){ 

}
```

#### Explicit canonical constructor

```java
record Student(int id, String name ){
    
    public Student(int id, String name){
        this.id = id + 1;
        this.name = name;
    }

}
```

#### Multiple constructors

```java
record Student(int id, String name ){

    public Student(int id, String name){
        this.id = id;
        this.name = name;
    }

    public Student(int id){
        this(id, "");
    }

    public Student(){
        this(10, "");
    }

}

```

{% hint style="danger" %}
**Danger hints** This is not valid.
{% endhint %}

```java
record Student(int id, String name ){

    public Student(int id, String name){
        this.id = id;
        this.name = name;
    }

    // THIS IS NOT VALID 
    // Non-canonical record constructor must delegate to another constructor
    public Student(){
        this.id = id;
        this.name = name;
    }

}
```

### Syntax

Records are implicitly final, but is redundant.

```java
public final record Student(int id, String name ){ 
}
```

A record may have at most one varargs component.

{% hint style="success" %}
**Success hints** Valid.
{% endhint %}

```java
public final record Student(int id, String... values ){ 
}
```

{% hint style="danger" %}
**Danger hints** Invalid.
{% endhint %}

```java
public final record Student(int... id, String... values ){ 
}
```



