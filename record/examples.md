# Examples

#### Simple declaration

```
public record Student(int id, String name ){ 

}
```

#### Explicit canonical constructor

```
record Student(int id, String name ){
    
    public Student(int id, String name){
        this.id = id + 1;
        this.name = name;
    }

}
```

#### Multiple constructors

```
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

> This is not valid

```
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
