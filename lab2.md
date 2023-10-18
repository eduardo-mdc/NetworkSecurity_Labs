# Exercise 1

## 1.1 Write a wireshark filter that allows you to filter just the network traffic on the interface that connects
to the Host network, originates on the that machine and is http. Look at the output from a session
accessing the Museu Nacional do Azulejo website. Repeat for Sigarra, during and after authentication
(you can do a bogus login). Can you see any password in transit? Why?

**Wireshark Filter:**

``ip.src == 192.168.0.200 and http``

**Result** (Museu Nacional do Azulejo):
```
POST /ca/gsatlasr3dvtlsca2023q3 HTTP/1.1
Host: ocsp.globalsign.com
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/ocsp-request
Content-Length: 83
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache
```

As we can see, the password is not in transit, because even though the request is made through http, the password is not sent in the request.

```
**Result** (Sigarra, First Page):

POST / HTTP/1.1
Host: geant.ocsp.sectigo.com
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/ocsp-request
Content-Length: 84
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache
```

## Exercise 1.2 Write a wireshark filter that allows you to filter just the network traffic on the interface that connects to the Host network, originates on the that machine and is http. Look at the output from a session accessing the Museu Nacional do Azulejo website. Repeat for Sigarra, during and after authentication (you can do a bogus login). Can you see any password in transit? Why?

### Page loading

```RTÛGºRTÚ}ËE×ÞM@@QeÀ¨Èú¹4P>?¶åGÇö8
Ñ¹%Õ«POST /gts1c3 HTTP/1.1
Host: ocsp.pki.goog
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/ocsp-request
Content-Length: 84
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache

0R0P0N0L0J0	+Ç.yÝÿa4³ºíGB¸»ÆÀ$ct¯ÍîÍ=ÐâFóq5'ËbÄ;Êý3	±:íø¶WÆ
```

```
RTÛGºRTÚ}ËEÚe^@@ØÀ¨Èhe¹:PëIq´ÅÕÙøö:´
³î$ÞìÃSPOST / HTTP/1.1
Host: geant.ocsp.sectigo.com
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/ocsp-request
Content-Length: 84
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache

0R0P0N0L0J0	+Ãýêª¾Þunìn[³ðñ.]o5Il2úY ¼è¾qz¯è÷´F¼GH p{~=N
```

### After Password

``no packets``

### Answer

I can't see any password in transit because the password is not sent through HTTP. Sigarra uses a more advanced protocol (https) that encrypts the data sent in the request.