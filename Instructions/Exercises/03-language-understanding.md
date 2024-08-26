---
lab:
  title: إنشاء نموذج فهم اللغة باستخدام خدمة لغة الذكاء الاصطناعي في Azure
  module: Module 5 - Create language understanding solutions
---

# إنشاء نموذج فهم اللغة باستخدام خدمة اللغة

> **ملاحظة** ميزة فهم لغة المحادثة الخاصة بخدمة لغة الذكاء الاصطناعي في Azure قيد المعاينة حاليًا، وهي عرضة للتغيير. في بعض الحالات، قد يفشل تدريب النموذج - إذا حدث ذلك، فحاول مرة أخرى.  

تمكنك خدمة لغة الذكاء الاصطناعي في Azure من تحديد نموذج*فهم لغة المحادثة*الذي يمكن للتطبيقات استخدامه لتفسير إدخال اللغة الطبيعية من المستخدمين، والتنبؤ بهدف* المستخدمين *(ما يريدون تحقيقه)، وتحديد أي *كيانات* يجب تطبيق الهدف عليها.

على سبيل المثال، قد يتوقع من نموذج لغة المحادثة لتطبيق الساعة معالجة الإدخال مثل:

*ما الوقت في لندن؟*

هذا النوع من الإدخال هو مثال *للكلام* (شيء قد يقوله المستخدم أو يكتبه)، والذي يكون *الهدف* المطلوب منه هو الحصول على الوقت في موقع معين (*كيان*)؛ في هذه الحالة، لندن.

> **ملاحظة**تتمثل مهمة نموذج لغة المحادثة في توقع هدف المستخدم وتحديد أي كيانات ينطبق الهدف عليها. <u>ليست</u>مهمة نموذج لغة المحادثة هي تنفيذ الإجراءات المطلوبة لتحقيق الهدف فعليًا. على سبيل المثال، يمكن لتطبيق الساعة استخدام نموذج لغة المحادثة لمعرفة أن المستخدم يريد معرفة الوقت في لندن؛ ولكن يجب على تطبيق العميل نفسه بعد ذلك تنفيذ المنطق لتحديد الوقت الصحيح وتقديمه للمستخدم.

## *توفير مورد *لغة الذكاء الاصطناعي في Azure

إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد **خدمة Azure AI Language** في اشتراك Azure لديك.

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
1. في حقل البحث في الأعلى، ابحث عن **خدمات الذكاء الاصطناعي في Azure**. ثم، في النتائج، حدد **إنشاء** ضمن **خدمة اللغة**.
1. حدد **Continue to create your resource**.
1. توفير المورد باستخدام الإعدادات التالية:
    - **الاشتراك**: *اشتراك Azure الخاص بك*.
    - **مجموعة الموارد**: *اختيار مجموعة موارد أو إنشاءها*.
    - **المنطقة**: *اختر أي منطقة متوفرة*
    - **الاسم**: *أدخل اسمًا مميزًا*.
    - **مستوى الأسعار**: حدد **F0** (*مجاني*)، أو **S** (*قياسي*) إذا لم يكن F متوفراً.
    - **إشعار الذكاء الاصطناعي المسؤول**: أوافق.
1. حدد **مراجعة + إنشاء**، ثم حدد **إنشاء** لتوفير المورد.
1. انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.
1. اعرض صفحة **المفاتيح ونقطة النهاية**. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التمرين.

## إنشاء مشروع فهم لغة المحادثة

الآن بعد أن قمت بإنشاء مورد تأليف، يمكنك استخدامه لإنشاء مشروع فهم لغة المحادثة.

1. في علامة تبويب جديدة بالمتصفح، افتح مدخل "استوديو لغة الذكاء الاصطناعي في Azure" في `https://language.cognitive.azure.com/`، ثم سجّل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure خاصتك.

1. إذا طلب منك اختيار مورد Language، حدد الإعدادات التالية:

    - **Azure Directory**: دليل Azure الذي يحتوي على اشتراكك.
    - **Azure subscription**: اشتراك Azure الخاص بك.
    - **نوع المورد**: اللغة.
    - **مورد اللغة**: مورد Azure AI Language الذي أنشأتَه سابقًا.

    إذا <u>لم</u> تتم مطالبتك باختيار مورد language، فقد يرجع ذلك إلى وجود موارد Language متعددة في اشتراكك؛ وفي هذه الحالة:

    1. في الشريط الموجود أعلى الصفحة، حدّد زر **الإعدادات (&#9881;)**.
    2. في الصفحة **Settings** اعرض علامة التبويب **Resources**.
    3. حدد مورد language الذي أنشأته للتو، وانقر فوق **Switch resource**.
    4. في أعلى الصفحة، انقر فوق **استوديو اللغة** للعودة إلى الصفحة الرئيسية في استوديو اللغة

1. في الجزء العلوي من المدخل، في قائمة **Create new**، حدد **Conversational Language Understanding**.

1. في مربع الحوار **إنشاء مشروع**، في الصفحة **أدخل المعلومات الأساسية**، أدخل التفاصيل التالية وانقر فوق **التالي**:
    - **الاسم:** `Clock`
    - **لغة النطق الأساسية**: الإنجليزية
    - **هل تريد تمكين لغات متعددة في المشروع؟**: *تم إلغاء التحديد*
    - **الوصف**: `Natural language clock`

1. في صفحة **مراجعة وإنهاء**، حدد **إنشاء**.

### إنشاء أهداف

أول شيء سنفعله في المشروع الجديد هو تحديد بعض الأهداف. سيتنبأ النموذج في النهاية بأي من هذه الأهداف التي يطلبها المستخدم عند إرسال كلام بلغة طبيعية.

> **تلميح**: عند العمل على مشروعك، إذا تم عرض بعض التلميحات، فاقرأها وحدد **الحصول عليها** أو رفضها، أو حدد **تخطي الكل**.

1. في **صفحة تعريف** المخطط، في **علامة التبويب الأهداف**، حدد **&65291; إضافة** لإضافة هدف جديد يحمل اسم `GetTime`.
1. تحقق من إدراج هدف** GetTime** (جنبًا إلى جنب مع هدف **لا شيء** الافتراضي). ثم أضف الأهداف الإضافية التالية:
    - `GetDay`
    - `GetDate`

### قم بتسمية كل هدف بتعبيرات نموذجية

لمساعدة النموذج على التنبؤ بالهدف الذي يطلبه المستخدم، يجب عليك تسمية كل هدف ببعض التعبيرات النموذجية.

1. في الجزء الموجود على اليسار، حدد صفحة **تسمية البيانات**.

> **تلميح**: يمكنك توسيع الجزء باستخدام الأيقونة **>>** لرؤية أسماء الصفحات وإخفائها مرة أخرى باستخدام الأيقونة **<<**.

1. حدد هدف GetTime** الجديد **وأدخل التعبير `what is the time?`. وهذا يضيف التعبير كإدخال نموذجي للهدف.
1. أضف التعبيرات الإضافية التالية للهدف **GetTime**:
    - `what's the time?`
    - `what time is it?`
    - `tell me the time`

    > **ملاحظة** لإضافة تعبير جديد، اكتب التعبير في مربع النص بجوار الهدف ثم اضغط على إدخال. 

1. حدد هدف** GetDay** وأضف التعبيرات التالية كمثال لإدخال هذا الهدف:
    - `what day is it?`
    - `what's the day?`
    - `what is the day today?`
    - `what day of the week is it?`

1. **حدد هدف GetDate** وأضف التعبيرات التالية له:
    - `what date is it?`
    - `what's the date?`
    - `what is the date today?`
    - `what's today's date?`

1. بعد إضافة تعبيرات لكل هدف من أهدافك، حدد **حفظ التغييرات**.

### تدريب واختبار النموذج

الآن بعد أن أضفت بعض الأهداف، دعنا ندرب نموذج اللغة ونرى ما إذا كان يمكنه التنبؤ بها بشكل صحيح من إدخال المستخدم.

1. حدد **تدريب المهام** من الجزء الموجود على اليسار. ثم حدد ** بدء مهمة تدريب**.

1. في **مربع الحوار بدء مهمة تدريب**، حدد خيار لتدريب نموذج جديد، وقم بتسميته`Clock`. حدد وضع **التدريب القياسي** والخيارات **الافتراضية لتقسيم البيانات**.

1. لبدء عملية تدريب النموذج الخاص بك، حدد **تدريب**.

1. عند اكتمال التدريب (والذي قد يستغرق عدة دقائق) **ستتغير حالة الوظيفة **إلى **نجح التدريب**.

1. حدد صفحة**أداء النموذج**، ثم حدد نموذج**الساعة**. راجع مقاييس التقييم الشاملة ولكل هدف (*الدقة* *والاستدعاء* و*درجة F1*) ومصفوفة * الارتباك*التي تم إنشاؤها بواسطة التقييم الذي تم إجراؤه عند التدريب (لاحظ أنه نظرًا للعدد الصغير من تعبيرات النموذج، لا يمكن تضمين جميع الأهداف في النتائج).

    > **ملاحظة** لمعرفة المزيد حول مقاييس التقييم، راجع [الوثائق](https://learn.microsoft.com/azure/ai-services/language-service/conversational-language-understanding/concepts/evaluation-metrics)

1. انتقل إلى **صفحة نشر النموذج**، ثم حدد **إضافة نشر**.

1. في **مربع الحوار إضافة نشر**، حدد **إنشاء اسم نشر جديد**، ثم أدخل`production`.

1. حدد نموذج**الساعة** في حقل**النموذج** ثم حدد **توزيع**. قد يستغرق التوزيع بعض الوقت.

1. عند نشر النموذج، حدد صفحة **اختبار عمليات النشر** ثم حدد **نشر الإنتاج** في حقل**اسم النشر**.

1. أدخل النص التالي في مربع النص الفارغ، ثم حدد **تشغيل الاختبار**:

    `what's the time now?`

    راجع النتيجة التي تم إرجاعها، مع ملاحظة أنها تتضمن الهدف المتوقع (والذي يجب أن يكون**GetTime**) ودرجة الثقة التي تشير إلى احتمالية قيام النموذج بحساب الهدف المتوقع. تُظهر علامة التبويب JSON الثقة النسبية لكل هدف محتمل (الهدف الذي يتمتع بأعلى درجة ثقة هو الهدف المتوقع)

1. قم بإلغاء تحديد مربع النص، ثم قم بتشغيل اختبار آخر باستخدام النص التالي:

    `tell me the time`

    مرة أخرى، راجع الهدف المتوقع ودرجة الثقة.

1. جرّب النص التالي:

    `what's the day today?`

    نأمل أن يتوقع النموذج بهدف **GetDay**.

## إضافة كيانات

لقد حددت حتى الآن بعض التعبيرات البسيطة التي تتوافق مع الأهداف. تتضمن معظم التطبيقات الأكثر واقعية تعبيرات أكثر تعقيدًا يجب استخراج كيانات بيانات محددة منها للحصول على مزيد من السياق للهدف.

### إضافة كيان متعلم

النوع الأكثر شيوعًا *من الكيانات هو كيان متعلم*، حيث يتعلم النموذج تحديد قيم الكيان استنادًا إلى الأمثلة.

1. في Language Studio، ارجع إلى **صفحة تعريف**المخطط ثم في **علامة التبويب الكيانات**، حدد **&65291; إضافة** لإضافة كيان جديد.

1. في مربع حوار**إضافة كيان**، أدخل اسم الكيان`Location` وتأكد من تحديد علامة تبويب**تعلّم**. ثم حدد **إضافة كيان**.

1. بعد إنشاء كيان **الموقع**، ارجع إلى صفحة **تسمية البيانات**.
1. حدد هدف** GetTime** وأدخل تعبير المثال الجديد التالي:

    `what time is it in London?`

1. عند إضافة التعبير، حدد الكلمة **لندن**، وفي القائمة المنسدلة التي تظهر، حدد **الموقع** للإشارة إلى أن "لندن" وهي مثال على موقع.

1. إضافة مثال آخر على التعبير للهدف **GetTime** :

    `Tell me the time in Paris?`

1. عند إضافة التعبير، حدد الكلمة **باريس**، وقم بتعيينها إلى كيان**الموقع**.

1. إضافة مثال آخر على التعبير للهدف **GetTime** :

    `what's the time in New York?`

1. عند إضافة التعبير، حدد الكلمة **نيويورك**، وقم بتعيينها إلى كيان**الموقع**.

1. حدد **حفظ التغييرات** لحفظ التعبيرات الجديدة.

### إضافة كيان في *القائمة*

في بعض الحالات، يمكن تقييد القيم الصالحة للكيان بقائمة من المصطلحات والمرادفات المحددة؛ والتي يمكن أن تساعد التطبيق في تحديد مثيلات للكيان في التعبيرات.

1. في Language Studio، ارجع إلى **صفحة تعريف**المخطط ثم في **علامة التبويب الكيانات**، حدد **&65291; إضافة** لإضافة كيان جديد.

1. في مربع حوار**إضافة كيان**، أدخل اسم الكيان`Weekday` وحدد علامة تبويب كيان**القائمة**. ثم حدد **إضافة كيان**.

1. في صفحة كيان**يوم عمل**في القسم **تعلّم**تأكد من تحديد **ليس مطلوبًا**. ثم في قسم **القائمة**، حدد **&65291، إضافة قائمة جديدة**. ثم أدخل القيمة والمرادف التالية وحدد **حفظ**:

    | مفتاح القائمة | المرادفات|
    |-------------------|---------|
    | `Sunday` | `Sun` |

    > **ملاحظة** لإدخال حقول القائمة الجديدة، قم بإدراج القيمة `Sunday` في حقل النص، ثم انقر فوق الحقل حيث "Type in value and press enter..." يتم عرضه، وأدخل المرادفات، واضغط على إدخال.

1. كرر الخطوة السابقة لإضافة مكونات القائمة التالية:

    | القيمة‬ | المرادفات|
    |-------------------|---------|
    | `Monday` | `Mon` |
    | `Tuesday` | `Tue, Tues` |
    | `Wednesday` | `Wed, Weds` |
    | `Thursday` | `Thur, Thurs` |
    | `Friday` | `Fri` |
    | `Saturday` | `Sat` |

1. بعد إضافة قيم القائمة وحفظها، ارجع إلى صفحة **تسمية البيانات**.
1. حدد هدف** GetDate** وأدخل تعبير المثال الجديد التالي:

    `what date was it on Saturday?`

1. عند إضافة التعبير، حدد الكلمة ***السبت***، وفي القائمة المنسدلة التي تظهر، حدد **يوم عمل**.

1. إضافة تعبير لمثال آخر للهدف **GetDate**:

    `what date will it be on Friday?`

1. عند إضافة التعبير، قم بتعيين **الجمعة** إلى كيان** يوم عمل**.

1. إضافة تعبير لمثال آخر للهدف **GetDate**:

    `what will the date be on Thurs?`

1. عند إضافة التعبير، قم بتعيين **الخميس** إلى كيان**يوم عمل**.

1. حدد **حفظ التغييرات** لحفظ التعبيرات الجديدة.

### إضافة كيان*تم إنشاؤه مسبقًا*

توفر خدمة لغة الذكاء الاصطناعي في Azure مجموعة من الكيانات *التي تم إنشاؤها مسبقًا* والتي تستخدم عادة في تطبيقات المحادثة.

1. في Language Studio، ارجع إلى **صفحة تعريف**المخطط ثم في **علامة التبويب الكيانات**، حدد **&65291; إضافة** لإضافة كيان جديد.

1. في مربع حوار**إضافة كيان**، أدخل اسم الكيان`Date` وحدد علامة تبويب كيان**تم إنشاؤه مسبقًا**. ثم حدد **إضافة كيان**.

1. في صفحة كيان**التاريخ**في القسم **تعلّم**تأكد من تحديد **ليس مطلوبًا**. ثم، في القسم **تم إنشاؤه مسبقًا**، حدد **&#65291; إضافة كيان** جديد تم إنشاؤه مسبقًا.

1. في القائمة ** تحديد كيان تم إنشاؤه مسبقًا**، حدد**التاريخ والوقت** ثم حدد **حفظ**.
1. بعد إضافة الكيان الذي تم إنشاؤه مسبقًا، ارجع إلى صفحة **تسمية البيانات**
1. حدد هدف** GetDay** وأدخل تعبير المثال الجديد التالي:

    `what day was 01/01/1901?`

1. عند إضافة التعبير، حدد الكلمة ***01/01/1901***، وفي القائمة المنسدلة التي تظهر، حدد **التاريخ**.

1. إضافة تعبير لمثال آخر للهدف **GetDay**:

    `what day will it be on Dec 31st 2099?`

1. عند إضافة التعبير، قم بتعيين **31 ديسمبر 2099** إلى كيان**التاريخ**.

1. حدد **حفظ التغييرات** لحفظ التعبيرات الجديدة.

### إعادة تدريب النموذج

والآن بعد أن قمت بتعديل المخطط، فأنت بحاجة إلى إعادة تدريب النموذج وإعادة اختباره.

1. في صفحة ** وظائف التدريب**، حدد **بدء وظيفة تدريب**.

1. في مربع حوار** بدء وظيفة تدريب**، حدد **الكتابة فوق نموذج موجود** وحدد نموذج **الساعة**. لتدريب النموذج، حدد **تدريب**. إذا طلب منك ذلك، فتأكد من رغبتك في الكتابة فوق النموذج الموجود.

1. عند اكتمال التدريب، سيتم تحديث **حالة**الوظيفة إلى **نجح التدريب**.

1. حدد صفحة**أداء النموذج**، ثم حدد نموذج**الساعة**. راجع مقاييس التقييم (*الدقة* *والاستدعاء* و*درجة F1*) ومصفوفة * الارتباك*التي تم إنشاؤها بواسطة التقييم الذي تم إجراؤه عند التدريب (لاحظ أنه نظرًا للعدد الصغير من تعبيرات النموذج، لا يمكن تضمين جميع الأهداف في النتائج).

1. في صفحة**نشر النموذج**، حدد **إضافة نشر**.

1. في مربع حوار **إضافة نشر**، حدد **تجاوز اسم النشر الموجود**، ثم حدد **إنتاج**.

1. حدد نموذج**الساعة** في حقل**النموذج** ثم حدد **نشر** لنشره. قد يستغرق هذا بعض الوقت.

1. عند نشر النموذج، في صفحة**اختبار عمليات النشر**، حدد نشر**الإنتاج** ضمن حقل**اسم النشر**، ثم اختبره باستخدام النص التالي:

    `what's the time in Edinburgh?`

1. راجع النتيجة التي يتم إرجاعها، والتي نأمل أن تتنبأ **بهدف GetTime** وكيان **الموقع** بالقيمة النصية "Edinburgh".

1. حاول اختبار التعبيرات التالية:

    `what time is it in Tokyo?`

    `what date is it on Friday?`

    `what's the date on Weds?`

    `what day was 01/01/2020?`

    `what day will Mar 7th 2030 be?`

## استخدام النموذج من تطبيق عميل

في مشروع حقيقي، يمكنك تحسين الأهداف والكيانات بشكل متكرر، وإعادة التدريب، وإعادة الاختبار حتى تكون راضيًا عن الأداء التنبؤي. بعد ذلك، عندما تختبره وتكون راضيًا عن أدائه التنبؤي، يمكنك استخدامه في تطبيق عميل عن طريق استدعاء واجهة REST الخاصة به أو SDK الخاص بوقت التشغيل.

### الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية

ستقوم بتطوير تطبيق فهم اللغة باستخدام تعليمة Visual Studio البرمجية. ملفات التعليمات البرمجية متوفرة لتطبيقك في مستودع GitHub.

> **تلميح**: إذا استنسخت بالفعل مستودع **mslearn-ai-language**، فافتحه في Visual Studio code وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-language` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في Visual Studio Code.

    > **ملاحظة**: إذا عرضت لك Visual Studio Code رسالة منبثقة لمطالبتك بالثقة في التعليمات البرمجية التي تفتحها، فانقر فوق **نعم، أثق في خيار الكُتاب** في النافذة المنبثقة.

4. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

### تكوين تطبيقك

تم توفير تطبيقات لكل من C# وPython، وكذلك ملف نصي نموذجي ستستخدمه لاختبار التلخيص. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد لغة الذكاء الاصطناعي في Azure .

1. في تعليمة Visual Studio البرمجية، في جزء **Explorer**، استعرض مجلد **Labfiles/03-language** ووسع نطاق المجلد **CSharp** أو **Python** استناداً إلى تفضيلات اللغة ومجلد **clock-client** الذي يحتوي عليها. يحتوي كل مجلد على الملفات الخاصة باللغة للتطبيق الذي ستقوم بدمج وظيفة الإجابة عن سؤال لغة الذكاء الاصطناعي في Azure فيه.
2. انقر بزر الماوس الأيمن فوق مجلد **clock-client** الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة SDK الخاصة بفهم لغة محادثة لغة الذكاء الاصطناعي في Azure عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#:**

    ```
    dotnet add package Azure.AI.Language.Conversations --version 1.1.0
    ```

    **Python**:

    ```
    pip install azure-ai-language-conversations
    ```

3. في جزء **Explorer**، في مجلد **clock-client**، افتح ملف التكوين للغتك المفضلة

    - **C#**: appsettings.json
    - **Python**: .env
    
4. قم بتحديث قيم التكوين لتضمين **نقطة النهاية** و**مفتاح** من مورد Azure Language الذي أنشأته (متوفر في صفحة **المفاتيح ونقطة النهاية** لمورد لغة الذكاء الاصطناعي في Azure في مدخل Microsoft Azure).
5. احفظ ملف التكوين.

### إضافة تعليمية برمجية إلى التطبيق

أنت الآن جاهز لإضافة التعليمة البرمجية اللازمة لاستيراد مكتبات SDK المطلوبة، وإنشاء اتصال مصادق عليه بمشروعك المنشور، وإرسال الأسئلة.

1. لاحظ أن مجلد **clock-client** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: clock-client.py

    افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:

    **C#**: Programs.cs

    ```c#
    // import namespaces
    using Azure;
    using Azure.AI.Language.Conversations;
    ```

    **Python**: clock-client.py

    ```python
    # Import namespaces
    from azure.core.credentials import AzureKeyCredential
    from azure.ai.language.conversations import ConversationAnalysisClient
    ```

1. في الدالة **الأساسية**، لاحظ أنه جرى بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية التنبؤ والمفتاح من ملف التكوين. ثم ابحث عن التعليق **إنشاء عميل لنموذج خدمة اللغات** وأضف التعليمات البرمجية التالية لإنشاء عميل تنبؤ لتطبيق خدمة اللغات لديك:

    **C#**: Programs.cs

    ```c#
    // Create a client for the Language service model
    Uri endpoint = new Uri(predictionEndpoint);
    AzureKeyCredential credential = new AzureKeyCredential(predictionKey);

    ConversationAnalysisClient client = new ConversationAnalysisClient(endpoint, credential);
    ```

    **Python**: clock-client.py

    ```python
    # Create a client for the Language service model
    client = ConversationAnalysisClient(
        ls_prediction_endpoint, AzureKeyCredential(ls_prediction_key))
    ```

1. لاحظ أن التعليمات البرمجية في الدالة **الرئيسية** تطالب بإدخال المستخدم حتى يدخل المستخدم "إنهاء". ضمن هذا التكرار الحلقي، ابحث عن التعليق **استدعاء نموذج خدمة اللغة للحصول على الهدف والكيانات** وأضف التعليمات البرمجية التالية:

    **C#**: Programs.cs

    ```c#
    // Call the Language service model to get intent and entities
    var projectName = "Clock";
    var deploymentName = "production";
    var data = new
    {
        analysisInput = new
        {
            conversationItem = new
            {
                text = userText,
                id = "1",
                participantId = "1",
            }
        },
        parameters = new
        {
            projectName,
            deploymentName,
            // Use Utf16CodeUnit for strings in .NET.
            stringIndexType = "Utf16CodeUnit",
        },
        kind = "Conversation",
    };
    // Send request
    Response response = await client.AnalyzeConversationAsync(RequestContent.Create(data));
    dynamic conversationalTaskResult = response.Content.ToDynamicFromJson(JsonPropertyNames.CamelCase);
    dynamic conversationPrediction = conversationalTaskResult.Result.Prediction;   
    var options = new JsonSerializerOptions { WriteIndented = true };
    Console.WriteLine(JsonSerializer.Serialize(conversationalTaskResult, options));
    Console.WriteLine("--------------------\n");
    Console.WriteLine(userText);
    var topIntent = "";
    if (conversationPrediction.Intents[0].ConfidenceScore > 0.5)
    {
        topIntent = conversationPrediction.TopIntent;
    }
    ```

    **Python**: clock-client.py

    ```python
    # Call the Language service model to get intent and entities
    cls_project = 'Clock'
    deployment_slot = 'production'

    with client:
        query = userText
        result = client.analyze_conversation(
            task={
                "kind": "Conversation",
                "analysisInput": {
                    "conversationItem": {
                        "participantId": "1",
                        "id": "1",
                        "modality": "text",
                        "language": "en",
                        "text": query
                    },
                    "isLoggingEnabled": False
                },
                "parameters": {
                    "projectName": cls_project,
                    "deploymentName": deployment_slot,
                    "verbose": True
                }
            }
        )

    top_intent = result["result"]["prediction"]["topIntent"]
    entities = result["result"]["prediction"]["entities"]

    print("view top intent:")
    print("\ttop intent: {}".format(result["result"]["prediction"]["topIntent"]))
    print("\tcategory: {}".format(result["result"]["prediction"]["intents"][0]["category"]))
    print("\tconfidence score: {}\n".format(result["result"]["prediction"]["intents"][0]["confidenceScore"]))

    print("view entities:")
    for entity in entities:
        print("\tcategory: {}".format(entity["category"]))
        print("\ttext: {}".format(entity["text"]))
        print("\tconfidence score: {}".format(entity["confidenceScore"]))

    print("query: {}".format(result["result"]["query"]))
    ```

    يؤدي استدعاء نموذج خدمة اللغة إلى إرجاع التنبؤ/النتيجة، والتي تتضمن الهدف الأعلى (الأكثر احتمالاً) بالإضافة إلى أي كيانات تم اكتشافها في تعبيرات الإدخال. يجب أن يستخدم تطبيق العميل الآن هذا التنبؤ لتحديد الإجراء المناسب وتنفيذه.

1. ابحث عن التعليق **تطبيق الإجراء المناسب** وأضف التعليمات البرمجية التالية، التي تتحقق من الأهداف التي يدعمها التطبيق (**GetTime** و **GetDate** و **GetDay**) وتحدد ما إذا تم الكشف عن أي كيانات ذات صلة، قبل استدعاء دالة موجودة لإنتاج استجابة مناسبة.

    **C#**: Programs.cs

    ```c#
    // Apply the appropriate action
    switch (topIntent)
    {
        case "GetTime":
            var location = "local";           
            // Check for a location entity
            foreach (dynamic entity in conversationPrediction.Entities)
            {
                if (entity.Category == "Location")
                {
                    //Console.WriteLine($"Location Confidence: {entity.ConfidenceScore}");
                    location = entity.Text;
                }
            }
            // Get the time for the specified location
            string timeResponse = GetTime(location);
            Console.WriteLine(timeResponse);
            break;
        case "GetDay":
            var date = DateTime.Today.ToShortDateString();            
            // Check for a Date entity
            foreach (dynamic entity in conversationPrediction.Entities)
            {
                if (entity.Category == "Date")
                {
                    //Console.WriteLine($"Location Confidence: {entity.ConfidenceScore}");
                    date = entity.Text;
                }
            }            
            // Get the day for the specified date
            string dayResponse = GetDay(date);
            Console.WriteLine(dayResponse);
            break;
        case "GetDate":
            var day = DateTime.Today.DayOfWeek.ToString();
            // Check for entities            
            // Check for a Weekday entity
            foreach (dynamic entity in conversationPrediction.Entities)
            {
                if (entity.Category == "Weekday")
                {
                    //Console.WriteLine($"Location Confidence: {entity.ConfidenceScore}");
                    day = entity.Text;
                }
            }          
            // Get the date for the specified day
            string dateResponse = GetDate(day);
            Console.WriteLine(dateResponse);
            break;
        default:
            // Some other intent (for example, "None") was predicted
            Console.WriteLine("Try asking me for the time, the day, or the date.");
            break;
    }
    ```

    **Python**: clock-client.py

    ```python
    # Apply the appropriate action
    if top_intent == 'GetTime':
        location = 'local'
        # Check for entities
        if len(entities) > 0:
            # Check for a location entity
            for entity in entities:
                if 'Location' == entity["category"]:
                    # ML entities are strings, get the first one
                    location = entity["text"]
        # Get the time for the specified location
        print(GetTime(location))

    elif top_intent == 'GetDay':
        date_string = date.today().strftime("%m/%d/%Y")
        # Check for entities
        if len(entities) > 0:
            # Check for a Date entity
            for entity in entities:
                if 'Date' == entity["category"]:
                    # Regex entities are strings, get the first one
                    date_string = entity["text"]
        # Get the day for the specified date
        print(GetDay(date_string))

    elif top_intent == 'GetDate':
        day = 'today'
        # Check for entities
        if len(entities) > 0:
            # Check for a Weekday entity
            for entity in entities:
                if 'Weekday' == entity["category"]:
                # List entities are lists
                    day = entity["text"]
        # Get the date for the specified day
        print(GetDate(day))

    else:
        # Some other intent (for example, "None") was predicted
        print('Try asking me for the time, the day, or the date.')
    ```

1. احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد **clock-client** وأدخل الأمر التالي لتشغيل البرنامج:

    - **C#:** `dotnet run`
    - **Python**: `python clock-client.py`

    > **تلميح**: يمكنك استخدام أيقونة **تكبير حجم اللوحة** (**^**) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.

1. عند المطالبة، أدخل التعبيرات لاختبار التطبيق. على سبيل المثال، جرِّب:

    *Hello*

    *كم الساعة؟*

    *ما هو الوقت في لندن؟*

    *ما هو التاريخ؟*

    *ما هو تاريخ يوم الأحد؟*

    *أي يوم هذا اليوم؟*

    *أي يوم الموافق 01/01/2025؟*

    > **ملاحظة**: المنطق في التطبيق بسيط عن عمد، ولديه عدد من القيود. على سبيل المثال، عند الحصول على الوقت، يتم دعم مجموعة مقيدة فقط من المدن ويتم تجاهل التوقيت الصيفي. الهدف هو رؤية مثال على نمط نموذجي لاستخدام خدمة اللغة حيث يجب أن يكون التطبيق الخاص بك:
    >   1. متصلاً بنقطة نهاية التنبؤ.
    >   2. يرسل تعبير للحصول على تنبؤ.
    >   3. ينفذ المنطق للاستجابة بشكل مناسب للهدف والكيانات المتوقعة.

1. عند الانتهاء من الاختبار، أدخل *إنهاء*.

## تنظيف الموارد

إذا انتهيت من استكشاف خدمة Azure AI Language، فيمكنك حذف الموارد التي قمت بإنشائها في هذا التمرين. وإليك الطريقة:

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
2. استعرض للوصول إلى مورد Azure AI Language الذي أنشأته في هذا المختبر.
3. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## مزيد من المعلومات

لمعرفة المزيد حول فهم لغة المحادثة في لغة الذكاء الاصطناعي في Azure راجع [وثائق لغة الذكاء الاصطناعي في Azure](https://learn.microsoft.com/azure/ai-services/language-service/conversational-language-understanding/overview).
