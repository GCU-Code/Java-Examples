---
title: LAB 2-34: Convert to Dollars
subtitle: CST-105
author: Brent L. Ricks
date: July 8, 2022
subject: Discussion Topic
---

# LAB 2-34: Convert to Dollars

```java
/*
Given four values representing counts of quarters, dimes, nickels and pennies, output the total amount as dollars and cents.

Output each floating-point value with two digits after the decimal point, which can be achieved as follows:
System.out.printf("Amount: $%.2f\n", dollars);

Ex: If the input is:

4 3 2 1
where 4 is the number of quarters, 3 is the number of dimes, 2 is the number of nickels, and 1 is the number of pennies, the output is:

Amount: $1.41
For simplicity, assume input is non-negative.
*/

import java.util.Scanner;

public class LabProgram {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);

      // Set Contants      
      final double QUARTER_VALUE = 0.25;
      final double DIME_VALUE = 0.10;
      final double NICKEL_VALUE = 0.05;
      final double PENNY_VALUE = 0.01;
      
      // Create variables to hold assignments
      int numQuarters;
      int numDimes;
      int numNickels;
      int numPennies;
      double numDollars;
      
      // Get input information
      numQuarters = scnr.nextInt();
      numDimes = scnr.nextInt();
      numNickels = scnr.nextInt();
      numPennies = scnr.nextInt();
      
      // Calulate total amount of money (dollars & cents) given inputs
      numDollars = (numQuarters * QUARTER_VALUE) + (numDimes * DIME_VALUE) + (numNickels * NICKEL_VALUE) + (numPennies * PENNY_VALUE);
      
      System.out.printf("Amount: $%.2f\n", numDollars);
   }
}
```