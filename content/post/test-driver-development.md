+++
author = "Darshan Chaudhary"
date = 2019-03-09
title = "Some thoughts on test driven development"
+++

Test driven development is a style of programming that involves writing unit tests before actually writing the feature and using them to guide the implementation of the feature. 

This is something we have been thinking a lot about at the Go-Jek engineering bootcamp I am currently in and exploring it with a dummy example. In our example, we are asked to write a Geometry library which can model various shapes, starting with a line. 

We start with the skeleton of the `Line` class. 

```
public class Line {

    private int x1, x2, y1, y2;
    
    public Line(int x1, int x2, int y1, int y2) {
        this.x1 = x1;
        this.x2 = x2;
        this.y1 = y1;
        this.y2 = y2;
    }
    
    public double getLength() {
        return -1.0;
    }
}
```

Here, the `getLength` method is dummy right now, returning `-1.0` for all values. 

We can add a test and run it to see it fail.

```
public class LineTest {

    @Test
    public void testLengthforZeroCoordinates() {
        Line testLine = new Line(0,0,0,0);
        assertEquals(0.0, testLine.getLength(), 0.0);
    }
}
```

This fails since it expects a `0.0` and we are returning `-1.0`.
Now, we can change the return value to `0.0` and the tests should pass.

At this point, we can add some more tests which should fail

```
public class LineTest {

    @Test
    public void testGetLengthReturnsZeroIfSameXCoordinates() {
        Line line = new Line(1, 1, 1, 5);
        assertEquals(4.0, line.getLength(), 0);
    }

    @Test
    public void testGetLengthReturnsZeroIfSameYCoordinates() {
        Line line = new Line(1, 6, 1, 1);
        assertEquals(5.0, line.getLength(), 0);
    }

    @Test
    public void testGetLengthReturnsZeroIfDifferentCoordinates() {
        Line line = new Line(0, 0, 3, 4);
        assertEquals(5.0, line.getLength(), 0);
    }
}
```

At this point, we can go ahead and implement the `getLength` method.

```
package com.bootcamp;

public class Line {
    private int x1;
    private int y1;
    private int x2;
    private int y2;

    public Line(int x1, int y1, int x2, int y2) {
        this.x1 = x1;
        this.y1 = y1;
        this.x2 = x2;
        this.y2 = y2;
    }

    public Double getLength() {
        return (double) Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
    }
}
```

Now, the tests should pass and we can move on the next functionality!

The advantages of this is that it allows you to pin down the correct and expected behavior. Now, one can go ahead and refactor with confidence and run the tests. If they pass, one can be assured that things didn't break.
