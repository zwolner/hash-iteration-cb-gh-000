# Iterating Over Hashes

## Objectives

1. Use lower level iterators like `.each` on a hash.

## Iterating Over Hashes

Previously, we've compared hashes to dictionaries or storage containers. Just like with these storage methods in real life, not only do we need to access our stored information, but then to utilize it in some way.

The `.each` and `.collect` iterators that we encountered in previous units can also be used to iterate over hashes. However, when we iterate over arrays, we iterate over one element at a time: each index in an array contains just one object. In a hash, data is stored in key/value pairs, so we will be iterating over those *pairs*. Let's take a look: 

```ruby
hash = {key1: "value1", key2: "value2"}

hash.each do |key, value|
  puts "#{key}, #{value}"
end
```

When we iterate over a hash, the `.each` method yields the key/value pair *together* into the block. Inside that block, you have access to the key *and* the value and can manipulate either one or both. 

Drop into IRB and enter in the above code. You should see this output: 

```ruby
key1, value1
key2, value2
 => {:key1=>"value1", :key2=>"value2"} 
```

Inside the iteration, we have access to and can `puts` out the key and value of a single pair. Then, the return value is the original hash. **Remember that `.each` returns the original collection on which you are calling the method.**

Let's take a look at one more example of iteration and manipulation before you try it on your own:

## Example: Cruise Ship 

The good news is you're on a cruise ship! The bad news is that you're *not* on vacation. You are a cruise ship director and you're selecting the day's lucky winner of free tickets to the 8:00pm magic show in the super swanky *Blue Room*. The criteria for picking the winner is that this person must be staying in Suite A and their name must start with the letter "A". We have a hash of passengers that looks like this: 

```ruby
passengers = {
suite_a: "Amanda Presley", 
suite_b: "Seymour Hoffman", 
suite_c: "Alfred Tennyson", 
suite_d: "Charlie Chaplin", 
suite_e: "Crumpet the Elf"
}
```

We need to iterate over that hash and collect the name of the passenger who is staying in Suite A *and* whose name begins with the letter "A". Let's give it a shot: 

```ruby
winner = ""
passengers.each do |suite, name|
  if suite == :suite_a && name.start_with?("A")
    winner = name
  end
end

winner  
```
Let's break this down: 

* We iterate through the hash using `.each`. We chose `.each` instead of collect because we don't want to collect the key/value pair that contains the winner, just the *name* of the winner. With `.each`, we have the control we need to simply grab the winner's name and set it equal to a variable that we can return later on. 
* Inside our iteration, we use an `if` statement combined with the `&&` ("and") boolean operator to check if we have the right suite and if the person in that suite has a name that begins with the letter "A". 
* If that condition returns true, we've found our winner! We set their name equal to the `winner` variable and end our iteration. 
* Then, we call on our `winner` variable to return the name of the lucky winner. 

This is just one example of how iterating over hashes allows us to access and manipulate the values that they contain. Now, you can try it out by completing the lab in the next lesson. 
