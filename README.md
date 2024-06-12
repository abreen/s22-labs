# S-22 Lab Exercises

CSCI S-22 at Harvard Summer School is an intensive 7-week course covering
fundamental data structures and classic algorithms using Java.

Lectures take place over Zoom, on Mondays and Wednesdays. There are optional
one-hour section meetings on Tuesdays and Thursdays.

In these lab exercises, we will put the concepts from lecture into action.
Unlike the problem sets,

- we provide a solution for each problem,
- you may share your work freely with fellow students without violating
  the collaboration policy, and
- some problem statements lack detail (on purpose, so we can discuss
  different approaches).

In the first 10 minutes of a lab, we'll summarize the relevant lecture topics.
Then we'll discuss the code and hack on it together until the hour is over.
You can consult me, your fellow students, and the solution freely during the hour.

You can follow me as I build a solution, or you can go into a breakout room with
one or more of your peers, or you can hack alone and let me know if you get stuck.

At the start of lab, I'll post an invite URL for a [VS Code Live Share][live-share]
session. You can connect to the session in a web browser and follow along with each
step of development.

If you want to edit your own copy of the code independent of what I'm doing, see
the **Setting up a local dev environment** section below.

## Schedule

| week   | date      | lecture/lab      | topics                                              |
| ------ | --------- | ---------------- | --------------------------------------------------- |
| week 1 | June 24   | Lecture 1        | Intro, ADTs and object-oriented programming         |
| _Tue_  | June 25   | Lab 1            | To-do list, test-driven development                 |
| _Wed_  | June 26   | Lecture 2        | Recursion and backtracking                          |
| _Thu_  | June 27   | Lab 2            | Debugging `NQueens.java`, combination sum           |
| week 2 | July 1    | Lecture 3        | Sorting and algorithm analysis (1/2)                |
| _Tue_  | July 2\*  | Lab 3            | Analyzing loops, timing sorting algorithms          |
| _Wed_  | July 3    | Lecture 4        | Sorting and analysis (2/2), linked lists (1/2)      |
| _Thu_  | July 4    | Lab 4 (recorded) | video: `partition()` trace, inferring big O         |
| week 3 | July 8    | Lecture 5        | Linked lists (2/2); lists, stacks & queues (1/2)    |
| _Tue_  | July 9\*  | Lab 5            | StringNode, using a stack to implement undo & redo  |
| _Wed_  | July 10   | Lecture 6        | Lists, stacks and queues (2/2)                      |
| _Thu_  | July 11   | _Review session_ | Practice midterm exam                               |
| week 4 | July 15   | _Midterm exam_   |                                                     |
| _Tue_  | July 16   | Lab 6            | `isBalanced()`, something with queues?              |
| _Wed_  | July 17   | Lecture 7        | Binary trees, Huffman encoding                      |
| _Thu_  | July 18   | Lab 7            | `ExprTree` class, something else?                   |
| week 5 | July 22   | Lecture 8        | Binary search trees, balanced search trees          |
| _Tue_  | July 23\* | Lab 8            | Red-black trees, |
| _Wed_  | July 24   | Lecture 9        | Heaps and priority queues                           |
| _Thu_  | July 25   | Lab 9            | kth largest number, merging k sorted lists          |
| week 6 | July 29   | Lecture 10       | Hash tables, graphs (1/2)                           |
| _Tue_  | July 30\* | Lab 10           | Longest unique substring, web server log processor  |
| _Wed_  | July 31   | Lecture 11       | Graphs (2/2)                                        |
| _Thu_  | Aug 1     | Lab 11           | Maze solver using shortest path?                    |
| week 7 | Aug 5     | _Review session_ | Practice final exam                                 |
| _Tue_  | Aug 6     |                  |                                                     |
| _Wed_  | Aug 7     | _Final exam_     |                                                     |

\* Indicates a problem set due date

## Setting up

I organized the lab exercises into [Gradle][gradle] projects. Gradle
is an industry-standard build and testing tool for Java.

You **don't** need Gradle to compile and run the code in the `src/main/java/`
folders. To run the tests in `src/test/java/`, you need Gradle.

### Gradle

See Gradle's documentation: https://docs.gradle.org/current/userguide/installation.html

- On macOS, you can use [SDKMAN][sdkman] or Homebrew
- On Windows, manually install Gradle and update the `Path` system environment variable

### VS Code extension

If you use VS Code, install the [extension for Gradle][gradle-extension].
We also recommend moving the Test Explorer to your secondary Side Bar.
This layout allows you to browse files on the left, edit code in the center,
and see the results of tests on the right.

### Getting the code

The code is [hosted on GitHub](https://github.com/abreen/s22-labs), but you don't need
to use Git. Download the source code in a ZIP file here:
https://github.com/abreen/s22-labs/archive/refs/heads/main.zip

Extract the files from the ZIP archive and open the newly created folder in your editor
or IDE.

### Build, test, and run

Using the `gradle` command (or the Gradle extension in your editor), use any of
these "run" tasks to compile and run the code for the appropriate exercise:

    gradle :lab1:run
    gradle :lab1-solution:run
    gradle :lab2:run
    gradle :lab2-solution:run
    gradle :lab3:run
    ...

Or if your current directory is `lab3/` (for example), you can do `gradle run`.

- To compile the code but not run it, do `gradle :labX:build`.
- To run the tests, use `gradle :labX:test`.

## Testing

You can run tests using `gradle test` (from inside a subdirectory)
or `gradle :labX:test` (from the parent directory). You can
also run tests directly from VS Code by clicking the gutter icons:

![The test gutter icons showing test results](gutter-icons.png)

We use the industry-standard [JUnit][junit] framework which assumes that
test code is located in a separate `test/` directory.
Test code should begin with these two `import` statements:

```java
import org.junit.Test;
import org.junit.Assert;
```

Here is a brief summary of the imported members (your editor
or IDE can provide inline documentation):

- The `@Test` annotation: put this before test case (a method
  that calls your code and makes assertions)
- `Assert.assertNull(value)` will fail the test if the supplied
  value is not `null` (also see `assertNotNull()`)
- `Assert.assertTrue(booleanValue)` will fail the test if the
  supplied value is not `true`
- `Assert.assertFalse(booleanValue)` will fail the test if the
  supplied value is not `false`
- `Assert.assertEquals(expected, actual)` asks JUnit to compare
  the given values and if `actual` doesn't equal `expected`, the
  test fails (also see `assertNotEquals()`); note that the expected
  value should be passed **first**
- `Assert.assertThrows()` takes an `Executable` (a block of code)
  and fails the test if the code doesn't throw a specific exception
- `Assert.assertArrayEquals()` is like `assertEquals()`, but
  compares invidivual array elements

[gradle]: https://gradle.org/s
[sdkman]: https://sdkman.io/
[wsl]: https://learn.microsoft.com/en-us/windows/wsl/install
[gradle-extension]: https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-gradle
[toolchains]: https://docs.gradle.org/current/samples/sample_jvm_multi_project_with_toolchains.html
[literate]: https://en.wikipedia.org/wiki/Literate_programming
[info-string]: https://spec.commonmark.org/0.31.2/#info-string
[junit]: https://junit.org/junit5/
[live-share]: https://code.visualstudio.com/learn/collaboration/live-share
