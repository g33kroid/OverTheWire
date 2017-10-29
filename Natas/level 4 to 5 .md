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
