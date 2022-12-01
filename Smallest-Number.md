---
title: LAB 3-29: Smallest Number
subtitle: CST-105
author: Brent L. Ricks
date: July 8, 2022
subject: Lab
---

# LAB 3-29: Smallest Number

```java
/*
Write a program whose inputs are three integers, and whose output is the smallest of the three values.

Ex: If the input is: 
7 15 3
the output is:
3
*/

import java.util.Scanner;

public class LabProgram {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);
      int numSmallest;
      
      int input1 = scnr.nextInt();
      numSmallest = input1;
      
      int input2 = scnr.nextInt();
      if (input2 < numSmallest) numSmallest = input2;
      
      int input3 = scnr.nextInt();
      if (input3 < numSmallest) numSmallest = input3;
      
      System.out.println(numSmallest);     
   }
}
```