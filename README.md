# CS2040-answers
My answers to CS2040's one day assignments &amp; take home assignments

## Sections:
1. [Autori](#Autori)

## Autori
```java
import java.util.*;

public class autori {
    public static void main(String[] args) {
        Scanner scVar = new Scanner(System.in);
        String x = scVar.next();
        String ans = x.substring(0,1);

        for (int i = 1; i < x.length(); i++){
            if(x.substring(i,i+1).equals("-")){
                ans = ans + x.substring(i+1,i+2);
            }
        }
        System.out.println(ans);
    }
}
```
