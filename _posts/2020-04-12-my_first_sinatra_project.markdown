---
layout: post
title:      "My first Sinatra project "
date:       2020-04-12 17:48:52 +0000
permalink:  my_first_sinatra_project
---


I'm so glad that I finished my first Sinatra project. The felling after I can run my application and it's doing everything, I asked from it like I want, that is the best. 

The idea of my Sinatra project is: A user (In my case a "Gamer") can Sign Up in my application, and able to create a game, give it name, publisher and rate. Also, he can edit this game or delete it. He can also view the other gamers and see what games they have, but he can just view the games not able to do anything with them. 

The main problem I faced when I 'm doing this project was (Where should I start?) that thing took from me a whole day just to think about. What should I do first? 

So, first thing was creating an idea for my project, after that I start to think about how is my database should look like, and how many tables I should have to make my app works. 

After I made my database, I was looking to do all the requirements that they ask from us. 

The CRUD is (Create, Read, Update and Delete), so I should be able to do all the CRUD operation in my app. 

First thing I created a gamer, by using sign up post in my Gamer controller. 

I gave every user a password by using has_secure_password in Gamer model and bcrypt in the Gimfile. 

```
class Gamer < ActiveRecord::Base 
    has_many :games 
    has_secure_password 
end 
``` 

I gave the user a session by enable it in my ApplicationController a sit the session secret. 

```
configure do
    set :public_folder, 'public'
    set :views, 'app/views'
    enable :sessions 
    set :session_secret, "secret"
    use Rack::Flash 

  end
```

Then I got my helper which contain two methods: 

```
 helpers do 
    def current_gamer
     @gamer ||= Gamer.find(session[:gamer_id])
     end 
   end 


   def logged_in? 
    !!session[:gamer_id]
   end
```

These two methods will help to know the current_gamer and if he logged in. 

My user can delete his profile, I did that by using the delete in GamerController: 

```
 delete '/gamers/:id/delete' do #delete action
         @gamer = Gamer.find_by_id(params[:id])
        session.clear 
        @gamer.delete
        redirect to '/'
    end

```

Then I got the patch and delete in my app, in order to delete or edit a game: 

```
  patch'/games/:id' do 
        if (params[:name]).empty? ||(params[:publisher]).empty?
            flash[:field_error] = "No change, Please all fields are required! "
         redirect '/games'
        end 
      @game = Game.find(params[:id])
        @game.update(name: params[:name], publisher: params[:publisher], rate: params[:rate]) 
        @game.save
        redirect to "/games"
    end 

    delete '/games/:id/delete' do 
        if !logged_in?
            redirect to '/login'
        end 
        @game = Game.find(params[:id])
            @game.delete 
            redirect to '/games'
    end 
```

In this way my user can create, view, edit and delete a game he wants to. All the CRUD is done. 

I enjoyed working on this project, to see your application working and do what you want from it, that is what we learning to do. Thank you. 


   
