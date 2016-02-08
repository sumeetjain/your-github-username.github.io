---
title: Description of my String Segmentation Program
---


> collect = []
> wordHash = {}

The first things I do are create an array (collect) and a hash (wordHash) to store words and letters during the process.

>i = 0
>skip_counter = 0

Here I set i (the iterator) and my skip counter to 0.

>str = str.split('')

This splits the input string into an array of letters, with one letter in each element.

>while i < (str.length) do

A conditional statement to make sure the loop only runs as many times as letters there are in the string.

>collect.push(str[i])
>word = collect.join('')

These move the letter one-by-one into the array, and then each time turn the array into a string (in order to check each string against the dictionary.)

>if valid_word?(word) == true

If the dictionary finds a word match, the loop moves into this if statement.

>if skip_counter == 1
>i += 1
>skip_counter = 0

Another if statement, for if the skip counter has already been set: It will add 1 to the iterator to begin again at the start, and will reset the skip counter to 0.

>else

If the skip counter is not set

>wordHash[word] = i
>collect = []
>i += 1
>end

Sends the just-found word to the wordHash, resets the collection array to nil, and adds 1 to the iterator to start the loop anew.

>else

if the dictionary hasn't found a word match after that specific letter

>i += 1
adds 1 to the iterator to begin the loop again (but doesn't clear out collection array)

>if i >= str.length
>collect = []
>skip_counter = 1

If a word hasn't been found and the iterator has reached the end of the string, the collection array is cleared, and the skip counter is set to 1.

>finalWord = wordHash.max_by { |k, v| v }
>finalWordKey = finalWord[0]
>wordHash.delete(finalWordKey)

Here, we find out the most recent word added to the wordHash by taking the key of that hash. That word is then removed from the hash.

>if wordHash.max_by { |k,v| v } == nil
>startHereValue = 0

This bit of code tells the program where to restart if there is no longer anything left in the hash.

>else

If there is already another word previously stored in the hash...

>startHere = wordHash.max_by { |k,v| v }
>startHereValue = startHere[1] + 1
>end
>i = startHereValue

This block resets the iterator to one number past the final letter in the final word in the wordHash.

>end
>end
>end
>return final_hash_to_string(wordHash)
>end


>def final_hash_to_string(wordHash)
>finalArray = wordHash.keys
>return finalArray
>end

This method returns the final array by converting wordHash's keys to an array after the loop has totally finished.