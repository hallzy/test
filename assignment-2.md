##Assignment 2

##Group 21
Kelly

Shelby

Steven

##Exercise 2.1

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


##Exercise 2.2

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


##Exercise 2.3

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


##Exercise 2.4

####testSpriteAt

We created a test to verify that a Sprite could be placed on a tile.

####testPut

We made 2 tests to test the two scenarios below:

* Tested that a sprite can be placed from one tile to another.
* Tested what happens multiple sprites try to be put at a tile. Whichever
  sprite was called last with the put method will be the TopSprite.

####testSpriteTypeAt

We created test cases to show that every type of sprite can be placed on a tile.
Then we tested that SpriteTypeAt returned the correct Sprite Type.

####testTileAtOffset

Made a test case to verify that the correct tile is returned given the offset.

##Exercise 2.5

####Domain Matrix

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

**OK = True,**
**R  = False**

####Test class for model.board.withinBorder.java

```java
package org.jpacman.test.framework.model;

import static org.junit.Assert.*;

import java.util.Arrays;
import java.util.Collection;

import org.jpacman.framework.model.Board;
import org.junit.Before;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.junit.runners.Parameterized;

@RunWith(Parameterized.class)
public class BoardWithinBorderTest {

  private Board board;
  private static final int WIDTH = 10;
  private static final int HEIGHT = 20;

  private int x;
  private int y;
  boolean expectedResult;

  /* Initialize the board */
  @Before
  public void init() {
    board = new Board (WIDTH, HEIGHT);
  }

  /* Each parameters is placed as an argument here */
  public BoardWithinBorderTest(int x, int y, boolean expectedResult) {
    this.x = x;
    this.y = y;
    this.expectedResult = expectedResult;
  }

  /* Declare all parameters here */
  @Parameterized.Parameters
  public static Collection<Object[]> input() {
    return Arrays.asList(new Object[][] {
      {0, 2, true},
      {-1, 5, false},
      {10, 13, false},
      {11, 18, false},
      {4, 0, true},
      {6, -1, false},
      {3, 20, false},
      {8, 21, false}
    });
  }

  /* This test will run 8 times since we have 8 parameters defined */
  @Test
  public void testWithinBorder() {
    assertEquals (expectedResult, board.withinBorders(x, y));
  }
}
```


##Exercise 2.6

####BoardTest.java

The coverage before was 0% and now coverage is at 100%. The test coverage is at 100% because all tests were feasible and passed.

The coverage of Board.java is 33%. This is because certain methods could not be tested such as tileInvariant because it is protected
and onBoardMessage because it is private. Additionally, tileAtDirection is tested in the class BoardTileAtTest. Lastly, all the assert
statements are missed.

####WithinBorders

The coverage before was 0% and now coverage is at 100%. The test coverage is at 100% because the test was feasible and passed.

The coverage of Board.java is 14.6%. This is because this class only tests the within Borders method.

##Exercise 2.7

Total Code Coverage: 79.0% (+4.4%)

Application Code Coverage: 68.2% (+1.4%)

Test Coverage: 98.6% (+0.4%)

The code coverage as shown in the brackets above, has increased after adding the
test cases.

The Application Code Coverage increased because we added test cases for code
that was previously not being tested.

The test coverage increased because we added more tests to the already existing
tests, which would increase the test code coverage (since all of the new tests
are executed).

Since both of those increased, that explains the increase in total code coverage.

##Exercise 2.8

####FactoryException.java:

Started at 0% coverage. The coverage is now 100%. The testcase file has only
91.8% coverage because there are 2 conditionals that check that the asserts
were actually executed, since the main asserts are inside of a try-catch block.

I did this by throwing the exception in two different ways to ensure that it
worked at intended.

####Sprite.java

Started at 32.3% coverage. The coverage is now 42.1%. We did this by adding two
testcases that cover GetSpriteType(), and the ToString() methods.
