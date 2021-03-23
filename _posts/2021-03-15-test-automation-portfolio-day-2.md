---
layout: post
title:  "Test Automation Portfolio - Day 2"
date:   2021-03-15 12:15:00 -0600
categories: testing portfolio
---
<style type="text/css">
  .rss-subscribe {
	  display: none;
  }
</style>

## On a quest to find a screenshot API

### Day 2 of building up my *Test Automation Portfolio*
I did some more searching to find a screenshot API that would give me good results to post for my *test automation portfolio*.  I'm hoping that I found that in <a href="https://apiflash.com" target="_blank" rel="noopener noreferrer">API Flash</a> 🧐.  From the looks of their site, it's easy to use and "simple and powerful".  I did what I knew how to do...signed up (another password).

#### API Flash and Postman
Log into API Flash and you're shown a *Dashboard* with usage - **0** ha!  This is kind of similar to Browshot but a much better user experience with API Flash.

At this point I can go either way.  I can read (blah, blah, here's how to get a screenshot) or I can use this fancy **Query builder**.  I'll check out the query builder...

Whoa!  The query builder is amazing!  I input the url to capture, click on a few more options and use the nifty *Copy to clipboard* option that refreshes on each click.  Let's paste that into Postman and find out what happens.

I set the request to **GET** and pasted in the copy from their site.  Again, like Browshot, the capture was for *https://www.ministryoftesting.com*.  I almost immediately - 10.69s - received a URL (I chose JSON format for the response type).  Copy and paste the URL into my browser.........Dang!  I see a screenshot of the site.  Now to play with changing the response type to *image*.  At this point there may not be much to talk about with **API Flash** since it just works out of the box.

I went back to the dashboard and selected the response to be *image* and also try out the *full page* option.  Then I copy and paste the request query from the dashboard into Postman and hit *Send*.  It took a little over 9 seconds - 19.85s - than the original request without *image* selected but it came back with an image in Postman's response body.

Here's the screenshot of the screenshot in Postman showing the bottom of the site to show you that it really did scroll and get the full page.

![](/assets/images/apiflash-ministryoftesting-screenshot.png)
