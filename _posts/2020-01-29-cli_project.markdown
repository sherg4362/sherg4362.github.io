---
layout: post
title:      "'cli project'"
date:       2020-01-29 06:14:00 +0000
permalink:  cli_project
---


My first flatiron project is to  build a CLI gem.  The requirements for this project are to scrape data from a website using Nokogiri  and that the data be at least one level deep.


Once I understood the requirements of the project I began thinking about what problem I could solve.  As I thought about the project more and more I realized that I want to do something which I can share with my son.  It is with my family’s support that I will be successful.  I then decided on a site that my son would be interested seeing in this project.  Currently he is a fan of the teen titans.  I thought that would be a great starting place.  I began my search for a teen titans website that would meet the requirements of my CLI project.  I found the DC Universe website which has a section two sections about the teen titans.  One section is about the animated series and the other section about the real.  I was really excited about finding two possible areas to scrape for data.  Unfortunately I discovered that the website uses angular for different sections to render the webpage.  I was disappointed my thoughts about being able to share this project with my son were dashed.


After checking other sections of the site, I did find a section that would work.  It met the requirements of the project and did not use angular to render the page.  This section lists the main DC Universe characters.  I decided to use this section as the focus of my project.


In this way I would have my first level being the interface for my CLI then the second level would be getting further information about each of these characters.  After using Nokogiri to make get some initial data.  I found that scrape the character pages would require a method for each character.  This is because the attributes for each  character may be in the left column or the right column.  In the scrapers for the character data some information is on either the left or the right column.  The character methods call an other methods for either the left or right column.


1.  gets page data
```
class CharacterFactsScraper
    def self.get_character_page(selection)
      character_name = Character.characters[selection].name
      character_page_url = Character.characters[selection].url
      # BASEURL + character_page_url
      html = Nokogiri::HTML(open(BASEURL + character_page_url))
      #puts "This is hero name: #{character_name}"
```

This section of the CharacterFactsScraper gets the html for the character.  This data is then passed to the left and right column methods for that particular html page.

2.  splits that data into either left column or the right column
```
# GET lEFT COLUMN OF CHARACTER PAGE
    		def self.left_column(html)
      		# LEFT COLUMN
      			left_column = html.css("div.left-col")
      			left_column
    		end
    	# GET RIGHT COLUMN OF CHARACTER PAGE
    		def self.right_column(html)
      		# Right COLUMN
      			right_column = html.css("div.right-col")
      			right_column
    		end
```

The character methods then use the column information to get the data attributes for each character. 
This was a tricky part because most of it had to be hard coded because there was not a standard order to the html for the page for each character.

I did learn more about classes and calling methods.

You can view my Github repo code [here](https://github.com/sherg4362/dc_characters)

