توضيح لآلية عمل ال HTTP قبل الشروع ال WebSocket، ال HTTP هو بروتوكول Request/Response، مما يعني أن السيرفر لا يمكنه بدء اتصال الا بعد وصول request من المستخدم.
تجارب لإنشاء live chat:
قديما، قبل ظهور ال WebSocket كان الإعتماد على HTTP بشكل كلي في التواصل بين السيرفر والمستخدم، فكان المستخدم يحتاج إلى إرسال Request لاستقبال Response من السيرفر. مما يعني أنه اذا احتاج مستخدم ان يطلع على أحدث الرسائل، كان يجب عليه ارسال request وهو ما كان يعرف ال HTTP Polling والذي كان يرسل Requests تلقائيا لجلب الرسائل الجديدة من السيرفر، مما يؤدي الى هدر كبير في ال Requests، فتم ابتكار طريقة جديدة تعرف باسم HTTP long Polling وهي الأقرب لل WebSocket تقوم بارسال Request والسيرفر يقوم بتعليقها حتى يتلقى رسالة جديدة من المستخدم الاخر ثم يرسل ال response الى المستخدم الأول.

الـ WebSocket بروتوكول حديث ظهر في 2011، بعد نجاح الـ HTTP handshake (اللي بيبدأه العميل دايمًا)، بيبقى السيرفر قادر **يبدأ يبعت بيانات** من غير ما يستنى request جديد من العميل — وده الفرق الجوهري عن HTTP العادي.
آلية العمل تتم عن طريق HTTP handshake:
Steps:

1. Opening handshake: HTTP request and HTTP response.
2. Frame-based message exchange: data, ping and pong messages.
3. Closing handshake: close message (request then echoed in response).

يقوم المستخدم بارسال Request يطلب فيه من السيرفر ترقية البروتوكول المستخدم الى WebSocket بدلا من HTTP، ثم يرد السيرفر ب 101 Switching Protocols في حالة نجاح الاتصال، بعد نجاح ال handshake يتوقف استخدام HTTP وتحويله الى ال WebSocket.
يعمل WebSocket فوق بروتوكول HTTP و HTTPS مما يعني أنه يستخدم نفس ال ports. يستخدم 80 لل `ws` و 443 لل `wss`.

شكل ال request:
```http
GET /chat HTTP/1.1
Host: server.example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Origin: http://example.com
Sec-WebSocket-Protocol: chat, superchat
Sec-WebSocket-Version: 13
```
ملاحظة: الـ `Origin` header بيتبعت تلقائيًا مع كل WebSocket handshake، والدفاع الأساسي ضد CSWSH هو إن السيرفر يتحقق منه صراحة عند الـ handshake — الفحص ده مش تلقائي زي CORS، فلو المطوّر نساه، الثغرة موجودة.

شكل ال response:
```http
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
Sec-WebSocket-Protocol: chat
```

يستخدم بروتوكول WebSocket ال `ws` أو `wss` كـ URL scheme.
ال `ws` ينقل البيانات في صورة plain text وال `wss` ينقل البيانات بصورة مشفرة.
