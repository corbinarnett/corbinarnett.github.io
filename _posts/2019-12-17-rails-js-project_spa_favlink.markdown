---
layout: post
title:      "Rails-JS-Project SPA: Favlink"
date:       2019-12-17 07:56:03 +0000
permalink:  rails-js-project_spa_favlink
---


## Concept
One of my favorite extensions on chrome is [Pocket](https://app.getpocket.com/), a place where your can save and store direct links to web pages and articles.  My goal for the project was to build a simplified version, a single-page-application that stores a link to a rails-api by category, the ability for a user to visit that link directly from the app, as well as delete the saved link from the database.

## Structure
Favlink is using a Rails-API with a simple vanilla-javascript interface, the API itself has two class models, which are a List and a Website, which correlate in a simple, has-many/belongs-to association. Think of each list as a category a user can save a website to, like saving a link to a recipe you would like to try to a Recipe List.  After saving this website to the database the user has the ability to visit that URL directly or delete the saved website.

The data is structured through the fast_jsonapi gem by Netflix, this gem was my saving-grace in this build of the app, it allowed me to choose specific attributes to display for each class model, as well as display their relationships in a hash that was much easier to traverse when working with the front-end.

### Before the serializer my data looked as follows:
```
{
    "id": 1,
    "title": "I Make the Best Amaretto Sour in The World",
    "link": "https://www.jeffreymorgenthaler.com/i-make-the-best-amaretto-sour-in-the-world/",
    "list_id": 2
  }
```

This code above didn't allow me to easily access the data for the websites correlating list, this caused many problems when trying to implement a simple dropdown menu in my interface, allowing a user to save a website to a specific list, rendering that List title.

### Using fast_jsonapi
Using the serializer class provided by the gem I was able to use this code:
```
class WebsiteSerializer
  include FastJsonapi::ObjectSerializer
  attributes :title, :link, :list
  # belongs_to :list

  private
  def lists
      ListSerializer.new(object.lists).attributes
  end
end
```

To manipulate the data hash to as follows:
```
{
  "data": [
    {
      "id": "1",
      "type": "website",
      "attributes": {
        "title": "I Make the Best Amaretto Sour in The World",
        "link": "https://www.jeffreymorgenthaler.com/i-make-the-best-amaretto-sour-in-the-world/",
        "list": {
          "id": 2,
          "title": "Cocktails"
        }
      }
    }, ...]
```
Providing an array of data hashes that displayed attributes to the List that the website belonged to.  



### What I would like to add in future versions
* A login and signup page for unique users
* The option to create a new list, *at the moment you can only select from a pre-rendered list of categories.*
* To sort the saved websites by the List they belong-to, or by the time they were added

### Key Take-a-ways

This project was great experience for learning how to communicate with an API as well as getting more practice with manipulating the DOM via Javascript. It also showed me my strength and weaknesses as a developer and helped me pinpoint what I need to focus more on when it comes to mastering Javascript.  Next up... React!


[Favlink](https://github.com/corbinarnett/favlink-rails-js)






