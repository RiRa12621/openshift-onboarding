---
title: "Unit 4"
date: 2020-04-22T16:40:13+02:00
weight: 40
---

## What's happening in this unit?
You will define an SLI and an SLO for your example application.


## Action items
* Define an SLI
* Define an SLO

## Task 1

Since we have deployed our example application and exposed metrics for it, people may actually use it.
Now it's time to think about the reliability part of our application.
To make this measurable and actionable we will define an SLI for it.

What is an SLI?
SLI stands for Service Level Indicator. Let's take a quick look into the [Google SRE book chapter 4](https://landing.google.com/sre/sre-book/chapters/service-level-objectives/)
```
An SLI is a service level indicator - a carefully defined quantitative measure of some aspect of the level of service that is provided.
```
Now in our real world example, how would we approach this?
The main questions are
* What can we measure?
We can measure whatever was exposed as metrics in this example, which makes us pretty flexible.

* What do our users care about?
This is tough to answer in the real world but for our example app, let's just assume that users want their response fast and they don't want errors.

Now let's translate this into an SLI.
Normally we'd be looking at historical data at this point about how our application performed in the past so we actually know how many errors we had in, let's say the past months.
Our application however is probably not going to live a month so we just have to make this up.
I would say 200ms for a response is a fair time and you don't really have a choice but to agree.

That's it for this task. We have established two SLIs:
* Proportion of errors
* Proportion of sufficiently fast requests.

## Task 2

While defining an SLO soudns pretty tricky, this task should actually be pretty easy as we can make most of the things up since we don't have real users.
An SLO or Service Level Objective is basically just a given goal that you want to achieve for your SLIs over a given period.
Let's assume we talk about a 28 day rolling window as the timeframe, just for the ease of it.

In Task 1 we found out what our users care about, now we have to ask ourselves, what the expectations are about the things they care about:
* How many errors are acceptable?
* How many slow requests are acceptable?

This can be a bit abstract to think about in percentages but @metalmatze thankfully made [a tool](https://promtools.dev/) that translate a given percentage into time.
That way you can easily visualize how long in the 30 day window your users will not be able to access your service.

Since not that many people are using our service and we don't really want to go oncall for it, 99% is fine for both our SLOs.
This is not very scientific and not production grade evaluation but should give you an understanding of how setting SLOs work.

This means 99% of requests should be successfull AND 99% of requests should be sufficiently fast.


Pro Tip: [promtools](also helps you to generate a prometheus query for this)

That's it.
We have defined two SLOs and two SLIs for our example service.
