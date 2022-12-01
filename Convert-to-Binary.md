---
title: LAB 3-32: Convert to Binary
subtitle: CST-105
author: Brent L. Ricks
date: July 8, 2022
subject: Lab
---

# LAB 3-32: Convert to Binary

```java
/*
Write a program that takes in a positive integer as input, and outputs a string of 1's and 0's representing the integer in binary. For an integer x, the algorithm is:

As long as x is greater than 0
   Output x % 2 (remainder is either 0 or 1)
   x = x / 2
Note: The above algorithm outputs the 0's and 1's in reverse order.

Ex: If the input is: 6
the output is:011

6 in binary is 110; the algorithm outputs the bits in reverse.
*/

import java.util.Scanner; 

public class LabProgram {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);
      int x;
      
      x = scnr.nextInt();
      
      while (x > 0) {
         System.out.print(x % 2);
         x = x / 2;
      }
      System.out.println();
   }
}
```