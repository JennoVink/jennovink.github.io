---
layout: post
title:  "The Gary Vaynerchuk doesn't exists yet... Until now."
date:   2020-11-20 17:00:07
description: Gary Vee bot in google assistant: a proof of concept.
image: /img/gary-vee-search.jpg
published: true
tags: hobby-project Flask Python google-assistant
---

## The story behind the Gary Vaynerchuk and integrating it with google assistant

A few weeks ago I saw this video of Gary Veynerchuck:

<iframe src="https://www.linkedin.com/embed/feed/update/urn:li:ugcPost:6727570316899446784" height="665" width="504" frameborder="0" allowfullscreen="" title="Embedded post"></iframe>

I was a bit disappointed at the moment he said:
> GaryVee Bot doesn't exists yet...

In another (non published) hobby project, I created a google assistant skill which picks a random item from my todo list (weekmenu) and reads it to the used. Me and my girlfriends always like to plan all the evening meals on sunday for the whole week. Letting a smart home assistant decide what to eat, based on a list was quite fun to make.

Based on that I already had some experience creating simple google assistant skills, I saw this as a fun project to do.

### Quick demo

<iframe width="560" height="315" src="https://www.youtube.com/embed/D8NguLdD6d4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Techniques used

For this Proof-Of-Concept, I gained experience using:

* a micro-framework called [Flask](https://www.fullstackpython.com/flask.html)
* [ngrok](https://ngrok.com/) for exposing my local flask app to the outer world.
* fetching results from API calls using python

My POC works by simply extracting everything an user said after 'ask gary vee'. So in case of the video, this was 'how to get success in life?'. This value is used to make a call to this endpoint:
```
https://search.garyvaynerchuk.com/api/search?page=1&search_value=how%20to%20get%20success%20in%20life
```

Then the API results are fetched, and formatted into json:

```python
  return {"fulfillmentMessages": [
    {
      "card": {
        "title": responseTitle,
        "subtitle": responseSubtitle,
        "imageUri": imageUrl,
        "buttons": [
          {
            "text": "click here to watch",
            "postback": youtubeUrl
          }
        ]
      }
    }
```

And there it is. I think that for a POC, it works pretty well. The next steps would be hosting this python script in a cloud environment such as Azure, adding error handling and [publishing it to google](https://developers.google.com/assistant/console/publish)