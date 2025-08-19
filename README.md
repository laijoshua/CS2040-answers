# CS2040-answers
My answers to CS2040's one day assignments &amp; take home assignments

## Sections:
1. [Autori](#Autori)

## Autori
Great scientific discoveries are often named by the last names of scientists that made them. For example, the most popular asymmetric cryptography system, RSA was discovered by Rivest, Shamir and Adleman. Another notable example is the Knuth-Morris-Pratt algorithm, named by Knuth, Morris and Pratt.

Scientific papers reference earlier works a lot and it’s not uncommon for one document to use two different naming conventions: the short variation (e.g. KMP) using only the first letters of authors last names and the long variation (e.g. Knuth-Morris-Pratt) using complete last names separated by hyphens.

We find mixing two conventions in one paper to be aesthetically unpleasing and would like you to write a program that will transform long variations into short.

Input
The first and only line of input will contain at most 
 characters, uppercase and lowercase letters of the English alphabet and hyphen (‘-’ ASCII 
). The first character will always be an uppercase letter. Hyphens will always be followed by an uppercase letter. All other characters will be lowercase letters.

Output
The first and only line of output should contain the appropriate short variation.

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
