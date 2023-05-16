# Examples

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

```markdown
{% raw %}
{% hint style="danger" %}
**Danger hints** are good for highlighting destructive actions or raising attention to critical information.
{% endhint %}
{% endraw %}

```

```markdown
**Danger hints** are good for highlighting destructive actions or raising attention to critical information.
```

```markdown
{% raw %}
{% endhint %}
{% endraw %}
```

>

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