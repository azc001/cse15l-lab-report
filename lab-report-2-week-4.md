# Week 4 Lab Report 2
`By Andrew Chen`

This lab report covers three changes to the file `MarkdownParse.java` made by the Kangaroo group.

## List of Changes
1. [Change 1 - Empty Line](/cse15l-lab-report/lab-report-2-week-4.html#change-1---empty-line)
2. [Change 2 - Images](/cse15l-lab-report/lab-report-2-week-4.html#change-2---images)
3. [Change 3 - Fixing the Fix](/cse15l-lab-report/lab-report-2-week-4.html#change-3---fixing-the-fix)

---

## Change 1 - Empty Line

![img1](images\week-4\img1.png)

[**Failure-Inducing Input**](https://github.com/azc001/markdown-parse/blob/main/test-file-1.md)
```
java MarkdownParse test-file-1.md
```
**Symptomatic Output**
```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.util.Arrays.copyOfRange(Arrays.java:3822)
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:769)
        at java.base/java.lang.String.substring(String.java:2709)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParse.main(MarkdownParse.java:26)
```
**Corrected Output**
```
[https://something.com, some-page.html]
```

The problem was that when the input file ended with an empty line break, `MarkdownParse.java` would go into an infinite loop when it was run. This was because the while loop would try to find `nextOpenBracket` at the end of the file, which was set to -1 as the character wasn't found. This meant the rest of the loop would search beginning from the start of the file, and that `currentIndex` was never incremented correctly so that the while loop exit condition would eventually be met.

The code we added meant that when `nextOpenBracket` or `nextCloseBracket` were unable to find a "["or "]" at the end of the file, the program assumed that there's no more links left in the file and breaks from the while loop, preventing an infinite loop.

---

## Change 2 - Images

![img2](images\week-4\img2.png)

[**Failure-Inducing Input**](https://github.com/azc001/markdown-parse/blob/main/test-file-2.md)
```
java MarkdownParse test-file-2.md
```
**Symptomatic Output**
```
[thisisalink.com, thisisanimage, thisisanotherlink.org]
```
**Corrected Output**
```
[thisisalink.com, thisisanotherlink.org]
```

The problem was that when the input file contained an image, the program would mistakenly interpret it as a link due to the similar markdown format used to include an image in the file.

The code we added meant that if the character immediately before the open bracket was an exclamation point, the index would be changed so that the code would skip over the image correctly. This allowed `MarkdownParse.java` to exclude image paths from its list of links.

---

## Change 3 - Fixing the Fix

![img3](images\week-4\img3.png)

[**Failure-Inducing Input**](https://github.com/azc001/markdown-parse/blob/main/test-file-4.md)
```
java MarkdownParse test-file-4.md
```
**Symptomatic Output**
```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: String index out of range: -1
        at java.base/java.lang.StringLatin1.charAt(StringLatin1.java:48)
        at java.base/java.lang.String.charAt(String.java:1512)
        at MarkdownParse.getLinks(MarkdownParse.java:20)
        at MarkdownParse.main(MarkdownParse.java:35)
```
**Corrected Output**
```
[thisisalink.com]
```

The problem was that when the input file immediately began with a link, the index would go out of bounds. This is because a file that has a link at the start contains the open bracket at index 0, meaning our code for fixing the image problem was trying to find a character at index `0 - 1 = -1`. The index of -1 was causing the program to throw `IndexOutOfBoundsException` errors.

The code we added meant that the program would only check for an image if an open bracket wasn't at the first position of the file. This fixed the problem without creating a new edge case since even if an image is at the start of the file, the open bracket will be at position 1 instead of 0 because of the !.