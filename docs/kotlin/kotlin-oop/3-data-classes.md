# Data Classes

Sometimes, we need a very basic object to represent a set of structured data. In low-level programming languages, we commonly have "structs", in Java we have POJOs and records, in Kotlin we have data classes.

## Creating Data Classes

In Java, we have a lot of ways to create data classes, from POJOs to getters/setters to records. All of our Java examples will use the getters/setters for now, as it's the idiomatic method(leaving records as I am lazy enough).

For Example:
```java
public class User{
    private String name;
    private String email;
    private int age;

    public User(String name, String email, int age){
        this.name = name;
        this.email = email;
        this.age = age;
    }

    public void setName(String name){
        this.name = name;
    }

    public void setEmail(String email){
        this.email = email;
    }

    public void setAge(int age){
        this.age = age;
    }

    public String getName(){
        return name;
    }

    public String getEmail(){
        return email;
    }

    public int getAge(){
        return age;
    }

    @Override
    public String toString(){
        return "User(name="+name+",email="+email+",age="+age+")";
    }
}
```

This was horrifying. Let's see how Kotlin can make it better.

```kotlin
data class User(var name: String, var email, var age: Int)
```

Only a single line. Amazing. This data class has a constructor and a toString method, exactly like the Java version.