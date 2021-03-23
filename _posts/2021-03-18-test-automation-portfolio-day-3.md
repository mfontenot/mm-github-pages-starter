---
layout: post
title:  "Test Automation Portfolio - Day 3"
date:   2021-03-18 16:30:00 -0600
categories: testing portfolio
---
<style type="text/css">
  .rss-subscribe {
	  display: none;
  }
</style>

## Thinking about automating Browshot testing

### Day 3 of building up my *Test Automation Portfolio*
This is kind of a Day 3a, since I already had a Day 3 where I revisited the Browshot API and got it working.  It gave me a nice JSON response that was more informative that API Flash's response.  I may revisit API Flash again but, for now, here are my thought's about automating Browshot.

#### The brain dump of ideas
Browshot gave me a fairly comprehensive JSON response that I feel I can automate a test within Postman.

The main thing that caught my eye to test for is the existence of the **screenshot_url** key/value pair.  From Day 1, the JSON given back to me during my failure did not have this key/value pair.  This is a perfect place to start and I have some experience with creating a test in Postman to check for this within a JSON response.

That's settled then!  I have what I am going to do, the API in test, and what the results should be.  I'll have a successful test and a failure test (I'm good at that one 😉).

#### The Test Plan
API in test
- Browshot API - create screenshots of a website

Steps to create a screenshot and test results
- Utilize Postman to send a **GET** request to the API */create* endpoint
- Ensure appropriate query parameters are set
- Send the request
- Create a test within Postman's **Tests** tab to check for existence of **screenshot_url** in the JSON response body
- Pass or Fail the test depending on key/value's existence