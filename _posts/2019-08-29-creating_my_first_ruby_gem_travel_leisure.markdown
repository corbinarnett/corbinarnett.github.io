---
layout: post
title:      "Creating my first Ruby Gem: travel_leisure"
date:       2019-08-30 03:01:22 +0000
permalink:  creating_my_first_ruby_gem_travel_leisure
---


For my first portfolio project assigned in Flatiron School Software Engineer program, I was assigned with building a CLI application that scrapped data from an outside source, an API or website. After searching for websites to scrape I finally landed on scrapping the travel guides from [Travel & Leisure](http://www.travelandleisure.com/travel-guide).

# Getting Started
I think one of the scariest parts of programming for anyone is starting off with a blank slate. I spent the first day or two alone just figuring out how to structure my application, which classes should be built, and what the heck is a gem-spec anyway ;) 
The hardest part for me was not only scraping the destinations of the travel guides but going another level deeper and scraping the data from each destinations correlating url.
	 
# Progress
I created three files for my application. **Scraper.rb**, which scrapped each destination and then created instances of each destination using its relationship with: **Destination.rb**; this class assigned attributes to each destination based on the data scrapped like the city, country, it's unique url, best time to visit, etc. And finally **ClI.rb** which contained all the logic needed to display and run my application to the user.

# Completion
One week later my gem is ready to use, check it out yourself!

You can install the travel_leisure gem by typing the following prompt in terminal:

```
gem install travel_leisure
```

and then run the following:

```
travel_leisure
```


Here is the walkthrough of my gem:

https://youtu.be/b91gAe7wIeE


Enjoy!


