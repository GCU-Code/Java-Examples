---
title: LAB 3-34: Output Range with Increment of 5
subtitle: CST-105
author: Brent L. Ricks
date: July 8, 2022
subject: Discussion Topic
---

# LAB 3-34: Output Range with Increment of 5

```java
/*
Write a program whose input is two integers, and whose output is the first integer and subsequent increments of 5 as long as the value is less than or equal to the second integer.

Ex: If the input is: -15 10
the output is: -15 -10 -5 0 5 10

Ex: If the second integer is less than the first as in: 20 5
the output is: Second integer can't be less than the first.

For coding simplicity, output a space after every integer, including the last.
*/

import java.util.Scanner;

public class LabProgram {
   public static void main(String[] args) {
      // Add error handling to ensure input is an integer.
      try (Scanner scnr = new Scanner(System.in)) {
         // Initialize variable and set to user input at start.
         int num1 = scnr.nextInt();
         int num2 = scnr.nextInt();
         
         if (num2 >= num1) {
            while (num2 >= num1) {
               System.out.print(num1 + " ");
               
               // Increment input by 5 and so on.
               num1 += 5;
            }
         }
         else {
            System.out.print("Second integer can't be less than the first.");
         }
         System.out.println();
      }
      catch (Exception e) {
         System.out.println("You did not enter an integer for at least one of your inputs.");
      }
   }
}
```