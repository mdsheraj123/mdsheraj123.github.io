---
layout: post
title: >
    Using logic in everyday life
hide_title: false
tags: []
excerpt_separator: <!--more-->
---
# Background

I did this Massive open online course

How to Reason and Argue \- Duke University on Coursera
[https://www.coursera.org/learn/understanding\-arguments](https://www.coursera.org/learn/understanding-arguments)

I did it only because if I was to become a scientist, engage in any academic activity or even in daily life I should know how to reason and argue in an established and correct way so as to leave no gaps in my reasoning. 

It would give me a lot of confidence in my reasoning along with being one of the skills that would help me immensely over my entire life, clear up my thinking and help me avoid mistakes that I have to pay for via consequences.

And I was right\! It's incredible what this course has taught me is helping me solve any problem in my life. Let me show you how.
# Software Engineering

One of the places where logic is almost everything we do is software engineering.

We solve problems using our logic and the guarantee that our code/architecture is correct is based on whether our logic is correct.

How do we know our code is correct?

Theory tells us all arguments in standard form are a set of premises that lead to a conclusion.
[
{% include image.html url="/assets/img/posts/Screenshot 2022-10-30 175211.png" caption="](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgqGElbI6PTHBkynjqmdMHd5gh6hd_HgQwwBwi3W_jURmLGR9Zd_3dxEpmlqfl9aZ1r4ajzVP2mv0cYuSe8AS2xE3UetNKVW2EChN0B_bSVk-E7HVbqO9bgGOhbZB-VjmrUUovzwegyQlYoUDqo6Bz0UNSSDvvF0Q03PUY-a1XdYp0hNE3ESB3B-Cg1fw/s539/Screenshot%202022-10-30%20175211.png)" alt="" %}

Here are a few examples:
[
{% include image.html url="/assets/img/posts/Screenshot 2022-10-30 175123.png" caption="](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgwc0dH5q5JBqT3raBOrE1SGbuMfhSKbfveMka7UeoPXPhC3XysSZMyMFJ52wFK8RCKwlKRrknZp5WS04WJuwN1naRpkbRh-wxY65xNCsLMjEhPwUmNQoi0U1LYtzMsVzhvfQxMgF9kgltNMpsKGpmIyTw5v5Q7gj0L6qNQ-fAtrtSJKUFRk6AEVcH6cw/s938/Screenshot%202022-10-30%20175123.png)" alt="" %}

You might think that the premises sometimes do not always lead to the conclusion and there is a fix for that in the standard form and that is to put the argument that the premises lead to the conclusion as a premise.

In our case the first argument changes to:

\(1\) I am a professor.

\(2\) If someone is a professor, he/she teaches classes.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Therefore \(3\) I teach classes. \(from 1 and 2\)

The second argument changes to:

\(1\) I teach classes.

\(2\) If someone teaches classes, he/she is a professor.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Therefore \(3\)  I am a professor.  \(from 1 and 2\)

We can use this standard form to make sure our code is correct. For example, a function

void incrementX \(const int x\) \{

    return x\+1;

\}

Can be proven to be correct by the following argument:

\(1\) The function takes an input x.

\(2\) The function does not modify x.

\(3\) The function returns x\+1.

\(4\) There are no side effects like integer overflow.

\(5\) The function is always guaranteed to produce output.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Therefore \(6\) The code is correct. \(from 1, 2, 3, 4, and 5\)

One more thing to note is our conclusion can be logical but not correct. There is a distinction as follows:

\- logical conclusion \- Assuming the premises are correct, the premises lead to the conclusion. \(valid argument\)

\- correct conclusion \- The premises are correct and the premises lead to the conclusion. \(sound argument\)

[
{% include image.html url="/assets/img/posts/Screenshot 2022-12-16 001638.png" caption="](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj7LlV1EYiYYQ2Tpz2VO8ZbzWJuEMnsFhgIyopJPMCCdwEEoo8OyDOeoz-AbvDZIrHHDjIZc7kIHEoIo30fWrf_lk1XjWfMFh5BHjYBj77MihzkenwRnJGcqB285XXuP4VyIzyoXI2sHnbUtQeUZmMn6MDO0dXcqezJTzQBoJqCoDuye2WTWppIQKfxDw/s962/Screenshot%202022-12-16%20001638.png)[" alt="" %}
{% include image.html url="/assets/img/posts/Screenshot 2022-12-16 002204.png" caption="](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjJKYmWtk11VcFa2UN3APoD62ozhHe9gc3jscEEEBZ6mEKKtd3pUsOKpNg-ShRwlUuokkXNKg_mq0UsEWE1tAdC4c5EjJsGJr9F000esTJ9Hxddx9LdpfwaW0w_VG5JMFnLmG7i1Mur_4ZOuOzbGmnqQdk2inkX3H2eM7c6PCk1V4tzLA4U6Z1nUF_TZQ/s1082/Screenshot%202022-12-16%20002204.png)" alt="" %}

Our conclusion that the code is correct, is correct only if the premises are correct. One of the premises can be incorrect, for example \(4\) if the number is too large for the size of int.

We can extend this logic to other areas of our life, even to software architectures and other conclusions in software engineering.
# Things to consider

However, please note that nothing is perfect, our logic and arguments should be reasonable for the task at hand.

No premise can be absolutely true and we can definitely miss out some premises required that lead to the conclusion but if there is reasonable accuracy at each step, we can reasonably conclude that our conclusion is correct.

Presentation I gave to class 10 kids as a part of CSR. [https://docs.google.com/presentation/d/19rUZIsd\-6Jbc67oxJT81iWJfwIwM2WYXgVTfZ2iGfxY/edit?usp=sharing](https://docs.google.com/presentation/d/19rUZIsd-6Jbc67oxJT81iWJfwIwM2WYXgVTfZ2iGfxY/edit?usp=sharing)