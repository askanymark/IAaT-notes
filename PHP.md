# PHP
Hypertext Preprocessor


Cookies:
If expiration time is set to 0 or omitted, the cookie expires when session is terminated.


Regex example:

```php
<? php

if (preg_match('/^[A-Z.-]{1,20}$/i', trim($_POST['name']))) {
    $name = trim($_POST['name']);
} else {
    $name = NULL;
    echo '<p> Please enter a valid name! </p>';
}

if (preg_match('/ˆ[\w.-]+@[\w.-]+\.[A-Za-z]{2,6}$/', trim($_POST['email']))) {
    $email = trim($_POST['email']);
} else {
    $email = NULL;
    echo '<p> Please enter a valid email! </p>';
}

if (!empty($_POST['comments'])) {
    $comments = $_POST['comments'];
} else {
    $comments = NULL;
    echo '<p> You forgot to enter your comments! </p>';
}

if (preg_match('/ˆ[0-9]{2}$/', trim($_POST['age']))) {
    $age = trim($_POST['age']);
} else {
    $age = NULL;
    echo 'Please enter a valid age!';
}

// if everything was filled out correctly, process the data
if ($name && $email && $comments && $age) {
    echo '<p> Thank you, <strong> $name</strong>, for the following comments: <br/> $comments </p> <p> We will reply to you at <i> $email</i>. </p><br/> Your age was entered as $age$.';
}
?>
```
Function example:

```php
function isPalindrome($str) {
    $str = strtolower($str);
    $len = strlen($str);
    for($i=0,$j=$len-1;$i<(int)$len/2;$i++,$j--) {
        if($str[$i]!=$str[$j]) {
            return false;
        }
        return true;
    }
}
```


Arrays:

```php
$word = 'Hello, World!';
$word[4] // returns 'o'

$students = array(); // creates an empty array
$students = array('My', 'Name', 'Jeff');
$students = "Bob"; // creates an array and adds "Bob", otherwise appends to end
$students = array(9=>"Mark"); // puts "Mark" on 9th place, making 0-8 empty
```


Array functions:
count(*$arr*) - returns the number of elements
print_r(*$arr*) - prints array's contents
array_merge(*$arr1, $arr2*) - combines two different arrays
sort(*$arr*) - sorts enumerated arrays by value
ksort(*$arr*) - sorts by key
array_slice(*array,start,length,preserve*) - returns selected parts of an array (substr() equivalent for arrays)
explode(*$str*) - break apart a string into an array
Implode(*$arr*) - merge an array into a unified string


Strings:

```php
// Concatenation
$str1 = 'Hello, ';
$str2 = 'World!';
echo $str1 . $str2 // returns 'Hello, World!'

// Functions
$name = 'Mark '
strlen($name) //Output: '5'
strtolower($name) // Output: 'mark '
strtoupper($name) // Output: 'MARK '
strpos($name, 'rk') // Output: 2
trim($name) // Output: 'Mark'
substr($name, 3, 1) // Output: 'k'
strcmp($name, 'Mark ') // Output: True
```


Math functions:
- abs($val) - Absolute value
- ceil(*number*), floor(*number*) - Ceiling (round up) and floor (round down)
- min(*number1, number2*), max(*array*) - Smallest or largest of a set of values
- pow(*x, y*) - returns *x* raised to the power of *y*.
- rand(*1, 100*) - Random integer in a given range
- rand() - Random integer
- round(*number*) - Round a floating-point number
- sqrt(*number*) - Square root


Files:
- Use include() and require() to add files to scripts


GET 
- Asks a server for a page or data
- Appends the information entered by the user to the URL in the
form of name-value pairs(query string)
- Not suitable for sending large volumes of data
- Not suitable for sensitive or confidential information
“www.mywebsite.com/form_action.php?firstname=Mickey&surname=Mouse”
POST
- Submits data to a web server and retrieves the response
- The values entered by the user are not appended to the URL but
stored within the body of the request.
- Can be used for large amounts of data
- Is more secure as it is not visible while being transmitted.


Examples:

```markup
<form action="http://www.google.com/search">
    <div>
        Let's search Google
        <input type="text" name="q">
        <input type="submit">
    </div>
</form>
http://www.google.com/search?q=Obama

=============================================================

<form action="exponent.php">
    <div>
        Base: <input type="text" name="base" size="10"><br>
        exponent: <input type="text" name="exponent" size="5">
        <input type="submit">
    </div>
</form>
http://localhost/lec4/exponent.php?base=2&exponent=6
```

```php
exponent.php:
<?php
$base = $_GET['base'];
$exp = $_REQUEST['exponent']; // Don't use request
$result = pow($base, $exp);

echo $base .'^'. $exp .'='. $result;
?>
```


Validation:

```php
isset($var) // True if $var has a value
empty($var) // True if NULL, 0, empty string or FALSE
is_numeric($var) // True if $var is a number or numeric string
```


To determine whether the form has been submitted:

```markup
<input type="hidden" name="submitted" value="true">
```


Hashing:

```php
md5($password);
sha1($password);

// check for passwords
$hash = md5($_POST['password']);
if ($row['password'] == $hash) {
    ... 
}
```


For HTML protection against injections:

```php
// in php
<?= htmlspecialchars($name) ?>
```


Uploading files:

```markup
<form action="param.php" method="post" enctype="multipart/form-data">
    Upload image:
    <input type="file" name="pic">
    <input type="submit">
</form>
```

```php
param.php
$name = $_FILES['pic']['name'];
$type = $_FILES['pic']['type'];

// associated methods
is_uploaded_file($filename); // True if the given file was uplaoded by the user
move_uploaded_file($from, $to); // moves from one location to another
```


Cookies:

```php
setcookie(name,[, value, expires, path, domain);
expires - how long will the cookie last
path - determines availability on other web pages on a server
domain - sharing cookies across servers in the same domain

// examples
setcookie('user', 'Mark');
setcookie('user', 'Mark', time() + 3600); // in seconds
setcookie('user', '', time() -3600) // delete this cookie

// retrieving
if (isset($_COOKIE['user'])) {
    $user = $_COOKIE['user'];
} else {
    ...
}
```


Redirection:

```php
header('Location: $url');
```


Session:

```php
session_start(); // open session
$_SESSION['user'] = 'Lucy'; // overwrite/change
unset($_SESSION['user']); // remove that user from session
$_SESSION = array(); // Unset all vars
session_destroy(); // end it all
```
















