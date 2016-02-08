---
title: How my segmenting program works
---

#### First I linked my code to the dictionary I created and created storage containers for all of my method's needs
```
	require_relative '../lib/dictionary.rb'


	def segment_string(str) 

	    word_index = Hash.new(0)
	    first_letter= 0
	    last_letter = 0

```

#### Then I started my loop which says that while the variable is less than or equal to the string length, do the following operation's

	`while last_letter <= str.length do`


#### If there are danglers, take the value of the previous last letter and add one to it. Then delete the key/value pair with highest value 

```
		if danglers?(str, first_letter, last_letter)
			last_letter = change_value_of_letter_variable
			delete_from_hash

```

#### If there is no previous word, then you need to start over at 0

#### But if there is a previous word, take the value of the previous word's last letter and add 1
			

```
			if you_just_deleted_the_first_word_in_hash
				first_letter = 0
			else 
				first_letter = change_value_of_letter_variable
			end
```


#### If the current collection of characters is not a word, add one to the last_letter variable


```
		elsif !valid_word?(str[first_letter..last_letter])
			last_letter += 1
```


#### If the collection of characters is a word, store the word & index pair in the hash,


```
		elsif valid_word?(str[first_letter..last_letter])
			word_index[str[first_letter..last_letter]] = last_letter	

```


#### then move on to the next character by reassigning the last_letter +1 to the first_letter spot and adding one to the last_letter


```
			first_letter = last_letter + 1
			last_letter += 1
		end
	end
```

#### Then return the keys from the hash

```
	return $word_index.keys
end
```

#### My other methods work as follows:


#### Check if the current value of last_letter is the same as the value of the length of the string _AND_ if the length of the joined array is less than the length of the original string.


```
def danglers?(str, first_letter, last_letter)
	last_letter == str.length && $word_index.keys.join.length < str.length
end
```


#### Take the value of the previous last letter and adds one to it


```
def change_value_of_letter_variable
	return $word_index.values.max + 1
end
```

#### Deletes the previous word and it's value from the Hash.
```
def delete_from_hash
	$word_index.delete($word_index.max_by{|k,v| v}[0])
end
```

#### If the first word of the Hash was the one that you deleted. Conditional stating that now the max value in the Hash is nil.

```
def you_just_deleted_the_first_word_in_hash
	$word_index.values.max == nil
end
```

