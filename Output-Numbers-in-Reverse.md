---
title: LAB 4-22: Output Numbers in Reverse
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-22: Output Numbers in Reverse

```java
/*
Write a program that reads a list of integers, and outputs those integers in reverse. The input begins with an integer indicating the number of integers that follow. For coding simplicity, follow each output integer by a comma, including the last one. Assume that the list will always contain fewer than 20 integers.

Ex: If the input is: 5 2 4 6 8 10
the output is: 10,8,6,4,2,

To achieve the above, first read the integers into an array. Then output the array in reverse.
*/

import java.util.Scanner;

public class LabProgram {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);
      int numElements;  // Number of integers in user's list

      numElements = scnr.nextInt();   // Input begins with number of integers that follow
      int[] userList = new int[numElements];   // List of numElement integers specified by the user
      for (int i = 0; i < numElements; ++i) {
         userList[i] = scnr.nextInt();
      }
      
      for (int i = userList.length - 1; i >= 0; --i)
      {
         System.out.print(userList[i] + ",");
      }
      
      System.out.println();
   }
}
```