[Switch Servers](Server-List#switch) > Connection Test
---

This server is used to check if the internet connection is working when you connect to a wifi network.

The server supports both HTTP and HTTPS. The Switch uses the former.

If HTTPS is used, the server certificate is signed by `Nintendo Class 2 CA - G3`.

The following request is sent to the server by the Switch:

```http
GET / HTTP/1.1
Host: ctest.cdn.nintendo.net
User-Agent: NX NIFM/00
Accept: */*
Connection: keep-alive
```

The server replies with the following response:

```http
HTTP/1.1 200 OK
Content-Length: 2
Expires: Mon, 05 Apr 2021 14:52:05 GMT
Cache-Control: max-age=0, no-cache, no-store
Pragma: no-cache
Date: Mon, 05 Apr 2021 14:52:05 GMT
Connection: keep-alive
X-Organization: Nintendo
Content-Type: text/plain

ok
```

If the user agent does not start with `NX NIFM/` the server sends the following response instead:

```http
HTTP/1.1 403 Forbidden
Server: AkamaiGHost
Mime-Version: 1.0
Content-Type: text/html
Content-Length: 275
Expires: Mon, 05 Apr 2021 14:53:52 GMT
Date: Mon, 05 Apr 2021 14:53:52 GMT
Connection: keep-alive

<HTML><HEAD>
<TITLE>Access Denied</TITLE>
</HEAD><BODY>
<H1>Access Denied</H1>
 
You don't have permission to access "http&#58;&#47;&#47;ctest&#46;cdn&#46;nintendo&#46;net&#47;" on this server.<P>
Reference&#32;&#35;18&#46;3faf3554&#46;1617634432&#46;da3d018
</BODY>
</HTML>
```