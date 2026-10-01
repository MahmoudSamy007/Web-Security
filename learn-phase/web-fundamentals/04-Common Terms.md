# الـ Proxy

يكون بين المستخدم والسيرفر، وظيفته باختصار أنه يكلم السيرفر نيابة عن المستخدم وبعد كدا يستقبل الرد من السيرفر ويوصله للمستخدم من غير ما يعرف السيرفر هو بيكلم مين.

له نوعين Forward proxy and revers proxy
ال Forward proxy هو النوع اللي اتكلمنا عنه في المقدمه، بحيث ان ال proxy server هو اللي بيتعامل مع العالم الخارجي(الانترنت) ويبعت ويستقبل الرسائل نيابة عن المستخدم، والسيرفر يكون مفكر انه بيكلم ال IP بتاع الproxy server السيرفر بيشوف بس IP البروكسي، ومش عارف إن فيه مستخدم حقيقي واقف وراه. البروكسي هو اللي بيوصّل رد السيرفر للمستخدم في الآخر.
ال forward proxy قد يكون مفيد أيضا في ال caching، حيث يخزن ال websites بصورة مؤقته واذا احتاجها مستخدم اخر داخل الشبكة يرسلها له اسرع من احضارها من الانترنت.
النوع الثاني وهو ال revers proxy وهو عكس ال forward proxy، المستخدم مش عارف هو بيكلم مين، المستخدم بيبعت request لسيرفر معين `example.com` وبعد ما ال proxy server دا يستقبل الطلب يبدأ هو يوجهه الى web server، يبقا المستخدم مفكر أنه بيكلم ال IP بتاع ال web server لكنه في الواقع بيكلم ال proxy server.

في الrevers proxy بعد ما ال proxy server يستقبل الطلب ويبدأ يوجهه الى internal network بيستخدم غالبا HTTP مش HTTPS، هو نظريا استخدام HTTPS ءأمن لمنع هجمات MITM في حالة ال internal network مش أمان 100%، لكن بسبب أن الserver بتستهلك موارد أكبر في فك تشفير ومعالجة HTTPS request، فالشركات  غالبا بستخدم HTTP على اعتبار ان الشبكة آمنة.

تطبيق عملي على ال Proxy في ال web security:
لو شركة بتستخدم proxy ممكن تضيف ال `X-Forwarded-For` ، الheader دا وظيفته تقول لل server انت جاي من IP ايه، ممكن تقول للserver انك جاي من ال internal network، لا في بعض الاحيان مش بيبقا في validation.

---
# الـ CDN
CDN = Content Delivery Network
ال CDN هي خدمه تقوم بنسخ وتوزيع ال Assets ال statics الخاصة بالموقع الاكتروني في سيرفرات حول العالم. 
الهدف منها الوصول الى ال assets من مناطق مختلفة حول العالم في اسرع وقت ممكن، لان المسافة بين المستخدم والweb server تؤثر على سرعة تحميل الموقع.
make websites faster by bringing websites content closer to user.

تعمل الCDNs عن طريق POP (Point Of Presence)، حيث تخزن ال POPs ال Cache الخاصة بال web server لاحضار الassetes الخاصة بالموقع أقرب الى المستخدم
مميزات ال CDN:
- توفر من ال Network bandwidth على ال web server الاصلي في حالة وجود الملايين من الزوار عليه، ولكن بتوزيع الحمل على CDNs مختلفة، فان ال Network bandwidth على ال web server يقل.
- توفر Availability and redundancy للموقع، حيث في حالة وقوع اي سيرفر من سيرفرات ال CDN يتم اللجوء الى اقرب CDN اخر
- تحمي ال web server الاساسي من DDOS attacks.

حاليا ال CDN بيشتغل ك Revers proxy وبيبقا هو اللي بيتواصل مع العميل ويستقبل الرد من السيرفر ويحوله للعميل. طيب ممكن المستخدم يقدر يوصل لل IP الحقيقي عن طريق:
1. DNS History
2. Subdomains
3. SSL Certificate Transparency Logs
4. Email headers
5. SSRF Attack

مشكلة أمنيه كمان في ال CDN، ثغرة ال Web Cache Deception / Cache Poisoning، ان ال CDN يحتفظ بصفحة فيها بيانات حساسة واي مستخدمها يطلبها بعد كدا تتبعت له وهو مش authorized لمجرد انها محفوظه على ال CDN.
نقدر نمنع دا عن طريق ان السيرفر يحط لل للendpoints المهمة `Cache-Control: private`, `Cache-Control: no-store` header.  نستخدم `private` لو عايزين الصفحة تتخزن في متصفح المستخدم و `no-store` لو مش عايز اخزن الصفحة خالص.
ويحط `Cache-Control: public, max-age=86400` header للصور وملفات ال CSS.

---
# الـ WAF
WAF = Web Application Firewall
هو جدار حماية لل web application يعمل على مستوى ال application layer، على عكس ال firewall العادي اللي بيعمل على مستوى ال network، حيث ان ال firewall العادي يقدر يراقب مين ال IPs اللي مسموحله يعدي وبأي port يتصل، لكن ال WAF وظيفته يكتشف الأنماط الشهير للثغرات عن طريق تحليل ال headers وال parameters وال request body عشان يمنع أي request فيه payload خبيث وال.

---
