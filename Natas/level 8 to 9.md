

```html
<div id="content">


<form method="post">
Input secret: <input name="secret"><br>
<input type="submit" name="submit">
</form>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
```
when we View Source 

```html
<?

$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
    } else {
    print "Wrong secret";
    }
}
?>

<form method=post>
Input secret: <input name=secret><br>
<input type=submit name=submit>
</form>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
```
so we have encodedSecret which we need to decode **bin2hex(strrev(base64_encode($secret)))** using the script below

```php
<?php
$encodedSecret = "3d3d516343746d4d6d6c315669563362";
$decrypt = base64_decode(strrev(hex2bin($encodedSecret)));
echo $decrypt;
?>
```

and here is the password : oubWYf2kBq
