---
title: Description of my String Segmentation Program
---

{% highlight ruby %}
> collect = []
> wordHash = {}
{% endhighlight %}

The first things I do are create an array (collect) and a hash (wordHash) to store words and letters during the process.

{% highlight ruby %}
>i = 0
>skip_counter = 0
{% endhighlight %}

Here I set i (the iterator) and my skip counter to 0.

{% highlight ruby %}
>str = str.split('')
{% endhighlight %}

This splits the input string into an array of letters, with one letter in each element.

{% highlight ruby %}
>while i < (str.length) do
{% endhighlight %}

A conditional statement to make sure the loop only runs as many times as letters there are in the string.

{% highlight ruby %}
>collect.push(str[i])
>word = collect.join('')
{% endhighlight %}

These move the letter one-by-one into the array, and then each time turn the array into a string (in order to check each string against the dictionary.)

{% highlight ruby %}
>if valid_word?(word) == true
{% endhighlight %}

If the dictionary finds a word match, the loop moves into this if statement.

{% highlight ruby %}
>if skip_counter == 1
>i += 1
>skip_counter = 0
{% endhighlight %}

Another if statement, for if the skip counter has already been set: It will add 1 to the iterator to begin again at the start, and will reset the skip counter to 0.

{% highlight ruby %}
>else
{% endhighlight %}

If the skip counter is not set

{% highlight ruby %}
>wordHash[word] = i
>collect = []
>i += 1
>end
{% endhighlight %}

Sends the just-found word to the wordHash, resets the collection array to nil, and adds 1 to the iterator to start the loop anew.

{% highlight ruby %}
>else
{% endhighlight %}

if the dictionary hasn't found a word match after that specific letter

{% highlight ruby %}
>i += 1
{% endhighlight %}

adds 1 to the iterator to begin the loop again (but doesn't clear out collection array)

{% highlight ruby %}
>if i >= str.length
>collect = []
>skip_counter = 1
{% endhighlight %}

If a word hasn't been found and the iterator has reached the end of the string, the collection array is cleared, and the skip counter is set to 1.

{% highlight ruby %}
>finalWord = wordHash.max_by { |k, v| v }
>finalWordKey = finalWord[0]
>wordHash.delete(finalWordKey)
{% endhighlight %}

Here, we find out the most recent word added to the wordHash by taking the key of that hash. That word is then removed from the hash.

{% highlight ruby %}
>if wordHash.max_by { |k,v| v } == nil
>startHereValue = 0
{% endhighlight %}

This bit of code tells the program where to restart if there is no longer anything left in the hash.

{% highlight ruby %}
>else
{% endhighlight %}

If there is already another word previously stored in the hash...

{% highlight ruby %}
>startHere = wordHash.max_by { |k,v| v }
>startHereValue = startHere[1] + 1
>end
>i = startHereValue
{% endhighlight %}

This block resets the iterator to one number past the final letter in the final word in the wordHash.

{% highlight ruby %}
>end
>end
>end
>return final_hash_to_string(wordHash)
>end
{% endhighlight %}

{% highlight ruby %}
>def final_hash_to_string(wordHash)
>finalArray = wordHash.keys
>return finalArray
>end
{% endhighlight %}

This method returns the final array by converting wordHash's keys to an array after the loop has totally finished.