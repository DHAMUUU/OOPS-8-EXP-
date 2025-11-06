# OOPS-8-EXP-
1) 
import java.util.*;
class WordThread extends Thread {
    String text;

    WordThread(String text) {
        this.text = text;
    }

    public void run() {
        String[] words = text.split(" ");
        try {
            for (String word : words) {
                System.out.println("Word: " + word);
                Thread.sleep(2000); // 2-second delay
            }
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

class VowelThread extends Thread {
    String text;

    VowelThread(String text) {
        this.text = text;
    }

    public void run() {
        try {
            for (int i = 0; i < text.length(); i++) {
                char ch = text.charAt(i);
                if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' ||
                    ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U') {
                    System.out.println("Vowel: " + ch);
                    Thread.sleep(2000); // 2-second delay
                }
            }
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        String paragraph = "Java supports multithreading";

        WordThread w = new WordThread(paragraph);
        VowelThread v = new VowelThread(paragraph);

        w.start();
        v.start();
    }
}

2)
import java.util.Scanner;

class EvenThread extends Thread {
    int[] numbers;

    EvenThread(int[] numbers) {
        this.numbers = numbers;
    }

    public void run() {
        try {
            for (int num : numbers) {
                if (num % 2 == 0) {
                    System.out.println("Even: " + num);
                    Thread.sleep(2000); // 2-second delay
                }
            }
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

class OddThread extends Thread {
    int[] numbers;

    OddThread(int[] numbers) {
        this.numbers = numbers;
    }

    public void run() {
        try {
            for (int num : numbers) {
                if (num % 2 != 0) {
                    System.out.println("Odd: " + num);
                    Thread.sleep(2000); // 2-second delay
                }
            }
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

public class oddeven {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] numbers = new int[10];

        System.out.println("Enter 10 numbers:");
        for (int i = 0; i < 10; i++) {
            numbers[i] = sc.nextInt();
        }

        EvenThread even = new EvenThread(numbers);
        OddThread odd = new OddThread(numbers);

        even.start();
        odd.start();

        sc.close();
    }
}


3) 
import java.util.Scanner;

class TableThread extends Thread {
    int num;

    TableThread(int num) {
        this.num = num;
    }

    public void run() {
        try {
            for (int i = 1; i <= 10; i++) {
                System.out.println("Table: " + num + " x " + i + " = " + (num * i));
                Thread.sleep(2000); // 2-second delay
            }
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

class DivisorThread extends Thread {
    int num;

    DivisorThread(int num) {
        this.num = num;
    }

    public void run() {
        try {
            System.out.println("Divisors of " + num + ":");
            for (int i = 1; i <= num; i++) {
                if (num % i == 0) {
                    System.out.println("Divisor: " + i);
                    Thread.sleep(2000); // 2-second delay
                }
            }
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

public class multidiv {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        TableThread t1 = new TableThread(num);
        DivisorThread t2 = new DivisorThread(num);

        t1.start();
        t2.start();

        sc.close();
    }
}

