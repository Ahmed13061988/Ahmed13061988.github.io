---
layout: post
title:      "												My first CLI project "
date:       2020-02-16 00:37:11 +0000
permalink:  my_first_cli_project
---

																																																
Well , that was my first project and I think this is the most defficult thing I ever done in my life , but it was so interesting to do it , and the first time in my life I did enjoy doing this Project .
					
My project was about the ski area in Colorado state , 32 ski area and an info about each area.
When I start to write my code a got some trouble to get my environment works good . 
					
After I did my envirorment works just fine , I started to think (How should my interface looks like ?) , this is the most important thing in my project , because I need to create a good interface to my app. , that the user could use it without any trouble and I want it to be clear , that can anybody understand it .
  
After get my environment works , I start build my interface .
My first method in my Ski:CLI class was greeting, this method responsible to run my greeting and menu methods . 
This method call on my scrape methods thta's I did in Ski class , in this case the data that we scrapped will be load at the moment when we runnig the app . When we run the app , the first thing the program is going to ask to type your name , with gets method and capitalized method this is not a problem.

My biggest fears was the scrape method , that method resposible of scrapping the real data from a real web page !! 
Not an easy thing to find a good website to scrape the info from it . I used this one https://www.uncovercolorado.com/ski-resorts-in-colorado/ . For my project this webiste is the best .

So when the user puts his name , the program will ask from the user to type "list" or "exit". 

If he chose to type "list" then the program will list all 32 ski area we have in Colorado , and then the user should choose one ski area from the 32 areas . 
The scrape method I did , its just one method who scrape the whole page and then is going to iterate on the array that we created by scraping the whole page .


        doc= Nokogiri::HTML(open("https://www.uncovercolorado.com/ski-resorts-in-colorado/"))  
			 
I used the require (Nokogiri) and require (open-uri) in order to able use those instruments of ruby .

By creating a new object doc , I pushed the https inside it . 

    section = doc.css("div.entry-content")
      section.each do |s|
			   headers = s.css("h2")
         info = s.css("ul")
            headers.each_with_index do |h, i|
                name = h.text
                stats = info[i].text 
          Ski.new(name, stats) 
					
The section object contain  the titles and the info about each area we have . In order to get the titles and the info separate , I iterate over the section array and then i created a new objects ( headers , info ). 

In this way I got the titles and the info separate , so the user now can call the titles and then choose one of them to get the info that related to this title.
  
    def list_ski
        Ski.all.each.with_index(1) do |ski, index|
          puts "#{index}. #{ski.name}"
        end 
          puts "\n Please enter the number of the ski area you want to get more info about:\n\n"
       list_info
    end 
		
In my cli class I have a list_ski method , the method responsible for calling list of the ski areas we scrapped from the website . But this conatin another method (list_info)

The list_info method is responsible to call the info to that area the user chosr to know more about it .


    def list_info 
      input = gets.to_i
      if input.between?(0,Ski.all.length)
        info = Ski.find_area(input)
          puts  "The area you choose is ---->
          ( #{info.name} )\n#{info.stats}"
      elsif input.between?(0,Ski.all.length) == false 
         puts "That's not a valid selection!Pleaase try again :)"
        list_info
      end 
        puts "\nDo you want to see another ski area ?\nType 'y' if yes or 'n' to exit ;)"
        input = nil 
        input = gets.strip.downcase
          if input == "y"
            puts list_ski
          elsif input == "n"
            farewell
            exit 
          else 
            puts "I'm not sure what you asking! Type exit to exit or again to show list"
            input = gets.strip.downcase
            if input == "exit"
              farewell
              exit
              else input == "again"
              list_ski
          end 
        end 
    end 
	
Inside this methode I have another class methode (find_area) method 

    def self.find_area(input)
      self.all[input-1]
    end
		
I was very excited about this project , it's was my first project . I had a lot of difficult build this code  , sometimes I didn't know what to do , and why I'm doing this ...  I used all the resources that Flatiron school gave us in order to finish my project in time , and it's not only finish it , I should finish this project and the final result should be the app I wanted to create , it's should work like I wanted to work . 

Try not be affried of coding , you will get stuck a lot of times , it's going to be difficult , but nothing is impossible . 

I hope you like my blog and it was useful . 
    


