# CS2040-answers
My answers to CS2040's one day assignments &amp; take home assignments, all of which are problems taken from Kattis.

## Ungraded Assignments:
1. [Autori](#Autori)
2. [Take Two Stones](#Take-Two-Stones)

## One Day Assignments
1. [Pea Soup & Pancakes](#Pea-Soup-&-Pancakes)
2. [T9 Spelling](#T9-Spelling)
3. [Sort of Sorting](#Sort-of-Sorting)
4. [Coconut Splat](#Coconut-Splat)
5. [Conformity](#Conformity)
6. [Assigning Workstations](#Assigning-Workstations)
7. [Kattis's Quest](#Kattis's-Quest)
8. [Weak Vertices](#Weak-Vertices)
9. [Islands](#Islands)
10. [Lost Map](#Lost-Map)
11. [Human Cannonball Run](#Human-Cannonball-Run)

## Take Home Assignments
1. [Best Relay Team](#Best-Relay-Team)
2. [Card Trading](#Card-Trading)
3. [Join Strings](#Join-Strings)
4. [Teque](#Teque)
5. [Almost Union Find](#Almost-Union-Find)
6. [Nicknames](#Nicknames)
7. [Millionaire Madness](#Millionaire-Madness)
8. [Dominos](#Dominos)

## Autori
Great scientific discoveries are often named by the last names of scientists that made them. For example, the most popular asymmetric cryptography system, RSA was discovered by Rivest, Shamir and Adleman. Another notable example is the Knuth-Morris-Pratt algorithm, named by Knuth, Morris and Pratt. Scientific papers reference earlier works a lot and it’s not uncommon for one document to use two different naming conventions: the short variation (e.g. KMP) using only the first letters of authors last names and the long variation (e.g. Knuth-Morris-Pratt) using complete last names separated by hyphens. We find mixing two conventions in one paper to be aesthetically unpleasing and would like you to write a program that will transform long variations into short.

Input
The first and only line of input will contain at most 100 characters, uppercase and lowercase letters of the English alphabet and hyphen (‘-’ ASCII 45). The first character will always be an uppercase letter. Hyphens will always be followed by an uppercase letter. All other characters will be lowercase letters.

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
Alice and Bob are playing a new game of stones. There are N stones placed on the ground, forming a sequence. The stones are labeled from 1 to N. Alice and Bob in turns take exactly two consecutive stones on the ground until there are no consecutive stones on the ground. That is, each player can take stone $`i`$ and stone $`i+1`$, where $`1\le i\le N-1`$. If the number of stone left is odd, Alice wins. Otherwise, Bob wins. Assume both Alice and Bob play optimally and Alice plays first, do you know who the winner is?

Input
The input contains an integer N ($`1\le N\le 10000000`$), the number of stones.

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
The first line of input contains a number $`n`$ ($`1\le n\le 10`$), the number of restaurants. Then follow the n restaurant menus. Each menu starts with a line containing a number $`k`$ ($`1\le k\le 10`$), the number of menu items for the day. The remainder of the menu consists of $`k+1`$ lines, each containing a nonempty string of at most 100 characters. The first of these lines is the restaurant name, and the rest are menu items. Strings consist only of lower case letters ‘a’-‘z’ and spaces, and they always start and end with a letter. All restaurant names are unique.

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
The Latin alphabet contains 26 characters and telephones only have ten digits on the keypad. We would like to make it easier to write a message to your friend using a sequence of keypresses to indicate the desired characters. The letters are mapped onto the digits as shown below. To insert the character ‘B’ for instance, the program would press “22”. In order to insert two characters in sequence from the same key, the user must pause before pressing the key a second time. The space character ‘ ’ should be printed to indicate a pause. For example, “2 2” indicates “AA” whereas “22” indicates “B”.

Input
The first line of input gives the number of cases, $`N`$ ($`1\le N\le 100`$). $`N`$ test cases follow. Each case is a line of text containing the desired message, which will be at most 1000 characters long. Each message will consist of only lowercase characters ‘a’–‘z’ and space characters ‘ ’. Pressing zero emits a space.

Output
For each test case, output one line containing “Case #x:" followed by the message translated into the sequence of key presses.

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
You are the coach of the national athletics team and need to select which sprinters should represent your country in the 4 x 100 m relay in the upcoming championships. As the name of the event implies, such a sprint relay consist of 4 legs, 100 meters each. One would think that the best team would simply consist of the 4 fastest 100 m runners in the nation, but there is an important detail to take into account: flying start. In the 2nd, 3rd and 4th leg, the runner is already running when the baton is handed over. This means that some runners – those that have a slow acceleration phase – can perform relatively better in a relay if they are on the 2nd, 3rd or 4th leg. You have a pool of runners to choose from. Given how fast each runner in the pool is, decide which four runners should represent your national team and which leg they should run. You are given two times for each runner – the time the runner would run the 1st leg, and the time the runner would run any of the other legs. A runner in a team can only run one leg.

Input
The first line of input contains an integer n, the number of runners to choose from ($`4\le n\le 500`$). Then follow $`n`$ lines describing the runners. The $`i`$’th of these lines contains the name of the $`i`$’th runner, the time $`a_i`$ for the runner to run the 1st leg, and the time $`b_i`$ for the runner to run any of the other legs ($`8\le b_i\le a_i<20`$). The names consist of between 2 and 20 (inclusive) uppercase letters ‘A’-‘Z’, and no two runners have the same name. The times are given in seconds with exactly two digits after the decimal point.

Output
First, output a line containing the time of the best team, accurate to an absolute or relative error of at most $`10^{-9}`$. Then output four lines containing the names of the runners in that team. The first of these lines should contain the runner you have picked for the 1st leg, the second line the runner you have picked for the 2nd leg, and so on. Any solution that results in the fastest team is acceptable.

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
Can you believe school has already started? It seems like we were just finishing last semester. Last semester was tough because the administration had a hard time keeping records of all the students in order, which slowed everything down. This year, they are going to be on top of things. They have recognized that you have the skills to help them get into shape with your programming ability, and you have volunteered to help. You recognize that the key to getting to student records quickly is having them in a sorted order. However, they don’t really have to be perfectly sorted, just so long as they are sort-of sorted.

Write a program that sorts a list of student last names, but the sort only uses the first two letters of the name. Nothing else in the name is used for sorting. However, if two names have the same first two letters, they should stay in the same order as in the input (this is known as a ‘stable sort’). Sorting is case sensitive based on ASCII order (with uppercase letters sorting before lowercase letters, i.e., $`A<B<...<Z<a<b<...<z`$).

Input
Input consists of a sequence of up to 500 test cases. Each case starts with a line containing an integer $`1\le n\le 200`$. After this follow $`n`$ last names made up of only letters (a–z, lowercase or uppercase), one name per line. Names have between 2 and 20 letters. Input ends when $`n`$=0.

Output
For each case, print the last names in sort-of-sorted order, one per line. Print a blank line between cases.

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
Anthony and Cora are playing Dominion, their favorite card game. In Dominion, there are $`T`$ different card types, and each player has a set of cards (known as a deck). A deck $`D`$ is said to have $`C`$ combos if $`C`$ is the largest integer such that for $`C`$ different card types in the game, $`D`$ contains at least two cards of that type. Anthony currently has $`N`$ cards and he wants to trade cards with Cora such that he’ll have a deck with exactly $`K`$ combos.

For each card type $`T`$ ($`1\le i \le T`$), Anthony can choose to perform at most one transaction. There are two types of transactions:
1. Buy up to two cards of $`i^{th}`$ type from Cora at $`a_i`$ coins each
2. Sell all his cards of $`i^{th}`$ type for $`b_i`$ coins each

Anthony wants to maximize his profit while obtaining a complete deck. Anthony is willing to spend coins in order to obtain a complete deck if necessary, but of course he wants to minimize his spending in that case. Note that he doesn’t care about keeping the rest of his cards which don’t contribute to the complete deck.

Anthony has hired you to help him calculate how much money he can make if he chooses the optimal strategy for obtaining enough combos. If he has to spend money, output a negative number.

Input
The first line of the input contains three integers $`N, T`$ and $`K`$, $`1\le K\le T\le100000`$, $`1\le N\le 2T`$.

The next line is a list of $`N`$ integers representing the cards in Anthony’s deck. Each integer on this line is between 1 and $`T`$ inclusive. It is guaranteed no integers appear more than twice.

Finally, each of the next $`T`$ lines of the input contains two integers each. The $`i^{th}`$ line contains $`a_i`$ and $`b_i`$, $`1\le a_i,\ b_i\le10^9`$, corresponding to the price of buying and selling a card of type $`i`$.

Output
Output a single integer denoting Anthony’s profit assuming he trades optimally.

Explanation of Sample Input
In the first example, Anthony should sell two of card 1 and buy one of card 2 and one of card 3 for a net profit of 10 coins. If he chooses to sell one of card 3 and buy one of card 2, then he’ll end up spending 20 coins.

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
## Coconut Splat
Coconut Splat is one of Theta’s favorite counting-out games. It goes like this: initially, all players stand in a circle with their hands folded together (like an intact coconut). In clockwise order, one player touches the hands of the other players and says the rhyme: “Co-co-nut, Co-co-nut, Co-co-nut, Splat!” At each syllable, the player touches a hand, and the player whose hand or hands is touched last takes one of the following actions:
1. If the player’s hands are still folded, they are split into two fists (the coconut is cracked in two halves). The next round starts with the fist that is the first half of the coconut, then the second half, then going to the next player.
2. If a fist is touched last, the hand is turned palm down (the milk spills out). The next round starts with the next hand in clockwise order, which could be the other hand of the same player, or it could be the hand or folded hands belonging to the next player.
3. If a hand that is already turned palm down is touched last, the player to whom it belongs puts the hand behind their back and this hand won’t be counted in the following rounds. The next round starts with the next hand in clockwise order as in the previous case.
4. If a player has put both of their hands behind their back, that player is out of the game. The game ends when there is only one player left.

The hand or hands of the player doing the counting are taken into account (for instance, the counting player touches their thigh when it would be her turn to be touched).

There are variations of this game, for instance, some kids say “Coconut, coconut, crack your nut!” instead, which has only 9 instead of 10 syllables as in the “Co-co-nut, Co-co-nut, Co-co-nut, Splat!” rhyme.

There are $`n`$ players, and counting always starts with the folded hands of player 1. For instance, in the first round, if the rhyme has 3 syllables, player 3 would be the one to first crack their coconut into two fists.

Write a program that determines the winner of the counting-out game based on the number of players and based on the number of syllables in the rhyme that is used!

Input
The input consists of a single test case with two numbers $`s`$ ($`0\le s\le 100`$) and $`n`$ ($`2\le n\le100`$) denoting the number of syllables in the rhyme and the number of players, respectively.

Output
Output a single integer $`p`$ ($`1\le p\le n`$), the number of the player who is left.

```java
import java.io.*;
import java.util.*;

class Person {
    public int no;
    public int hand;
    public Person (int no, int hand) {
        this.no = no;
        this.hand = hand;
        // 0 if folded
        // 1 if fist
        // 2 if palm down
    }
    public int getNo() {return no;}
    public int getHand() {return hand;}
    public void setHand(int new_hand) {this.hand = new_hand;}
}

public class coconutsplat {
    public static void main(String[] args) throws IOException {
        Reader sc = new Reader();
        PrintWriter pw = new PrintWriter(System.out);
        int syllables = sc.nextInt() ;
        int players = sc.nextInt();

        ArrayList<Person> arrlst = new ArrayList<Person>();
        for (int i = 0; i < players; i++) {
            arrlst.add(new Person(i+1, 0));
        }
        
        int idx = 0;
        while (arrlst.size() > 1) {
            idx =  (idx + syllables - 1) % arrlst.size();
            if (arrlst.get(idx).getHand() == 0) { //if hand is folded, change to fist and add another fist
                arrlst.get(idx).setHand(1);
                int person_no = arrlst.get(idx).getNo();
                arrlst.add(idx, new Person(person_no, 1));
            } else if (arrlst.get(idx).getHand() == 1) { //if hand is fist, change to palm down
                arrlst.get(idx).setHand(2);
                idx += 1;
            } else if (arrlst.get(idx).getHand() == 2) { //if hand is palm down, remove from game
                arrlst.remove(arrlst.get(idx));
            }
        }
        pw.println(arrlst.get(0).getNo());
        pw.flush(); // need to flush!
    }

    static class Reader {
        final private int BUFFER_SIZE = 1 << 16;
        private DataInputStream din;
        private byte[] buffer;
        private int bufferPointer, bytesRead;
        public Reader() {
            din = new DataInputStream(System.in);
            buffer = new byte[BUFFER_SIZE];
            bufferPointer = bytesRead = 0;
        }
        public int nextInt() throws IOException {
            int ret = 0;
            byte c = read();
            while (c <= ' ') c = read();
            boolean neg = (c == '-');
            if (neg) c = read();
            do {
                ret = ret * 10 + c - '0';
            } while ((c = read()) >= '0' && c <= '9');
            return neg ? -ret : ret;
        }
        private void fillBuffer() throws IOException {
            bytesRead = din.read(buffer, bufferPointer = 0, BUFFER_SIZE);
            if (bytesRead == -1) buffer[0] = -1;
        }
        private byte read() throws IOException {
            if (bufferPointer == bytesRead) fillBuffer();
            return buffer[bufferPointer++];
        }
    }
}
```

## Join Strings
You are given a collection of $`N`$ non-empty strings, denoted by $`S_1,...,S_n`$. Then you are given $`N-1`$ operations which you execute in the order they are given. The $`i^{th}`$ operation is has the following format: ‘$`ab`$’ (1-based indexing, without the quotes), which means that you have to make the following changes:
1. $`S_a=S_a+S_b`$, i.e. concatenate $`a^{th}`$ string and $`b^{th}`$ string and store the result in $`a^{th}`$ string
2. $`S_b`$ = "", i.e. make the $`b^{th}`$ string empty, after doing the previous step.

You are ensured that after the $`i^{th}`$ operation, there will be no future operation that will be accessing $`S_b`$. Given these operations to join strings, print the last string that will remain at the end of this process.

Input
The first line contains an integer $`N`$ ($`1\le N \le 10^5`$) denoting the number of strings given. Each of the next $`N`$ lines contains a string denoting the $`S_i`$. All the characters in the string $`S_i`$ are lowercase alphabets from ‘a’ to ‘z’. The total number of characters over all the strings is at most $`10^6`$, i.e $`\sum^N_{i=1}|S_i|\le10^6`$, where $`|S_i|`$ denotes the length of the $`i^{th}`$ string. After these $`N`$ strings, each of the next $`N-1`$ lines contain two integers $`a`$ and $`b`$, such that $`a\ne b`$ and $`1\le a,\ b\le N`$ denoting the $`i^{th}`$ operation.

Output
Print the last string which remains at the end of the $`N-1`$ operations.

Warning
The I/O files are large. Please use fast I/O methods.

```java
import java.io.*;
import java.util.*;

public class joinstrings {
    public static void main(String[] args) throws IOException {
        FastIO fio = new FastIO();
        int no_words = fio.nextInt();

        TailedLL[] arr = new TailedLL[no_words]; //creates an empty tailed linked list with the size specified
        for (int i = 0; i < no_words; i++) {
            ListNode node = new ListNode(fio.nextLine()); //creates a node storing word
            TailedLL list = new TailedLL();
            list.insertNode(node); //adds the node into a tailed linked list
            arr[i] = list; //adds the tailed linked list containing the node into the larger tailed linked list
        }

        int print_idx = 0;
        for (int j = 0; j < no_words - 1; j++) {
            int a = fio.nextInt() - 1;
            int b = fio.nextInt() - 1;
            arr[a].insertLL(arr[b]); //links the 2 linked lists tgt
            print_idx = a; //changes the index to print to the first no of the input line
        }

        TailedLL list_to_print = arr[print_idx];
        ListNode cur = list_to_print.head; //creates a pointer pointing to the head of the tailed linked list to print
        fio.print(cur.getItem());
        for (int y = 0; y < list_to_print.no_nodes - 1; y++){
            cur = cur.next; //moves to neighbour
            fio.print(cur.getItem());
        /*for (TailedLL list : arr) {
            ListNode cur = list.head;
            fio.print(cur.getItem());
            for (int k = 0; k < list.no_nodes - 1; k++){
                cur = cur.next;
                fio.print(cur.getItem());*/
        }
        fio.close();
    }
}
class ListNode {//from lecture notes
    public String word;
    public ListNode next;
    public ListNode (String word) {
        this.word = word;
        this.next = null;
    }
    public ListNode getNext() {return next;}
    public void setNext(ListNode n) {this.next = n;}
    public String getItem() {return word;}
    public void setItem(String word) {this.word = word;}
}

class TailedLL {
    public ListNode head;
    public ListNode tail;
    public int no_nodes;
    public TailedLL() {
        no_nodes = 0;
    }
    public void insertNode (ListNode node) {
        node.setNext(this.head);
        this.head = node;
        this.tail = head;
        no_nodes++;
    }
    public void insertLL (TailedLL list) {
        tail.next = list.head;
        tail = list.tail;
        no_nodes += list.no_nodes;
    }
}

class FastIO extends PrintWriter {
    BufferedReader br;
    StringTokenizer st;

    public FastIO() {
        super(new BufferedOutputStream(System.out));
        br = new BufferedReader(new InputStreamReader(System.in));
    }

    String next() {
        while (st == null || !st.hasMoreElements()) {
            try {
                st = new StringTokenizer(br.readLine());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        return st.nextToken();
    }

    int nextInt() {
        return Integer.parseInt(next());
    }

    long nextLong() {
        return Long.parseLong(next());
    }

    double nextDouble() {
        return Double.parseDouble(next());
    }

    String nextLine() {
        String str = "";
        try {
            str = br.readLine();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return str;
    }
}
```

## Teque
You have probably heard about the deque (double-ended queue) data structure, which allows for efficient pushing and popping of elements from both the front and back of the queue. Depending on the implementation, it also allows for efficient random access to any index element of the queue as well. Now, we want you to bring this data structure up to the next level, the teque (triple-ended queue)!

The teque supports the following four operations:
1. push_back x: insert the element $`x`$ into the back of the teque.
2. push_front x: insert the element $`x`$ into the front of the teque.
3. push_middle x: insert the element $`x`$ into the middle of the teque. The inserted element $`x`$ now becomes the new middle element of the teque. If $`k`$ is the size of the teque before the insertion, the insertion index for $`x`$ is $`\frac{k+1}{2}`$ (using 0-based indexing).
4. get i: prints out the $`i^{th}`$ index element (0-based) of the teque.

Input
The first line contains an integer $`N`$ ($`1\le N\le 10^6`$) denoting the number of operations for the teque. Each of the next $`N`$ lines contains a string $`S`$, denoting one of the above commands, followed by one integer $`x`$. If $`S`$ is a push_back, push_front, or push_middle command, $`x`$ ($`1\le x\le 10^9`$), else for a get command, $`i`$ ($`0\le i \le \text{size of teque}-1`$). We guarantee that the teque is not empty when any get command is given.

Output
For each get i command, print the value inside the $`i^{th}`$ index element of the teque in a new line.

Warning
The I/O files are large. Please use fast I/O methods.

```java
import java.io.*;
import java.util.*;

public class Teque {
    public static void main(String[] args) throws IOException {
        FastIO fio = new FastIO();
        int no_ops = fio.nextInt();

        HashMap<Integer, Integer> front_half = new HashMap<>(); //1st half of teque
        HashMap<Integer, Integer> back_half = new HashMap<>(); //2nd half of teque
        int front_head = 0;
        int front_tail = 0;
        int back_head = 0;
        int back_tail = 0;

        for (int i = 0; i < no_ops; i++) {
            String cmd = fio.next();
            int no = fio.nextInt();

            if (cmd.equals("push_front")) { //insert at the front of 1st hashmap ie key is as low as possible
                front_head -= 1;
                front_half.put(front_head, no);
            } else if (cmd.equals("push_back")) { //insert at the end of 2nd hashmap ie key is as high as possible
                back_half.put(back_tail, no);
                back_tail += 1;
            } else if (cmd.equals("push_middle")) { //insert at (k+1)/2 index of entire teque
                if (front_half.size() == back_half.size()) { //insert at the start of 2nd hashmap ie key is as low as possible
                    back_head -= 1;
                    back_half.put(back_head, no);
                } else { //insert at the end of 1sr hashmap ie key is as low as possible
                    front_half.put(front_tail, back_half.get(back_head));
                    front_tail += 1;
                    back_half.put(back_head, no);
                }
            } else if (cmd.equals("get")) {
                if (no >= front_half.size()) { //find out which hashmap the key is in
                    int back_key = no - front_half.size() + back_head;
                    fio.println(back_half.get(back_key));
                } else {
                    int front_key = no + front_head;
                    fio.println(front_half.get(front_key));
                }
            }
            //rebalancing the 2 hashmap to make sure front_tail or back_head is in the middle
            if (front_half.size() > back_half.size()) { //if 1st half bigger than 2nd half, remove end of 1st half and insert in start of 2nd half
                front_tail -= 1;
                back_head -= 1;
                back_half.put(back_head,front_half.get(front_tail));
                front_half.remove(front_tail);;
            } else if (front_half.size()  < back_half.size() - 1) { //if 1st half smaller than 2nd half, remove start of 2nd half and insert in end of 1st half
                front_half.put(front_tail, back_half.get(back_head));
                front_tail += 1;
                back_head += 1;
                back_half.remove(back_head - 1);
            }
        }
        fio.close();
    }
}


class FastIO extends PrintWriter {
    BufferedReader br;
    StringTokenizer st;

    public FastIO() {
        super(new BufferedOutputStream(System.out));
        br = new BufferedReader(new InputStreamReader(System.in));
    }

    String next() {
        while (st == null || !st.hasMoreElements()) {
            try {
                st = new StringTokenizer(br.readLine());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        return st.nextToken();
    }

    int nextInt() {
        return Integer.parseInt(next());
    }

    long nextLong() {
        return Long.parseLong(next());
    }

    double nextDouble() {
        return Double.parseDouble(next());
    }

    String nextLine() {
        String str = "";
        try {
            str = br.readLine();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return str;
    }
}
```

## Conformity
Frosh commencing their studies at Waterloo have diverse interests, as evidenced by their desire to take various combinations of courses from among those available.

University administrators are uncomfortable with this situation, and therefore wish to offer a conformity prize to frosh who choose one of the most popular combinations of courses. How many frosh will win the prize?

Input
The input begins with an integer $`1\le n\le 10000`$, the number of frosh. For each frosh, a line follows containing the course numbers of five distinct courses selected by the frosh. Each course number is an integer between 100 and 499.

Output
The popularity of a combination is the number of frosh selecting exactly the same combination of courses. A combination of courses is considered most popular if no other combination has higher popularity. Output a single line giving the total number of students taking some combination of courses that is most popular.

```java
import java.io.*;
import java.util.*;

public class conformity {
    public static void main(String[] args) throws IOException {
        Reader sc = new Reader();
        PrintWriter pw = new PrintWriter(System.out);
        int no_students= sc.nextInt();

        HashMap<String, Integer> dict = new HashMap<>();
        for (int i = 0; i < no_students; i++) {
            int[] subject_combi = new int[5];
            for (int j = 0; j < 5; j++) {
                int subject = sc.nextInt();
                subject_combi[j] = subject;
            }
            Arrays.sort(subject_combi);
            String x = Arrays.toString(subject_combi);
            //pw.println(Arrays.toString(subject_combi));
            if (dict.containsKey(x)) {
                int value = dict.get(x);
                dict.put(x, value + 1);
                //dict.get(subject_combi) += 1;
            } else {
                dict.put(x, 1);
            }
        }
        Collection<Integer> arr = dict.values();
        ArrayList<Integer> list_values = new ArrayList<>(arr);
        //pw.println(list_values);
        int max = Collections.max(arr);
        int ans = 0;
        for (int item : list_values) {
            if (item == max) {
                ans += item;
            }
        }
        pw.println(ans);
        pw.flush();
    }
}

class Reader {
    final private int BUFFER_SIZE = 1 << 16;
    private DataInputStream din;
    private byte[] buffer;
    private int bufferPointer, bytesRead;
    public Reader() {
        din = new DataInputStream(System.in);
        buffer = new byte[BUFFER_SIZE];
        bufferPointer = bytesRead = 0;
    }
    public int nextInt() throws IOException {
        int ret = 0;
        byte c = read();
        while (c <= ' ') c = read();
        boolean neg = (c == '-');
        if (neg) c = read();
        do {
            ret = ret * 10 + c - '0';
        } while ((c = read()) >= '0' && c <= '9');
        return neg ? -ret : ret;
    }
    private void fillBuffer() throws IOException {
        bytesRead = din.read(buffer, bufferPointer = 0, BUFFER_SIZE);
        if (bytesRead == -1) buffer[0] = -1;
    }
    private byte read() throws IOException {
        if (bufferPointer == bytesRead) fillBuffer();
        return buffer[bufferPointer++];
    }
}
```

## Assigning Workstations
Penelope is part of the admin team of the newly built supercomputer. Her job is to assign workstations to the researchers who come here to run their computations at the supercomputer.
Penelope is very lazy and hates unlocking machines for the arriving researchers. She can unlock the machines remotely from her desk, but does not feel that this menial task matches her qualifications. Should she decide to ignore the security guidelines she could simply ask the researchers not to lock their workstations when they leave, and then assign new researchers to workstations that are not used any more but that are still unlocked. That way, she only needs to unlock each workstation for the first researcher using it, which would be a huge improvement for Penelope.

Unfortunately, unused workstations lock themselves automatically if they are unused for more than $`m`$ minutes. After a workstation has locked itself, Penelope has to unlock it again for the next researcher using it. Given the exact schedule of arriving and leaving researchers, can you tell Penelope how many unlockings she may save by asking the researchers not to lock their workstations when they leave and assigning arriving researchers to workstations in an optimal way? You may assume that there are always enough workstations available.

Input
The input consists of:
1. one line with two integers $`n`$ ($`1\le n\le 300000`$), the number of researchers, and $`m`$ ($`1\le m\le 10^8`$), the number of minutes of inactivity after which a workstation locks itself;
2. $`n`$ lines each with two integers $`a`$ and $`s`$ ($`1\le a,\ s\le 10^8`$), representing a researcher that arrives after $`a`$ minutes and stays for exactly $`s`$ minutes.

Output
Output the maximum number of unlockings Penelope may save herself.

```java
import java.io.*;
import java.util.*;

public class workspace {
    public static void main(String[] args) throws IOException {
        Reader sc = new Reader();
        PrintWriter pw = new PrintWriter(System.out);
        int no_researchers = sc.nextInt();
        int mins_inactivity = sc.nextInt();

        arrival_comparator arrival_comp = new arrival_comparator();
        PriorityQueue<Researcher> workstation_queue = new PriorityQueue<>(no_researchers, arrival_comp);
        PriorityQueue<Integer> workstation = new PriorityQueue<>();

        for (int i = 0; i < no_researchers; i++) {
            int a = sc.nextInt();
            int s = sc.nextInt();
            workstation_queue.add(new Researcher(a, s));
        }

        int counter = 0;
        while (!workstation_queue.isEmpty()) {
            Researcher x = workstation_queue.poll();
            while (!workstation.isEmpty() && x.getArrival_time() > workstation.peek() + mins_inactivity) {
                workstation.poll();
                //pw.println(1);
            }
            if (workstation.isEmpty()) { //if empty, unlock one time, and add the time that the workstation will be free to PQ2
                workstation.add(x.getDeparture_time());
                counter++;
            } else if (x.getArrival_time() < workstation.peek()) { //if workstation is still being used, unlock another workstation and add the time that the workstation will be free to PQ2
                workstation.add(x.getDeparture_time());
                counter++;
            } else if (x.getArrival_time() > workstation.peek() + mins_inactivity) { //if workstation is not used, and time > the no of mins of inactivity has passed, unlock workstation and add the time that the workstation will be free to PQ2
                workstation.poll();
                workstation.add(x.getDeparture_time());
                counter++;
            } else {//if (x.getArrival_time() <= workstation.peek() + mins_inactivity || x.getArrival_time() >= workstation.peek()) { //dont need to unlock workstation, researcher can just take over; add time that workstation will be free to PQ2
                workstation.poll();
                workstation.add(x.getDeparture_time());
            }
            //pw.println(workstation);
            //pw.println("end");
        }
        pw.println(no_researchers - counter);
        pw.flush();
    }
}

class Researcher {
    public int arrival_time;
    public int duration;
    public Researcher(int arrival_time, int duration){
        this.arrival_time = arrival_time;
        this.duration = duration;
    }
    public int getArrival_time() {return arrival_time;}
    public int getDuration() {return duration;}
    public int getDeparture_time() {return arrival_time + duration;}
}

class arrival_comparator implements Comparator <Researcher> {
    public int compare (Researcher r1, Researcher r2) {
        if (Integer.compare(r1.getArrival_time(), r2.getArrival_time()) == 0 ) {
            return Integer.compare(r1.getDeparture_time(), r2.getDeparture_time());
        } else {
            return Integer.compare(r1.getArrival_time(), r2.getArrival_time());
        }
    }
}

class Reader {
    final private int BUFFER_SIZE = 1 << 16;
    private DataInputStream din;
    private byte[] buffer;
    private int bufferPointer, bytesRead;
    public Reader() {
        din = new DataInputStream(System.in);
        buffer = new byte[BUFFER_SIZE];
        bufferPointer = bytesRead = 0;
    }
    public int nextInt() throws IOException {
        int ret = 0;
        byte c = read();
        while (c <= ' ') c = read();
        boolean neg = (c == '-');
        if (neg) c = read();
        do {
            ret = ret * 10 + c - '0';
        } while ((c = read()) >= '0' && c <= '9');
        return neg ? -ret : ret;
    }
    private void fillBuffer() throws IOException {
        bytesRead = din.read(buffer, bufferPointer = 0, BUFFER_SIZE);
        if (bytesRead == -1) buffer[0] = -1;
    }
    private byte read() throws IOException {
        if (bufferPointer == bytesRead) fillBuffer();
        return buffer[bufferPointer++];
    }
}
```

## Kattis's Quest
Kattis the Cat enjoys clearing quests on her mobile game. Each quest has an energy consumption $`E`$, and gold reward $`G`$. However, as Kattis has become very busy lately with grading her student’s problem sets, she does not have much spare time as before to keep clearing quests. As such, she has adopted a new ‘greedy’ strategy to clear her quests in each session as quickly as possible. With energy $`X`$ for a session, she will do the following:
1. Find the largest energy quest from the current pool of quest which is smaller or equal to $`X`$, if tied, by the largest gold reward
2. Clear the quest, removing it from current pool. Reduce energy $`X`$ by $`E`$ of the quest, and add up the gold reward $`G`$ earned this session.
3. Repeat steps 1 and 2 with remaining amount of energy, until energy left becomes 0, or if there are no more quests to be cleared with remaining energy.

However, she is not sure if this strategy is optimal, and wants your help in determining how much she has earned in each playing session. Kattis the Cat will give a list of 2 commands:
1. add E G: add a copy of the quest with energy consumption $`E`$ and gold reward $`G`$ into the pool
2. query X: using the ‘greedy’ quest clearing strategy described above, print out the total amount of gold Kattis the Cat earned in this session with energy $`X`$.

Input
The first line contains an integer $`N`$ ($`1\le N\le 2*10^5`$) denoting the number of commands. Each of the next $`N`$ lines contains a string S, denoting one of the above commands. For the add command, two integers will follow, $`E`$ and $`G`$ ($`1\le E,\ G\le10^5`$), denoting the energy consumption and gold reward of the quest respectively. For the query command, one integer will follow, $`X`$ ($`1\le X\le10^5`$), denoting the amount of energy Kattis the Cat has for this session.

Output
For each query X command, print the amount of gold Kattis the Cat earned for that session in a new line.

```java
import java.io.*;
import java.util.*;

public class kattisquest {
    public static void main(String[] args) throws IOException {
        FastIO fio = new FastIO();
        int no_cmd = fio.nextInt();

        questComparator questComp = new questComparator();
        TreeMap<ArrayList<Long>, Integer> quest_list = new TreeMap<ArrayList<Long>, Integer>(questComp);
        for (int i = 0; i < no_cmd; i++) {
            String cmd = fio.next();
            if (cmd.equals("add")) {
                long energy = fio.nextLong();
                long gold = fio.nextLong();
                ArrayList<Long> x = new ArrayList<Long>();
                x.add(energy);
                x.add(gold);
                //fio.println(x);
                if (quest_list.containsKey(x)) { //if key in treemap, increase value by 1
                    quest_list.put(x, quest_list.get(x) + 1);
                } else { //if key not in treemap, put in treemap with default value of 1
                    quest_list.put(x, 1);
                }
            } else if (cmd.equals("query")){
                long x = fio.nextLong();
                long total = 0;
                while (quest_list.floorKey(new ArrayList<Long>(Arrays.asList(x,(long)1000000))) != null) {  //(!quest_list.isEmpty() && x >= quest_list.firstKey().get(0)) {
                    ArrayList<Long> quest = new ArrayList<Long>();
                    quest.add(x);
                    quest.add((long)1000000);
                    ArrayList<Long> q = quest_list.floorKey(quest);
                    if (quest_list.get(q) == 1) {
                        quest_list.remove(q);
                    } else {
                        quest_list.put(q, quest_list.get(q) - 1);
                    }
                    x -= q.get(0);
                    total += q.get(1);
                }
                fio.println(total);
            }
        }
        //fio.print(quest_list);
        fio.flush();
    }
}

class FastIO extends PrintWriter {
    BufferedReader br;
    StringTokenizer st;

    public FastIO() {
        super(new BufferedOutputStream(System.out));
        br = new BufferedReader(new InputStreamReader(System.in));
    }

    String next() {
        while (st == null || !st.hasMoreElements()) {
            try {
                st = new StringTokenizer(br.readLine());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        return st.nextToken();
    }

    int nextInt() {
        return Integer.parseInt(next());
    }

    long nextLong() {
        return Long.parseLong(next());
    }

    double nextDouble() {
        return Double.parseDouble(next());
    }

    String nextLine() {
        String str = "";
        try {
            str = br.readLine();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return str;
    }
}

class questComparator implements Comparator<ArrayList<Long>>{
    public int compare(ArrayList<Long> o1, ArrayList<Long> o2) {
        if (Long.compare(o1.get(0), o2.get(0)) == 0) {
            return Long.compare(o1.get(1), o2.get(1));
        } else {
            return Long.compare(o1.get(0), o2.get(0));
        }
    }
}
```

## Almost Union Find
I hope you know the beautiful Union-Find structure. In this problem, you’re to implement something similar, but not identical. The data structure you need to write is also a collection of disjoint sets, supporting 3 operations:
1. $`1\ p\ q`$: Union the sets containing $`p`$ and $`q`$. If $`p`$ and $`q`$ are already in the same set, ignore this command.
2. $`2\ p\ q`$: Move $`p`$ to the set containing $`q`$. If $`p`$ and $`q`$ are already in the same set, ignore this command
3. $`3\ p`$Return the number of elements and the sum of elements in the set containing $`p`$.

Initially, the collection contains $`n`$ sets: $`\{1\}, \{2\},...,\{n\}`$.

As an example, consider the sequence of operations in sample input 1 below.
1. Initially: $`\{1\}, \{2\},\{3\},\{4\},\{5\}`$
2. Collection after operation 1 1 2: $`\{1,2\},\{3\},\{4\},\{5\}`$
3. Collection after operation 2 3 4: $`\{1,2\},\{3,4\},\{5\}`$ (we omit the empty set that is produced when taking out 3 from $`\{3\}`$)
4. Collection after operation 1 3 5: $`\{1,2\},\{3,4,5\}`$
5. Collection after operation 2 4 1: $`\{1,2,4\},\{3,5\}`$

Input
There are several test cases. Each test case begins with a line containing two integers $`n`$ and $`m`$ ($`1\le n,\ m\le 100000`$), the number of integers, and the number of commands. Each of the next $`m`$ lines contains a command. For every operation, $`1\le p,\ q\le n`$. The input is terminated by end-of-file (EOF). There are at most 20 cases, and the size of the input file does not exceed 5 MB.

Output
For each type-3 command, output 2 integers: the number of elements and the sum of elements.
 
```java
import java.io.*;
import java.util.Arrays;

public class almostunionfindv3 {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter pw = new PrintWriter(System.out);
        String line1 = br.readLine();
        while(line1 != null && !line1.isEmpty()) {
            String[] line = line1.split(" ");
            int no_int = Integer.parseInt(line[0]);
            int no_cmd = Integer.parseInt(line[1]);
            UnionFind disjointSet = new UnionFind(no_int + 1);
            for (int i = 0; i < no_cmd; i++) {
                String subline1 = br.readLine();
                String[] subline = subline1.split(" ");
                int cmd = Integer.parseInt(subline[0]);
                if (cmd == 1) {
                    int p = Integer.parseInt(subline[1]);
                    int q = Integer.parseInt(subline[2]);
                    disjointSet.unionSet(p, q);
                    /*pw.println(Arrays.toString(disjointSet.p));
                    pw.println(Arrays.toString(disjointSet.next));
                    pw.println(Arrays.toString(disjointSet.sum));
                    pw.println(Arrays.toString(disjointSet.size));*/
                } else if (cmd == 2) {
                    int p = Integer.parseInt(subline[1]);
                    int q = Integer.parseInt(subline[2]);
                    disjointSet.move(p, q);
                    /*pw.println(Arrays.toString(disjointSet.p));
                    pw.println(Arrays.toString(disjointSet.next));
                    pw.println(Arrays.toString(disjointSet.sum));
                    pw.println(Arrays.toString(disjointSet.size));*/
                } else {
                    int set = Integer.parseInt(subline[1]);
                    int p = disjointSet.findSet(set);
                    //pw.println(p);
                    pw.println(disjointSet.size[p] + " " + disjointSet.sum[p]);
                    /*pw.println(Arrays.toString(disjointSet.p));
                    pw.println(Arrays.toString(disjointSet.next));
                    pw.println(Arrays.toString(disjointSet.sum));
                    pw.println(Arrays.toString(disjointSet.size));*/
                    /*pw.println(disjointSet.findSet(5));
                    pw.println(disjointSet.findSet(3));
                    pw.println(disjointSet.findSet(4));*/

                }
            }
            line1 = br.readLine();
        }
        pw.flush();
    }
}

class UnionFind {
    public int[] p;
    public int[] next;
    public int[] size;
    public long[] sum;
    public int[] rank;

    public UnionFind(int N) {
        p = new int[N];
        next = new int [N];
        size = new int[N];
        sum = new long[N];
        rank = new int[N];
        for (int i = 0; i < N; i++) {
            p[i] = i;
            next[i] = i;
            size[i] = 1;
            sum[i] = i;
            rank[i] = 0;
        }
    }

    public int findSet(int i) {
        while (next[i] != p[next[i]]) {
            next[i] = p[next[i]];
            //p[i] = findSet(p[i]);
        }
        return next[i];
        /*while (p[i] != i) {
            i = p[i];
            p[i] = findSet(p[i]);
        }
        return p[i];*/
        /*if (p[i] == i) return i;
                else {
                    p[i] = findSet(p[i]);
                    return p[i];
                }*/
    }

    public Boolean isSameSet(int i, int j) {
        return findSet(i) == findSet(j);
    }

    public void unionSet(int i, int j) {
        if (!isSameSet(i, j)) {
            int x = findSet(i), y = findSet(j);
            // rank is used to keep the tree short
            if (rank[x] > rank[y]) {
                p[y] = x;
                next[i] = x;
                size[x] += size[y];
                sum[x] += sum[y];
            } else {
                p[x] = y;
                next[i] = y;
                size[y] += size[x];
                sum[y] += sum[x];
                if (rank[x] == rank[y])
                    rank[y] = rank[y] + 1;
            }
        }
    }

    public void move(int i, int j) {
        if (!isSameSet(i, j)) {
            int x = findSet(i), y = findSet(j);
            next[i] = y;
            size[x]--;
            size[y]++;
            sum[x] -= i;
            sum[y] += i;
        }
    }
}

    /*public int size(int i) {
        int ans = 0;
        int root = findSet(i);
        for (int j = 0; j < p.length; j++) {
            //p[j] = findSet(j);
            if (p[j] == root) {
                ans++;
            }
        }
        return ans;
    }

    public int sum(int i) {
        int ans = 0;
        int root = findSet(i);
        for (int j = 0; j < p.length; j++) {
            //p[j] = findSet(j);
            if (p[j] == root) {
                ans += j;
            }
        }
        return ans;
    }
}
```

## Weak Vertices

```java
import java.io.*;
import java.util.*;

public class weakvertices {
    public static void main(String[] args) throws IOException {
        FastIO fio = new FastIO();
        int matrix_size = fio.nextInt();
        while (matrix_size != -1) {
            int[][] AdjMatrix = new int[matrix_size][matrix_size];
            for (int i = 0; i < matrix_size; i++) {
                for (int j = 0; j < matrix_size; j++) {
                    AdjMatrix[i][j] = fio.nextInt();
                }
            }
            boolean[] vertices = new boolean[matrix_size];
            for (int a = 0; a < matrix_size; a++) {
                for (int b = 0; b < matrix_size; b++) {
                    for (int c = 0; c < matrix_size; c++) {
                        if (AdjMatrix[a][b] == 1 && AdjMatrix[a][c] == 1 && AdjMatrix[b][c] == 1) {
                            if (a != b && a != c && b != c) {
                                vertices[a] = true;
                                vertices[b] = true;
                                vertices[c] = true;
                            }
                        }
                    }
                }
            }
            for (int k = 0; k < vertices.length; k++) {
                if (!vertices[k]) {
                    fio.print(k + " ");
                }
            }
            fio.println();
            /*for (int i = 0; i < matrix_size; i++) {
                fio.println(Arrays.toString(AdjMatrix[i]));
            }*/
            matrix_size = fio.nextInt();
        }
        fio.flush();
    }
}

class FastIO extends PrintWriter {
    BufferedReader br;
    StringTokenizer st;

    public FastIO() {
        super(new BufferedOutputStream(System.out));
        br = new BufferedReader(new InputStreamReader(System.in));
    }

    String next() {
        while (st == null || !st.hasMoreElements()) {
            try {
                st = new StringTokenizer(br.readLine());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        return st.nextToken();
    }

    int nextInt() {
        return Integer.parseInt(next());
    }

    long nextLong() {
        return Long.parseLong(next());
    }

    double nextDouble() {
        return Double.parseDouble(next());
    }

    String nextLine() {
        String str = "";
        try {
            str = br.readLine();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return str;
    }
}
```

## Nicknames

```java
import java.io.*;
import java.util.*;

public class nicknames {
    public static void main(String[] args) throws IOException {
        FastIO fio = new FastIO();
        int no_names = fio.nextInt();
        HashMap<Character, AVL> treeHashMap = new HashMap<Character, AVL>();
        for (int i = 0; i < no_names; i++) {
            String name = fio.next();
            char name_beginning_letter = name.charAt(0);
            if (treeHashMap.containsKey(name_beginning_letter)) {
                treeHashMap.get(name_beginning_letter).insert(name);
            } else {
                AVL tree = new AVL();
                tree.insert(name);
                treeHashMap.put(name_beginning_letter,tree);
            }
        }
        int no_nicknames = fio.nextInt();
        HashMap<String, Integer> nicknameHashMap = new HashMap<>(); //For duplicated nicknames
        for (int j = 0; j < no_nicknames; j++) {
            String nickname = fio.next();
            char nickname_beginning_letter = nickname.charAt(0);
            int ans = 0;
            if (nicknameHashMap.containsKey(nickname)) {
                ans = nicknameHashMap.get(nickname);
            } else {
                if (treeHashMap.containsKey(nickname_beginning_letter)) {
                    AVL tree = treeHashMap.get(nickname_beginning_letter);
                    Node max = AVL.findHighestValid(tree.root, nickname, null);
                    ans = tree.count(max, nickname);
//                    if (nickname.length() == 1) {
//                        ans = tree.size;
//                    } else {
//                        Node max = AVLTree.findHighestValid(tree.root, nickname, null);
//                        ans = tree.count(max, nickname);
//                    }
                }
                nicknameHashMap.put(nickname, ans);
            }
            fio.println(ans);
        }
        fio.flush();
    }
}


class Node {
    String data;
    Node parent, left, right;
    int height;
    int size;

    Node(String data) {
        this.data = data;
        this.parent = null;
        this.left = null;
        this.right = null;
        this.height = 0;
        this.size = 1;
    }

@Override
    public String toString() {
        return this.data;
    }
}

class AVL {
    public Node root;

    public int size = 0;

    public AVL() {
        root = null;
    }

    public int height(Node N) {
        if (N == null) {
            return 0;
        }
        return N.height;
    }

    public int size (Node N) {
        if (N == null) {
            return 0;
        }
        return N.size;
    }
    public void updateSize(Node N) {
        if (N != null) {
            N.size = size(N.left) + size(N.right) + 1;
        }
    }

    public int max(int a, int b) {
        return Math.max(a, b);
    }

    public Node rightRotate(Node y) {
        if (y.left != null) {
            Node x = y.left;
            y.left = x.right;
            if (x.right != null) {
                x.right.parent = y;
            }
            x.parent = y.parent;
            if (y.parent == null) {
                this.root = x;
            } else if (y == y.parent.right) {
                y.parent.right = x;
            } else {
                y.parent.left = x;
            }
            x.right = y;
            y.parent = x;
            x.size = y.size;
            updateSize(y);
            y.height = max(height(y.left), height(y.right)) + 1;
            x.height = max(height(x.left), height(x.right)) + 1;
            return x;
        }
        return y;
    }

    public Node leftRotate(Node x) {
        if (x.right != null) {
            Node y = x.right;
            x.right = y.left;
            if (y.left != null) {
                y.left.parent = x;
            }
            y.parent = x.parent;
            if (x.parent == null) {
                this.root = y;
            } else if (x == x.parent.left) {
                x.parent.left = y;
            } else {
                x.parent.right = y;
            }
            y.left = x;
            x.parent = y;
            y.size = x.size;
            updateSize(x);
            x.height = max(height(x.left), height(x.right)) + 1;
            y.height = max(height(y.left), height(y.right)) + 1;
            return y;
        }
        return x;
    }

    public int getBalance(Node N) {
        if (N == null) {
            return 0;
        } else {
            return height(N.left) - height(N.right);
        }
    }

    public void insert(String data) {
        this.size++;
        this.root = insert(this.root, data);
    }

    public Node insert(Node node, String data) {
        if (node == null) {
            return (new Node(data));
        }
        if (data.compareTo(node.data) < 0) {//(data < node.data)
            node.left = insert(node.left, data);
            node.left.parent = node;
        } else {//(data > node.data)
            node.right = insert(node.right, data);
            node.right.parent = node;
        }
        updateSize(node);
        node.height = 1 + max(height(node.left), height(node.right));
        int balance = getBalance(node);
        if (balance > 1 && data.compareTo(node.left.data) < 0) { //data < node.left.data
            return rightRotate(node);
        } else if (balance < -1 && data.compareTo(node.right.data) > 0) {//data > node.right.data
            return leftRotate(node);
        } else if (balance > 1 && data.compareTo(node.left.data) > 0) { //data > node.left.data
            node.left = leftRotate(node.left);
            return rightRotate(node);
        } else if (balance < -1 && data.compareTo(node.right.data) < 0) { //data < node.right.data
            node.right = rightRotate(node.right);
            return leftRotate(node);
        }
        return node;
    }

    public void preOrder(Node node) {
        if (node != null) {
            System.out.print(node.data + " ");
            preOrder(node.left);
            preOrder(node.right);
        }
    }

    public void inOrder() {
        inOrderTraversal(root);
    }

    public  void inOrderTraversal(Node root) {
        if (root != null) {
            inOrderTraversal(root.left);
            System.out.print(root.data + " ");
            inOrderTraversal(root.right);
        }
    }

    public static Node findHighestValid(Node node, String query, Node highestValid) {
        if (node == null) {
            return null;
        }
        //System.out.println("FindHighest: " + node + " L:" + node.left + "R:" + node.right);
        String curr = node.data;
        if (curr.indexOf(query) == 0) {
            return node;
        }
        int compare = query.compareTo(curr);
        if (compare < 0) {
            return findHighestValid(node.left, query, highestValid);
        } else if (compare > 0) {
            return findHighestValid(node.right, query, highestValid);
        }
        return node;
    }

    public int count (Node node, String nickname) {
        int counter = 0;
        if (node == null) {
            return counter;
        }
//        Node max = AVLTree.findHighestValid(this.root, nickname, null);
//        System.out.println("Count: " + node + " L:" + node.left + "R:" + node.right);
//        if (node.data.indexOf(nickname) == 0 ) {
//            counter++;
//        } else {
//            return counter;
//        }
//        Boolean isEnd = false;
//        counter = findLeft(node.left, nickname, isEnd);
//        if (isEnd) {
//            return counter;
//        } else {
//            return count(node.parent, counter, nickname);
//        }
        return 1 + findLeft(node.left, nickname, false) + findRight(node.right, nickname, false);
    }

    public int findLeft(Node node, String nickname, Boolean isEnd) {
        int counter = 0;
        if (node == null) {
            return counter;
        }
        //System.out.println("FindLeft: " + node + " L:" + node.left + "R:" + node.right);
        if (node.data.indexOf(nickname) == 0) {
            counter += size(node.right); //weight(node.right);
            //System.out.println();
            return 1 + findLeft(node.left, nickname, isEnd) + counter;
        } else {
            isEnd = true;
            return findLeft(node.right, nickname, isEnd);
        }
    }

    public int findRight(Node node, String nickname, Boolean isEnd) {
        int counter = 0;
        if (node == null) {
            return counter;
        }
        //System.out.println("FindRight: " + node + " L:" + node.left + "R:" + node.right);
        if (node.data.indexOf(nickname) == 0) {
            counter += size(node.left); //weight(node.left);
            //System.out.println();
            return 1 + findRight(node.right, nickname, isEnd) + counter;
        } else {
            isEnd = true;
            return findRight(node.left, nickname, isEnd);
        }
    }
}

class FastIO extends PrintWriter {
    BufferedReader br;
    StringTokenizer st;

    public FastIO() {
        super(new BufferedOutputStream(System.out));
        br = new BufferedReader(new InputStreamReader(System.in));
    }

    String next() {
        while (st == null || !st.hasMoreElements()) {
            try {
                st = new StringTokenizer(br.readLine());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        return st.nextToken();
    }

    int nextInt() {
        return Integer.parseInt(next());
    }

    long nextLong() {
        return Long.parseLong(next());
    }

    double nextDouble() {
        return Double.parseDouble(next());
    }

    String nextLine() {
        String str = "";
        try {
            str = br.readLine();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return str;
    }
}
```

## Islands

```java
import java.io.*;
import java.util.*;

public class islands {
    public static void main(String[] args) throws IOException {
        FastIO fio = new FastIO();
        int no_rows = fio.nextInt();
        int no_col = fio.nextInt();
        char[][] map = new char[no_rows][no_col];
        for (int i = 0; i < no_rows; i++) {
            String line = fio.nextLine();
            for (int j = 0; j < no_col; j++) {
                map[i][j] = line.charAt(j);
            }
            //fio.print(Arrays.toString(map[i]));
        }
        boolean[][] visited = new boolean[no_rows][no_col];
        int ans = 0;
        for (int i = 0; i < no_rows; i++) {
            for (int j = 0; j < no_col; j++) {
                if (map[i][j] == 'L' && !visited[i][j]) {
                    ans++;
                    DFS(map, visited, i, j, no_rows, no_col);
                }
            }
        }
        fio.println(ans);
        fio.flush();
    }

    public static void DFS(char[][] map, boolean[][] visited, int row, int column, int no_rows, int no_col) {
        if (!visited[row][column]) {
            visited[row][column] = true;
            if (row + 1 < no_rows) {
                if (!visited[row + 1][column]) { //|| !visited[row - 1][column] || !visited[row][column + 1] || !visited[row][column - 1] ){
                    if (map[row + 1][column] == 'C' || map[row + 1][column] == 'L') {
                        DFS(map, visited, row + 1, column, no_rows, no_col);
                    }
                }
            }
            if (row - 1 >= 0) {
                if (!visited[row - 1][column]) {
                    if (map[row - 1][column] == 'C' || map[row - 1][column] == 'L') {
                        DFS(map, visited, row - 1, column, no_rows, no_col);
                    }
                }
            }
            if (column + 1 < no_col) {
                if (!visited[row][column + 1]) {
                    if (map[row][column + 1] == 'C' || map[row][column + 1] == 'L') {
                        DFS(map, visited, row, column + 1, no_rows, no_col);
                    }
                }
            }
            if (column - 1 >= 0) {
                if (!visited[row][column - 1]) {
                    if (map[row][column - 1] == 'C' || map[row][column - 1] == 'L') {
                        DFS(map, visited, row, column - 1, no_rows, no_col);
                    }
                }
            }
        }
    }
}

class FastIO extends PrintWriter {
    BufferedReader br;
    StringTokenizer st;

    public FastIO() {
        super(new BufferedOutputStream(System.out));
        br = new BufferedReader(new InputStreamReader(System.in));
    }

    String next() {
        while (st == null || !st.hasMoreElements()) {
            try {
                st = new StringTokenizer(br.readLine());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        return st.nextToken();
    }

    int nextInt() {
        return Integer.parseInt(next());
    }

    long nextLong() {
        return Long.parseLong(next());
    }

    double nextDouble() {
        return Double.parseDouble(next());
    }

    String nextLine() {
        String str = "";
        try {
            str = br.readLine();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return str;
    }
}
```

## Millionaire Madness

```java
import java.io.*;
import java.util.*;
import static java.lang.Math.abs;
import static java.lang.Math.max;

public class madness {
    public static void main(String[] args) throws IOException {
        Reader sc = new Reader();
        PrintWriter pw = new PrintWriter(System.out);
        int length = sc.nextInt();
        int width = sc.nextInt();
        int[][] vault = new int[length][width];
        for (int i = 0; i < length; i++) {
            for (int j = 0; j < width; j++) {
                vault[i][j] = sc.nextInt();
            }
            //pw.println(Arrays.toString(vault[i]));
        }
        boolean[][] visited = new boolean[length][width];
        int ans = 0;
        // Modified Prim's algo
        PriorityQueue<int[]> pq = new PriorityQueue<int[]>(new PairComparator());
        int[] start = {0, 0, vault[0][0], 0};
        pq.add(start);
        visited[0][0] = true;
        while(!visited[length -1][width - 1]) {
            int[] current = pq.poll();
            visited[current[0]][current[1]] = true;
            ans = Math.max(current[3], ans);
            int[] horizontal = {0, 0, -1, 1};
            int[] vertical = {1, -1, 0, 0};
            for (int i = 0; i < 4; i++) {
                int row = current[0] + vertical[i];
                int column = current[1] + horizontal[i];
                if (row > -1 && column > -1 && row < length && column < width) {
                    if (!visited[row][column]) {
                        int difference = vault[row][column] - current[2];
                        int[] next = {row, column, vault[row][column], difference};
                        pq.add(next);
                    }
                }
            }
        }
//        ans = DFS(vault, visited, 0, 0, length, width, ans);
        pw.print(ans);
        pw.flush();
    }
}

class PairComparator implements Comparator<int[]>{
    public int compare (int[] arr1, int[] arr2) {
        return Integer.compare(arr1[3], arr2[3]);
    }
}

class Reader {
    final private int BUFFER_SIZE = 1 << 16;
    private DataInputStream din;
    private byte[] buffer;
    private int bufferPointer, bytesRead;
    public Reader() {
        din = new DataInputStream(System.in);
        buffer = new byte[BUFFER_SIZE];
        bufferPointer = bytesRead = 0;
    }
    public int nextInt() throws IOException {
        int ret = 0;
        byte c = read();
        while (c <= ' ') c = read();
        boolean neg = (c == '-');
        if (neg) c = read();
        do {
            ret = ret * 10 + c - '0';
        } while ((c = read()) >= '0' && c <= '9');
        return neg ? -ret : ret;
    }
    private void fillBuffer() throws IOException {
        bytesRead = din.read(buffer, bufferPointer = 0, BUFFER_SIZE);
        if (bytesRead == -1) buffer[0] = -1;
    }
    private byte read() throws IOException {
        if (bufferPointer == bytesRead) fillBuffer();
        return buffer[bufferPointer++];
    }
}
```

## Lost Map

```java
import java.io.*;
import java.util.*;

public class lostmap {
    public static void main(String[] args) throws IOException {
        Reader sc = new Reader();
        PrintWriter pw = new PrintWriter(System.out);
        int no_villages = sc.nextInt();
        ArrayList<int[]> EdgeList = new ArrayList<int[]>();
        for (int i = 0; i < no_villages; i++) {
            for (int j = 0; j < no_villages; j++) {
                int weight = sc.nextInt();
                if (weight != 0) {
                    int[] arr = {i, j, weight};
                    EdgeList.add(arr);
                } else {
                    continue;
                }
            }
        }
        Collections.sort(EdgeList, new TripleComp());
        UnionFind UFDS = new UnionFind(no_villages);
        for (int[] arr : EdgeList) {
            if (!UFDS.isSameSet(arr[0], arr[1])) {
                UFDS.unionSet(arr[0], arr[1]);
                int vertex1 = arr[0] + 1;
                int vertex2 = arr[1] + 1;
                pw.print(vertex1 + " " + vertex2);
                pw.println();
            }
        }
        pw.flush();
    }
}

class TripleComp implements Comparator<int[]>{
    public int compare(int[] arr1, int[] arr2) {
        return Integer.compare(arr1[2], arr2[2]);
    }
}

class UnionFind {
    public int[] p;
    public int[] rank;

    public UnionFind(int N) {
        p = new int[N];
        rank = new int[N];
        for (int i = 0; i < N; i++) {
            p[i] = i;
            rank[i] = 0;
        }
    }

    public int findSet(int i) {
        if (p[i] == i) return i;
        else {
            p[i] = findSet(p[i]);
            return p[i];
        }
    }

    public boolean isSameSet(int i, int j) {
        return findSet(i) == findSet(j);
    }

    public void unionSet(int i, int j) {
        if (!isSameSet(i, j)) {
            int x = findSet(i), y = findSet(j);
            // rank is used to keep the tree short
            if (rank[x] > rank[y])
                p[y] = x;
            else {
                p[x] = y;
                if (rank[x] == rank[y])
                    rank[y] = rank[y] + 1;
            }
        }
    }
}

class Reader {
    final private int BUFFER_SIZE = 1 << 16;
    private DataInputStream din;
    private byte[] buffer;
    private int bufferPointer, bytesRead;
    public Reader() {
        din = new DataInputStream(System.in);
        buffer = new byte[BUFFER_SIZE];
        bufferPointer = bytesRead = 0;
    }
    public int nextInt() throws IOException {
        int ret = 0;
        byte c = read();
        while (c <= ' ') c = read();
        boolean neg = (c == '-');
        if (neg) c = read();
        do {
            ret = ret * 10 + c - '0';
        } while ((c = read()) >= '0' && c <= '9');
        return neg ? -ret : ret;
    }
    private void fillBuffer() throws IOException {
        bytesRead = din.read(buffer, bufferPointer = 0, BUFFER_SIZE);
        if (bytesRead == -1) buffer[0] = -1;
    }
    private byte read() throws IOException {
        if (bufferPointer == bytesRead) fillBuffer();
        return buffer[bufferPointer++];
    }
}
```

## Dominos

```java
import java.io.*;
import java.util.*;

public class Dominos {
    public static void main(String[] args) throws IOException {
        Reader sc = new Reader();
        PrintWriter pw = new PrintWriter(System.out);
        int no_cases = sc.nextInt();
        for (int i = 0; i < no_cases; i++) {
            int no_tiles = sc.nextInt();
            int no_lines = sc.nextInt();
            ArrayList<ArrayList<Integer>> AdjList = new ArrayList<ArrayList<Integer>>();
            ArrayList<ArrayList<Integer>> TAdjList = new ArrayList<ArrayList<Integer>>(); //for transposed AdjList
            int SCC = 0;
            for (int j = 0; j < no_tiles + 1; j++) {
                AdjList.add(new ArrayList<Integer>());
                TAdjList.add(new ArrayList<Integer>());
            }
            for (int k = 0; k < no_lines; k++) {
                int x = sc.nextInt();
                int y = sc.nextInt();
                ArrayList neighbour_list = AdjList.get(x);
                neighbour_list.add(y);
                ArrayList Tneighbour_list = TAdjList.get(y);
                Tneighbour_list.add(x);
            }
//            for (int k = 0; k <= no_tiles; k++) {
//                pw.println(AdjList.get(k));
//                pw.println(TAdjList.get(k));
//            }
//            Kosaraju's algo to count no of SCCs
//            Group all cyclic nodes into 1 bigger node
//            DFS to find topo sort
            DAG graph = new DAG(AdjList, TAdjList, no_tiles + 1);
            SCC = graph.Kosaraju() - 1; // -1 due to extra node 0
            pw.println(SCC);
        }
        pw.flush();
    }
}

class DAG {
    public ArrayList<ArrayList<Integer>> AdjList;
    public ArrayList<ArrayList<Integer>> TAdjList;
    public int size;

    public DAG(ArrayList<ArrayList<Integer>> AdjList, ArrayList<ArrayList<Integer>> TAdjList, int size) {
        this.AdjList = AdjList;
        this.TAdjList = TAdjList;
        this.size = size;
    }

    public int[] DFS(ArrayList<ArrayList<Integer>> Lst, int[] p, boolean[] visited, int u, int next) {
        visited[u] = true;
        p[u] = next;
        for (int v : Lst.get(u)) {
            if (visited[v]) {
                continue;
            } else {
                DFS(Lst, p, visited, v, next);
            }
        }
        return p;
    }

    public void DFS2(ArrayList<ArrayList<Integer>> Lst, Stack<Integer> s, boolean[] visited, int u) {
        visited[u] = true;
        for (int v : Lst.get(u)) {
            if (visited[v]) {
                continue;
            } else {
                DFS2(Lst, s, visited, v);
            }
        }
        s.push(u);
    }

    public int Kosaraju() {
        int[] p = new int[this.size];
        boolean[] visited = new boolean[this.size];
        Stack<Integer> s = new Stack<Integer>();
        for (int i = 0; i < this.size; i++) {
            if (visited[i]) {
                continue;
            } else {
                DFS2(this.AdjList, s, visited, i);
            }
        }
        boolean[] Tvisited = new boolean[this.size];
        int next = 0;
        while (s.size() > 0) {
            int u = s.pop();
            if (Tvisited[u]) {
                continue;
            } else {
                next++;
                DFS(this.TAdjList, p, Tvisited, u, next);
            }
        }
        int ans = 0;
        boolean[] arr = new boolean[next];
        for (int i = 0; i < this.size; i++) {
            for (int v : AdjList.get(i)) {
                if (p[i] != p[v]) {
                    if (arr[p[v]]) {
                        continue;
                    } else {
                        arr[p[v]] = true;
                        ans++;
                    }
                }
            }
        }
        return next - ans;
    }
}

class Reader {
    final private int BUFFER_SIZE = 1 << 16;
    private DataInputStream din;
    private byte[] buffer;
    private int bufferPointer, bytesRead;
    public Reader() {
        din = new DataInputStream(System.in);
        buffer = new byte[BUFFER_SIZE];
        bufferPointer = bytesRead = 0;
    }
    public int nextInt() throws IOException {
        int ret = 0;
        byte c = read();
        while (c <= ' ') c = read();
        boolean neg = (c == '-');
        if (neg) c = read();
        do {
            ret = ret * 10 + c - '0';
        } while ((c = read()) >= '0' && c <= '9');
        return neg ? -ret : ret;
    }
    private void fillBuffer() throws IOException {
        bytesRead = din.read(buffer, bufferPointer = 0, BUFFER_SIZE);
        if (bytesRead == -1) buffer[0] = -1;
    }
    private byte read() throws IOException {
        if (bufferPointer == bytesRead) fillBuffer();
        return buffer[bufferPointer++];
    }
}
```

## Human Cannonball Run

```java
import java.io.*;
import java.util.*;
import static java.lang.Math.*;

public class cannonball {
    public static void main(String[] args) throws IOException {
        FastIO fio = new FastIO();
        double start_x = fio.nextDouble();
        double start_y = fio.nextDouble();
        double[] start = {start_x, start_y};
        double end_x = fio.nextDouble();
        double end_y = fio.nextDouble();
        double[] end = {end_x, end_y};
        int no_cannons = fio.nextInt();
        double[][] cannons = new double[no_cannons][2];
        for (int i = 0; i < no_cannons; i++) {
            double x = fio.nextDouble();
            double y = fio.nextDouble();
            double[] cannon = {x, y};
            cannons[i] = cannon;
        }
//        for (int i = 0; i < no_cannons; i++) {
//            fio.println(Arrays.toString(cannons[i]));
//        }
        double[][] AdjMatrix = new double[no_cannons + 2][no_cannons + 2]; // +2 to size to account for start and end
        AdjMatrix[1][0] = distance(start, end) / 5; // walk from start to end
        AdjMatrix[0][1] = distance(start, end) / 5; // walk from end to start
        for (int j = 0; j < no_cannons; j++) {
            AdjMatrix[0][j + 2] = distance(start, cannons[j]) / 5; // walk from start to cannon
            AdjMatrix[1][j + 2] = distance(end, cannons[j]) / 5; // walk from end to cannon
            AdjMatrix[j + 2][0] = abs(distance(cannons[j], start) - 50) / 5 + 2; // launch from cannon and walk to start
            AdjMatrix[j + 2][1] = abs(distance(cannons[j], end) - 50) / 5 + 2; // launch from cannon and walk to end
            for (int k = 1; k < no_cannons; k++) {
                AdjMatrix[j + 2][k + 2] = abs(distance(cannons[j], cannons[k]) - 50) / 5 + 2; // launch from cannon and walk to other cannon
                AdjMatrix[k + 2][j + 2] = abs(distance(cannons[j], cannons[k]) - 50) / 5 + 2; // launch from cannon and walk to other cannon
            }
        }
//        for (int i = 0; i < no_cannons+2; i++) {
//            fio.println(Arrays.toString(AdjMatrix[i]));
//        }

        fio.println(Dijkstra(AdjMatrix, no_cannons));
        fio.flush();
    }

    public static double distance(double[] arr1, double[] arr2) { // calculate distance using pythagoras thm
        double x_diff = arr1[0] - arr2[0];
        double y_diff = arr1[1] - arr2[1];
        return hypot(x_diff, y_diff);
    }

    public static double Dijkstra(double[][] AdjMatrix, int no_cannons) {
        double[] duration = new double[no_cannons + 2];
        for (int i = 0; i < no_cannons + 2; i++) {
            duration[i] = Double.MAX_VALUE;
        }
        PriorityQueue<IntegerPair> pq = new PriorityQueue<IntegerPair>(new PairComparator());
        IntegerPair first = new IntegerPair(0, 0);
        pq.add(first);
        while (!pq.isEmpty()) {
            IntegerPair current = pq.poll();
            for (int i = 0; i < no_cannons + 2; i++) {
                if (i != current.getIndex() && duration[i] > current.getDuration() + AdjMatrix[current.getIndex()][i] ) {
                    duration[i] = current.getDuration() +  AdjMatrix[current.getIndex()][i];
                    IntegerPair next = new IntegerPair(duration[i], i);
                    pq.add(next);
                }
            }
        }
        return duration[1];
    }
}

class IntegerPair {
    public double duration;
    public int index;

    public IntegerPair(double time, Integer idx) {
        duration = time;
        index = idx;
    }
    public double getDuration() {
        return duration;
    }
    public int getIndex() {
        return index;
    }
}

class PairComparator implements Comparator<IntegerPair> {
    public int compare(IntegerPair i1, IntegerPair i2) {
        return Double.compare(i1.getDuration(), i2.getDuration());
    }
}

class FastIO extends PrintWriter {
    BufferedReader br;
    StringTokenizer st;
    public FastIO() {
        super(new BufferedOutputStream(System.out));
        br = new BufferedReader(new InputStreamReader(System.in));
    }
    String next() {
        while (st == null || ! st.hasMoreElements()) {
            try { st = new StringTokenizer(br.readLine()); }
            catch (IOException  e) { e.printStackTrace(); }
        }
        return st.nextToken();
    }
    int nextInt() { return Integer.parseInt(next()); }
    long nextLong() { return Long.parseLong(next()); }
    double nextDouble() { return Double.parseDouble(next()); }
    String nextLine() {
        String str = "";
        try { str = br.readLine(); }
        catch (IOException e) { e.printStackTrace(); }
        return str;
    }
}
```
