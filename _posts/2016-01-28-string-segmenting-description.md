---
title: String Segmentation Description
---

#Below is a description I tried to write during our first week of Code School regarding the String Segmentation Program we had been working on since day two.

I was thinking about re-writing the whole thing, but I think I'll leave it like this because it'll be nice to see how my explanations and understanding of this stuff deepends and expands as I go through this class. I have a feeling I'll look back on this description and say to myself "Yeah... but I didn't *really* know what I was doing." Heh.

##Description of String Segmenting Program:

def segment_string(str)
  i = 0 #Sets our count variable for while loop
  index = -1
  cut = 1 
  arr = []

-------------------

##Defining variables:

Initially, there a few variables/counters that we needed to
assign an initial value.

The first is the "i" variable (typical when using loops), which we have set at
0. This is so that we can begin our "while" loop at the very 
beginning.

The next variable we set was "index". WE set this to -1 as the approach we ultimately decided to take was to start at the end of our string. Using -1 allows us to do this.

Lastly, we begin with an empty array. This is the array into which
our final output will be stored (hopefully an array full of "real" words as found in our dictionary AND leaving no characters or words out from the first string)

-------------------

  if valid_word?(str) 
    arr << str

-------------------

##Simple Scenario

This if statement is for the absolute simplest scenario. 
It calls the valid_word?() method as defined in our dictionary method - which essentially looks at an array of words and returns true or false depending on whether or not the word is contained in the dictionary.

The simpliest scenario is where the string that is passed through our method is a string that is simply one word. In this case, no parsing needs to occur in our string and we can run it, as is, through our valid_word checker and we'll should get the string returned into our final array.

--------------------

else #For complex scenarios

    while i < str.length 

      test_word = str[index, cut] #This creates the variable we'll be passing into our valid word test.
      #puts "test word is #{test_word}"

---------------------

##Complex Scenarios

Above we have our code to anticipate the more complicated scenarios.

###The While loop
Here is the loop upon which all of the rest of the code hangs. This allows us to iterate through our entire array (in our case we chose to go backwards).

What's happening in the while loop is that we are asking the loop to do the following code while "i" is less than the length of the string. We do this so that the loop eventually stops once it has iterated through the length of the string.

Next, we have the code that we'd like the loop to perform: namely, that we'd like it to take the index (initially set at -1, the end of the string), and take the letter at the index and cut off the number of letters that has been previously set at 1. So essentially we're taking one character at a time here until the loop passes in a valid dictionary word through the valid_word? method. Which happens next.

---------------------


      if valid_word?(test_word) #If the test word is valid do the following
        #puts "#{test_word} is a valid word! Adding it to arr"

        arr << test_word #Adds test_word to final array if it passed test
        #puts "array is #{arr}. Incrementing values"

        index -= 1 #Moves anchor to the left by one
        #puts "index is now #{index}"
        cut = 1 #Resets the number of letters to cut off
        i += 1 # Advances loop count by 1
        #puts "i is now #{i}"


---------------------


#If Statement:

Here our if statement simply passes in each portion of the string that the loop has given it at whichever point it is in the loop. 

What we're doing is saying *IF* what we have so far is in the dictionary, take this word and put it into our final array.

The next portion simply resets our variables so that they continue to iterate through our string properly.

index moves one to the left (by the -1), cut is reset to 1 (so that we do not cut more letters than we need) and i increases by one so that we can continue our loop.

----------------------

      else
        #puts "test_word is not a word :-( Moving on..."
        index -= 1 #Moves anchor to the left by one
        #puts "index is now #{index}"
        cut += 1 #Cuts one additional character.
        #puts "cut is now #{cut}"
        i += 1 #Advances loop count by 1
        #puts "i is now #{i}"

  --------------------

#Else Statement:
Our else statement is telling our program what to do each time the portion of the string passed through it is NOT a valid word in the dictionary.
In these cases, the index continues to iterate through the array, from left to right. This is done by having the index decrease by 1 (-1), having the "cut" and "i" increase by one. 

The big difference here is that nothing is added to the array and the loop continues.

-----------------------

Below we have our basic endings to tell the program that each block of code needs to end, as follows:
      
      end #ends the if/else loop
    end #ends while loops
  end #end if/else
  arr.reverse #displays array in reverse in order to satisfy "left to right" order.
end #Ends defining the "segment_string(str)"

-----------------------

puts segment_string("onetwothree")

-----------------------
Above we call our segment_string() method that we just described. This tells the interpreter to go ahead and begin running the code in the method.
