---
layout: post
current: post
navigation: True
title: "How my string segmenting program works"
excerpt: "What happens when you try to split a string up into individual words."
categories: Programming
tags: [ruby, algorithms]
date: 2016-01-28
class: post-template
comments: false
subclass:
author:
---

#### We were tasked with created a program that split up a string into individual words. For example `"catsurethra"` should be split up into `"cats"` & `"urethra"`. However, you'll notice that there are other words inside of that string like `"cat"`, `"at"`, and `"sure"`. I needed to make sure I accounted for all possible words that my program would find and also ensure that there were no leftover letters at the end. After some sketching out of ideas into plain text, I felt I had a working concept.

**1. First, I linked my code to the dictionary I created and created storage containers for all of my method's needs:**

```ruby

require_relative '../lib/dictionary.rb'

def segment_string(str)
  word_index = Hash.new(0)
  first_letter= 0
  last_letter = 0
```

**2. Then I started my loop which says that while the variable is less than or equal to the string length, do the following operation:**

```ruby
  while last_letter <= str.length do
```

**3. If there are danglers (or letters left over that do not form a word), take the value of the previous last letter and add one to it. Then delete the key/value pair with highest value:**

```ruby
  if danglers?(str, first_letter, last_letter)
    last_letter = change_value_of_letter_variable
    delete_from_hash
```
				
**4. If there is no previous word, then you need to start over at 0. But if there is a previous word, take the value of the previous word's last letter and add 1:**

```ruby
  if you_just_deleted_the_first_word_in_hash
    first_letter = 0
  else 
    first_letter = change_value_of_letter_variable
  end
```

**5. If the current collection of characters is not a word, add one to the last_letter variable:**

```ruby
  elsif !valid_word?(str[first_letter..last_letter])
    last_letter += 1
```

**6. If the collection of characters is a word, store the word & index pair in the hash:**

```ruby
elsif valid_word?(str[first_letter..last_letter])
  word_index[str[first_letter..last_letter]] = last_letter	
```

**7. Then move on to the next character by reassigning the last_letter +1 to the first_letter spot and adding one to the last_letter:**

```ruby

    first_letter = last_letter + 1
    last_letter += 1
  end
end
```

**8. Then return the keys from the hash:**
   
```ruby
  return $word_index.keys
end
```

#### My other methods work as follows:


**A. Check if the current value of last_letter is the same as the value of the length of the string _AND_ if the length of the joined array is less than the length of the original string:**

```ruby

def danglers?(str, first_letter, last_letter)
  last_letter == str.length && $word_index.keys.join.length < str.length
end
```

**B.  Take the value of the previous last letter and add one to it:**

```ruby

def change_value_of_letter_variable
  return $word_index.values.max + 1
end
```

**C. Delete the previous word and it's value from the Hash:**

```ruby

def delete_from_hash
  $word_index.delete($word_index.max_by{|k,v| v}[0])
end
```

**D. If the first word of the Hash was the one that you deleted. Conditional stating that now the max value in the Hash is nil.**

```ruby

def you_just_deleted_the_first_word_in_hash
  $word_index.values.max == nil
end
```

