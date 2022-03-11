# Week 10 Lab Report 5
`By Andrew Chen`

This lab report details how I went about comparing the difference between the implementation of MarkdownParse by my group and the provided one for lab 9.

## How you found the tests with different results

I first went to the official implementation and ran the following command to save the script output to a file named `official-results.txt`

```
$ bash script.sh > official-results.txt
```

I then went to our implementation, copied over the test files and the script file, and ran the same command, saving it to a file named `our-results.txt` instead.

```
$ bash script.sh > our-results.txt
```

I then used the diff command to compare both files and see where they differed after moving them into the same folder.

```
$ diff our-results.txt official-results.txt
```

Doing so gave me a long list of differences in between the output code, which let me know which test files were being treated differently between implementations..

# Different Ouput 1 - Test 481
**File Contents**
```
[link](/url "title")
```

**Provided Implementation's Output**
```
[]
```

**Our Implementation's Output**
```
['/url "title"']
```

**Which is Correct?**

Neither implementation is correct in this case, since the title of the link (which is placed in quotation marks) is not a part of the link. The correct output would only be `[url]` since title isn't included in the link.

**Fix**

The way both codes could fix this is a check of any spaces within the link. It would then check if the space is followed by a pair of quotation marks, excluding whatever was in between them from the link if it found one.

---

# Different Ouput 2 - Test 577
**File Contents**
```
![foo](train.jpg)
```

**Provided Implementation's Output**
```
[train.jpg]
```

**Our Implementation's Output**
```
[]
```

**Which is Correct?**

Our implementation is correct since images don't count as links. Since the input file only has an image, there shouldn't be any links that are returned in the output.

**Fix**

The fix would be to add a line of code that detects whether there is an `!` before the first square bracket of a would-be link. If there is one, skip the link as it's an image instead.