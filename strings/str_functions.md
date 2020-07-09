# 🔥String Functions

## ⚡Matching Strings

| Function         | Purpose                                                                   |
| ---------------- | ------------------------------------------------------------------------- |
| strcmp()         | Perform binary safe string comparisons.(Case Sensitive)                   |
| strcasecmp()     | First converts strings to lowercase and then compares them.               |
| similar_text()   | Calculates the similarity between two strings.(Computationally Expensive) |
| substr_compare() | To compare substring inside a String.                                     |

## ⚡Extracting Strings

| Function       | Purpose                                                   |
| -------------- | --------------------------------------------------------- |
| substr()       | To return a portion, or slice, of a string.               |
| substr_count() | Returns the number of sub string occurrences in a string. |

## ⚡Searching Strings

| Function  | Purpose                                                                                                         |
| --------- | --------------------------------------------------------------------------------------------------------------- |
| strpos()  | Finds the position of the first occurrence of a string inside another string.                                   |
| stripos() | A case-insensitive version of strpos().                                                                         |
| strstr()  | Searches for the first occurrence of a string inside another string.                                            |
| stristr() | A case-insensitive version of strstr().                                                                         |
| strchr()  | Finds the position of the last occurrence of a string within another string.                                    |
| strspn()  | Returns the number of characters found in the string that contains only characters from the charlist parameter. |
| strcspn() | Return the number of characters found in a string.                                                              |

## ⚡Replacing Strings

| Function         | Purpose                                                          |
| ---------------- | ---------------------------------------------------------------- |
| str_replace()    | Replaces some characters with some other characters in a string. |
| str_ireplace()   | Case-insensitive version str_replace()                           |
| substr_replace() | Replaces a part of a string with another string.                 |

## ⚡Formatting Strings

| Function         | Purpose                                                                 |
| ---------------- | ----------------------------------------------------------------------- |
| printf()         | Output a formatted string.                                              |
| setlocale()      | Output a formatted string specific to locale.                           |
| preg_match()     | Returns whether a match was found in a string.                          |
| preg_match_all() | Returns the number of matches of a pattern that were found in a string. |
