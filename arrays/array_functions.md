# 🔥Array Functions

```php

<?php
$city = [
  'name' => 'Frankfurt',
  'country' => 'Germany',
  'population' => 785000,
  'latitude' => 50.110924,
  'longitude' => 8.682127
];

/*
|--------------------------------------------------------------------------
| array_keys
|--------------------------------------------------------------------------
|
| Returns all keys or a subset of keys of an array.
|
*/

$keys = array_keys($city);

/*
|--------------------------------------------------------------------------
| array_values
|--------------------------------------------------------------------------
|
| Return all values of an array
|
*/

$values = array_values($city);

/*
|--------------------------------------------------------------------------
| in_array
|--------------------------------------------------------------------------
|
| Check if a value exists in an array.
|
*/

$in = in_array('Berlin', $city);

/*
|--------------------------------------------------------------------------
| array_key_exists
|--------------------------------------------------------------------------
|
| Check if the given key or index exists in an array
|
*/

$exists = array_key_exists('longitude', $city);

/*
|--------------------------------------------------------------------------
| array_search
|--------------------------------------------------------------------------
|
| Searches the array for a given value and 
| returns the first corresponding key if successful.
|
*/

$key = array_search('Germany', $city);

/*
|--------------------------------------------------------------------------
| array_count_values
|--------------------------------------------------------------------------
|
| Counts of different values in an array.
|
*/

$numbers = [10, 10, 20, 20, 30, 30, 40];
$valueCount = array_count_values($numbers);

/*
|--------------------------------------------------------------------------
| array_unique
|--------------------------------------------------------------------------
|
| Removed duplicates and return unique values from an array. 
| Returns original keys of values.
|
*/

$unique = array_unique($numbers);

/*
|--------------------------------------------------------------------------
| array_column
|--------------------------------------------------------------------------
|
| Returns the values from a single column in the input array.
|
*/

$cities = [
  [
    'name' => 'Frankfurt',
    'country' => 'Germany',
    'population' => 785000,
    'latitude' => 50.110924,
    'longitude' => 8.682127
  ],
  [
    'name' => 'Mumbai',
    'country' => 'India',
    'population' => 785000,
    'latitude' => 19.110924,
    'longitude' => 72.682127
  ]
];
$countries = array_column($cities, 'country');

/*
|--------------------------------------------------------------------------
| array_unshift
|--------------------------------------------------------------------------
|
| Apends elements to the begining of an array. It will mutate the array.
|
*/

array_unshift($countries, 'USA', 'Canada', 'Mexico');

/*
|--------------------------------------------------------------------------
| array_pop
|--------------------------------------------------------------------------
|
| Remove element from the end of the array. It will mutate the array.
|
*/

$poppedItem = array_pop($countries);

/*
|--------------------------------------------------------------------------
| array_shift
|--------------------------------------------------------------------------
|
| Remove element from the begining of the array. It will mutate the array.
|
*/

$shiftedItem = array_shift($countries);

/*
|--------------------------------------------------------------------------
| array_push
|--------------------------------------------------------------------------
|
| Pushes elements on to the end of an array
|
*/

array_push($countries, 'Pakisthan', 'Srilanka', 'Bangladesh');

/*
|--------------------------------------------------------------------------
| array_diff
|--------------------------------------------------------------------------
|
| Computes the difference of arrays. 
| Returns elements present in array1 that are not in other arrays
|
*/

$arrayOne = [1, 2, 3, 4];
$arrayTwo = [1, 2, 4, 5, 6];
$arrayThree = [1, 4, 5, 6, 7];
$diff = array_diff($arrayOne, $arrayTwo, $arrayThree);

/*
|--------------------------------------------------------------------------
| array_intersect
|--------------------------------------------------------------------------
|
| Computes the common values of arrays. 
| Returns elements commonly present in all arrays
|
*/

$arrayOne = [1, 2, 3, 4];
$arrayTwo = [1, 2, 4, 5, 6];
$arrayThree = [1, 4, 5, 6, 7];
$intersect = array_intersect($arrayOne, $arrayTwo, $arrayThree);

/*
|--------------------------------------------------------------------------
| array_slice
|--------------------------------------------------------------------------
|
| Extract a slice of the array. 
| This function will take array starting index and length.
|
*/

$slice = array_slice($arrayTwo, 2, 2);

/*
|--------------------------------------------------------------------------
| range
|--------------------------------------------------------------------------
|
| Create an array containing a range of elements
|
*/

$arrayFour = range(0, 99);

/*
|--------------------------------------------------------------------------
| array_map
|--------------------------------------------------------------------------
|
| Applies the callback to every element of the array.
|
*/

$arrayFive = array_map(function ($item) {
  return $item ** 2;
}, $arrayTwo);

/*
|--------------------------------------------------------------------------
| array_filter
|--------------------------------------------------------------------------
|
| Filter elements of the given array by 
| applying a callback function on each element value.
|
*/

$squaredFilter = array_filter($arrayFive, function ($item) {
  return $item > 8;
});
# If we have to filter array elements by keys
$cityFilter = array_filter($city, function ($item) {
  return in_array($item, ['city', 'town', 'country']);
}, ARRAY_FILTER_USE_KEY);

/*
|--------------------------------------------------------------------------
| array_combine
|--------------------------------------------------------------------------
|
| Creates an array by using one array for keys and 
| another array for its values.
|
*/

$keys = ['name', 'country', 'population', 'latitude', 'longitude'];
$citiesArray = [
  ['Frankfurt', 'Germany', 785000, 50.110924, 8.682127],
  ['Mumbai', 'india', 20667659, 19.076090, 72.85269]
];
$keyValueCities = [];
foreach ($citiesArray as $city) {
  $keyValueCities[] = array_combine($keys, $city);
}

/*
|--------------------------------------------------------------------------
| array_merge
|--------------------------------------------------------------------------
|
| Merges the elements of one or more arrays together.
|
*/

$mergedCities = array_merge($citiesArray, [['Valencia', 'Spain', 834920, 39.52689, -0.3856987]]);

/*
|--------------------------------------------------------------------------
| array_replace
|--------------------------------------------------------------------------
|
| Replaces the values of the first array with the same values 
| from the following arrays
|
*/

$globalConfig = [
  'env' => 'prod',
  'debug' => false,
  'db_name' => 'prod_db'
];
$devConfig = [
  'env' => 'dev',
  'debug' => true,
  'db_name' => 'dev_db'
];
$localConfig = [
  'db_name' => 'local_db'
];
$myConfig = array_replace($globalConfig, $devConfig, $localConfig);

/*
|--------------------------------------------------------------------------
| array_sum
|--------------------------------------------------------------------------
|
| Calculates sum of values in an array
|
*/

$sum = array_sum([1, 2, 3, 4.5, 6, 7]);

/*
|--------------------------------------------------------------------------
| array_product
|--------------------------------------------------------------------------
|
| Product of values in an array
|
*/

$product = array_product([1, 2, 3, 4.5]);

/*
|--------------------------------------------------------------------------
| array_reduce
|--------------------------------------------------------------------------
|
| Send values in an array to callback function to return a String
|
*/

$animals = ['Dog', 'Cat', 'Horse'];
$reducedString = array_reduce($animals, function($item1, $item2){
  return "{$item1} - {$item2}";
});

/*
|--------------------------------------------------------------------------
| list
|--------------------------------------------------------------------------
|
| Assign a list of variables in one operation
|
*/

$values = [23, 45, 67];
list($a, $b, $c) = $values;

/*
|--------------------------------------------------------------------------
| explode
|--------------------------------------------------------------------------
|
| Split a string into an array
|
*/

$csvString = 'PHP,JavaScript,Python,C';
$languageArray = explode(',', $csvString);

/*
|--------------------------------------------------------------------------
| implode
|--------------------------------------------------------------------------
|
| Join array elements into a string
|
*/

$languageString = implode(',', $languageArray);

/*
|--------------------------------------------------------------------------
| compact
|--------------------------------------------------------------------------
|
| Create an array from variables and their values
|
*/

$name = 'Amaravathi';
$country = 'India';
$state = 'Andhra Pradesh';
$population = 35050000;
$cityCompactArray = compact('name', 'country', 'state', 'population');

```