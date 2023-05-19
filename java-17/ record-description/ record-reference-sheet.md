# 📎 Record reference sheet

## constructor

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

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f6d1">🛑</span> Invalid</summary>

```java
record Student(int id, String name ){

    public Student(int id, String name){
        this.id = id;
        this.name = name;
    }

    // THIS IS NOT VALID 
    // Non-canonical record constructor 
    //must delegate to another constructor
    public Student(){
        this.id = id;
        this.name = name;
    }

}
```

</details>

### Syntax

Records are implicitly final, but is redundant.

```java
public final record Student(int id, String name ){ 
}
```

A record may have at most one varargs component.

```java
public final record Student(int id, String... values ){ 
}
```

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f6d1">🛑</span> Invalid</summary>

```java
public final record Student(int... id, String... values ){ 
}
```



</details>
