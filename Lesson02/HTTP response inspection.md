### HTTP response inspection

Use `curl` to inspect HTTP responses on several websites. Notice that most default installations can only request HTTP/1.1.

In case a large body causes too long an output, display only the header with the parameter `--head`.

Analyse the information displayed by the tool.

**Example with added comments**  

`curl -v https://ek.dk`
```
* Host ek.dk:443 was resolved.            # Port for HTTPS (443)
* IPv6: (none)                            # At present Denmark only has around a 20% IPv6 adoption
# However, this IPv4 address is in the address block 20.48.0.0/14 (from 20.48.0.0 to 20.51.255.255),
# which belongs to Microsoft Corporation, specifically to Azure cloud services.
# The server's precise geolocation is uncertain.
* IPv4: 20.50.2.66                        
*   Trying 20.50.2.66:443...              
* schannel: disabled automatic use of client certificate
# Standard versions of curl can only request HTTP/1.1, regardless of the version the server uses
* ALPN: curl offers http/1.1              
* ALPN: server accepted http/1.1
# The local client application is curl. The remote server application is a web server (specified below)
# My local client socket (192.168.0.200:2625) connects to the remote server socket (20.50.2.66:443)
* Established connection to ek.dk (20.50.2.66 port 443) from 192.168.0.200 port 2625
* using HTTP/1.x
> GET / HTTP/1.1
> Host: ek.dk
# The user agent is the client performing the request. It can be a browser, a tool like Postman, or, in this case, curl
> User-Agent: curl/8.16.0                  
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 301 Moved Permanently           # The returned HTTP status code indicates a redirection
< Content-Length: 0
< Date: Wed, 10 Dec 2025 09:14:25 GMT
< Server: Microsoft-IIS/10.0               # The web server is an IIS (Microsoft Internet Information Server)
< Location: https://www.ek.dk/
< Request-Context: appId=cid-v1:b01b66ff-a9ac-40e1-a909-5f16da5837ff
< X-Powered-By: ASP.NET
<
* Connection #0 to host ek.dk:443 left intact
```

Try inspecting several websites from different business areas and supposedly different geolocations.
