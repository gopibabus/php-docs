# 🔥Array Functions

### ❇Create an Array

| Function     | Purpose                                                |
| ------------ | ------------------------------------------------------ |
| explode()    | Used to split up a string into an array.               |
| implode()    | Joins the elements of an array together into a string. |
| preg_split() | Splits a string into an array.                         |
| str_split()  | Break a string into an array of chunks.                |

### ❇Filling up an Array

| Function          | Purpose                                                                              |
| ----------------- | ------------------------------------------------------------------------------------ |
| range()           | Add values to an array based on a range of values you specify.                       |
| array_combine()   | Creates an array by using the elements from one "keys" array and one "values" array. |
| array_fill()      | Fills an array with values.                                                          |
| array_fill_keys() | Fills an array with values, specifying keys.                                         |

### ❇Alter an Array

| Function        | Purpose                                              |
| --------------- | ---------------------------------------------------- |
| array_shift()   | Removes the first element from an array.             |
| array_unshift() | Inserts new elements to the begining of an array.    |
| array_pop()     | Deletes the last element of an array.                |
| array_push()    | Inserts one or more elements to the end of an array. |

### ❇Comparing Arrays

| Function                | Purpose                                                                                                                |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| array_diff()            | Compares the values of two (or more) arrays.                                                                           |
| array_diff_assoc()      | Compares the keys and values of two (or more) arrays.                                                                  |
| array_intersect()       | Compares the values of two (or more) arrays and returns the matches                                                    |
| array_intersect_assoc() | Compares the keys and values of two (or more) arrays, and returns the matches.                                         |
| array_udiff()           | Compares the values of two or more arrays, and returns the differences.                                                |
| array_udiff_assoc()     | Compares the keys and values of two or more arrays, and returns the differences.                                       |
| array_udiff_uassoc()    | Compare the keys and values of two arrays (using two user-defined functions for comparison) and return the differences |

### ❇Combining Arrays

| Function        | Purpose                                                                                 |
| --------------- | --------------------------------------------------------------------------------------- |
| array_replace() | Replace the values of the first array ($a1) with the values from the second array ($a2) |
| array_merge()   | Merge two arrays into one array.                                                        |

### ❇Splitting Arrays

| Function       | Purpose                                                         |
| -------------- | --------------------------------------------------------------- |
| array_chunk()  | Split an array into chunks of two.                              |
| array_column() | Returns the values from a single column in the input array.     |
| array_slice()  | Returns selected parts of an array.                             |
| array_splice() | Remove elements from an array and replace it with new elements. |
| extract()      | Imports variables into the local symbol table from an array.    |
| array_rand()   | Return an array of random keys.                                 |

### ❇Destructing Arrays

| Function | Purpose                                                |
| -------- | ------------------------------------------------------ |
| list()   | assign values to a list of variables in one operation. |

### ❇Calculating with Arrays

| Function             | Purpose                                                          |
| -------------------- | ---------------------------------------------------------------- |
| array_count_values() | Counts all the values of an array.                               |
| array_product()      | Calculates and returns the product of values in an array.        |
| array_sum()          | Returns the sum of all the values in the array.                  |
| count()              | Return the number of elements in an array.                       |
| sizeof()             | Alias of the count(). Return the number of elements in an array. |

### ❇Using Array Cursors

| Function  | Purpose                                                                        |
| --------- | ------------------------------------------------------------------------------ |
| reset()   | Moves the internal pointer to the first element of the array.                  |
| end()     | Moves the internal pointer to, and outputs, the last element in the array.     |
| next()    | Moves the internal pointer to, and outputs, the next element in the array.     |
| prev()    | Moves the internal pointer to, and outputs, the previous element in the array. |
| current() | Returns the value of the current element in an array.                          |
| key()     | Returns the element key from the current internal pointer position..           |

### ❇Walking through Arrays

| Function     | Purpose                                            |
| ------------ | -------------------------------------------------- |
| array_walk() | Run each array element in a user-defined function. |

### ❇Sorting Arrays

| Function  | Purpose                                                                                            |
| --------- | -------------------------------------------------------------------------------------------------- |
| sort()    | Sorts an indexed array in ascending order.                                                         |
| rsort()   | Sorts an indexed array in descending order.                                                        |
| asort()   | Sorts an associative array in ascending order, according to the value.                             |
| arsort()  | Sorts an associative array in descending order, according to the value.                            |
| ksort()   | Sorts an associative array in descending order, according to the key.                              |
| usort()   | Sorts an array using a user-defined comparison function..                                          |
| shuffle() | Randomizes the order of the elements in the array. Assigns new keys for the elements in the array. |
| natsort() | Sorts an array by using a "natural order" algorithm. The values keep their original keys.          |
