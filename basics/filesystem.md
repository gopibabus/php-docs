# FileSystem Functions

```php

/*
|--------------------------------------------------------------------------
| chmod
|--------------------------------------------------------------------------
|
| Changes file mode
|
*/

// Read and write for owner, nothing for everybody else
chmod("/somedir/somefile", 0600);

// Read and write for owner, read for everybody else
chmod("/somedir/somefile", 0644);

// Everything for owner, read and execute for others
chmod("/somedir/somefile", 0755);

// Everything for owner, read and execute for owner's group
chmod("/somedir/somefile", 0750);

/*
|--------------------------------------------------------------------------
| chown
|--------------------------------------------------------------------------
|
| Changes file owner. Only the superuser may change the owner of a file.
|
*/

// File name and username to use
$file_name= "foo.php";
$path = "/home/sites/php.net/public_html/sandbox/" . $file_name ;
$user_name = "root";

// Set the user
chown($path, $user_name);

/*
|--------------------------------------------------------------------------
| copy
|--------------------------------------------------------------------------
|
| Copies file. If the destination file already exists, 
| it will be overwritten.
|
*/

$file = 'example.txt';
$newfile = 'example.txt.bak';

if (!copy($file, $newfile)) {
    echo "failed to copy $file...\n";
}

/*
|--------------------------------------------------------------------------
| dirname
|--------------------------------------------------------------------------
|
| Returns a parent directory's path. 
|
*/

echo dirname("/etc/passwd") . PHP_EOL; #/etc
echo dirname("/etc/") . PHP_EOL; # / (or \ on Windows)
echo dirname(".") . PHP_EOL; # .
echo dirname("C:\\") . PHP_EOL; # C:\
echo dirname("/usr/local/lib", 2); # /usr

/*
|--------------------------------------------------------------------------
| disk_free_space
|--------------------------------------------------------------------------
|
| Returns available space on filesystem or disk partition.
|
*/

// $df contains the number of bytes available on "/"
$df = disk_free_space("/");

// On Windows:
$df_c = disk_free_space("C:");
$df_d = disk_free_space("D:");

/*
|--------------------------------------------------------------------------
| disk_total_space
|--------------------------------------------------------------------------
|
| Returns the total size of a filesystem or disk partition
|
*/

// $ds contains the total number of bytes available on "/"
$ds = disk_total_space("/");

// On Windows:
$ds = disk_total_space("C:");
$ds = disk_total_space("D:");

/*
|--------------------------------------------------------------------------
| fopen
|--------------------------------------------------------------------------
|
| Opens file or URL
|
*/

$handle = fopen("c:\\folder\\resource.txt", "r");

/*
|--------------------------------------------------------------------------
| file_exists
|--------------------------------------------------------------------------
|
| Checks whether a file or directory exists
|
*/

$filename = '/path/to/foo.txt';

if (file_exists($filename)) {
    echo "The file $filename exists";
} else {
    echo "The file $filename does not exist";
}


/*
|--------------------------------------------------------------------------
| fclose
|--------------------------------------------------------------------------
|
| Closes an open file pointer
|
*/

$handle = fopen('somefile.txt', 'r');

fclose($handle);

/*
|--------------------------------------------------------------------------
| feof
|--------------------------------------------------------------------------
|
| Tests for end-of-file on a file pointer
|
*/

// if file can not be read or doesn't exist fopen function returns FALSE
$file = @fopen("no_such_file", "r");

// FALSE from fopen will issue warning and result in infinite loop here
while (!feof($file)) {
	//Do something with data in file
}

fclose($file);

/*
|--------------------------------------------------------------------------
| file_get_contents
|--------------------------------------------------------------------------
|
| Reads entire file into a string
|
*/

// If strict types are enabled i.e. declare(strict_types=1);
$file = file_get_contents('./people.txt', true);

// Otherwise
$file = file_get_contents('./people.txt', FILE_USE_INCLUDE_PATH);

/*
|--------------------------------------------------------------------------
| file
|--------------------------------------------------------------------------
|
| Reads entire file into an array
|
*/

// Get a file into an array.  In this example we'll go through HTTP to get
// the HTML source of a URL.
$lines = file('http://www.example.com/');

// Loop through our array, show HTML source as HTML source; and line numbers too.
foreach ($lines as $line_num => $line) {
    echo "Line #<b>{$line_num}</b> : " . htmlspecialchars($line) . "<br />\n";
}

// Using the optional flags parameter
$trimmed = file('somefile.txt', FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);

/*
|--------------------------------------------------------------------------
| file_put_contents
|--------------------------------------------------------------------------
|
| Write data to a file
|
*/

$file = 'people.txt';

// Open the file to get existing content
$current = file_get_contents($file);

// Append a new person to the file
$current .= "John Smith\n";

// Write the contents back to the file
file_put_contents($file, $current);


/*
|--------------------------------------------------------------------------
| fgetc
|--------------------------------------------------------------------------
|
| Gets a character from the given file pointer.
|
*/

$fp = fopen('somefile.txt', 'r');

if (!$fp) {
    echo 'Could not open file somefile.txt';
}

while (false !== ($char = fgetc($fp))) {
    echo "$char\n";
}

/*
|--------------------------------------------------------------------------
| fgets
|--------------------------------------------------------------------------
|
| Gets line from file pointer
|
*/

$handle = @fopen("/tmp/inputfile.txt", "r");

if ($handle) {
    while (($buffer = fgets($handle, 4096)) !== false) {
        echo $buffer;
    }
    
    if (!feof($handle)) {
        echo "Error: unexpected fgets() fail\n";
    }
    fclose($handle);
}


/*
|--------------------------------------------------------------------------
| fgetcsv
|--------------------------------------------------------------------------
|
| Gets line from file pointer and parse for CSV fields
|
*/

$row = 1;
if (($handle = fopen("test.csv", "r")) !== FALSE) {
    while (($data = fgetcsv($handle, 1000, ",")) !== FALSE) {
        $num = count($data);
        echo "<p> $num fields in line $row: <br /></p>\n";
        $row++;
        for ($c=0; $c < $num; $c++) {
            echo $data[$c] . "<br />\n";
        }
    }
    fclose($handle);
}

/*
|--------------------------------------------------------------------------
| fileatime
|--------------------------------------------------------------------------
|
| Gets last access time of file
|
*/

$filename = 'somefile.txt';
if (file_exists($filename)) {
    echo "$filename was last accessed: " . date("F d Y H:i:s.", fileatime($filename));
}

/*
|--------------------------------------------------------------------------
| filemtime
|--------------------------------------------------------------------------
|
| Gets the time when the content of the file was changed
|
*/

$filename = 'somefile.txt';
if (file_exists($filename)) {
    echo "$filename was last modified: " . date ("F d Y H:i:s.", filemtime($filename));
}

/*
|--------------------------------------------------------------------------
| filesize
|--------------------------------------------------------------------------
|
| Gets file size in bytes
|
*/

$filename = 'somefile.txt';
echo $filename . ': ' . filesize($filename) . ' bytes';

/*
|--------------------------------------------------------------------------
| filetype
|--------------------------------------------------------------------------
|
| Gets file type
|
*/

cho filetype('/etc/passwd');  // file
echo filetype('/etc/');       // dir

/*
|--------------------------------------------------------------------------
| fnmatch
|--------------------------------------------------------------------------
|
| Match filename against a pattern
|
*/

if (fnmatch("*gr[ae]y", $fileName)) {
  echo "{$fileName} getting uploaded ...";
}

/*
|--------------------------------------------------------------------------
| fputcsv
|--------------------------------------------------------------------------
|
| Formats a line (passed as a fields array) as CSV and 
| writes it (terminated by a newline) to the specified file handle.
|
*/

$list = array (
    array('aaa', 'bbb', 'ccc', 'dddd'),
    array('123', '456', '789'),
    array('"aaa"', '"bbb"')
);

$fp = fopen('file.csv', 'w');

foreach ($list as $fields) {
    fputcsv($fp, $fields);
}

fclose($fp);

/*
|--------------------------------------------------------------------------
| fread
|--------------------------------------------------------------------------
|
| Reads up to length bytes from the file pointer referenced by stream.
|
*/

// get contents of a file into a string
$filename = "/usr/local/something.txt";
$handle = fopen($filename, "r");
$contents = fread($handle, filesize($filename));
fclose($handle);

/*
|--------------------------------------------------------------------------
| fscanf
|--------------------------------------------------------------------------
|
| Parses input from a file according to a format.
|
*/

$handle = fopen("users.txt", "r");
while ($userinfo = fscanf($handle, "%s\t%s\t%s\n")) {
    list ($name, $profession, $countrycode) = $userinfo;
    //do something with the values
}
fclose($handle);

/*
|--------------------------------------------------------------------------
| fstat
|--------------------------------------------------------------------------
|
| Gets information about a file using an open file pointer
|
*/

// open a file
$fp = fopen("/etc/passwd", "r");

// gather statistics
$fstat = fstat($fp);

// close the file
fclose($fp);

// print only the associative part
print_r(array_slice($fstat, 13));

/*
|--------------------------------------------------------------------------
| ftell
|--------------------------------------------------------------------------
|
| Returns the current position of the file read/write pointer
|
*/

// opens a file and read some data
$fp = fopen("/etc/passwd", "r");
$data = fgets($fp, 12);

// where are we ?
echo ftell($fp); // 11

fclose($fp);

/*
|--------------------------------------------------------------------------
| ftruncate
|--------------------------------------------------------------------------
|
|  Truncates a file to a given length
|
*/

$filename = 'lorem_ipsum.txt';

$handle = fopen($filename, 'r+');
ftruncate($handle, rand(1, filesize($filename)));
rewind($handle);
echo fread($handle, filesize($filename));
fclose($handle);

/*
|--------------------------------------------------------------------------
| fwrite
|--------------------------------------------------------------------------
|
| Writes the contents of string to the file stream pointed to by handle.
|
*/

$filename = 'test.txt';
$somecontent = "Add this to the file\n";

// Write $somecontent to our opened file.
if (fwrite($handle, $somecontent) === FALSE) {
    echo "Cannot write to file ($filename)";
    exit;
}

echo "Success, wrote ($somecontent) to file ($filename)";

fclose($handle);

/*
|--------------------------------------------------------------------------
| glob
|--------------------------------------------------------------------------
|
| Find pathnames matching a pattern
|
*/

foreach (glob("*.txt") as $filename) {
    echo "$filename size " . filesize($filename) . "\n";
}

/*
|--------------------------------------------------------------------------
| is_dir 
|--------------------------------------------------------------------------
|
| Tells whether the filename is a directory
|
*/

var_dump(is_dir('a_file.txt')); //false
var_dump(is_dir('bogus_dir/abc')); //false
var_dump(is_dir('..')); //true

/*
|--------------------------------------------------------------------------
| is_executable 
|--------------------------------------------------------------------------
|
| Tells whether the filename is executable
|
*/

$file = '/home/vincent/somefile.sh';

if (is_executable($file)) {
    echo $file.' is executable';
} else {
    echo $file.' is not executable';
}

/*
|--------------------------------------------------------------------------
| is_file 
|--------------------------------------------------------------------------
|
| Tells whether the filename is a regular file
|
*/

var_dump(is_file('a_file.txt')); //true
var_dump(is_file('/usr/bin/')); //false

/*
|--------------------------------------------------------------------------
| is_link 
|--------------------------------------------------------------------------
|
| Tells whether the filename is a symbolic link
|
*/

$link = 'uploads';

if (is_link($link)) {
    echo(readlink($link));
} else {
    symlink('uploads.php', $link);
}

/*
|--------------------------------------------------------------------------
| is_readable 
|--------------------------------------------------------------------------
|
| Tells whether a file exists and is readable
|
*/

$filename = 'test.txt';
if (is_readable($filename)) {
    echo 'The file is readable';
} else {
    echo 'The file is not readable';
}

/*
|--------------------------------------------------------------------------
| is_uploaded_file 
|--------------------------------------------------------------------------
|
| Tells whether the file was uploaded via HTTP POST
|
*/

if (is_uploaded_file($_FILES['userfile']['tmp_name'])) {
   echo "File ". $_FILES['userfile']['name'] ." uploaded successfully.\n";
   echo "Displaying contents\n";
   readfile($_FILES['userfile']['tmp_name']);
} else {
   echo "Possible file upload attack: ";
   echo "filename '". $_FILES['userfile']['tmp_name'] . "'.";
}

/*
|--------------------------------------------------------------------------
| is_writable 
|--------------------------------------------------------------------------
|
| Tells whether the filename is writable
|
*/

$filename = 'test.txt';

if (is_writable($filename)) {
    echo 'The file is writable';
} else {
    echo 'The file is not writable';
}

/*
|--------------------------------------------------------------------------
| link 
|--------------------------------------------------------------------------
|
| Create a hard link
|
*/

$target = 'source.ext'; // This is the file that already exists
$link = 'newfile.ext'; // This the filename that you want to link it to

link($target, $link);

/*
|--------------------------------------------------------------------------
| linkinfo 
|--------------------------------------------------------------------------
|
| Gets information about a link
|
*/

echo linkinfo('/vmlinuz'); // 835

/*
|--------------------------------------------------------------------------
| lstat 
|--------------------------------------------------------------------------
|
| Gives information about a file or symbolic link
|
*/

symlink('uploads.php', 'uploads');

// Contrast information for uploads.php and uploads
array_diff(stat('uploads'), lstat('uploads'));

/*
|--------------------------------------------------------------------------
| mkdir 
|--------------------------------------------------------------------------
|
| Makes directory
|
*/

$structure = './depth1/depth2/depth3/';

if (!mkdir($structure, 0777, true)) {
    die('Failed to create directories...');
}

/*
|--------------------------------------------------------------------------
| move_uploaded_file 
|--------------------------------------------------------------------------
|
| Moves an uploaded file to a new location
|
*/

$uploads_dir = '/uploads';
foreach ($_FILES["pictures"]["error"] as $key => $error) {
    if ($error == UPLOAD_ERR_OK) {
        $tmp_name = $_FILES["pictures"]["tmp_name"][$key];
        // basename() may prevent filesystem traversal attacks;
        // further validation/sanitation of the filename may be appropriate
        $name = basename($_FILES["pictures"]["name"][$key]);
        move_uploaded_file($tmp_name, "$uploads_dir/$name");
    }
}

/*
|--------------------------------------------------------------------------
| parse_ini_file 
|--------------------------------------------------------------------------
|
| Parse a configuration file
|
*/

// Parse without sections
$ini_array = parse_ini_file("sample.ini");
print_r($ini_array);

// Parse with sections
$ini_array = parse_ini_file("sample.ini", true);
print_r($ini_array);

/*
|--------------------------------------------------------------------------
| parse_ini_string 
|--------------------------------------------------------------------------
|
| Parse a configuration string
|
*/

$ini = '

    [simple]
    val_one = "some value"
    val_two = 567

    [array]
    val_arr[] = "arr_elem_one"
    val_arr[] = "arr_elem_two"
    val_arr[] = "arr_elem_three"

    [array_keys]
    val_arr_two[6] = "key_6"
    val_arr_two[some_key] = "some_key_value"

';

$arr = parse_ini_string_m($ini);

/*
|--------------------------------------------------------------------------
| pathinfo 
|--------------------------------------------------------------------------
|
| Returns information about a file path
|
*/

$path_parts = pathinfo('/www/htdocs/inc/lib.inc.php');

echo $path_parts['dirname'];
echo $path_parts['basename'];
echo $path_parts['extension'];
echo $path_parts['filename'];


/*
|--------------------------------------------------------------------------
| readfile 
|--------------------------------------------------------------------------
|
| Outputs a file
|
*/

$file = 'monkey.gif';

if (file_exists($file)) {
    header('Content-Description: File Transfer');
    header('Content-Type: application/octet-stream');
    header('Content-Disposition: attachment; filename="'.basename($file).'"');
    header('Expires: 0');
    header('Cache-Control: must-revalidate');
    header('Pragma: public');
    header('Content-Length: ' . filesize($file));
    readfile($file);
    exit;
}

/*
|--------------------------------------------------------------------------
| readlink 
|--------------------------------------------------------------------------
|
| Returns the target of a symbolic link
|
*/

echo readlink('/vmlinuz');

/*
|--------------------------------------------------------------------------
| realpath 
|--------------------------------------------------------------------------
|
| Returns canonicalized absolute pathname
|
*/

chdir('/var/www/');
echo realpath('./../../etc/passwd') . PHP_EOL;

echo realpath('/tmp/') . PHP_EOL;

/*
|--------------------------------------------------------------------------
| rename 
|--------------------------------------------------------------------------
|
| Renames a file or directory
|
*/

rename("/tmp/tmp_file.txt", "/home/user/login/docs/my_file.txt");

/*
|--------------------------------------------------------------------------
| rewind 
|--------------------------------------------------------------------------
|
| Rewind the position of a file pointer. 
| Sets the file position indicator for stream to the beginning of stream.
*/

$handle = fopen('output.txt', 'r+');

fwrite($handle, 'Really long sentence.');
rewind($handle);
fwrite($handle, 'Foo');
rewind($handle);

echo fread($handle, filesize('output.txt'));

fclose($handle);

/*
|--------------------------------------------------------------------------
| rmdir 
|--------------------------------------------------------------------------
|
| Removes directory 
| 
*/

if (!is_dir('examples')) {
    mkdir('examples');
}

rmdir('examples');

/*
|--------------------------------------------------------------------------
| stat 
|--------------------------------------------------------------------------
|
| Gives information about a file
| 
*/

/* Get file stat */
$stat = stat('C:\php\php.exe');

/*
 * Print file access time, this is the same 
 * as calling fileatime()
 */
echo 'Access time: ' . $stat['atime'];

/*
 * Print file modification time, this is the 
 * same as calling filemtime()
 */
echo 'Modification time: ' . $stat['mtime'];

/* Print the device number */
echo 'Device number: ' . $stat['dev'];

/*
|--------------------------------------------------------------------------
| symlink 
|--------------------------------------------------------------------------
|
| Creates a symbolic link
| 
*/

$target = 'uploads.php';
$link = 'uploads';
symlink($target, $link);

echo readlink($link);

/*
|--------------------------------------------------------------------------
| tempnam 
|--------------------------------------------------------------------------
|
| Create file with unique file name
| 
*/

$tmpfname = tempnam("/tmp", "FOO");

$handle = fopen($tmpfname, "w");
fwrite($handle, "writing to tempfile");
fclose($handle);

// do here something

unlink($tmpfname);

/*
|--------------------------------------------------------------------------
| tmpfile 
|--------------------------------------------------------------------------
|
| Creates a temporary file
| 
*/

$temp = tmpfile();
fwrite($temp, "writing to tempfile");
fseek($temp, 0);
echo fread($temp, 1024);
fclose($temp); // this removes the file

/*
|--------------------------------------------------------------------------
| touch 
|--------------------------------------------------------------------------
|
| Sets access and modification time of file
| 
*/

if (touch($filename)) {
    echo $filename . ' modification time has been changed to present time';
} else {
    echo 'Sorry, could not change modification time of ' . $filename;
}

/*
|--------------------------------------------------------------------------
| unlink 
|--------------------------------------------------------------------------
|
| Deletes a file
| 
*/

$fh = fopen('test.html', 'a');
fwrite($fh, '<h1>Hello world!</h1>');
fclose($fh);

unlink('test.html');

```