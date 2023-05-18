# 📘 Record

## Description

A record declaration specifies a new record class, a restricted kind of class that defines a simple aggregate of values. A record declaration implicitly creates instance fields, which are private and final. It also implicitly creates public accessor methods for these fields. Together, the fields and the corresponding methods are called record "components". An accessor method is a method with the same name as the record field and an empty formal parameter list. Such methods act as the getter methods for those fields. For example:

```java
public record Student(
  int id, //record component
  String name //record component
) //record header
{ } //record body
```

This is roughly equivalent to the following class:

```java
public final class Student extends Record
{
   private final int id; //component field
   private final String name; //component field
   public Student(int id, String name){  //canonical constructor
      this.id = id;
	  this.name = name;
   }
   
   public int id(){ return id; } //accessor
   public String name(){ return name; } //accessor
   
   //hashCode, equals, and toString methods are also provided by the compiler.
}
```

Observe that the accessor methods do not follow the JavaBeans convention (where a getter method is prefixed with get). Further observe that instance fields are final and the class does not have any setters.

### Basic Rules

* A record class is implicitly final. It is permitted for the declaration of a record class to redundantly specify the final modifier. **Records cannot be marked abstract, sealed, or non-sealed.**
* The direct superclass type of a record class is Record. Thus, a record cannot have an extends clause and so **it cannot extend any other class.**
* The serialization mechanism treats instances of a record class differently than ordinary serializable or externalizable objects. In particular, a record object is deserialized using the canonical constructor.

The body of a record declaration may contain constructor and member declarations as well as static initializers. But there are some restrictions as well:

* It cannot contain an instance field declaration (static fields are allowed).
* It cannot have an instance initializer (static initializers are allowed).
* It cannot have abstract or native methods.

### Constructors and methods

* canonical constructor:

```java
public record Student(int id, String name){
    public Student{ //no parameter list is specified here
	   if(id <0) throw new IllegalArgumentException();
	}
}
```

* non-canonical constructor

```java
public record Student(int id, String name){
    public Student(){ //a non-canonical constructor
        this(10); //this line or a call to the canonical constructor is required 
    }
    public Student(int id){ //another non-canonical constructor
        this(id, ""); //this line is required 
    }
    public Student(int id, String name){ //regular form canonical constructor
        this.id = id; this.name=name;
    }
}
```

**An important difference between a record and a regular class with respect to constructors is that the compiler provides a canonical constructor for a record**
