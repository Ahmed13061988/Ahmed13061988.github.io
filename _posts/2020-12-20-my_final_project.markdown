---
layout: post
title:      "                      My Final Project "
date:       2020-12-20 21:01:01 +0000
permalink:  my_final_project
---


This is my final project with Flatiron, I'm so happy that knowing I have come this far, it's was not easy but fun. My project e- commerce website, where you can Signup and Login, browsing the shop you can choose any item you want and add it to the cart, the user can check the items he chose in the cart, and place the order. when the user place the order, the cart automatically will be destroyed and creating a new cart for him. The user after that can check the items, he ordered in the Orders page. 

Using rails API I built the backend part of it. I created users_items, cartitems, and session model that allows me to add a new user with create method, the user has_secure_password, that mean I use the bcrypt gem in the Gemfile, so the user's password will be safe. 

The biggest difficulty I have found is with the frontend. Using react and redux gave me the ability to store my state in the redux store, which made my work easier. 

I used create_react_app to create my app in the frontend. I needed to install all things I need to make this work. I installed 
		 
	 ``` 
	 npm isntall 
	 npm install react-redux
	 npm install redux 
	 npm install thunk 
	 npm install ract-router-dom
		```
		
Installing all these node- packages gives me the ability to have (thunk, redux, routes) installed and use it.  

The frontend has (Components, Actions, Containers and Reducers).  

  

The two things I worried about it is the state and the rendering, for example in my cart I needed to render all items in the cart, the items that the user clicked add to the cart, the code is : 
```
import React from 'react';
import Item from './Item';

const Cart = (props) => {
   
    const buttonText = "Remove Item"
    const cartItems = props.cartItems.map((cartItem) => <Item item={cartItem} handleButtonClick={() => props.handleButtonClick(cartItem)} buttonText={buttonText} />)
    
    
    return (
        <div> 
            <h4>Shopping Cart</h4>
             {cartItems}
            <button onClick={props.submitOrder}>Place Order</button>
        </div>
    )
}

export default Cart;
```

This code is rendering my cart page, as you can see, I have cartItems variable that contain all my items that goes to the cart, iterate over all this items and rendering it in the Item component that I imported inside the cart component, then in the return inside my divs I just put all the cartItem's items, so the user can see it. I was in a big trouble to bring all the proper state and render it here.  

I needed to create a variable that is an empty array of cartId and cartItems, to push all the items to this array an assign the cart id with it. So i have a fetch request for that: 
```

export const addItemToCart = (item, cartId) => {
    return (dispatch) => {
        dispatch({type:'ADDING_TO_CART'})
        fetch('http://localhost:3000/carts', 
        {
          method: 'POST', 
          headers: {
              'Content-Type': 'application/json'
          },
          body: JSON.stringify({
           item: item,
           cart_id: cartId
          }),
        })
        .then(resp => resp.json())
        .then(res => {
            =
            localStorage.setItem("cart", JSON.stringify(res.cart))
            dispatch(updateCart(res))
        })
    }
```

As you can see, I took the item, and the cartId as an argument, and return the dispatch of the action that says"ADDING_TO_CART", then going to the end point of the backend in carts to grab the cart I need to add to it, in the body of the fetch I sent the items and cartId, save it all in local storage and then call the updateCart action to it to update the cart.  

I liked the idea of local storage and want to experiment with it and save all the data to it.  

  

The other thing that I got a lot of errors from it, was the delete the item from the cart. The idea was to delete just one item from the cart, when a user clicks a removeItem from the cart all the similar items (with similar id) was deleted automatically, like if I have three games of (God of War) and I wanted just to delete one of it, all other God of War games deleted, because the id was the same for this game. I tried to do in the backend the clone method, that takes the items make a duplicate to it and save it in a variable then give him a unique id then delete it, it's worked, but that was not the proper way to do it, using a lot of space and resource, so I decided to find another way to delete just one game, I found that way by this code: 
```
 current_cart = Cart.find(params[:cart_id])
        item =current_cart.cart_items.find_by(item_id: params["item"]["itemId"])
```
Find_by method will always bring me only the first id it will found, by this way I will be able to delete just one item, even though I have other items with the same id.  

  

The project I did is not the best in this kind of projects, I still have a lot to study and learn, but I'm so proud that I did all that and came so far with this. This is only the beginning and I'm sure the will a lot to learn and discover in the future. 

			 
			 
