# Game Over

Above all, games need to provide real-time feedback to players, as well as goals to achieve. However not every attempt at gamification has managed to do this.

### Google News

In Late 2011, Google News introduces badges to their news feed. When players read a news article, they were sometimes presented with a badge to appear on their profile.

![Google Badges](../images/Google Badges Full.jpg)

Some gamers wanted to rise to the challenge and collect every badge they could. There was just one problem; nobody knew how to do it. Google refused to release an official list of all of the badges or requirements, but players managed to track over 500 different types of badges.

The badges also had no meaning to the players. They could not be exchanged for anything else, and were not seen as an indication of effort, just luck. Because of this, many readers shunned the idea of the badges, and they were finally removed in Late 2012.

Had these badges been more open to the players about how much effort was required they might have been seen as more worthwhile, being similar to the badges earned by the Scouts for fire making and safety skills or rope skills.

### Marriott Hotel

Another from 2011, the Marriott Hotel group wanted to expand its workforce and hire 50,000 new employees. To do this, they created "My Marriott Hotel"; a Facebook Game similar to Farmville and Restaurant City. Players were tasked with overseeing every aspect of the hotel, starting in the kitchen.

![My Marriott Hotel](../images/my-marriott.jpg)

The game was seen as unpolished and slow, with players in the demo having to stare at a progress bar of food cooking for 20 seconds without anything else to do. After food was cooked, players had to "inspect for quality" and choose whether to re-cook the food or send it out.

Players quickly became bored of the game and stopped playing; the entertainment factor was missing. The Marriott Hotel Group had previously promised to add other chapters to the game, but ultimately dropped the idea entirely.

### The Continuous Integration Game (again)

A few chapters ago, we introduced the "Continuous Integration Game", where players are rewarded for adding new tests, and punished for breaking the build. As a reminder:

* Breaking the build (-10)
* Breaking a broken build (0)
* Build with no test failures (+1)
* New test failures (-1 each)
* New passing tests (+1 each)

The primary issue here is that software developers are smart, and used to analysing systems. Given a game system, it is likely that some will try to exploit the system, and some will even succeed.

For example, a developer might see that an easy way to climb the leaderboard is to focus on adding new passing tests, as these are worth one point each. The original idea behind giving points per test is to encourage small, simple tests be written instead of large sprawling tests covering everything.

The problem arises when the developer starts writing short *meaningless* tests. Testing that the getter and setter for each of their new properties works, or testing that the library they are linking against is doing what it should be.

```
testFreePoints() {
   // +1 points for me!
   expect(true).toEqual(true);
}
```

If the developer was just writing empty tests such as above, then we would expect the code review to flag it up. However adding a test for the following might still be a dud test, but would most likely make it past the code review:

```
testSetterGivesMeFreePoints() {
    //Given:
    obj.setValue(5);

    //Then:
    expect(obj.underlyingValue).toEqual(5);
}
```

In contrast, the developer who writes a small test to demonstrate a very tricky bug is spending much time for less points, so would appear lower on the leaderboard.

The culture around the game needs to develop to discourage this kind of point-boosting, while the game itself is developing.
