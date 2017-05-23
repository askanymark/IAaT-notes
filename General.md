# General
### Two-Tier Client/Server Architecture
> A client requests, a server processes that request
- Client
  - Presents an interface to the user
  - Gathers information from the user, submits it  to a server, then receives, formats, and  presents the results returned from the server
- Server
  - Responsible for data storage and management
  - Fulfills a request for information by managing he request or sending the requested information to the client
### Three-Tier Client/Server Architecture
- Client tier
  - User interface tier, such as Web Browser
- Processing tier
  - Handles the interraction between the Web Browser client nd the data storage tier
- Data storage tier
  - Stores data in a database and returns requests presented by he processing tier


# PHP is Server-side scripting
- HTML is static
  - It uses tags that **ONLY **provide instructions to web browsers indicating how to display each stage
  - The server sends the HTML data o the web browser
  - No server-side interpretation occuring
- PHP
  - PHP codes reside on the server
  - Server reads the PHP code and processes it ccording to cripted directions
  - PHP creates an HTML page based on parameters
- **Client-side** **scripting** is a language that runs on a local browser
- **Server-side scripting **programs running on a web server create web pages before sending them back to the requesting web clients
> **NB:** PHP takes longer to process, than HTML


### PHP Functions
1. Names must start with either an **underscore** or a **letter**
1. Function names are case-insensitive
**PSA**: You can add default arguments to functions like this:

```php
function print_separated($str, $separator = ","){
    if(strlen($str) > 0){
        print $str[0];
        for($i=1; $i < strlen($str); $i++){
            print $separator . $str[$i];
        }
    }
}
```


### Injections
Don't enter variables directly into a query!
- use quote() to escape the string before you include it in a query
- alternatively, use try{} and catch{} blocks to keep everything safe
- use <?= htmlspecialchars($var) ?> to escape HTML characters


### States
> HTTP is stateless! Use cookies or sessions!


**Cookies are client-side!**
- A web page script can read the previously tored browser cookie data
- Uses: authentication, user tracking and maintaining user preferences, shopping carts
- Cookies' data cnsists of name and value pairs
- Limitations:
  - User can disable/delete cookies
  - PHP sets limit size on cookies
  - Must be set before HTTP headers are sent
  - Less secure than session
Sessions are server-side!
- Cannot be disabled/deleted by the user
- Serves as a references to the session data
- Sessions are built on top of cookies
# Object-oriented PHP
Classes are just like in Java:

```php
class php_class { ... }
```
- Using a static field/method

```php
ClassName::$name; // outside of class
Self::$name // within
```
- Using a constant field

```php
ClassName::NAME; // outside of class
Self::NAME; // within
```


# MVC
- **Model**: the part of the application which takes data (from any source) and processes it. The model also handles all data access and storage
- **View**: the part of the application which generates the HTML. It is responsible to display the data provided by the model in a specific format
- **Controller**: takes user input and invokes the model to perform the requested operations and sends the data to the View. It does not contain or generate any HTML, pushing that onto the views
![Image](http://php-html.net/tutorials/wp-content/uploads/2009/08/mvc-sequence1.png)
1. Client submits a form
1. Controller receives that form, gets information from the post/get and sends it to the model
1. Model processes it and sends back result
1. Controller passes result to the view to format
1. Formatted result sent back to the controller
1. Controller sends this on to the client browser to display


