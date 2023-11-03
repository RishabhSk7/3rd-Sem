> Marker interface: Interface with no member, example `Clonnable`

Syntax:
```
(<params>) -> {};
```

Example:
```java
(a,b) -> {expression};
```

Example in java:
```java
public class lambdaclass {
    public static void main(String[] args) {
        Thread t1 = new Thread(
            ()->{System.out.println("HIHI");}
        );
        t1.run();
        System.out.println(t1.getState());
    };
}

```

### Exceptions in Thread
- Checked Exceptions. Like: `Interrupted Exception`, `CloneNotSupportedException` 
- Unchecked Exception. like `Illegal Argument Exception`, `Illegal Thread state Exception`

> Shutdown Hook
> Runtime Class