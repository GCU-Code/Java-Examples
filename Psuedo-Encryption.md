---
title: Pseudo Encryption
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Exercise
---

# Pseudo Encryption

```java
/*
Write a program that reads text from a file called input.in.  For each word in the file, output the original word and its encrypted equivalent in all-caps. The output should be in a tabular format, as shown below. The output should be written to a file called results.out. 

Here are the rules for our encryption algorithm:

a.	If a word has n letters, where n is an even number, move the first n/2 letters to the end of the word.  For example, ‘before’ becomes ‘orebef’ 

b.	If a word has n letters, where n is an odd number, move the first (n+1)/2 letters to the end of the word.  For example: ‘kitchen’ becomes ‘henkitc’

Here is a sample run of the program for the following input file. Your program should work with any file, not just the sample below:

SAMPLE INPUT:
Life is either a daring adventure or nothing at all

SAMPLE OUTPUT:
Life			FELI
is				SI
either			HEREIT
a				A
daring			INGDAR
adventure		TUREADVEN
or				RO
nothing			INGNOTH
at				TA
all				LAL
*/

import java.util.ArrayList;
import java.util.Scanner;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.PrintWriter;

public class Start {
	public static void ReadFile() throws IOException {
		FileInputStream fileByteStream = null;
		Scanner fileReader = null;
		ArrayList<String> wordList = new ArrayList<String>();

		// Open file stream and reader. Retrieve file.
		fileByteStream = new FileInputStream("src/input.in");
		fileReader = new Scanner(fileByteStream);

		System.out.println("-----------------------------------------");
		System.out.println("Reading contents of  file \'input.in\'...");

		// Read to end of file and add each found to ArrayList.
		while (fileReader.hasNext()) {
			wordList.add(fileReader.next());
		}

		fileReader.close();
		WriteDataToFile(wordList);
	}

	public static void WriteDataToFile(ArrayList<String> wordList) throws IOException {
		/*
		 * To ensure columns are lined up properly (most of the time), Set Spacing based
		 * on the 8th longest English word, Thyroparathyroidectomized"
		 */
		final int WORD_SPACING = 25;
		String part1; // Stores the 1st half of the string;
		String part2; // Stores the 2nd half of the string;
		String strEncrypted;
		int strLength = 0;
		int charCount = 0;
		FileOutputStream fileOutStream = null;

		// Open file stream to write to file.
		fileOutStream = new FileOutputStream("src/results.out");

		// Open file writer.
		PrintWriter fileWriter = null;
		fileWriter = new PrintWriter(fileOutStream);

		System.out.println("-----------------------------------------");
		System.out.println("Formatting data for output and writing to \n\'results.out\'...");

		for (String str : wordList) {
			/*
			 * Removes the special characters from string. Although many might want special
			 * characters as part of the encryption, I chose not to include for this
			 * project.
			 */
			str = str.replaceAll("([&!-/:-?])", "");
			strLength = str.length();
			
			// To find the required index to split on, take the string length and divide by 2.
			if (strLength % 2 != 0) {
				// Account for any remainder.
				charCount = (strLength + 1) / 2;
			} else {
				charCount = strLength / 2;
			}
			
			// Use the charCount as index to find the substrings for each part.
			part1 = str.substring(0, charCount).toUpperCase();
			part2 = str.substring(charCount).toUpperCase();
			strEncrypted = part2 + part1;
			fileWriter.println(String.format("%-" + WORD_SPACING + "s %-1s", str, strEncrypted));
		}
		System.out.println("-----------------------------------------");
		System.out.println("Completed writing to file \'results.out\'.");
		fileWriter.close();

		System.out.println("=========================================");
		System.out.println("Exiting program.");
		System.exit(0);
	}

	public static void main(String[] args) throws IOException {
		// Let the end-user know that the program has started.
		System.out.println("Program is starting.");
		ReadFile();
	}
}
```

