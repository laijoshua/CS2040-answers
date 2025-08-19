# CS2040-answers
My answers to CS2040's one day assignments &amp; take home assignments

## Ungraded Assignments:
1. [Autori](#Autori)
2. [Take Two Stones](#Take-Two-Stones)

## One Day Assignments
1. [Pea Soup & Pancakes](#Pea-Soup-&-Pancakes)
2. [T9 Spelling](#T9-Spelling)
3. [Sort of Sorting](#Sort-of-Sorting)

## Take Home Assignments
1. [Best Relay Team](#Best-Relay-Team)
2. [Card Trading](#Card-Trading)

## Autori
Great scientific discoveries are often named by the last names of scientists that made them. For example, the most popular asymmetric cryptography system, RSA was discovered by Rivest, Shamir and Adleman. Another notable example is the Knuth-Morris-Pratt algorithm, named by Knuth, Morris and Pratt. Scientific papers reference earlier works a lot and it’s not uncommon for one document to use two different naming conventions: the short variation (e.g. KMP) using only the first letters of authors last names and the long variation (e.g. Knuth-Morris-Pratt) using complete last names separated by hyphens. We find mixing two conventions in one paper to be aesthetically unpleasing and would like you to write a program that will transform long variations into short.

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

## Take Two Stones
Alice and Bob are playing a new game of stones. There are N stones placed on the ground, forming a sequence. The stones are labeled from 1 to N. Alice and Bob in turns take exactly two consecutive stones on the ground until there are no consecutive stones on the ground. That is, each player can take stone i and stone i+1, where 1<=i<=N-1. If the number of stone left is odd, Alice wins. Otherwise, Bob wins. Assume both Alice and Bob play optimally and Alice plays first, do you know who the winner is?

Input
The input contains an integer N (1<=N<=10000000), the number of stones.

Output
Output the winner, “Alice” or “Bob” (without the quotes), on a line.

```java
import java.util.*;

public class twostones {
    public static void main(String[] args) {
        // read user input
        Scanner scVar = new Scanner(System.in);
        // convert user input to int
        int x = scVar.nextInt();

        if (x % 2 == 0) {
            System.out.println("Bob");
        }
        else {
            System.out.println("Alice");
        }
    }
}
```

## Pea Soup & Pancakes
As a Swede, you hold a deep love for the traditional Thursday lunch of pea soup and pancakes. You love it so much, in fact, that you will eat it any meal it is available. You find yourself looking at the menus for all your favorite restaurants every day to see if this combination is available, and realized you can do this more easily with a program. Given a list of restaurant menus, decide where to eat.

Input
The first line of input contains a number n (1<=n<=10), the number of restaurants. Then follow the n restaurant menus. Each menu starts with a line containing a number k (1<=k<=10), the number of menu items for the day. The remainder of the menu consists of k+1 lines, each containing a nonempty string of at most 100 characters. The first of these lines is the restaurant name, and the rest are menu items. Strings consist only of lower case letters ‘a’-‘z’ and spaces, and they always start and end with a letter. All restaurant names are unique.

Output
Output a single line. If at least one restaurant has both “pea soup” and “pancakes” as menu items, output the name of the first of those restaurants, by the order in which the restaurants appear in the input. Otherwise, output “Anywhere is fine I guess”.

```java
import java.util.Scanner;

public class peasoup {
    public static void main(String[] args) {
        Scanner scVar = new Scanner(System.in);
        int store_no = Integer.parseInt(scVar.nextLine());
        boolean isfound = false;

        for (int i = 0; i < store_no; i++) {
            int item_no = Integer.parseInt(scVar.nextLine());
            String store_name = scVar.nextLine();
            boolean pea = false;
            boolean pan = false;
            for (int j = 0; j < item_no; j++) {
                String item_name = scVar.nextLine();
                if (item_name.equals("pea soup")) {
                    pea = true;
                } else if (item_name.equals("pancakes")) {
                    pan = true;
                }
                if (pea && pan) {
                    System.out.println(store_name);
                    isfound = true;
                    System.exit(0);
                }
            }
        }
        if (!isfound) {
            System.out.println("Anywhere is fine I guess");
        }
    }
}
```

## T9 Spelling

```java
import java.io.*;
import java.util.*;

public class t9spelling {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter pw = new PrintWriter(System.out);
        int cases = Integer.parseInt(br.readLine());

        //Dictionary<Character, Integer> dict = new Hashtable<>();
        HashMap<Character, Integer> dict = new HashMap<Character, Integer>();
        dict.put('a', 2);
        dict.put('b', 22);
        dict.put('c', 222);
        dict.put('d', 3);
        dict.put('e', 33);
        dict.put('f', 333);
        dict.put('g', 4);
        dict.put('h', 44);
        dict.put('i', 444);
        dict.put('j', 5);
        dict.put('k', 55);
        dict.put('l', 555);
        dict.put('m', 6);
        dict.put('n', 66);
        dict.put('o', 666);
        dict.put('p', 7);
        dict.put('q', 77);
        dict.put('r', 777);
        dict.put('s', 7777);
        dict.put('t', 8);
        dict.put('u', 88);
        dict.put('v', 888);
        dict.put('w', 9);
        dict.put('x', 99);
        dict.put('y', 999);
        dict.put('z', 9999);
        dict.put(' ', 0);

        for (int i = 1; i <= cases; i++) {
            pw.print("Case #" + i + ": ");
            String input = br.readLine();
            for (int j = 0; j < input.length() - 1; j++) {
                pw.print(dict.get(input.charAt(j))); //prints out number on keypad
                if (dict.get(input.charAt(j)) % 10 == dict.get(input.charAt(j + 1)) % 10) { //checks if digits are the same
                    pw.print(" "); //print space if same
                }
            }
            pw.print(dict.get(input.charAt(input.length()-1)));
            pw.print("\n");
        }
        pw.flush(); // need to flush!
    }
}
```

## Best Relay Team

```java
import java.util.*;

class Person {
    public String name;
    public double first;
    public double second;
    public Person (String name, double first, double second) {
        this.name = name;
        this.first = first;
        this.second = second;
    }
    public String getname() {return name;}
    public double getfirst() {return first;}
    public double getsecond() {return second;}
}
class second_comparator implements Comparator <Person> {
    public int compare (Person p1, Person p2) {
        return Double.compare(p1.getsecond(), p2.getsecond());
    }
    //public boolean equals (Object obj) {
        //return this == obj;
    }//end second_comparator

public class bestrelayteam {
    public static void main(String[] args) {
        second_comparator second_comp = new second_comparator();
        Scanner scVar = new Scanner(System.in); //take in input
        int n = scVar.nextInt(); //reads number of runners
        scVar.nextLine(); //skips to after newline char

        Person[] p = new Person[n];
        for (int i = 0; i < n; i++) {
            p[i] = new Person(scVar.next(), scVar.nextDouble(), scVar.nextDouble()); //add people to the array p
        }
        List<Person> list = Arrays.asList(p);
        Collections.sort(list, second_comp); //sort list of people by their 2nd leg timing
        double fastest_time = Double.MAX_VALUE; //safe maximum fastest time for comparison
        String[] fastest_team = new String[4]; //Array of members in the fastest team possible
        for (Person person : list) { //iterate thru the list
            double time = 0;
            String[] team = new String[4];
            Person p1 = person;
            time += p1.getfirst(); //add first leg's person time to time
            team[0] = p1.getname(); //add first leg's person name to team
            int no_of_runners_needed = 3; //3 more empty spots to fill up the team
            for (Person other : list) {//iterate thru the list
                if (person.getname().equals(other.getname())) { //checks if person is repeated twice
                    continue;
                } else { //if person is not repeated
                    time += other.getsecond(); //add fastest 2nd leg's person time to time
                    team[no_of_runners_needed] = other.getname(); //add fastest 2nd leg's person name to team
                    no_of_runners_needed--; //reduce the no of empty spots by 1
                }
                if (no_of_runners_needed == 0) { //when team is full
                    break;
                }
            }
            if ( fastest_time >= time) { //compare between time and fastest time
                fastest_time = time; //replace the fastest time with time
                fastest_team = team; //replace the fastest team with team
            }
        }
        System.out.println(fastest_time);
        for ( String name : fastest_team) {
            System.out.println(name);
        }
    }
}
```

## Sort of Sorting

```java
import java.io.*;
import java.util.*;

class letterComparator implements Comparator<String> {
    public int compare(String s1, String s2) {
        String substring1 = s1.substring(0, 2); //gets first 2 letters from s1
        String substring2 = s2.substring(0, 2); //gets first 2 letters from s2
        return substring1.compareTo(substring2);
        /*if (s1.charAt(0) < s2.charAt(0)) {
            return -1;
        } else if (s1.charAt(0) > s2.charAt(0)) {
            return 1;
        } else if (s1.charAt(0) == s2.charAt(0)) {
            if (s1.charAt(1) < s2.charAt(1)) {
                return -1;
            } else if (s1.charAt(1) > s2.charAt(1)) {
                return 1;
            } else if (s1.charAt(1) == s2.charAt(1)) {
                return 0;
            }
        }*/
    }
}

public class sortofsorting {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter pw = new PrintWriter(System.out);
        int words = Integer.parseInt(br.readLine());
        letterComparator letterComp = new letterComparator();

        if (words == 0) {
            System.exit(0); //terminates code when 0 is read
        } else {
            while (words != 0) {
                String[] arr = new String[words]; //Creates an array with size = words
                for (int i = 0; i < words; i++) { //Reads input for the names
                    arr[i] = br.readLine();
                }
                Arrays.sort(arr, letterComp); //sorts using comparator implemented
                //pw.print(Arrays.toString(arr));
                for (String word : arr) {
                    pw.println(word);
                }
                pw.print("\n");
                words = Integer.parseInt(br.readLine());
            }
        }
        pw.flush(); // need to flush!
    }
}
```

## Card Trading

```java
import java.util.*;

class Cards {
    public int type;
    public int qty;
    public long buy;
    public long sell;
    public Cards (int type, int qty, long buy, long sell) {
        this.type = type;
        this.qty = qty;
        this.buy = buy;
        this.sell = sell;
    }
    public int gettype() {return type;}
    public int getqty() {return qty;}
    public long getbuy() {return buy;}
    public long getsell() {return sell;}
}

class Cardscomparator implements Comparator<Cards> {
    public int compare(Cards c1, Cards c2) {
        long bs1 = c1.getbuy() * (2 - c1.getqty()) + c1.getsell() * c1.getqty();
        long bs2 = c2.getbuy() * (2 - c2.getqty()) + c2.getsell() * c2.getqty();
        return (int) (bs1 - bs2);
    }
}

public class cardtrading {
    public static void main(String[] args) {
        Scanner scVar = new Scanner(System.in);
        int N = scVar.nextInt();
        int T = scVar.nextInt();
        int K = scVar.nextInt();
        //scVar.nextLine();

        //String hand = scVar.nextLine();
        int[] arr_qty = new int[T];
        for (int i = 0; i < N; i++) {
            int x = scVar.nextInt();
            arr_qty[x-1] += 1;
        }
        /*for (int i = 0; i < hand.length(); i++) { //creates an array of qty per card type, where index = card type - 1
            if (hand.charAt(i) != ' ') {
                int x = Integer.parseInt(String.valueOf(hand.charAt(i)));
                arr_qty[x - 1] += 1;
            }
        }*/
        //System.out.println(Arrays.toString(arr_qty));

        Cards[] arr = new Cards[T];
        for (int j = 0; j < T; j++) { //creates an class Cards, where index = card type - 1
            int qty = arr_qty[j];
            long buy = scVar.nextLong();
            long sell = scVar.nextLong();
            arr[j] = new Cards(j+1, qty, buy, sell);
        }
        //System.out.println(Arrays.toString(arr));
        Cardscomparator CardsComp = new Cardscomparator();
        Arrays.sort(arr, CardsComp); //sorts the cards based off buy+sell price
        //System.out.println(Arrays.toString(arr));

        long profit = 0;
        for (int x = 0; x < K; x++) { //subtracts cost to buy cards needed
            int qty_needed = 2 - arr[x].getqty();
            profit -= qty_needed * arr[x].getbuy();
            //System.out.println(qty_needed);
            //System.out.println(arr[x].getbuy());
        }
        //System.out.println(profit);
        for (int y = K; y < arr.length; y++) { //adds money earned from selling extra cards
            profit += arr[y].getqty() * arr[y].getsell();
            //System.out.println(arr[y].getqty());
            //System.out.println(arr[x].getsell());
        }
        System.out.println(profit);
    }
}
```



