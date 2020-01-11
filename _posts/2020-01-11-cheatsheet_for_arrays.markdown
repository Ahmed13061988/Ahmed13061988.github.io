---
layout: post
title:      "                                cheatsheet for arrays "
date:       2020-01-11 06:29:41 +0000
permalink:  cheatsheet_for_arrays
---




The keys in array is very important , they make our work easy ... as we know that we are so lazy and we will use any shortcat available to do our code more understandable.
So here I chooce the more use keys in array that's going to help us to write our code.
I will give an example for an array :
array = ["Johnny Cash" , "Bruno Mars" , "Justin Timberlake"]
Our key words :

-*Length*=> this key is going to give us the length of our array , in our example the result is => 3 .

-*Split*=>will split a string into an array. It takes an argument of a string to decide where to split the array items, otherwise it splits by space.Like in the example bellow :
```
array = "This is a string".split 
=>["This" ,"is" , "a" ,"string"].```

-*Index*=> one of the important keys we have when we dealing with arrays , we can get the value of variable inside the array by using the index of that variable . Like in the example 
```
array = ["Johnny Cash" , "Bruno Marc" , "Justin Timberlake"]

array[0]=> "Johnny Cash"

array[1]=>"Bruno Mars"

array[2]=>"Justin Timberlake"
```

-*Include?*=> with this key , we can test if we have the variable inside our array , the result will be true or false 

```
array.include?("Bruno Mars")=> true 
array.include?("Ray")=>false
```

-*Shovel operatoror <<* with this key we can add a value to the end of the array 

```
array<< "Tito"
=>
 array =  ["Johnny Cash" , "Bruno Mars" , "Justin Timberlake", "Tito"]
 ```

-*unshift* we can use this key to add a value to the star of the array 

```
array.unshift ("Adele")
=>
array=["Adele", "Johnny Cash" , "Bruno Mars" , "Justin Timberlake"]
```

-*Delete* With this key we can delte a value from our array 

```
array.delete("Johnny Cash")

=> 

array=["Bruno Mars" , "Justin Timberlake"]
``` 

-*Each* we can iterate through the array with this key 
```
array.each do |val|
puts "The value is #{val}"
end 
```



