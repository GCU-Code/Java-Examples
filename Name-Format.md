---
title: LAB 4-28: Name Format
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-28: Name Format

```java
/*
Many documents use a specific format for a person's name. Write a program whose input is:

firstName middleName lastName

and whose output is:

lastName, firstInitial.middleInitial.

Ex: If the input is: Pat Silly Doe
the output is: Doe, P.S.

If the input has the form: firstName lastName
the output is: lastName, firstInitial.

Ex: If the input is: Julia Clark
the output is: Clark, J.
*/

import java.util.Scanner; 
import java.util.ArrayList;

public class LabProgram {
   public static void main(String[] args) {
      Scanner input = new Scanner(System.in);
      ArrayList<String> userNames = new ArrayList<String>();
      String firstName = "";
      String middleName = "";
      String lastName = "";
      String fullName = "";
      
      while (input.hasNext()) {
         userNames.add(input.next());
      }

      for (String s: userNames) {
         firstName = userNames.get(0);
         if (userNames.size() > 2){
            middleName = userNames.get(1);
            lastName = userNames.get(2);
            fullName = lastName + ", " + firstName.charAt(0) + "." + middleName.charAt(0) + ".";
         } else {
            lastName = userNames.get(1);
            fullName = lastName + ", " + firstName.charAt(0) + ".";
         }
      }
      System.out.println(fullName);
   }
}
```

