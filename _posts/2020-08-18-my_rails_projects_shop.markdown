---
layout: post
title:      "                   My rails projects "Shop""
date:       2020-08-18 21:46:50 +0000
permalink:  my_rails_projects_shop
---

**Ruby on Rails: Rails is a development framework which gives web developers a structural framework for all the code they write. The Rails framework assist programmers to build websites and apps by abstracting and simplifying most of the repetitive tasks.**


The key role of Ruby on Rails development is convention over configuration. This helps the programmer doesn’t have to spend a lot of time in configuring files in order to set up, Rails comes with a set of conventions which helps to speed up the development process.

The most important thing I needed to know to start my project, is what about the app will be.  

First, I needed to know how many models I will have in my app, and the associations among the models I will have.  

The associations among the models is very important, because all your code in the app will depend on all this associations.  

I have four models in my app: 

User, Shop, Review, Category.  

It was very hard for me to do all the associations in the right way, my User model looks like that:  

```
has_many :reviews 

has_many :reviewed_shops, through: :reviews, source: :shop  

has_many :shops 
```

So, as we can see the User has many reviews, and `has many reviewed_shops t`hrough the reviews and has many shops. In this case that will allow me to have all these methods: 

`@user.reviews, @user.reviewed_shops and @user.shops . `

All these methods will make my life and my code easier for me.  

And my Shop model has these associations: 

```
  belongs_to :user 

  belongs_to :category    

  has_many :reviews, dependent: :destroy  

  has_many :users, through: :reviews 
```

  

We can see here that the shop is belongs to a user, this one will give @shop.user (not users).  

I found a difficult to make my app works, the main idea of the app that, any user can sign up and add a new shop with its own category and price range. And the user can use his Gmail to sign in to the app.  

The user can edit or delete the shop that he created earlier. 

The user can also add a review to the others shop that been add by other users.  

Using the bycript and has_secure_password, gives me a very strong defense against any attempt of hack the app.  

In order to sign in with the g-mail account, I needed to use the omniauth, in my case this will be without a device.  

So, in my sessions controller I add this method  

```
def google_omniauth_create 

			omniauth = request.env['omniauth.auth']['info'] 

			@user = User.find_or_create_by(email: omniauth['email']) do |u| 

			u.username = omniauth["name"] 

			u.password = SecureRandom.hex 

			end  

			session[:user_id] = @user.id 

			redirect_to user_path(@user) 

End 
```

 

 

With this method we can retrieve the user info from his google account and use it for the app as a user.  

What I learned:
 > Ruby on Rails is one of these technologies that are mature enough to get rid of teething problems yet modern enough to be compatible with the newest trends. 

This is most hard thing I did since I don’t remember, coding make your brain work 100% every step I did in my code there is a new error, dealing with those errors made my code skill way better, trying to resolve the problem, googling the error and reading a lot of articles about this specifics errors I found out that every error has to many ways to resolve. I have learned not to give up after every fail there will be a success, I need to remain calm and focusing and never lose the ability to think clearly in my code.  

 

 

 

 

 
	
