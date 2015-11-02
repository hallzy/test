#Assignment 3

##Group 21
* Kelly
* Shelby
* Steven

##Exercise 3.1

####PIT

#####Ease of Use:
* Really easy to use.
* pom.xml for PIT is easy to use and understand
* One command runs PIT
* Nice html file to easily view results

#####Set of Mutation Operators supported:
* Activated by Default:
  * Conditionals Boundary Mutator
  * Increments Mutator
  * Invert Negatives Mutator
  * Math Mutator
  * Negate Conditionals Mutator
  * Return Values Mutator
  * Void Method Calls Mutator
* Deactivated by Default:
  * Constructor Calls Mutator
  * Inline Constant Mutator
  * Non Void Method Calls Mutator
  * Remove Conditionals Mutator
  * Experimental Member Variable Mutator
  * Experimental Switch Mutator

#####Mutation Testing Strategy and Effectiveness in Mutation Testing:
* Strategy:
  * Generate mutants by manipulating byte code
  * Test selections are coverage based
  *  Handles equivalent mutants by not generating mutations for lines that contain a call to common logging frameworks
  * Unique feature: Incremental analysis feature
* Effectiveness:
  * Quite effective - There are quite a lot of mutation operations supported, and a good amount of them are enabled by default
  * Faster - PIT test entire code bases rather than single classes at a time


####Javalanche

#####Ease of Use:
* Not easy to use
  * Need to manually specify the properties in javalanche.xml. This step can be very tedious.
  * Need Apache Ant.
  * No sufficient documentation troubleshooting and no public issue tracking.
* Nice to have
  * Automated HTML report
    * The report provides detailed measure of the mutation testing. For each mutation, a table shows its database id, line number, mutation type, detected/not-detected and its mutation impact.

#####Set of Mutation Operators supported:
* Negate Jump Condition Mutator - replace a conditional jump by its counterpart/
* Replace Numerical Constant Mutator - replace a numerical constant X by X+1, X-1 or 0.
* Replace Arithmetic Operator mutator - e.g. replace + by -.
* Omit Method Call Mutator - if a method call has a return value, a default value is used instead

#####Mutation Testing Strategy and Effectiveness in Mutation Testing:
* Strategy
  * Generate mutants by manipulating byte code
  * Test selections are coverage based
  * Handles equivalent mutants by checking for invariants violations
  * Unique feature: equivalent mutation detection
* Effectiveness:
  * Javalanche allows mutation testing of programs to be at several orders of magnitude larger than its original program.
  * Mutations that violates invariants are more likely to be detectable by test suites. Focusing on these mutations when improving test suites will generate more efficient and precise measure of the adequacy of a test suite.


####Which one would we choose to use?

#####We would choose to use PIT:
  * PIT is much easier to setup and use
  * PIT is faster, support is available and has sufficient documentation
  * PIT integrates with major build systems (Ant and Maven) and is the only project to provide a Maven plugin
  * PIT is the only system to have no known issues yet

We conducted the assessment by **ease of use, support/documentation availability, tool integration, efficiency and their unique feature**

| Tool                 | PIT                                                                                        | Javalanche                                                      |
|:--------------------:|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| **Ease of Use**      | easy to setup and use                                                                      | not easy to setup and use, require Ant                          |
| **Support**          |  actively developed and releases frequently                                                | not actively developed and releases frequently                  |
|                      | supports are readily available                                                             | support available are unclear                                   |
| **Documentation**    | has better documentation                                                                   | has limited documentation                                       |
| **Tool Integration** | integrated with Ant and Maven                                                              | not integrated with main build systems                          |
| **Efficiency**       | faster by testing entire code bases rather than single classes at a time                   |  can produce large number of mutations                          |
|                      | support many mutation operations by default                                                | least time consuming given a larger number of surviving mutants |
| **Unique feature**   | **Incremental analysis**                                                                   | **Equivalent mutation detection**                               |
| **Pros**             | avoid re-running coverage analysis                                                         | least time consuming given a large number of surviving mutants  |
|                      | killed mutations in the previous runs are assumed to be killed in a current run            |                                                                 |
| **Cons**             | can be time consuming because it runs coverage analysis before performing mutation testing | high computational cost                                         |


##Exercise 3.2

PIT generated 33 Mutations, 32 of which were killed mutations for a mutation
score of 97%.

#####Mutation Coverage Scores

* DefaultGameFactory.java  = 7/7 = 100%
* Board.java               = 7/7 = 100%
* Game.java                = 6/7 = 86%
* PointManager.java        = 7/7 = 100%
* Sprite.java              = 5/5 = 100%

##Exercise 3.3

There was only one mutant not killed, and that was in Game.java on line 204 for
the won() method.

This is not an equivalent mutant, but a weakness of the test suite.

This mutant is living because there is no coverage for this method, so adding a
test case for it should fix this problem.

The mutation score for the test suite is 97%

##Exercise 3.4

To fix the mutant score for Game.java, two lines needed to be added to a test in GameTest.java:

```java
assertEquals("Game Not won yet", false, game.won());
assertEquals("Game has been won", true, game.won());
```

In the below test:

```java
  @Test
  public void testC5_PlayerMovesToFood() throws FactoryException {
    Game game = makePlay("P.#");
    Food food = (Food) game.getBoard().spriteAt(1, 0);
    Player player = game.getPlayer();

    assertEquals("Game not won yet", false, game.won()); //

    game.movePlayer(Direction.RIGHT);

    Tile newTile = tileAt(game, 1, 0);
    assertEquals("Food added", food.getPoints(), player.getPoints());
    assertEquals("Player moved", newTile.topSprite(), player);
    assertFalse("Food gone", newTile.containsSprite(food));

    assertEquals("Game has been won", true, game.won());//
  }
```

This gave Game.java a mutation score of 7/7 so that now our total mutation score is 100%.

