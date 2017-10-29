Username: natas4

URL:      http://natas4.natas.labs.overthewire.org

```html
<div id="content">
There is nothing on this page
<!-- No more information leaks!! Not even Google will find it this time... -->
</div>
```
Hint -> Google wont find it so its disallowed in robots.txt

Lets Check Robots.txt

http://natas3.natas.labs.overthewire.org/robots.txt

```text
User-agent: *
Disallow: /s3cr3t/
```
Lets Check this Directory

http://natas3.natas.labs.overthewire.org/s3cr3t/

it has file called users.txt

```text
natas4:Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ
```
