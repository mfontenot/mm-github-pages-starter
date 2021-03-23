---
layout: post
title:  "Test Automation Portfolio - Day 1"
date:   2021-03-12 12:45:00 -0600
categories: testing portfolio
---
<style type="text/css">
  .rss-subscribe {
	  display: none;
  }
</style>

## "Build up your *Test Automation Portfolio*", they say, "It'll be fun", they say

### Day 1 of building up my *Test Automation Portfolio*
First things first, props to Angie Jones' post on <a href="https://techbeacon.com/app-dev-testing/10-portfolio-projects-aspiring-automation-engineers" target="_blank" rel="noopener noreferrer">TechBeacon</a> for calling me out.  I jumped into being a QA/Test Engineer 1+ years ago and don't have too much to show for it (except my actual job performance 😉).  This will be a way for others to follow along and to showcase things I am good at (still learning).

I read the 10 projects and then pretty much jumped right in and visited the link in the third paragraph (test automation portfolio).  That brought me to another page on TechBeacon that I browsed through and noticed **Any-Api.com**.  It caught my attention and I visited that link next.

I went to XKCD's example but didn't like that I may have to know which comic I wanted to ask for.  I then noticed **PasswordUtility.Web** and thought, "wow, that would be cool if I could get Postman to generate some passwords for me", so I went into that API.  Clicked through a couple things to get me to /api/password/generate > Password_Generate then *Try it out*.  I set a couple request parameters and hit *Send Request*.  There was some garbled stuff in the response and I thought, "dang, that is either a cool password or it is totally messed up".  This then led me to visit the website in the **POST** request - **NOTE:  Do not visit the website in the POST request!  It is NSFW!**  Anyway...back to searching for a good API to use for my 1st day of building my portfolio.

I clicked into *TOOLS* on the Any-api.com page and noticed **Browshot** - "Take screenshots of any website in real time".  That sounds like a cool thing to do.  Clicked into it and searched the site first, instead of going directly to it like before.  It is legit and so I signed up for a free account.  If you confirm your email then you get 100 free screenshots each month - Done!  Onto using Postman to grab some web page screenshots.

#### Browshot API, Postman, and me
Once on the Browshot site and logged in, you are greeted with your *Dashboard* and the #2 option is what I'm looking for - **Use the API** "Take screenshots programmatically with our API.....Your API key is **blahBlahblah**".

You'll have to click into the **API Documentation** at the top of the site, then *screenshot/create* on the right side menu.  This is what I want to try out first - capturing (creating) a screenshot.  There are only 2 required request parameters and that is perfect for now.  They are the *url* of the page to get a screenshot for and *instance_id* to use.  Not sure I can use anything for *instance_id* but I'll give it a go.

The **Any-Api.com** site will give you a good idea of how to form the request for **Browshot** but you can also see the endpoint above - */api/v1/screenshot/create*.  The top of the API Documentation also gives a quick example of the complete URL to use, and can be put into Postman and edited as you need.  I used the example (copy/paste) and edited with my API Key.

I set the request to **GET** and pasted in the example.  I put in my key at the end and the website to capture was *https://www.ministryoftesting.com*.  So far so good...now, let's hit **Send** in Postman.  Well, that didn't work.  It took a few seconds and came back with an error.  The example I copied from the top of the API documentation page has */simple/* within it and I wanted the full-blown screenshot API abilities.  Mistakes were made 😜.  I fixed up the request (removed /simple) and resubmitted...Blam-O!  I receive a JSON response with some details:

``` JSON
{
    "steps": "",
    "priority": "1",
    "headers": "",
    "post_data": "",
    "status": "in_process",
    "delay": "5",
    "shot_interval": "5",
    "size": "screen",
    "target": "",
    "anchor": "",
    "html": "",
    "script_inline": "",
    "url": "https://www.ministryoftesting.com/",
    "id": .....,
    "referer": "",
    "max_wait": "",
    "cost": 1,
    "instance_id": "1",
    "script": "",
    "shots": 1,
    "final_urls": [
        "https://www.ministryoftesting.com/"
    ],
    "cookie": "",
    "details": "2",
    "hide_popups": "",
    "flash_delay": "10",
    "scale": 1,
    "shared_url": ""
}
```
What does it mean?!?  Nothing to be concerned about at this point.  The request was successful!  Now, onto checking out where my browshot is at.

There is a */screenshot/info* endpoint that may give us some status information for this screenshot.  Here goes nothing.  There's an example here as well and looks formed to what I need, so I create a second **GET** request in Postman using my **id** (redacted so you don't steal my stuff..LOL) from the JSON above and my **key** (API key).  That worked!  I got the reply back, but hmmm....still "in_process" after a couple hours.  I can't complain about a free service, but I know I had well-formed Postman requests both times.  I will dig around their API and see what went wrong, if anything, or if there is another endpoint I can hit to find more information.

The response JSON from */screenshot/info*:
``` JSON
{
    "priority": "1",
    "shot_interval": "5",
    "target": "",
    "anchor": "",
    "script_inline": "",
    "url": "https://www.ministryoftesting.com/",
    "id": .....,
    "screenshot_url": "",
    "max_wait": "",
    "cost": 1,
    "shots": 1,
    "final_urls": [
        "https://www.ministryoftesting.com/"
    ],
    "cookie": "",
    "details": 2,
    "flash_delay": "10",
    "scale": 1,
    "steps": "",
    "width": "",
    "headers": "",
    "post_data": "",
    "status": "in_process",
    "delay": "5",
    "size": "screen",
    "html": 0,
    "0": "",
    "referer": "",
    "script": "",
    "instance_id": "1",
    "time_added": "....",
    "height": "",
    "final_url": "https://www.ministryoftesting.com/",
    "shared_url": ""
}
```

Hey, let's try to get a thumbnail image (PNG) of the screenshot I requested.  I created another **GET** request to the */screenshot/thumbnail* using their example.  This one wants my screenshot **id**, **key**, and **zoom** percentage in the query parameters.  Hit send request and....uh oh!....I have no image.  Again, props to this free API.  It got close but not close enough.

![](/assets/images/browshot-image-not-found-404.png)

I'll try another cool API I can find on **Any-Api.com** for Day 2 and hopefully get better results.  Maybe I'll even ask the developer of Browshot API if they can help with what, if anything, I did wrong.  *Edit March 15, 2021:  I reached out to the developer and am awaiting a response.*