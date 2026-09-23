# تقرير تنفيذ أدوات ispscripts.com — 21 September 2026

## النتيجة

تمت إضافة خمس قدرات عملية إلى الموقع، مع صفحات تفاعلية تعمل بالكامل داخل المتصفح وشرح تحليلي لكل أداة. المخرجات قابلة للنسخ والتنزيل، لكنها لا تُطبق تلقائيًا على أي راوتر ولا ترسل مدخلات المستخدم إلى خادم خارجي.

## الأدوات المنفذة

### MikroTik WireGuard Generator

الصفحة `wireguard.html` تنشئ RouterOS v7 interface وaddress وpeer وWAN firewall rule اختياريًا، إضافة إلى ملف عميل WireGuard. تدعم أوضاع public endpoint وCGNAT client وsite-to-site، وتشرح tunnel addressing وallowed-address وpersistent keepalive وملكية المفاتيح. تترك مفاتيح الإنتاج كـ placeholders عندما لا يقدمها المستخدم بدل توليد مفاتيح وهمية.

### Port Forwarding وdst-nat Planner

الصفحة `port-forwarding.html` تنشئ قاعدة `dst-nat` وقاعدة `forward` مرتبطة بـ `connection-nat-state=dstnat`، مع Hairpin NAT اختياري وتقييد مصدر اختياري. تفحص عناوين `100.64.0.0/10` وتصدر تحذير CGNAT، وتشرح لماذا لا يستطيع JavaScript داخل المتصفح إثبات أن منفذًا واردًا متاح من الإنترنت.

### IPv4 / CIDR / VLSM Expansion

تم توسيع `subnet-calculator.html` بإضافة VLSM planner يوزع الطلبات الأكبر أولًا، يحاذي الكتل على حدودها الصحيحة، ويعرض الشبكة والمدى القابل للاستخدام والبث وحجم الكتلة. أضيف كذلك overlap checker يقارن فترات العناوين بعد تطبيع CIDR ويكشف التداخل الجزئي. تم تحديث `subnet-calculator-guide.html` بشرح عملي لـ VLSM.

### MikroTik QoS وQueue Calculator

الصفحة `qos-calculator.html` تدعم Simple Queue وQueue Tree. تنتج PCQ download وupload منفصلين، وتطلب parent interfaces وpacket marks في وضع Queue Tree بدل افتراضها. كما تشرح اتجاهات upload/download، ومتطلبات Mangle، وتسلسل الاختبار والرجوع.

### WISP Wireless Link Budget

الصفحة `wireless-link-budget.html` تحسب FSPL، مستوى الاستقبال، fade margin، نصف قطر Fresnel في منتصف المسار، وهدف 60% clearance. تعرض المعادلات وحدود الحساب، وتنبه إلى أن التداخل والمطر والمحاذاة والطيف واللوائح تحتاج إلى قياس ميداني.

### صفحة تجميع الأدوات

تم إنشاء `tools.html` لتعريف المستخدم بكل الأدوات واختيار الأداة حسب الحالة العملية. تمت إضافة روابط الأدوات الجديدة إلى قوائم الموقع والصفحة الرئيسية و`sitemap.xml`.

## إصلاحات الفهرسة

كان `sitemap.xml` في النسخة السابقة يحتوي على HTML لصفحة RADIUS بدل XML sitemap صالح. تم إعادة إنشائه كـ XML صالح يضم 28 صفحة، مع تواريخ وتكرار وأولوية مناسبة. تم التحقق من الملف عبر XML parser.

## الاختبار

تم تشغيل فحص JavaScript بواسطة `node --check` على الصفحات التفاعلية الخمس. تم فحص 29 صفحة HTML و28 رابط sitemap ووجدت أداة التحقق صفر أخطاء وصفر تحذيرات. تم التحقق من الروابط المحلية والعناصر المطلوبة في كل أداة بواسطة smoke test مستقل.

تم تشغيل خادم المعاينة محليًا والتحقق من استجابة HTTP 200 للصفحات الجديدة وملف CSS وsitemap، ثم التحقق من الرابط العام للمعاينة. في المتصفح العام، ظهرت الحسابات الافتراضية لـ Wireless Link Budget، وأعيد حسابها حيًا عند تغيير المسافة من 5 إلى 10 كيلومترات. ظهرت كذلك مخرجات WireGuard وdst-nat وQoS وVLSM وفحص التداخل كما هو متوقع.

## الملفات الأساسية المضافة أو المعدلة

| الملف | الغرض |
| --- | --- |
| `toolkit.css` | تنسيق مشترك للصفحات التفاعلية الجديدة |
| `tools.html` | صفحة تجميع الأدوات |
| `wireguard.html` | مولد WireGuard لم MikroTik |
| `port-forwarding.html` | مولد Port Forwarding وdst-nat |
| `qos-calculator.html` | حاسبة QoS وPCQ وQueue Tree |
| `wireless-link-budget.html` | حاسبة Wireless Link Budget |
| `subnet-calculator.html` | إضافة VLSM وفحص التداخل |
| `subnet-calculator-guide.html` | إضافة شرح VLSM |
| `index.html` | إضافة قسم الأدوات الجديدة |
| `changelog.html` | تسجيل إصدار الأدوات |
| `sitemap.xml` | إعادة بناء XML sitemap صالح |

## ملاحظات النشر

قبل اعتماد التغييرات على GitHub Pages، راجع مخرجات RouterOS على نسخة RouterOS الفعلية لديك، واستبدل placeholders الخاصة بالمفاتيح، واختبر كل تغيير مع مسار إدارة بديل أو وصول محلي. لا تجعل Port Forwarding وسيلة الإدارة الأساسية؛ استخدم WireGuard لخدمات الإدارة.
