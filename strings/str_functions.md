# 🔥String Functions

```php

/*
|--------------------------------------------------------------------------
| parse_str
|--------------------------------------------------------------------------
|
| Parses string as if it were the query string passed via a URL and sets variables in the current scope.
|
*/

$str = "first=value&arr[]=foo+bar&arr[]=baz";

parse_str($str, $output);
echo $output['first'];  // value
echo $output['arr'][0]; // foo bar
echo $output['arr'][1]; // baz

# Because variables in PHP can't have dots and spaces in their names, those are converted to underscores.
parse_str("My Value=Something", $output);
echo $output['My_Value']; // Something

/*
|--------------------------------------------------------------------------
| number_format
|--------------------------------------------------------------------------
|
| Format a number with grouped thousands and optionally decimal digits.
|
*/

$number = 1234.56;

// english notation (default)
$english_format_number = number_format($number);// 1,235

// French notation
$nombre_format_francais = number_format($number, 2, ',', ' ');// 1 234,56

$number = 1234.5678;

// english notation without thousands separator
$english_format_number = number_format($number, 2, '.', '');// 1234.57

/*
|--------------------------------------------------------------------------
| htmlspecialchars
|--------------------------------------------------------------------------
|
| Convert special characters to HTML entities.
|
*/

$new = htmlspecialchars("<a href='test'>Test</a>", ENT_QUOTES);

echo $new; // &lt;a href=&#039;test&#039;&gt;Test&lt;/a&gt;

/*
|--------------------------------------------------------------------------
| htmlentities
|--------------------------------------------------------------------------
|
| Convert all applicable characters to HTML entities
|
*/

$str = "A 'quote' is <b>bold</b>";

// Outputs: A 'quote' is &lt;b&gt;bold&lt;/b&gt;
echo htmlentities($str);

// Outputs: A &#039;quote&#039; is &lt;b&gt;bold&lt;/b&gt;
echo htmlentities($str, ENT_QUOTES);

// Outputs an empty string
echo htmlentities($str, ENT_QUOTES, "UTF-8");

// Outputs "!!!"
echo htmlentities($str, ENT_QUOTES | ENT_IGNORE, "UTF-8");

/*
|--------------------------------------------------------------------------
| strip_tags
|--------------------------------------------------------------------------
|
| Strip HTML and PHP tags from a string
|
*/

$text = '<p>Test paragraph.</p><!-- Comment --> <a href="#fragment">Other text</a>';

echo strip_tags($text);//Test paragraph. Other text

// Allow <p> and <a>
echo strip_tags($text, ['p', 'a']);//<p>Test paragraph.</p> <a href="#fragment">Other text</a>

/*
|--------------------------------------------------------------------------
| lcfirst
|--------------------------------------------------------------------------
|
| Make a string's first character lowercase
|
*/

$foo = 'HelloWorld';
$foo = lcfirst($foo);// helloWorld

$bar = 'HELLO WORLD!';
$bar = lcfirst($bar);// hELLO WORLD!

/*
|--------------------------------------------------------------------------
| ucfirst
|--------------------------------------------------------------------------
|
| Make a string's first character uppercase
|
*/

$foo = 'hello world!';
$foo = ucfirst($foo);             // Hello world!

$bar = 'HELLO WORLD!';
$bar = ucfirst($bar);             // HELLO WORLD!

/*
|--------------------------------------------------------------------------
| ucwords
|--------------------------------------------------------------------------
|
| Uppercase the first character of each word in a string
|
*/

$foo = 'hello world!';
$foo = ucwords($foo);             // Hello World!

$bar = 'HELLO WORLD!';
$bar = ucwords($bar);             // HELLO WORLD!

/*
|--------------------------------------------------------------------------
| md5
|--------------------------------------------------------------------------
|
| Calculate the md5 hash of a string.
| Used to hash passwords and store in DB.
|
*/

$str = 'PASSWORD123';
$dbValue = '1f3870be274f6c49b3e31a0c6728957f';

if (md5($str) === $dbValue) {
    //"Permission granted";
}

/*
|--------------------------------------------------------------------------
| nl2br
|--------------------------------------------------------------------------
|
| Inserts HTML line breaks before all newlines in a string
|
*/

echo nl2br("foo isn't\n bar");//foo isn't<br />bar

echo nl2br("Welcome\r\nThis is my HTML document", false);//Welcome<br>This is my HTML document

/*
|--------------------------------------------------------------------------
| similar_text
|--------------------------------------------------------------------------
|
| Calculate the similarity between two strings
|
*/

$sim = similar_text('bafoobar', 'barfoo', $perc);

echo "similarity: $sim ($perc %)\n";//similarity: 5 (71.428571428571 %)

$sim = similar_text('barfoo', 'bafoobar', $perc);

echo "similarity: $sim ($perc %)\n";//similarity: 3 (42.857142857143 %)

/*
|--------------------------------------------------------------------------
| sprintf
|--------------------------------------------------------------------------
|
| Return a formatted string
|
*/

$num = 5;
$location = 'tree';

$format = 'There are %d monkeys on the %s';
echo sprintf($format, $num, $location); //There are 5 monkeys on the tree

/*
|--------------------------------------------------------------------------
| str_getcsv
|--------------------------------------------------------------------------
|
| Parses a string input for fields in CSV format and 
| returns an array containing the fields read.
|
*/

$csv = array_map('str_getcsv', file('data.csv'));

/*
|--------------------------------------------------------------------------
| wordwrap
|--------------------------------------------------------------------------
|
| Wraps a string to a given number of characters
|
*/

$text = "The quick brown fox jumped over the lazy dog.";
$newtext = wordwrap($text, 20, "<br />\n");

echo $newtext;

// The quick brown fox<br />
// jumped over the lazy<br />
// dog.


```