# مقدمة
> HTTP: Hyper Text Transfer Protocol


ال HTTP protocol، هو ال protocol المسئول عن الاتصال بين السيرفر والعميل. 

يعمل HTTP protocol على port 80.

آلية العمل: يعمل HTTP protocol عن طريق request من متصفح العميل الى ال web server، ثم يستقبل العميل HTTP response من الserver يحتوي على معلومات حول ال request الذي ارسله.

# القصور في HTTP وظهور HTTPS
عند ارسال HTTP Request الى الserver فانه يرسل محتويات ال Request and Response في صورة plain test بدون أي تشفير، مما يسمح لأي شخص داخل الشبكة برؤية محتوى HTTP Request. مما يعد خطيرا في حالة ارسال credentials او معلومات مالية أو معلومات حساسة الى ال web server او استقبالها مما يعرف باسم Man In The Middle attack لذا ظهر HTTP Secure والذي يرسل ال HTTP request and response في صورة مشفرة
.
يعمل HTTPS protocol على port 443.


# HTTP request and response
## HTTP Request

```HTTP
GET / HTTP/1.1
Host: evil.com
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/146.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Ch-Ua: "Not-A.Brand";v="24", "Chromium";v="146"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
Connection: keep-alive
```
ال HTTP request هو الطلب الذي يرسله متصفح العميل الى الserver.
يتكون ال HTTP request من مكونات أهمها: 
- HTTP Method
- Endpoint  
- HTTP request headers
- HTTP request body
ال HTTP methods هي التي تخبر ال server ماذا تريد ابتداءً، هل تريد طلب صفحة (GET) أم تريد أرسال بيانات الى السيرفر (POST) أم تريد تعديل بيانات (PUT) أم تريد حذف بيانات (DELETE) أم تريد معرفة ال methods المتاحة (OPTIONS) وغيرها من ال HTTP methods.

ال endpoint هي التي تحدد وجهة الطلب، تحدد إلى أي مسار أو directory يذهب اليه ال request على ال web application.

ال HTTP headers تعد من أهم مكونات ال HTTP request، يضعها متصفح العميل ليخبر المتصفح من هو، واللغة التي يدعمها، ونوع الملف المرسل في الطلب، ونوع المتصفح الذي ارسل الطلب، وغيرها من ال http headers المهمة والتي ترسل حسب احتياج ال web application لها.

ال request body هو الجزء الذي يحتوي على البيانات المرسلة الى ال web server سواء كان ال request POST او PUT أو DELETE، فقد يرسل فيه ال credentials، او بيانات شخصية، او ملف صور أو txt عن طريق HTML form، قد يرسل ال request body في صورة JSON، او key=value، كما في ال REST APIs او ك Graph endpoint كما في ال Graph APIs.

## HTTP Response
```HTTP
HTTP/2 200 OK
Server: openresty/1.31.1.1
Date: Sun, 27 Sep 2026 15:07:38 GMT
Content-Type: text/html
Vary: Accept-Encoding
Last-Modified: Mon, 29 Jun 2026 20:39:59 GMT
Etag: W/"f8b-6556a7647936a"
Client-Ip: (null)
Strict-Transport-Security: max-age=31536000
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: "1; mode=block"
Referrer-Policy: no-referrer-when-downgrade
X-Webcom-Cache-Status: BYPASS

<HTML>
	...
</HTML
```

ال HTTP Response هو الرد الذي يرسله الserver الى العميل بناء على طلبه.
يحتوي ال HTTP response على مكونات أساسية أيضا أهمها:
- HTTP response code
- HTTP response headers
- HTTP response body

ال response code هو الذي يحدد حالة الطلب، هل هو مقبول (200) أم أن الصفحة المطلوبه غير متوفرة (404) أم أنك تواجه مشاكل في ال authentication وال authorization بدخولك هذه الصفحة (403,401) أم أن هناك مشكلة في في السيرفر (500)

ام ال response headers فهي تحتوي على headers مخصصة لمعلومات حول ال web server أو ال web application.

وال response body هو الطلب نفسه الذي طلبه المتصفح من السيرفر، قد يتكون من صفحة HTML أو JSON وغيرها.





