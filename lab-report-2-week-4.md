# Week 4 Lab Report 2
`By Andrew Chen`

This lab report covers three changes to the file `MarkdownParse.java` made by the Kangaroo group.

## Changes
1. [](https://azc001.github.io/cse15l-lab-report/lab-report-2-week-4.html#)
2. [](https://azc001.github.io/cse15l-lab-report/lab-report-2-week-4.html#installing-vscode)
3. [](https://azc001.github.io/cse15l-lab-report/lab-report-2-week-4.html#installing-vscode)

---

## Change 1 - Empty Line
![img1](images\week-4\img1.png)

[**Failure-Inducing Input**]()
```
PS C:\Users\andrz\Documents\GitHub\markdown-parse-clone\markdown-parse> java MarkdownParse test-file-1.md
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

![img2](images\week-4\img2.png)
![img3](images\week-4\img3.png)