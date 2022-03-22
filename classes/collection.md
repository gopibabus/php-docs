# Collections

```php

<?php

use Doctrine\Common\Collections\ArrayCollection;

require __DIR__ . '/vendor/autoload.php';

/*
|--------------------------------------------------------------------------
| Collection
|--------------------------------------------------------------------------
|
| Collection is the base interface which covers functionality common to
| all the data structures in this library. It gaurantees that all structures
| are traversable, countable and can be converted to json using json_encode();
| We are using Doctrine ArrayCollection, which is implementation of Collection Interface
|
| NOTE: Doctrine has many Collections like PersistentCollection etc., ArrayCollection is one of them
*/
$cities = [
  [
    'name'       => 'Frankfurt',
    'country'    => 'Germany',
    'population' => 785_000,
  ],
  [
    'name'       => 'Mumbai',
    'country'    => 'India',
    'population' => 20_000_000,
  ],
  [
    'name'       => 'Valencia',
    'country'    => 'Spain',
    'population' => 834_920,
  ]
];

$lille = [
  'name'                => 'Lille',
  'country'             => 'France',
  'population'          => 238_381,
  'geohash_coordinates' => 'u140j97nqjd'
];

$citiesCollection = new ArrayCollection($cities);
$lilleCollection = new ArrayCollection($lille);

# Iterating on Collection
// foreach ($citiesCollection as $index => $city) {
//   print $city['name'] . PHP_EOL;
// }

# Filter on Collection
$filteredCities = $citiesCollection->filter(function($city){
  return $city['population'] > 800_000;
});

# Adding element to Collection
$citiesCollection->add($lille);

# Remove element in a Collection at the given index
$citiesCollection->remove(2);

# Check element is present in Collection
$containsLille =  $citiesCollection->contains($lille);

# Get the index of element in the Collection
$indexOf = $citiesCollection->indexOf($lille);

# Get first Item in the Collection
$first = $citiesCollection->first();

# Get last Item in the Collection
$first = $citiesCollection->last();

# Find the Item in the Collection matching given criteria
$cityExists = $citiesCollection->exists(function($key, $city){
  return $city['population'] > 15_000_000;
});

# Find the Item in the Collection matching given criteria by returing collection 
# that macth the filter criteria and other not matching the criteria.
$cityExists = $citiesCollection->partition(function ($key, $city) {
  return $city['population'] > 15_000_000;
});

# Turn Collection back into an Array
$lilliArray = $lilleCollection->toArray();

```