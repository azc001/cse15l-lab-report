# Skill Demo Guide
`By Andrew Chen`

A checklist of instructions to make my skill demonstration go as smooth as possible.

0. Show ID and face
1. Create repo on Github
2. Create new file `SkillDemo.java`
3. Commit the file after putting in some dummy code
4. Copy HTTPS link, open Github Desktop
5. Clone Repo and paste URL
6. Open in Visual Studio Code
7. Paste
```
public class SkillDemo {
	public static int multiply (int num1, int num2) {
		return num1 * num2;
	}
}
```
8. Create new file, `SkillDemoTest.java`
9. Paste
```
public class SkillDemoTest {
	@Test
	public void multiplyTest() {
		assertEquals(5, SkillDemo.multiply(2, 2));
	}

}
```
10. Create a folder called `libs`
11. Drag and drop in `hamcrest-core-1.3` and `junit-4.13.2`
12. Ctrl+Shift+P to open configure classpath, add the libs
13. Open a new terminal and run `ssh cs15lwi22aek@ieng6.ucsd.edu`
14. Run `git clone ` and copy and paste the html link from github at the end
15. Run `cd skill-demo`
16. Run `javac -cp ".;libs\junit-4.13.2.jar;libs\hamcrest-core-1.3.jar" SkillDemo.java SkillDemoTest.java`
17. Run `java -cp ".;libs\junit-4.13.2.jar;libs\hamcrest-core-1.3.jar" org.junit.runner.JUnitCore SkillDemoTest`
18. Succesfully get a failure
19. Fix the code (change the expected to 4)
20. Save and open Github desktop
21. Commit to main and push origin
22. Run `git pull`
23. Run `javac -cp ".;libs\junit-4.13.2.jar;libs\hamcrest-core-1.3.jar" SkillDemo.java SkillDemoTest.java`
24. Run `java -cp ".;libs\junit-4.13.2.jar;libs\hamcrest-core-1.3.jar" org.junit.runner.JUnitCore SkillDemoTest`
25. Done!