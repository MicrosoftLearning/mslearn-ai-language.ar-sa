<div class="Box-sc-g0xbh4-0 eoaCFS js-snippet-clipboard-copy-unpositioned undefined" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div dir="rtl"><markdown-accessiblity-table data-catalyst=""><table>
  <thead>
  <tr>
  <th>lab</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto"><table>
  <thead>
  <tr>
  <th>title</th>
  <th>module</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto">إنشاء نموذج فهم اللغة باستخدام خدمة لغة الذكاء الاصطناعي في Azure</div></td>
  <td><div dir="auto">Module 5 - Create language understanding solutions</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">إنشاء نموذج فهم اللغة باستخدام خدمة اللغة</h1><a id="user-content-إنشاء-نموذج-فهم-اللغة-باستخدام-خدمة-اللغة" class="anchor" aria-label="Permalink: إنشاء نموذج فهم اللغة باستخدام خدمة اللغة" href="#إنشاء-نموذج-فهم-اللغة-باستخدام-خدمة-اللغة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong> ميزة فهم لغة المحادثة الخاصة بخدمة لغة الذكاء الاصطناعي في Azure قيد المعاينة حاليًا، وهي عرضة للتغيير. في بعض الحالات، قد يفشل تدريب النموذج - إذا حدث ذلك، فحاول مرة أخرى.</p>
</blockquote>
<p dir="auto">تمكنك خدمة لغة الذكاء الاصطناعي في Azure من تحديد نموذج<em>فهم لغة المحادثة</em>الذي يمكن للتطبيقات استخدامه لتفسير إدخال اللغة الطبيعية من المستخدمين، والتنبؤ بهدف* المستخدمين *(ما يريدون تحقيقه)، وتحديد أي <em>كيانات</em> يجب تطبيق الهدف عليها.</p>
<p dir="auto">على سبيل المثال، قد يتوقع من نموذج لغة المحادثة لتطبيق الساعة معالجة الإدخال مثل:</p>
<p dir="auto"><em>ما الوقت في لندن؟</em></p>
<p dir="auto">هذا النوع من الإدخال هو مثال <em>للكلام</em> (شيء قد يقوله المستخدم أو يكتبه)، والذي يكون <em>الهدف</em> المطلوب منه هو الحصول على الوقت في موقع معين (<em>كيان</em>)؛ في هذه الحالة، لندن.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>تتمثل مهمة نموذج لغة المحادثة في توقع هدف المستخدم وتحديد أي كيانات ينطبق الهدف عليها. ليستمهمة نموذج لغة المحادثة هي تنفيذ الإجراءات المطلوبة لتحقيق الهدف فعليًا. على سبيل المثال، يمكن لتطبيق الساعة استخدام نموذج لغة المحادثة لمعرفة أن المستخدم يريد معرفة الوقت في لندن؛ ولكن يجب على تطبيق العميل نفسه بعد ذلك تنفيذ المنطق لتحديد الوقت الصحيح وتقديمه للمستخدم.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">*توفير مورد *لغة الذكاء الاصطناعي في Azure</h2><a id="user-content-توفير-مورد-لغة-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: *توفير مورد *لغة الذكاء الاصطناعي في Azure" href="#توفير-مورد-لغة-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد <strong>خدمة Azure AI Language</strong> في اشتراك Azure لديك.</p>
<ol dir="rtl">
<li>افتح مدخل Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</li>
<li>في حقل البحث في الأعلى، ابحث عن <strong>خدمات الذكاء الاصطناعي في Azure</strong>. ثم، في النتائج، حدد <strong>إنشاء</strong> ضمن <strong>خدمة اللغة</strong>.</li>
<li>حدد <strong>Continue to create your resource</strong>.</li>
<li>توفير المورد باستخدام الإعدادات التالية:
<ul dir="rtl">
<li><strong>الاشتراك</strong>: <em>اشتراك Azure الخاص بك</em>.</li>
<li><strong>مجموعة الموارد</strong>: <em>اختيار مجموعة موارد أو إنشاءها</em>.</li>
<li><strong>المنطقة</strong>: <em>اختر من إحدى المناطق التالية</em>*
<ul dir="rtl">
<li>شرق أستراليا</li>
<li>وسط الهند‬</li>
<li>منطقة شرق الصين 2</li>
<li>شرق الولايات المتحدة</li>
<li>East US 2</li>
<li>أوروبا الشمالية</li>
<li>South Central US</li>
<li>شمال سويسرا</li>
<li>جنوب المملكة المتحدة</li>
<li>أوروبا الغربية</li>
<li>West US 2</li>
<li>غرب الولايات المتحدة الأمريكية 3</li>
</ul>
</li>
<li><strong>الاسم</strong>: <em>أدخل اسمًا مميزًا</em>.</li>
<li><strong>مستوى الأسعار</strong>: حدد <strong>F0</strong> (<em>مجاني</em>)، أو <strong>S</strong> (<em>قياسي</em>) إذا لم يكن F متوفراً.</li>
<li><strong>إشعار الذكاء الاصطناعي المسؤول</strong>: أوافق.</li>
</ul>
</li>
<li>حدد <strong>مراجعة + إنشاء</strong>، ثم حدد <strong>إنشاء</strong> لتوفير المورد.</li>
<li>انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</li>
<li>اعرض صفحة <strong>المفاتيح ونقطة النهاية</strong>. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التمرين.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء مشروع فهم لغة المحادثة</h2><a id="user-content-إنشاء-مشروع-فهم-لغة-المحادثة" class="anchor" aria-label="Permalink: إنشاء مشروع فهم لغة المحادثة" href="#إنشاء-مشروع-فهم-لغة-المحادثة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن قمت بإنشاء مورد تأليف، يمكنك استخدامه لإنشاء مشروع فهم لغة المحادثة.</p>
<ol dir="rtl">
<li>
<p dir="auto">في علامة تبويب جديدة بالمتصفح، افتح مدخل "استوديو لغة الذكاء الاصطناعي في Azure" في <code>https://language.cognitive.azure.com/</code>، ثم سجّل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure خاصتك.</p>
</li>
<li>
<p dir="auto">إذا طلب منك اختيار مورد Language، حدد الإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>Azure Directory</strong>: دليل Azure الذي يحتوي على اشتراكك.</li>
<li><strong>Azure subscription</strong>: اشتراك Azure الخاص بك.</li>
<li><strong>نوع المورد</strong>: اللغة.</li>
<li><strong>مورد اللغة</strong>: مورد Azure AI Language الذي أنشأتَه سابقًا.</li>
</ul>
<p dir="auto">إذا لم تتم مطالبتك باختيار مورد language، فقد يرجع ذلك إلى وجود موارد Language متعددة في اشتراكك؛ وفي هذه الحالة:</p>
<ol dir="rtl">
<li>في الشريط الموجود أعلى الصفحة، حدّد زر <strong>الإعدادات (⚙)</strong>.</li>
<li>في الصفحة <strong>Settings</strong> اعرض علامة التبويب <strong>Resources</strong>.</li>
<li>حدد مورد language الذي أنشأته للتو، وانقر فوق <strong>Switch resource</strong>.</li>
<li>في أعلى الصفحة، انقر فوق <strong>استوديو اللغة</strong> للعودة إلى الصفحة الرئيسية في استوديو اللغة</li>
</ol>
</li>
<li>
<p dir="auto">في الجزء العلوي من المدخل، في قائمة <strong>Create new</strong>، حدد <strong>Conversational Language Understanding</strong>.</p>
</li>
<li>
<p dir="auto">في مربع الحوار <strong>إنشاء مشروع</strong>، في الصفحة <strong>أدخل المعلومات الأساسية</strong>، أدخل التفاصيل التالية وانقر فوق <strong>التالي</strong>:</p>
<ul dir="rtl">
<li><strong>الاسم:</strong> <code>Clock</code></li>
<li><strong>لغة النطق الأساسية</strong>: الإنجليزية</li>
<li><strong>هل تريد تمكين لغات متعددة في المشروع؟</strong>: <em>تم إلغاء التحديد</em></li>
<li><strong>الوصف</strong>: <code>Natural language clock</code></li>
</ul>
</li>
<li>
<p dir="auto">في صفحة <strong>مراجعة وإنهاء</strong>، حدد <strong>إنشاء</strong>.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إنشاء أهداف</h3><a id="user-content-إنشاء-أهداف" class="anchor" aria-label="Permalink: إنشاء أهداف" href="#إنشاء-أهداف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أول شيء سنفعله في المشروع الجديد هو تحديد بعض الأهداف. سيتنبأ النموذج في النهاية بأي من هذه الأهداف التي يطلبها المستخدم عند إرسال كلام بلغة طبيعية.</p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: عند العمل على مشروعك، إذا تم عرض بعض التلميحات، فاقرأها وحدد <strong>الحصول عليها</strong> أو رفضها، أو حدد <strong>تخطي الكل</strong>.</p>
</blockquote>
<ol dir="rtl">
<li>في <strong>صفحة تعريف</strong> المخطط، في <strong>علامة التبويب الأهداف</strong>، حدد <strong>&amp;65291; إضافة</strong> لإضافة هدف جديد يحمل اسم <code>GetTime</code>.</li>
<li>تحقق من إدراج هدف** GetTime** (جنبًا إلى جنب مع هدف <strong>لا شيء</strong> الافتراضي). ثم أضف الأهداف الإضافية التالية:
<ul dir="rtl">
<li><code>GetDay</code></li>
<li><code>GetDate</code></li>
</ul>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">قم بتسمية كل هدف بتعبيرات نموذجية</h3><a id="user-content-قم-بتسمية-كل-هدف-بتعبيرات-نموذجية" class="anchor" aria-label="Permalink: قم بتسمية كل هدف بتعبيرات نموذجية" href="#قم-بتسمية-كل-هدف-بتعبيرات-نموذجية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لمساعدة النموذج على التنبؤ بالهدف الذي يطلبه المستخدم، يجب عليك تسمية كل هدف ببعض التعبيرات النموذجية.</p>
<ol dir="rtl">
<li>في الجزء الموجود على اليسار، حدد صفحة <strong>تسمية البيانات</strong>.</li>
</ol>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: يمكنك توسيع الجزء باستخدام الأيقونة <strong>&gt;&gt;</strong> لرؤية أسماء الصفحات وإخفائها مرة أخرى باستخدام الأيقونة <strong>&lt;&lt;</strong>.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="auto">حدد هدف GetTime** الجديد **وأدخل التعبير <code>what is the time?</code>. وهذا يضيف التعبير كإدخال نموذجي للهدف.</p>
</li>
<li>
<p dir="auto">أضف التعبيرات الإضافية التالية للهدف <strong>GetTime</strong>:</p>
<ul dir="rtl">
<li><code>what's the time?</code></li>
<li><code>what time is it?</code></li>
<li><code>tell me the time</code></li>
</ul>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong> لإضافة تعبير جديد، اكتب التعبير في مربع النص بجوار الهدف ثم اضغط على إدخال.</p>
</blockquote>
</li>
<li>
<p dir="auto">حدد هدف** GetDay** وأضف التعبيرات التالية كمثال لإدخال هذا الهدف:</p>
<ul dir="rtl">
<li><code>what day is it?</code></li>
<li><code>what's the day?</code></li>
<li><code>what is the day today?</code></li>
<li><code>what day of the week is it?</code></li>
</ul>
</li>
<li>
<p dir="auto"><strong>حدد هدف GetDate</strong> وأضف التعبيرات التالية له:</p>
<ul dir="rtl">
<li><code>what date is it?</code></li>
<li><code>what's the date?</code></li>
<li><code>what is the date today?</code></li>
<li><code>what's today's date?</code></li>
</ul>
</li>
<li>
<p dir="auto">بعد إضافة تعبيرات لكل هدف من أهدافك، حدد <strong>حفظ التغييرات</strong>.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">تدريب واختبار النموذج</h3><a id="user-content-تدريب-واختبار-النموذج" class="anchor" aria-label="Permalink: تدريب واختبار النموذج" href="#تدريب-واختبار-النموذج"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أضفت بعض الأهداف، دعنا ندرب نموذج اللغة ونرى ما إذا كان يمكنه التنبؤ بها بشكل صحيح من إدخال المستخدم.</p>
<ol dir="rtl">
<li>
<p dir="auto">حدد <strong>تدريب المهام</strong> من الجزء الموجود على اليسار. ثم حدد ** بدء مهمة تدريب**.</p>
</li>
<li>
<p dir="auto">في <strong>مربع الحوار بدء مهمة تدريب</strong>، حدد خيار لتدريب نموذج جديد، وقم بتسميته<code>Clock</code>. حدد وضع <strong>التدريب القياسي</strong> والخيارات <strong>الافتراضية لتقسيم البيانات</strong>.</p>
</li>
<li>
<p dir="auto">لبدء عملية تدريب النموذج الخاص بك، حدد <strong>تدريب</strong>.</p>
</li>
<li>
<p dir="auto">عند اكتمال التدريب (والذي قد يستغرق عدة دقائق) **ستتغير حالة الوظيفة **إلى <strong>نجح التدريب</strong>.</p>
</li>
<li>
<p dir="auto">حدد صفحة<strong>أداء النموذج</strong>، ثم حدد نموذج<strong>الساعة</strong>. راجع مقاييس التقييم الشاملة ولكل هدف (<em>الدقة</em> <em>والاستدعاء</em> و<em>درجة F1</em>) ومصفوفة * الارتباك*التي تم إنشاؤها بواسطة التقييم الذي تم إجراؤه عند التدريب (لاحظ أنه نظرًا للعدد الصغير من تعبيرات النموذج، لا يمكن تضمين جميع الأهداف في النتائج).</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong> لمعرفة المزيد حول مقاييس التقييم، راجع <a href="https://learn.microsoft.com/azure/ai-services/language-service/conversational-language-understanding/concepts/evaluation-metrics" rel="nofollow">الوثائق</a></p>
</blockquote>
</li>
<li>
<p dir="auto">انتقل إلى <strong>صفحة نشر النموذج</strong>، ثم حدد <strong>إضافة نشر</strong>.</p>
</li>
<li>
<p dir="auto">في <strong>مربع الحوار إضافة نشر</strong>، حدد <strong>إنشاء اسم نشر جديد</strong>، ثم أدخل<code>production</code>.</p>
</li>
<li>
<p dir="auto">حدد نموذج<strong>الساعة</strong> في حقل<strong>النموذج</strong> ثم حدد <strong>توزيع</strong>. قد يستغرق التوزيع بعض الوقت.</p>
</li>
<li>
<p dir="auto">عند نشر النموذج، حدد صفحة <strong>اختبار عمليات النشر</strong> ثم حدد <strong>نشر الإنتاج</strong> في حقل<strong>اسم النشر</strong>.</p>
</li>
<li>
<p dir="auto">أدخل النص التالي في مربع النص الفارغ، ثم حدد <strong>تشغيل الاختبار</strong>:</p>
<p dir="auto"><code>what's the time now?</code></p>
<p dir="auto">راجع النتيجة التي تم إرجاعها، مع ملاحظة أنها تتضمن الهدف المتوقع (والذي يجب أن يكون<strong>GetTime</strong>) ودرجة الثقة التي تشير إلى احتمالية قيام النموذج بحساب الهدف المتوقع. تُظهر علامة التبويب JSON الثقة النسبية لكل هدف محتمل (الهدف الذي يتمتع بأعلى درجة ثقة هو الهدف المتوقع)</p>
</li>
<li>
<p dir="auto">قم بإلغاء تحديد مربع النص، ثم قم بتشغيل اختبار آخر باستخدام النص التالي:</p>
<p dir="auto"><code>tell me the time</code></p>
<p dir="auto">مرة أخرى، راجع الهدف المتوقع ودرجة الثقة.</p>
</li>
<li>
<p dir="auto">جرّب النص التالي:</p>
<p dir="auto"><code>what's the day today?</code></p>
<p dir="auto">نأمل أن يتوقع النموذج بهدف <strong>GetDay</strong>.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة كيانات</h2><a id="user-content-إضافة-كيانات" class="anchor" aria-label="Permalink: إضافة كيانات" href="#إضافة-كيانات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لقد حددت حتى الآن بعض التعبيرات البسيطة التي تتوافق مع الأهداف. تتضمن معظم التطبيقات الأكثر واقعية تعبيرات أكثر تعقيدًا يجب استخراج كيانات بيانات محددة منها للحصول على مزيد من السياق للهدف.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إضافة كيان متعلم</h3><a id="user-content-إضافة-كيان-متعلم" class="anchor" aria-label="Permalink: إضافة كيان متعلم" href="#إضافة-كيان-متعلم"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">النوع الأكثر شيوعًا <em>من الكيانات هو كيان متعلم</em>، حيث يتعلم النموذج تحديد قيم الكيان استنادًا إلى الأمثلة.</p>
<ol dir="rtl">
<li>
<p dir="auto">في Language Studio، ارجع إلى <strong>صفحة تعريف</strong>المخطط ثم في <strong>علامة التبويب الكيانات</strong>، حدد <strong>&amp;65291; إضافة</strong> لإضافة كيان جديد.</p>
</li>
<li>
<p dir="auto">في مربع حوار<strong>إضافة كيان</strong>، أدخل اسم الكيان<code>Location</code> وتأكد من تحديد علامة تبويب<strong>تعلّم</strong>. ثم حدد <strong>إضافة كيان</strong>.</p>
</li>
<li>
<p dir="auto">بعد إنشاء كيان <strong>الموقع</strong>، ارجع إلى صفحة <strong>تسمية البيانات</strong>.</p>
</li>
<li>
<p dir="auto">حدد هدف** GetTime** وأدخل تعبير المثال الجديد التالي:</p>
<p dir="auto"><code>what time is it in London?</code></p>
</li>
<li>
<p dir="auto">عند إضافة التعبير، حدد الكلمة <strong>لندن</strong>، وفي القائمة المنسدلة التي تظهر، حدد <strong>الموقع</strong> للإشارة إلى أن "لندن" وهي مثال على موقع.</p>
</li>
<li>
<p dir="auto">إضافة مثال آخر على التعبير للهدف <strong>GetTime</strong> :</p>
<p dir="auto"><code>Tell me the time in Paris?</code></p>
</li>
<li>
<p dir="auto">عند إضافة التعبير، حدد الكلمة <strong>باريس</strong>، وقم بتعيينها إلى كيان<strong>الموقع</strong>.</p>
</li>
<li>
<p dir="auto">إضافة مثال آخر على التعبير للهدف <strong>GetTime</strong> :</p>
<p dir="auto"><code>what's the time in New York?</code></p>
</li>
<li>
<p dir="auto">عند إضافة التعبير، حدد الكلمة <strong>نيويورك</strong>، وقم بتعيينها إلى كيان<strong>الموقع</strong>.</p>
</li>
<li>
<p dir="auto">حدد <strong>حفظ التغييرات</strong> لحفظ التعبيرات الجديدة.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إضافة كيان في <em>القائمة</em></h3><a id="user-content-إضافة-كيان-في-القائمة" class="anchor" aria-label="Permalink: إضافة كيان في القائمة" href="#إضافة-كيان-في-القائمة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في بعض الحالات، يمكن تقييد القيم الصالحة للكيان بقائمة من المصطلحات والمرادفات المحددة؛ والتي يمكن أن تساعد التطبيق في تحديد مثيلات للكيان في التعبيرات.</p>
<ol dir="rtl">
<li>
<p dir="auto">في Language Studio، ارجع إلى <strong>صفحة تعريف</strong>المخطط ثم في <strong>علامة التبويب الكيانات</strong>، حدد <strong>&amp;65291; إضافة</strong> لإضافة كيان جديد.</p>
</li>
<li>
<p dir="auto">في مربع حوار<strong>إضافة كيان</strong>، أدخل اسم الكيان<code>Weekday</code> وحدد علامة تبويب كيان<strong>القائمة</strong>. ثم حدد <strong>إضافة كيان</strong>.</p>
</li>
<li>
<p dir="auto">في صفحة كيان<strong>يوم عمل</strong>في القسم <strong>تعلّم</strong>تأكد من تحديد <strong>ليس مطلوبًا</strong>. ثم في قسم <strong>القائمة</strong>، حدد <strong>&amp;65291، إضافة قائمة جديدة</strong>. ثم أدخل القيمة والمرادف التالية وحدد <strong>حفظ</strong>:</p>
<markdown-accessiblity-table data-catalyst=""><table>
<thead>
<tr>
<th>مفتاح القائمة</th>
<th>المرادفات</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Sunday</code></td>
<td><code>Sun</code></td>
</tr>
</tbody>
</table></markdown-accessiblity-table>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong> لإدخال حقول القائمة الجديدة، قم بإدراج القيمة <code>Sunday</code> في حقل النص، ثم انقر فوق الحقل حيث "Type in value and press enter..." يتم عرضه، وأدخل المرادفات، واضغط على إدخال.</p>
</blockquote>
</li>
<li>
<p dir="auto">كرر الخطوة السابقة لإضافة مكونات القائمة التالية:</p>
<markdown-accessiblity-table data-catalyst=""><table>
<thead>
<tr>
<th>القيمة‬</th>
<th>المرادفات</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Monday</code></td>
<td><code>Mon</code></td>
</tr>
<tr>
<td><code>Tuesday</code></td>
<td><code>Tue, Tues</code></td>
</tr>
<tr>
<td><code>Wednesday</code></td>
<td><code>Wed, Weds</code></td>
</tr>
<tr>
<td><code>Thursday</code></td>
<td><code>Thur, Thurs</code></td>
</tr>
<tr>
<td><code>Friday</code></td>
<td><code>Fri</code></td>
</tr>
<tr>
<td><code>Saturday</code></td>
<td><code>Sat</code></td>
</tr>
</tbody>
</table></markdown-accessiblity-table>
</li>
<li>
<p dir="auto">بعد إضافة قيم القائمة وحفظها، ارجع إلى صفحة <strong>تسمية البيانات</strong>.</p>
</li>
<li>
<p dir="auto">حدد هدف** GetDate** وأدخل تعبير المثال الجديد التالي:</p>
<p dir="auto"><code>what date was it on Saturday?</code></p>
</li>
<li>
<p dir="auto">عند إضافة التعبير، حدد الكلمة <em><strong>السبت</strong></em>، وفي القائمة المنسدلة التي تظهر، حدد <strong>يوم عمل</strong>.</p>
</li>
<li>
<p dir="auto">إضافة تعبير لمثال آخر للهدف <strong>GetDate</strong>:</p>
<p dir="auto"><code>what date will it be on Friday?</code></p>
</li>
<li>
<p dir="auto">عند إضافة التعبير، قم بتعيين <strong>الجمعة</strong> إلى كيان** يوم عمل**.</p>
</li>
<li>
<p dir="auto">إضافة تعبير لمثال آخر للهدف <strong>GetDate</strong>:</p>
<p dir="auto"><code>what will the date be on Thurs?</code></p>
</li>
<li>
<p dir="auto">عند إضافة التعبير، قم بتعيين <strong>الخميس</strong> إلى كيان<strong>يوم عمل</strong>.</p>
</li>
<li>
<p dir="auto">حدد <strong>حفظ التغييرات</strong> لحفظ التعبيرات الجديدة.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إضافة كيان<em>تم إنشاؤه مسبقًا</em></h3><a id="user-content-إضافة-كيانتم-إنشاؤه-مسبقًا" class="anchor" aria-label="Permalink: إضافة كيانتم إنشاؤه مسبقًا" href="#إضافة-كيانتم-إنشاؤه-مسبقًا"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">توفر خدمة لغة الذكاء الاصطناعي في Azure مجموعة من الكيانات <em>التي تم إنشاؤها مسبقًا</em> والتي تستخدم عادة في تطبيقات المحادثة.</p>
<ol dir="rtl">
<li>
<p dir="auto">في Language Studio، ارجع إلى <strong>صفحة تعريف</strong>المخطط ثم في <strong>علامة التبويب الكيانات</strong>، حدد <strong>&amp;65291; إضافة</strong> لإضافة كيان جديد.</p>
</li>
<li>
<p dir="auto">في مربع حوار<strong>إضافة كيان</strong>، أدخل اسم الكيان<code>Date</code> وحدد علامة تبويب كيان<strong>تم إنشاؤه مسبقًا</strong>. ثم حدد <strong>إضافة كيان</strong>.</p>
</li>
<li>
<p dir="auto">في صفحة كيان<strong>التاريخ</strong>في القسم <strong>تعلّم</strong>تأكد من تحديد <strong>ليس مطلوبًا</strong>. ثم، في القسم <strong>تم إنشاؤه مسبقًا</strong>، حدد <strong>＋ إضافة كيان</strong> جديد تم إنشاؤه مسبقًا.</p>
</li>
<li>
<p dir="auto">في القائمة ** تحديد كيان تم إنشاؤه مسبقًا**، حدد<strong>التاريخ والوقت</strong> ثم حدد <strong>حفظ</strong>.</p>
</li>
<li>
<p dir="auto">بعد إضافة الكيان الذي تم إنشاؤه مسبقًا، ارجع إلى صفحة <strong>تسمية البيانات</strong></p>
</li>
<li>
<p dir="auto">حدد هدف** GetDay** وأدخل تعبير المثال الجديد التالي:</p>
<p dir="auto"><code>what day was 01/01/1901?</code></p>
</li>
<li>
<p dir="auto">عند إضافة التعبير، حدد الكلمة <em><strong>01/01/1901</strong></em>، وفي القائمة المنسدلة التي تظهر، حدد <strong>التاريخ</strong>.</p>
</li>
<li>
<p dir="auto">إضافة تعبير لمثال آخر للهدف <strong>GetDay</strong>:</p>
<p dir="auto"><code>what day will it be on Dec 31st 2099?</code></p>
</li>
<li>
<p dir="auto">عند إضافة التعبير، قم بتعيين <strong>31 ديسمبر 2099</strong> إلى كيان<strong>التاريخ</strong>.</p>
</li>
<li>
<p dir="auto">حدد <strong>حفظ التغييرات</strong> لحفظ التعبيرات الجديدة.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إعادة تدريب النموذج</h3><a id="user-content-إعادة-تدريب-النموذج" class="anchor" aria-label="Permalink: إعادة تدريب النموذج" href="#إعادة-تدريب-النموذج"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">والآن بعد أن قمت بتعديل المخطط، فأنت بحاجة إلى إعادة تدريب النموذج وإعادة اختباره.</p>
<ol dir="rtl">
<li>
<p dir="auto">في صفحة ** وظائف التدريب**، حدد <strong>بدء وظيفة تدريب</strong>.</p>
</li>
<li>
<p dir="auto">في مربع حوار** بدء وظيفة تدريب**، حدد <strong>الكتابة فوق نموذج موجود</strong> وحدد نموذج <strong>الساعة</strong>. لتدريب النموذج، حدد <strong>تدريب</strong>. إذا طلب منك ذلك، فتأكد من رغبتك في الكتابة فوق النموذج الموجود.</p>
</li>
<li>
<p dir="auto">عند اكتمال التدريب، سيتم تحديث <strong>حالة</strong>الوظيفة إلى <strong>نجح التدريب</strong>.</p>
</li>
<li>
<p dir="auto">حدد صفحة<strong>أداء النموذج</strong>، ثم حدد نموذج<strong>الساعة</strong>. راجع مقاييس التقييم (<em>الدقة</em> <em>والاستدعاء</em> و<em>درجة F1</em>) ومصفوفة * الارتباك*التي تم إنشاؤها بواسطة التقييم الذي تم إجراؤه عند التدريب (لاحظ أنه نظرًا للعدد الصغير من تعبيرات النموذج، لا يمكن تضمين جميع الأهداف في النتائج).</p>
</li>
<li>
<p dir="auto">في صفحة<strong>نشر النموذج</strong>، حدد <strong>إضافة نشر</strong>.</p>
</li>
<li>
<p dir="auto">في مربع حوار <strong>إضافة نشر</strong>، حدد <strong>تجاوز اسم النشر الموجود</strong>، ثم حدد <strong>إنتاج</strong>.</p>
</li>
<li>
<p dir="auto">حدد نموذج<strong>الساعة</strong> في حقل<strong>النموذج</strong> ثم حدد <strong>نشر</strong> لنشره. قد يستغرق هذا بعض الوقت.</p>
</li>
<li>
<p dir="auto">عند نشر النموذج، في صفحة<strong>اختبار عمليات النشر</strong>، حدد نشر<strong>الإنتاج</strong> ضمن حقل<strong>اسم النشر</strong>، ثم اختبره باستخدام النص التالي:</p>
<p dir="auto"><code>what's the time in Edinburgh?</code></p>
</li>
<li>
<p dir="auto">راجع النتيجة التي يتم إرجاعها، والتي نأمل أن تتنبأ <strong>بهدف GetTime</strong> وكيان <strong>الموقع</strong> بالقيمة النصية "Edinburgh".</p>
</li>
<li>
<p dir="auto">حاول اختبار التعبيرات التالية:</p>
<p dir="auto"><code>what time is it in Tokyo?</code></p>
<p dir="auto"><code>what date is it on Friday?</code></p>
<p dir="auto"><code>what's the date on Weds?</code></p>
<p dir="auto"><code>what day was 01/01/2020?</code></p>
<p dir="auto"><code>what day will Mar 7th 2030 be?</code></p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استخدام النموذج من تطبيق عميل</h2><a id="user-content-استخدام-النموذج-من-تطبيق-عميل" class="anchor" aria-label="Permalink: استخدام النموذج من تطبيق عميل" href="#استخدام-النموذج-من-تطبيق-عميل"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في مشروع حقيقي، يمكنك تحسين الأهداف والكيانات بشكل متكرر، وإعادة التدريب، وإعادة الاختبار حتى تكون راضيًا عن الأداء التنبؤي. بعد ذلك، عندما تختبره وتكون راضيًا عن أدائه التنبؤي، يمكنك استخدامه في تطبيق عميل عن طريق استدعاء واجهة REST الخاصة به أو SDK الخاص بوقت التشغيل.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية</h3><a id="user-content-الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية" href="#الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">ستقوم بتطوير تطبيق فهم اللغة باستخدام تعليمة Visual Studio البرمجية. ملفات التعليمات البرمجية متوفرة لتطبيقك في مستودع GitHub.</p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: إذا استنسخت بالفعل مستودع <strong>mslearn-ai-language</strong>، فافتحه في Visual Studio code وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="auto">ابدأ تشغيل Visual Studio Code.</p>
</li>
<li>
<p dir="auto">افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع <code>https://github.com/MicrosoftLearning/mslearn-ai-language</code> إلى مجلد محلي (لا يُهم أي مجلد).</p>
</li>
<li>
<p dir="auto">عند استنساخ المستودع، افتح المجلد في Visual Studio Code.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا عرضت لك Visual Studio Code رسالة منبثقة لمطالبتك بالثقة في التعليمات البرمجية التي تفتحها، فانقر فوق <strong>نعم، أثق في خيار الكُتاب</strong> في النافذة المنبثقة.</p>
</blockquote>
</li>
<li>
<p dir="auto">انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد <strong>ليس الآن</strong>.</p>
</blockquote>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">تكوين تطبيقك</h3><a id="user-content-تكوين-تطبيقك" class="anchor" aria-label="Permalink: تكوين تطبيقك" href="#تكوين-تطبيقك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تم توفير تطبيقات لكل من C# وPython، وكذلك ملف نصي نموذجي ستستخدمه لاختبار التلخيص. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد لغة الذكاء الاصطناعي في Azure .</p>
<ol dir="rtl">
<li>
<p dir="auto">في تعليمة Visual Studio البرمجية، في جزء <strong>Explorer</strong>، استعرض مجلد <strong>Labfiles/03-language</strong> ووسع نطاق المجلد <strong>CSharp</strong> أو <strong>Python</strong> استناداً إلى تفضيلات اللغة ومجلد <strong>clock-client</strong> الذي يحتوي عليها. يحتوي كل مجلد على الملفات الخاصة باللغة للتطبيق الذي ستقوم بدمج وظيفة الإجابة عن سؤال لغة الذكاء الاصطناعي في Azure فيه.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن فوق مجلد <strong>clock-client</strong> الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة SDK الخاصة بفهم لغة محادثة لغة الذكاء الاصطناعي في Azure عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:</p>
</li>
<p dir="rtl"><strong>:#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.AI.Language.Conversations --version 1.1.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.AI.Language.Conversations --version 1.1.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>Python</strong>:</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-ai-language-conversations
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-ai-language-conversations" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">في جزء <strong>Explorer</strong>، في مجلد <strong>clock-client</strong>، افتح ملف التكوين للغتك المفضلة</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
</li>
<li>
<p dir="auto">قم بتحديث قيم التكوين لتضمين <strong>نقطة النهاية</strong> و<strong>مفتاح</strong> من مورد Azure Language الذي أنشأته (متوفر في صفحة <strong>المفاتيح ونقطة النهاية</strong> لمورد لغة الذكاء الاصطناعي في Azure في مدخل Microsoft Azure).</p>
</li>
<li>
<p dir="auto">احفظ ملف التكوين.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمية برمجية إلى التطبيق</h3><a id="user-content-إضافة-تعليمية-برمجية-إلى-التطبيق" class="anchor" aria-label="Permalink: إضافة تعليمية برمجية إلى التطبيق" href="#إضافة-تعليمية-برمجية-إلى-التطبيق"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أنت الآن جاهز لإضافة التعليمة البرمجية اللازمة لاستيراد مكتبات SDK المطلوبة، وإنشاء اتصال مصادق عليه بمشروعك المنشور، وإرسال الأسئلة.</p>
<ol dir="rtl">
<li>
<p dir="auto">لاحظ أن مجلد <strong>clock-client</strong> يحتوي على ملف تعليمات برمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: clock-client.py</li>
</ul>
<p dir="auto">افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// import namespaces
using Azure;
using Azure.AI.Language.Conversations;</code></pre></div>
<p dir="rtl"><strong>Python</strong>: clock-client.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Import namespaces
from azure.core.credentials import AzureKeyCredential
from azure.ai.language.conversations import ConversationAnalysisClient</code></pre></div>
<li>
<p dir="auto">في الدالة <strong>الأساسية</strong>، لاحظ أنه جرى بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية التنبؤ والمفتاح من ملف التكوين. ثم ابحث عن التعليق <strong>إنشاء عميل لنموذج خدمة اللغات</strong> وأضف التعليمات البرمجية التالية لإنشاء عميل تنبؤ لتطبيق خدمة اللغات لديك:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Create a client for the Language service model
Uri endpoint = new Uri(predictionEndpoint);
AzureKeyCredential credential = new AzureKeyCredential(predictionKey);
<br>
ConversationAnalysisClient client = new ConversationAnalysisClient(endpoint, credential);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: clock-client.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Create a client for the Language service model
client = ConversationAnalysisClient(
    ls_prediction_endpoint, AzureKeyCredential(ls_prediction_key))</code></pre></div>
<li>
<p dir="auto">لاحظ أن التعليمات البرمجية في الدالة <strong>الرئيسية</strong> تطالب بإدخال المستخدم حتى يدخل المستخدم "إنهاء". ضمن هذا التكرار الحلقي، ابحث عن التعليق <strong>استدعاء نموذج خدمة اللغة للحصول على الهدف والكيانات</strong> وأضف التعليمات البرمجية التالية:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Call the Language service model to get intent and entities
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
}</code></pre></div>
<p dir="rtl"><strong>Python</strong>: clock-client.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Call the Language service model to get intent and entities
cls_project = 'Clock'
deployment_slot = 'production'
<br>
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
<br>
top_intent = result["result"]["prediction"]["topIntent"]
entities = result["result"]["prediction"]["entities"]
<br>
print("view top intent:")
print("\ttop intent: {}".format(result["result"]["prediction"]["topIntent"]))
print("\tcategory: {}".format(result["result"]["prediction"]["intents"][0]["category"]))
print("\tconfidence score: {}\n".format(result["result"]["prediction"]["intents"][0]["confidenceScore"]))
<br>
print("view entities:")
for entity in entities:
    print("\tcategory: {}".format(entity["category"]))
    print("\ttext: {}".format(entity["text"]))
    print("\tconfidence score: {}".format(entity["confidenceScore"]))
<br>
print("query: {}".format(result["result"]["query"]))</code></pre></div>
<p dir="auto">يؤدي استدعاء نموذج خدمة اللغة إلى إرجاع التنبؤ/النتيجة، والتي تتضمن الهدف الأعلى (الأكثر احتمالاً) بالإضافة إلى أي كيانات تم اكتشافها في تعبيرات الإدخال. يجب أن يستخدم تطبيق العميل الآن هذا التنبؤ لتحديد الإجراء المناسب وتنفيذه.</p>

<li>
<p dir="auto">ابحث عن التعليق <strong>تطبيق الإجراء المناسب</strong> وأضف التعليمات البرمجية التالية، التي تتحقق من الأهداف التي يدعمها التطبيق (<strong>GetTime</strong> و <strong>GetDate</strong> و <strong>GetDay</strong>) وتحدد ما إذا تم الكشف عن أي كيانات ذات صلة، قبل استدعاء دالة موجودة لإنتاج استجابة مناسبة.</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Apply the appropriate action
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
}</code></pre></div>
<p dir="rtl"><strong>Python</strong>: clock-client.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Apply the appropriate action
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
    print('Try asking me for the time, the day, or the date.')</code></pre></div>

<li>
<p dir="auto">احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد <strong>clock-client</strong> وأدخل الأمر التالي لتشغيل البرنامج:</p>
<ul dir="rtl">
<li><strong>:#C</strong> <code>dotnet run</code></li>
<li><strong>Python</strong>: <code>python clock-client.py</code></li>
</ul>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: يمكنك استخدام أيقونة <strong>تكبير حجم اللوحة</strong> (<strong>^</strong>) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.</p>
</blockquote>
</li>
<li>
<p dir="auto">عند المطالبة، أدخل التعبيرات لاختبار التطبيق. على سبيل المثال، جرِّب:</p>
<p dir="auto"><em>Hello</em></p>
<p dir="auto"><em>كم الساعة؟</em></p>
<p dir="auto"><em>ما هو الوقت في لندن؟</em></p>
<p dir="auto"><em>ما هو التاريخ؟</em></p>
<p dir="auto"><em>ما هو تاريخ يوم الأحد؟</em></p>
<p dir="auto"><em>أي يوم هذا اليوم؟</em></p>
<p dir="auto"><em>أي يوم الموافق 01/01/2025؟</em></p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: المنطق في التطبيق بسيط عن عمد، ولديه عدد من القيود. على سبيل المثال، عند الحصول على الوقت، يتم دعم مجموعة مقيدة فقط من المدن ويتم تجاهل التوقيت الصيفي. الهدف هو رؤية مثال على نمط نموذجي لاستخدام خدمة اللغة حيث يجب أن يكون التطبيق الخاص بك:</p>
<ol dir="rtl">
<li>متصلاً بنقطة نهاية التنبؤ.</li>
<li>يرسل تعبير للحصول على تنبؤ.</li>
<li>ينفذ المنطق للاستجابة بشكل مناسب للهدف والكيانات المتوقعة.</li>
</ol>
</blockquote>
</li>
<li>
<p dir="auto">عند الانتهاء من الاختبار، أدخل <em>إنهاء</em>.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف الموارد</h2><a id="user-content-تنظيف-الموارد" class="anchor" aria-label="Permalink: تنظيف الموارد" href="#تنظيف-الموارد"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا انتهيت من استكشاف خدمة Azure AI Language، فيمكنك حذف الموارد التي قمت بإنشائها في هذا التمرين. وإليك الطريقة:</p>
<ol dir="rtl">
<li>افتح مدخل Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</li>
<li>استعرض للوصول إلى مورد Azure AI Language الذي أنشأته في هذا المختبر.</li>
<li>في صفحة المورد، حدد <strong>حذف</strong> واتبع الإرشادات لحذف المورد.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لمعرفة المزيد حول فهم لغة المحادثة في لغة الذكاء الاصطناعي في Azure راجع <a href="https://learn.microsoft.com/azure/ai-services/language-service/conversational-language-understanding/overview" rel="nofollow">وثائق لغة الذكاء الاصطناعي في Azure</a>.</p>
</article>
</div>
</div>
