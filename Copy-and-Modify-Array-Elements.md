---
title: CA 4-11-2: Copy and Modify Array Elements
subtitle: CST-105
author: Brent L. Ricks
date: July 8, 2022
subject: Discussion Topic
---

# CA 4-11-2: Copy and Modify Array Elements

```java
/*
Write a loop that sets newScores to oldScores shifted once left, with element 0 copied to the end. Ex: If oldScores = {10, 20, 30, 40}, then newScores = {20, 30, 40, 10}.

Note: These activities may test code with different test values. This activity will perform two tests, both with a 4-element array (int oldScores[4]).

Also note: If the submitted code tries to access an invalid array element, such as newScores[9] for a 4-element array, the test may generate strange results. Or the test may crash and report "Program end never reached", in which case the system doesn't print the test case that caused the reported message.
*/

import java.util.Scanner;
public class StudentScores {
   public static void main (String [] args) {
      Scanner scnr = new Scanner(System.in);
      final int SCORES_SIZE = 4;
      int[] oldScores = new int[SCORES_SIZE];
      int[] newScores = new int[SCORES_SIZE];
      int i;

      for (i = 0; i < oldScores.length; ++i) {
         oldScores[i] = scnr.nextInt();
      }
      int tempInt = oldScores[0];
      
      for (i = 0; i < oldScores.length; ++i){
         if(i != 0){
            newScores[i - 1] = oldScores[i];
         }
      }
      newScores[SCORES_SIZE - 1] = tempInt;
      
      for (i = 0; i < newScores.length; ++i) {
         System.out.print(newScores[i] + " ");
      }
      System.out.println();
   }
}
```