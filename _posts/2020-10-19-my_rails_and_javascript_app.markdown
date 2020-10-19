---
layout: post
title:      "My Rails and JavaScript app "
date:       2020-10-19 19:35:45 +0000
permalink:  my_rails_and_javascript_app
---

*   By learning JavaScript, I realized JS is weird and fun! JavaScript sometimes not giving any errors, while Ruby will give
	a whole page of errors if you miss one of the arguments. 
	
	By understanding the DOM monipulation and how I can edit on my HTML collection, the thing become easier to me. One 
	
	of the most important thing in JavaScript is how I can work with arrays, objects and function. The function will do the 
	
	same job that method did in Ruby. 
	
```
	function () {
	
	}
```

   This is an example of function in JavaScript. 

   The class in JavaScript is simillar to the class in Ruby all about OOP. Using class made the coding easier and more DRY.

This is an example of a class in my code *

```
class Game {
    constructor(gameAttributes) {
        this.title = gameAttributes.title;
        this.price = gameAttributes.price;
        this.category = gameAttributes.category;
        this.description = gameAttributes.description;
        this.link = gameAttributes.link;
        this.image = gameAttributes.image;
        this.id = gameAttributes.id;
    }

    render() {
        return `<div class="card">
                  <h2>${this.title} ($${this.price})</h2>
                  <h4 class="game-cat">${this.category}</h4> 
                  <a href=${this.link} target="_blank"><img src=${this.image} class="game-image" /></a>
                  <p>${this.description}<p>
                  <button data-game-id=${this.id} class="like-btn">♡</button>
                </div>`
    }
}
	
```

The fetch in JavaScript is very important to know how it is work. JS has two kind of fetch ( get and post), fetch will bring 

data from the database to the DOM and post any changes the user will do with the informations. 


```
function fetchGames(){
    fetch(GAMES_URL)
    .then(res => res.json())
    .then(games => putGamesOnDom(games))
}
```

This is an example of fetch (get). 

```
gameCollection.addEventListener('click', function(e){
    // console.log(event.target.className, event.target.style.color)
    // e.preventDefault() was preventing images from being clickable
    if ((e.target.className == "like-btn") && (e.target.style.color !== 'red')) {
        let target = e.target
            fetch(FAVORITES_URL, {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                    Accept: "application/json"
                },
                body: JSON.stringify({
                        user_id: `${currentUser.id}`,
                        game_id: `${e.target.dataset.gameId}`
                })
        })
        .then( res => res.json())
        .then( res => target.dataset.favId = res.id);
        e.target.style.color = 'red';}
    else if ((e.target.className == "like-btn") && (e.target.style.color == 'red')) {
        e.target.style.color = 'black';
        fetch(FAVORITES_URL + '/' + e.target.dataset.favId, {
            method: "DELETE"
        })
    }
})
```

This is an example of fetch with post method. 

The CSS was the most fun thing in this project, it's a design work. This is how your app will looks, we need it clean 

and clear. 

Conclusion 

This project is the most fun project I ever did. However, working out the correct syntax and code in some of the 

functions did set me back a few hours, days and even weeks.  I am looking forward to learn REACT and have more 

tools to solve more problems. 





	 





				

