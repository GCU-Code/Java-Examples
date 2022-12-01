---
title: LAB 4-23: Middle Item
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# Middle Item

```java
/*
Given a sorted list of integers, output the middle integer. A negative number indicates the end of the input (the negative number is not a part of the sorted list). Assume the number of integers is always odd.

Ex: If the input is: 2 3 4 8 11 -1 
the output is: Middle item: 4

The maximum number of inputs for any test case should not exceed 9. If exceeded, output "Too many numbers".

Hint: First read the data into an array. Then, based on the array's size, find the middle item.
*/

import java.util.Scanner; 
import java.util.ArrayList;

public class LabProgram {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);
      int[] userValues = new int[9];  // Set of data specified by the user 
      ArrayList<Integer> tempValues = new ArrayList<Integer>();
      int numCount = 0;
      int newSize = 0;
      int midIndex = 0;
      
      while(scnr.hasNextInt()){
         int i = scnr.nextInt();
         tempValues.add(i);
         ++numCount;
      }
      if(numCount > userValues.length + 1){
         System.out.println("Too many numbers");
      } 
      else {
         for(int n = 0; n < tempValues.size(); ++n){
            int numCurrent = tempValues.get(n);
            if(numCurrent > 0){
               userValues[n] = numCurrent;
               ++newSize;
            }
            else{
               break;
            }
         }
         int[] newValues = new int[newSize];
         for(int i = 0; i < userValues.length; ++i){
            if(i < newSize){
               newValues[i] = userValues[i];
            }
         }
         if(newValues.length % 2 != 0){
            midIndex = (newValues.length + 1) / 2;
         }
         else {
            midIndex = newValues.length / 2;
         }
         System.out.println("Middle item: " + newValues[midIndex - 1]);
      }
   }
}
```

