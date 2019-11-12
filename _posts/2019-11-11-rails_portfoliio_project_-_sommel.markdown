---
layout: post
title:      "Rails Portfoliio Project - Sommel"
date:       2019-11-12 00:12:43 +0000
permalink:  rails_portfoliio_project_-_sommel
---


## Concept

Living in a city like Portland, its hard to have a boring glass of wine, we are minutes away from some of the best wine-country in the world and because of this Portland is having quite the "wine-boom".   I wanted to create an application that I could keep track of the wines that I was tasting and give them a simple rating for future-reference and friends.  

Sommel is a web-application to log your favorite wines, add reviews/tasting-notes and discover what bottle to check out next.

## Structure

Sommel has four models

* **User**:  has_many :tasting_notes  has_many :wines, through: :tasting_notes
* **TastingNote**: belongs_to :user, belongs_to :wine
* **Wine**: has_many :tasting_notes; belongs_to :producer; has_many :users, through: :tasting_notes
* **Producer**: has_many :wines


## Early Struggles

Sommel was not my first go at this rails portfolio project, in fact it was my third time restarting from scratch.  Through this project I really discovered the importance of having well defined models and associations. Early on my models and associations were either too complex or not well-defined, this led me to trying to bridge gaps that didn't exist or utterly complex code with associations being missed


## What I Learned

Use the tools you have:  byebug and the rails console are great tools to debug and find out what is going on behind all that rails 'magic'. A common problem I was running into were objects weren't saving  on creation, after inspecting params and running .save! in the console,  I discovered that some of my model objects were dependent on the creation of others in order to be saved.

Authentication and validations are so important, protect your forms against unwanted data and don't allow your user to move freely through your application via the 'url'. For example, if a user were to input an index for a wine that doesn't exist a simple helper method like this: 

`def set_wine
    @wine = Wine.find_by(id: params[:id])
    redirect_to wines_path if !@wine
  end`
	
Will redirect the user to the wines index view if the wine is not found and not throw a rails error.  Our goal as developers is  to guide and direct the user to pages we want them to have access to.

##  Scope Methods

Scope methods are a great way to grab the right objects out of your database, I wanted to provide a way for the user to not just view all the wines in the database but have an option to view just wines that have tasting notes.

```
app/model/wine.rb

scope :rated, -> { joins(:tasting_notes).distinct}
```

It would be implemented like so:
```
/app/controllers/wines_controller.rb

def index
  @wine = Wine.all
end

def rated
#accessing all wines that have a tasting-note
  @wine = Wine.rated
end
```

## What I Would Do Next
* Add a wine api to have a bigger database and include more attributes 
* Add average rating to list highest rated wines in order of popularity
* Add sign-up capabliity with omniauth
* Add capability to link producer to the producers website
* Write a blog post on the miseries of using bootstrap in erb files
	
