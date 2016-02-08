---
title: Describing My String Segmenting Program
---

### Describing My String Segmenting Program

First, call the dictionary using **_require_relative 'dictionary'_** to help run the following method. Define the method as segment_string and display the word "BEGIN" on the screen.

Set a variable for how many characters are in a string. Set a variable for the starting point of string characters to check, ours will start at zero. Set an ending point of string characters to check until, again ours will start at zero. Set a variable for a skip counter to zero and set a hash to store found words in to empty.

Display the word "LOOP" on the screen. While the ending point of the characters of the string is not yet equal to how many characters are in the actual string itself, this means you have not reached the end of the string and therefore should proceed with the following:

1. Display "Checking letters (with the respective starting point) until (the respective ending point)."

2. Lowercase the string and call the entire span of letters that is being checked (from starting point to ending point) "range".

3. Display "Is (respective range) a word?"

4. Range will be checked using the _**valid_word?**_ method to see if there is a dictionary entry to match it.

5. **IF** there **_IS_** a match, meaning **valid_word(range)** is **TRUE** then display "Yes" on the screen.

6. **IF valdi_word?(range)** is **TRUE** _AND_ the skip counter is greater than zero, display "Disabled skip for next word", then subtract 1 from the skip counter.

7. **IF valid_method?** is **TRUE _AND_** the skip counter is _**NOT**_ greater than zero then display "Archiving word". Save the current range to the empty hash variable as a value with a key equal to its ending point, display the collected words of the hash so far, display that the starting point of the range will now be moved up to the last ending point, then make the starting point equal to the ending point.

8. **IF valid_word(range)** is **_NOT_ TRUE**, meaning that it is **FALSE _AND_** the ending point is still not yet equal to the length of characters in the string display "Dangler! Removing last word". Create a new variable and make it equal to the last key of the hash, then delete the last key of the hash (which will also delete the value). Display an update of the words saved in the hash. Make a new variable and set it to the last key still contained in the hash.

9. **IF** the last key still contained in the hash is _nothing_ display that the hash is empty now and reset the starting point and ending point to 0.

10. **IF** the last key still contained inside the hash is **_NOT_** nothing then make that key the new starting point and display that we are now starting from the respective point in the string.  Move the ending point back to be equal to the starting point.
 
11. **IF** the ending point is equal to the length of characters in the string and the range is _**NOT**_ a valid word, display that skip is now in effect and increase the skip counter by 1.

12. No matter if the range is a match or not always the ending point must increase by 1.

13. Display that the loop is complete and return the words collected in the hash.