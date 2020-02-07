---
layout: post
title: How To Create A Linear Regression in TypeScript
tags:
  - coding
  - typescript
comments: true
---

I've been doing some work with [CodeForFoco](https://github.com/CodeForFoco/).  Namely in the area of creating linear models for them.  In this post, what I did, and why.

Last thing before I get started!  If you just want to use a good working regression library, this one is the best I've found:  [regression-js](https://github.com/Tom-Alexander/regression-js)


### Why didn't I just use regression.js?
I just recommended them for you, why didn't I take my own advice?  Simply because, the project that's going to use this, needed a simplified model, with all the complixities removed.

By creating my own library, I was able to keep the input/output system simple enough where even a beginner programmer could integrate my code!

However the best approach may still be to use regression-js and create a wrapper for it.

### Ok, lets dig in!

Lets create our class

    class LinearModel {
        original: number[][];
        slope: number;
        intercept: number;
        r_squared: number;
        constructor(original: number[][]) {
            this.original = original;
        }
    }

We know we are going to need the slope, intercept, and r_squared (if your not sure what R<sup>2</sup> is, I'll talk about it more later).  

The most important method we are going to create is `linear_regression`.

It's going to do the math required to determine the slope and intercept.  In turn that will allow us to create a "[Line of Best Fit]()", finally with that done, we can determine our [coefficient of determination]() (R<sup>2</sup>).

I will be walking through what I'm doing, not why.  If you don't understand the math, here are some helpful links: CREATE LINKS


    linear_regression() {
        // This generates our slope + intercept

        // Lets get our x and y into their own array
        var x = []
        var y = []
        this.original.forEach(element => {
            x.push(element[0])
            y.push(element[1])
        });

        // _sum(val) just is a helper function that sums an array (not included)

        // We are setting some needed vars before we start
        let sum_x = this._sum(x)
        let sum_y = this._sum(y)
        let length = this.original.length

        // This creates ∑x²
        let sum_x_squared = 0
        x.forEach(element => {
            sum_x_squared += element * element
        });

        // This creates ∑y²
        let sum_y_squared = 0
        y.forEach(element => {
            sum_y_squared += element * element
        });

        // Now we are doing ∑(x+y)
        let sum_of_products = 0
        this.original.forEach(element => {
            sum_of_products += element[0] * element[1]
        });

        // This is the formula for slope
        this.slope = (sum_of_products - (sum_x * sum_y) / length) / (sum_x_squared - ((sum_x ** 2) / length))
        // And the formula for intercept
        this.intercept = (sum_y - this.slope * sum_x) / length
    }

Whoot!  And with that, we have our linear regression.  Pretty easy overall, right?  Now we need two more things to call this complete.  

1. We need a to get our R<sup>2</sup>
2. We need to use that to create a simple confidence band.

I'll be covering those two issues in a later post.
