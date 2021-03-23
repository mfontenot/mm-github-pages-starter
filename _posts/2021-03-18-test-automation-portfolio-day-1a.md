---
layout: post
title:  "Test Automation Portfolio - Day 1a"
date:   2021-03-18 13:30:00 -0600
categories: testing portfolio
---
<style type="text/css">
  .rss-subscribe {
	  display: none;
  }
</style>

## Let's revisit Browshot from Day 1, shall we

### Day 3 or 1a of building up my *Test Automation Portfolio*
Hey, mistakes were made on Day 1 and I own up to them.  Thanks to Julien Sobrier with Browshot to point me in the right direction.  I bring you...a working example of the Browshot API.

#### Browshot API and Postman - revisited
After a reply from the Browshot developer, I've gone back over the steps and found something new (all I had to do was scroll down on the *Dashboard* page 🤦‍♂️).

Scroll down to the *Choose a browser* section within the Browshot Dashboard page.  At this point I selected the *Chrome 89 - Free* option which gives you an instance id of 26.  This was what I had wrong withing Postman and was never going to give me anything for instance id=1 (which is what I inputted).  It also gives you a sample **API call:** to copy/paste, kind of like **API Flash** did in my [Day 2](https://mike-fontenot.dev/testing/portfolio/2021/03/15/test-automation-portfolio-day-2.html) experience.  I ticked a couple of options above this API Call example and copied it - `https://api.browshot.com/api/v1/screenshot/create?url=https://www.ministryoftesting.com/&instance_id=12&key=mySecretKey&size=page&hide_popups=0`.

The query parameters are fairly straightforward in their intentions.  Url - the url you want to capture ; instance_id - the instance id from Chrome 89 - Free ; key - my secret key to use the API ; size - I chose "page" to capture the entire page but there is also "screen", which I'm assuming will take only what shows up without scrolling ; hide_popups - because why not 🤓.

I pasted the API Call example into Postman and hit Send.  Wow!  This time I immediately see a "screenshot_url" in the response.  Clicking into the URL and it sends me to an image of the full capture of ministryoftesting.com's page.  Unlike Day 1, this worked perfectly.  I put any instance_id but that was incorrect and the developer told me to see the ones that were available.  A quick fix and now Browshot is working as expected!

Day 3/1a goes down in the books as a successful day of testing - still not automated yet 😅.

![](/assets/images/browshot-ministryoftesting.png)