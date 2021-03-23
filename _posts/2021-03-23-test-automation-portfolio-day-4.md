---
layout: post
title:  "Test Automation Portfolio - Day 4"
date:   2021-03-23 07:30:00 -0600
categories: testing portfolio
---
<style type="text/css">
  .rss-subscribe {
	  display: none;
  }
</style>

## Browshot API "automated" testing with Postman

### Day 4 of building up my *Test Automation Portfolio*
I've thought a lot about whether or not having a "Test" within Postman should hold a place in my **Automation Portfolio**.  The answer is, "maybe, yeah".  If all I have to do is press a button and check a result - Pass or Fail - then I would consider that an automation of a test.

Postman can be used for a number of different things - if we view some of their shared collections - and automating tests is one of them.  I've not even tried the Newman command line interface, which gives the ability to run collections of requests from the command line.  I'm pretty certain that people have used this as automation testing and it is perfect for those that need some sort of test suite.

#### Back to Browshot and Postman
Let's go through my original Test Plan from Day 3 and see how I did.

`- Utilize Postman to send a **GET** request to the API */create* endpoint`
That one was easily setup in Postman and now ready for the next one.  *Done*

`- Ensure appropriate query parameters are set`
I put this here because my exploratory testing with Browshot on Day 1 was a failure.  I now have the appropriate query paramaters - scroll down in the Dashboard for example - after the developer helped me out.  *Done*

`- Send the request`
Wow!  Sometimes the simplest steps in your plan could be forgotten.  But wait...I added something to this step.  I went a step further with this one and created a "Test" script to write to an environment variable (**screenshot_id**) which captures the id from the JSON response body I receive back from Browshot.  Postman forum search or favorite search engine to find out how to do this (my Test script below).  *Done - get a good response back and my environment variable holds the id*
```
var jsonData = JSON.parse(responseBody);
pm.environment.set("screenshot_id", jsonData["id"])
```

`- Create a test within Postman's **Tests** tab to check for existence of **screenshot_url** in the JSON response body`
Pro tip:  Another search was done to get this going.  I took this a step further as well and opted to test for the contents of **screenshot_url**.  I noticed it had my **screenshot_id** in the response JSON, and is why I save it to an environment variable in the previous request's test script.  I use that id along with the correctly formed URL to check whether or not my screenshot was successful.  If it has the full **screenshot_url** and is correctly formed then I can easily browse (or get a thumbnail image using another endpoint) to the screenshot.  *Done - Test script below*
```
// This begins the test - whatever is within quotes will print in your "Tests" results and Pass or Fail
pm.test("Has full 'screenshot_url' in JSON body with 'screenshot_id' from original screenshot request", function () {

// Put the response into a variable for checking later
var jsonData = pm.response.json();

// This says, to expect that the JSON response data and screenshot_url equals (matches) what is in parentheses.  Add the + symbol and pm.environment.get to get the screenshot_id that was saved earlier.
pm.expect(jsonData.screenshot_url).to.eql("https://browshot.com/screenshot/image/"+pm.environment.get("screenshot_id")+"?key=mySuperSecretKey&scale=1");

});
```


`- Pass or Fail the test depending on key/value's existence`
The final step of my "automation" of the Browshot API - screenshot of ministryoftesting.com site.  This is pretty much done with the previous step but still here because it explains what I expect the outcome to be - Pass or Fail, but Pass mostly.  After all the above has been done then I should be able to look at the **Tests** tab of my **Screenshot Info/Status** request and see **Pass** and the text I placed into the *pm.test* section above.  *Done*

![](/assets/images/browshot-screenshot-info-pass.png)

I went a little further just to see how the thumbnail endpoint performed.  It was pretty great - here it is.

![](/assets/images/browshot-thumbnail.png)