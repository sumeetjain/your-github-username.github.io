---
title: String Segmenter Project -- First Pass
---

Our solution was devised as a group.  We decided that since our problems seemed to stem from the code we were writing biting off too early on words that had suffixes.  So, to sort of sidestep this issue, we start our search at the end of the word vs the beginning of the word.  That way the code would only see that it had a valid word when it got to the first letter of the word.  Somewhat to our surprise, when we coded it this way, it passed all the tests.  After thinking about it overnight, we may have just traded our original suffix problem for a prefix problem.  The reason that this didn't trip any of our tests just boils down to how we were thinking when we drafted our tests.  Specifically, the tests were written to trip up a search if the word had a suffix.  So, our method deals with that rather well.  It's not really a surprise that it'd pass when viewed in light of that.  Still, this is not to undercut the value of the solution in hand, just to say that it needs to be made better.

require 'dictionary' #This calls in the dictionary and attendant messages so that we can make use of it in the following code.

def segment_string(str)
  i = 0 #Sets our count variable for the while loop.
  index = -1 #This sets the variable we're using to anchor our word search.
  cut = 1 #This variable gradually increases to test strings against the dictionary.
  arr = [] #This creates an empty array that we'll be filling with the words we find.
  
  if valid_word?(str) #String is a word.
    arr << str #Adds the str to the empty array we created.
  
  else # More complex cases.
    while i < str.length #This begins the loop.
      test_word = str[index, cut] #This creates the variable we'll be passing into our valid word test to see if the string we've cut off is a word.
      
      if valid_word?(test_word) #If the test word is a valid word. Do this.
        arr << test_word #Add test word to array.
        index -= 1 #Move our anchor left from the first/last letter of the found word.
        cut = 1 #Reset the number of letters we're cutting off.
        i += 1 #Advance the loop count by 1.
      
      else #If our test word isn't a word. Do this.
        index -= 1 #Move the anchor to the left.
        cut += 1 #Cut off one more letter.
        i += 1 #Advance the loop count by 1.
      
      end #Ends the if/else.
    end #Ends the while loop.
  end #ends the if/else.
  arr.reverse #Since our word search starts at the end of the string, it's actually populating our array in reverse order, so this puts it in the right order, or the order you'd encounter them moving from left to right.
end #Ends defining the method "segment_string(str)"
puts segment_string("onetwothree") #Calls the method we just defined and passes an argument into it.