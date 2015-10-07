Assignment 2
============

Group 21
--------
Kelly
Shelby
Steven

Exercise 2.1
------------

Scenario Chosen: Move Pacman in several directions to test movement

Coverage: 50.1%

3 Interesting Findings From Inspection (Explanation):
  * The tests are 0% covered because we ran the coverage tool as a java app,
    instead of a junit test.
  * In the Board.java file the method "tileInvariant()" was never run, even
    though it should return true, iff all tiles are created correctly. There are
    several other functions that were also never executed.
  * The start() method in "ButtonPanel.java" has some lines highlighted with
    yellow (showing asserts). The start() method shows 42.1% coverage, even
    though it looks like the lines should have been covered. The asserts appear to
    have altered the outcome of the coverage tool.


Exercise 2.2
------------

With Assertion Checking

Scenario Chosen: Move Pacman in several directions to test movement

Coverage: 57.2%

3 Interesting Findings From Inspection (Explanation):
  * The tests still have 0% coverage because we ran the coverage tool as a java
    app, instead of a junit test.
  * This time the tileInvariant() method in Board.java was run with 97.5%
    coverage.
  * the start() method from ButtonPanel.java executed with 65.8% this time,
    instead of the 42.1% that was covered last time.


Exercise 2.3
------------

Total Code Coverage: 74.6%

Application Code Coverage: 66.8%

Test Coverage: 98.2%


  The Application Code Coverage is the best representative because, the test
coverage should be close to 100% anyways since it is just instructions for
running the program a specific way, so the test coverage would not give a good
idea of the coverage of the application.

  The total code coverage is just a combination of the two, and since the test
coverage should always be close to 100%, the total code coverage would not have
much of an indication of the coverage of the application.


Exercise 2.4
------------

Exercise 2.5
------------

### Domain Matrix
**Boundary condition for: x >= 0 && x < width && y >=0 && y < height**
**_set: width = 10, height = 20_**

| Variable | Condition   | Type   | t1 | t2 | t3 | t4 | t5 | t6 | t7 | t8 |
|----------|------------|-------|----|----|----|----|----|----|----|----|
| x      | >= 0     | on   | 0   |    |     |    |    |    |    |    |
|       |          | off  |   | -1 |    |    |    |    |    |    |
|         | < 10     | on   |     |    | 10 |    |    |    |    |    |
|       |          | off  |   |    |    | 11 |    |    |    |    |
|       |      | in  |   |    |    |    | 4  | 6  | 3  | 8  |
| y      | >= 0     | on   |    |    |     |    | 0  |    |    |    |
|       |          | off  |   |    |    |    |    | -1 |    |    |
|         | < 20     | on   |     |    |    |    |    |    | 20 |    |
|       |          | off  |   |    |    |    |    |    |    | 21 |
|       |      | in  | 2   | 5  | 13 | 18 |    |    |    |    |
| Result   |            |    | OK | R  | R  | R  | OK | R  | R  | R  |

**OK = True**
**R  = False**



Exercise 2.6
------------

Exercise 2.7
------------

Exercise 2.8
------------

#####FactoryException.java:

Started at 0% coverage. The coverage is now 100%. The testcase file has only
91.8% coverage because there are 2 conditionals that check that the asserts
were actually executed, since the main asserts are inside of a try-catch block.

I did this by throwing the exception in two different ways to ensure that it
worked at intended.

#####Sprite.java

started at 32.3% coverage. The coverage is now 42.1%. We did this by adding two
testcases that cover GetSpriteType(), and the ToString() methods.
