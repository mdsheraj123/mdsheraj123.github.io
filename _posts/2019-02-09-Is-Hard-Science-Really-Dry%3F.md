---
layout: post
title: >
    Is Hard Science Really Dry?
hide_title: false
tags: []
excerpt_separator: <!--more-->
---

Some people question what is the use of education? What difference does knowing what they teach in school bring in our everyday life?

I used to struggle in answering this question because honestly apart from getting three annual exam back to back 100s in science \(6th, 7th, 8th\) and receiving praise, or to write code and earn money; I could not see how it would bring about any difference in how I would go to a shop to buy stuff or what physics I'd use to improve my basketball game \(honestly, I never used any physics dynamics equations there\) or how I could use my knowledge of organic chemistry to improve the way I bought grocery better than my mom\!

All in all, you'd live your life easily without knowing the math and science taught in school just by learning a language which can be done at home.

I got this question in my 12th board Physics viva and I arrogantly shrugged it off by saying I can use my knowledge to solve problems \(can't recall a single instance\) and that I would know better \(knowing about food chain made no difference in what I ate though\) along with how a better understanding of natural phenomenon would let you not simply getting mesmerised like an idiot.

But now, I think life isn't worth living without understanding how the world works even though you may be the richest business dealer around.

I'll show you two instances where I actually used plain school stuff to know something which'd help me tremendously.

Let's start with something I saw in the news a couple of days back \->
### ***<u>What should I feel if I am not a sheep?</u>***
[https://timesofindia.indiatimes.com/india/union\-cabinet\-approves\-10\-reservation\-for\-economically\-weaker\-sections/articleshow/67418734.cms](https://timesofindia.indiatimes.com/india/union-cabinet-approves-10-reservation-for-economically-weaker-sections/articleshow/67418734.cms)

Let's not discuss the concept of reservation here as I'm an ardent advocate of free markets:P

Back to the point, the way reservation works' that if you're having reservation and scored better than a general category candidate for the same seat, you'll be transferred to the general category. This basically translates to any candidate coming via reservation to be inferior \(at max the worst general student is equal to the best reserved\) to any general category unreserved candidate as per their scores. And this is guaranteed because if you're reserved and better than general, you're no longer coming via reservation.

Currently, 50% of the seats are reserved currently via caste and 10% reservation is for the economically weaker sections.

Now, something which is my concern, how do the people with more than ₹8Lakh ~ $10k per annum which is ~5% of the population get affected by the additional 10% economic reservation? You'd guess they will only lose 10% of the seats they were filling up... and that's where you're wrong\!

It's actually more than 20%, and this is how.

Suppose we have 100 seats with 50 general category seats remaining and assuming that the poor and the rich have equal intelligence, earlier

Poor \- 95% of 50 general category seats => 47.5 seats

Rich \- 5% of 50 general category seats => 2.5 seats

Now,

Poor\_A \- 100% of 10 general category economically reserved seats => 10 seats

Since the population is too large with <1% selection rate, we can assume no change in population,

Poor\_B \- 95% of 40 general category unreserved seats => 38 seats

Rich \- 5% of 40 general category unreserved seats => 2 seats

So, if the rich were getting 2.5 seats before the new additional 10% economic reservation, they are now getting just 2, a drop of 20%, not 10% which seems innocent.

In reality, the situation is even worse with much less than 50% of the seats going to the general category candidates and if 40% seats are remaining, then only 1.5% seats are going to the rich when they are 5% of the population.
### ***<u>Is the 80/20 rule spooky?</u>***
[https://en.wikipedia.org/wiki/Pareto\_principle](https://en.wikipedia.org/wiki/Pareto_principle)

80% of the effects come from 20% of the causes. Known as the Pareto Principle after Italian economist Vilfredo Pareto, who noted the 80/20 connection while at the University of Lausanne in 1896, as published in his first work, Cours d'économie politique. Essentially, Pareto showed that approximately 80% of the land in Italy was owned by 20% of the population.

This can be extended just about anywhere you can ever imagine, 80% of the work is done by 20% of the employees, 80% of the fish will be in 20% of the waters, a caelo usque ad centrum.

This sometimes starts to feel spooky and you begin to have thoughts of a master designer... unless, you know the math of normal distributions\!

I am going to prove that the 80/20 rule is a characteristic of the Gaussian Distribution.

\\[P\(x\) = \frac\{1\}\{\sigma\sqrt\{2\pi\}\}e\(\frac\{\-\(x\-\mu\)^2\}\{2\sigma^2\}\)\\]

This is the Gaussian distribution, also known as the normal distribution. Here,

μ = mean

σ = Standard Deviation

Total area under the graph = 1

{% include image.html url="/assets/img/posts/edited2000px-Gaussian_distribution_thick_lines.svg.png" caption="" alt="" %}

Our aim is to find λ for which the 80/20 rule will hold. \\[0.1 = \int\_\{0\}^\{\lambda\}\frac\{1\}\{\sigma\sqrt\{2\pi\}\}e\(\frac\{\-\(x\-\mu\)^2\}\{2\sigma^2\}\)dx\\]

Here μ is 0.

We aim to do this integral via Maclaurin series

{% include image.html url="/assets/img/posts/FinalMaclaurin.png" caption="" alt="" %}

A Maclaurin series is a power series that allows one to calculate an approximation of a function f\(x\) for input values close to zero, given that one knows the values of the successive derivatives of the function at zero. In many practical applications, it is equivalent to the function it represents.

Here \\[e^\{\-y^\{2\}\}=1\-y^\{2\}\+\frac\{y^\{5\}\}\{2\}\+...\\] Substituting in \\[0.1 = \int\_\{0\}^\{\lambda\}\frac\{1\}\{\sigma\sqrt\{2\pi\}\}e\(\frac\{\-\(x\-\mu\)^2\}\{2\sigma^2\}\)dx\\] we get

\\[48\sigma^6\sqrt\{2\pi\}\-480\lambda\sigma^5\+40\lambda^3\sigma^3\-5\sqrt\{2\}\sigma^6=0\\] If we assume λ=Cσ where C a constant, and are able to prove it, then we just proved 80/20 rule to hold for any normal distribution and in extension, to everything natural because this \\[e^\{\-y^\{2\}\}\\] stuff makes up the most basic of physics equations with the structure of the quantum wavefunction being one of them\!

Our final equation is

\\[48\sqrt\{2\pi\}\-480c\+40c^3\-5\sqrt\{2\}c^6=0\\] And this just happens to have roots at \-3.499, 0.251 and 3.424.

0.251 satisfies all out conditions as  λ should be around 0.2534σ from [http://onlinestatbook.com/2/calculators/normal\_dist.html](http://onlinestatbook.com/2/calculators/normal_dist.html)

The existence of this solution is enough to prove that the 80/20 rule is just an extension of the normal distribution.

It was fun doing this on a postcard\-sized book here \->
[https://drive.google.com/open?id=1QV7pknYxy3RCEOEo5NzRgxHsFilQZwqJ](https://drive.google.com/open?id=1QV7pknYxy3RCEOEo5NzRgxHsFilQZwqJ)