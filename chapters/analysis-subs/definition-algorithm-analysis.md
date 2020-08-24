# Definition of Algorithm Analysis

As we mentioned before, the same problem addressed by two developers can easily end with two differents programs. So the question is How do we know which solution to select?

At this point, we should put the light on the difference between two important terms, a program and an algorithm that the program is implementing.

An algorithm is a generic way, to describe a step-by-step list of instructions to make the computer able to solve a certain problem.

However, the program, on the other hand, is an algorithm that has been translated into a specific programming language. So different programs are possible for the same algorithm, depending on the person who wrote them and the used programming language.

Algorithm analysis is concerned with comparing algorithms based upon the number of computing resources that each algorithm consumes.

## What is a Computing Resources?

The term can be understood in two ways. The first is by considering the amount of space of memory an algorithm requires to function. Or by considering it as the amount of space required for the program dictated by its instance itself.

## Alternative

We can analyze and compare programs performances based on the amount of time they require to execute, referred to as the "execution time" or "running time".
In JavaScript, we can track the actual time required for a program to compute its result by using ```performance.now()``` method which return a DOMHighResTimeStamp (unit: milliseconds).

### How?

We need to call the method twice, at the beginning and the end. Then by calculating the difference between these two values, we get the "execution time".

> You should know that ```performance.now()``` is not a server-side method.
> instead you should use ```process.hrtime()```.
> It returns a tuple array [seconds, nanoseconds] of the current high-resolution real-time.

#### Client-side usage

```javascript
    function sumOfN (n)
    {
        let start = performance.now();
        let sum   = 0;

        for (let i = 0; i < (n + 1); ++i)
        {
            sum  += i;
        };

        let end   = performance.now();
        console.log(
            end
        );

        return sum;
    };

    console.log(sumOfN(8));
```

#### Server side usage

```javascript
    function sumOfN (n)
    {
        let start = process.hrtime();
        let sum   = 0;

        for (let i = 0; i < (n + 1); ++i)
        {
            sum  += i;
        };

        let end = process.hrtime();
        end     = end[0] * 1000000 + end[1] / 1000;
        console.log(
            'Execution time: %i [unit: milliseconds]',
            end
        );

        return sum;
    };

    console.log(sumOfN(8));
```

### Next

[Big-O Notation](analysis-subs/big-o-notation.md)
