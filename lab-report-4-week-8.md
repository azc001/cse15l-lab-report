# Week 6 Lab Report 3
`By Andrew Chen`

This lab report details how both [my group](https://github.com/ocboogie/markdown-parse)'s and [my reviewed group]()'s versions of the `MarkdownParse` file fare with the input snippets as tests.

## List of Changes
1. [Snippet 1](/cse15l-lab-report/lab-report-4-week-8.html#snippet-1)
2. [Snippet 2](/cse15l-lab-report/lab-report-4-week-8.html#snippet-2)
3. [Snippet 3](/cse15l-lab-report/lab-report-4-week-8.html#snippet-3)

---

## Snippet 1

**Markdown Input**

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

**Expected Markdown Output**

![img1](images\week-8\img1.png)

**Test Implementation**

-

**My Group's Output**

-

**Reviewed Group's Output**

-

**Question**

*Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.*

text

---

## Snippet 2

**Markdown Input**

```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```

**Expected Markdown Output**

![img1](images\week-8\img2.png)

**Test Implementation**

-

**My Group's Output**

-

**Reviewed Group's Output**

-

**Question**

*Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.*

text

---

## Snippet 3

**Markdown Input**

```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
    https://ucsd-cse15l-w22.github.io/
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```

**Expected Markdown Output**

![img1](images\week-8\img3.png)

**Test Implementation**

-

**My Group's Output**

-

**Reviewed Group's Output**

-

**Question**

*Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.*

text