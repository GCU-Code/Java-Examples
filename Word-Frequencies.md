---
title: LAB 4-26: Word Frequencies
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-26: Word Frequencies

```java
/*
Write a program that reads a list of words. Then, the program outputs those words and their frequencies. The input begins with an integer indicating the number of words that follow. Assume that the list will always contain fewer than 20 words.

Ex: If the input is: 5 hey hi Mark hi mark
the output is:
hey - 1
hi - 2
Mark - 1
hi - 2
mark - 1

Hint: Use two arrays, one array for the strings and one array for the frequencies.
*/

import java.util.Scanner; 
import java.util.ArrayList;

public class LabProgram {
   public static void main(String[] args)  
   {
      Scanner input = new Scanner(System.in);
      int size = input.nextInt();
      int frequency[] = new int[size];
      String words[] = new String[size];
      
      for(int i = 0; i < size; ++i){
         words[i] = input.next();
      }
      for(int i = 0; i < size; ++i)  
      {
         for(int n = 0; n < size; ++n)  
         {
            if(words[i].equals(words[n])){
               ++frequency[i];
            }
         }
      }
      for(int i = 0; i < size; ++i){
        System.out.println(words[i] + " - "+ frequency[i]);
      }
   }
}
```

