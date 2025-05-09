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
  <td><div dir="auto">تصنيف نص مخصص</div></td>
  <td><div dir="auto">Module 3 - Getting Started with Natural Language Processing</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">تصنيف نص مخصص</h1><a id="user-content-تصنيف-نص-مخصص" class="anchor" aria-label="Permalink: تصنيف نص مخصص" href="#تصنيف-نص-مخصص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">توفر خدمة Azure AI Language العديد من قدرات NLP، بما في ذلك تعريف العبارة الرئيسية، وتلخيص النص، وتحليل التوجه. توفر خدمة Language أيضا ميزات مخصصة مثل الإجابة على الأسئلة المخصصة وتصنيف النص المخصص.</p>
<p dir="auto">لاختبار تصنيف النص المخصص لخدمة Azure AI Language، سنقوم بتكوين النموذج باستخدام Language Studio ثم استخدام تطبيق سطر أوامر صغير يعمل في Cloud Shell لاختباره. يمكن اتباع نفس النمط والوظائف المستخدمة هنا لتطبيقات العالم الحقيقي.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">توفير مورد <em>Azure AI Language</em></h2><a id="user-content-توفير-مورد-azure-ai-language" class="anchor" aria-label="Permalink: توفير مورد Azure AI Language" href="#توفير-مورد-azure-ai-language"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد <strong>خدمة Azure AI Language</strong>. بالإضافة إلى ذلك، لاستخدام تصنيف النص المخصص، ينبغي لك تمكين ميزة <strong>تصنيف النص المخصص واستخراجه</strong>.</p>
<ol dir="rtl">
<li>
<p dir="auto">في متصفح، افتح مدخل Microsoft Azure في ⁧<code>https://portal.azure.com</code>⁩، وسجّل الدخول باستخدام حسابك في Microsoft.</p>
</li>
<li>
<p dir="auto">حدد حقل البحث في أعلى المدخل، وابحث عن <code>Azure AI services</code>، وأنشئ <strong>مورد Language Service</strong> .</p>
</li>
<li>
<p dir="auto">حدد المربع الذي يتضمن <strong>تصنيف النص المخصص</strong>. ثم حدد <strong>متابعة لإنشاء المورد الخاص بك</strong>.</p>
</li>
<li>
<p dir="auto">إنشاء المورد بالإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>الاشتراك</strong>: <em>اشتراك Azure الخاص بك</em>.</li>
<li><strong>مجموعة الموارد</strong>: <em>تحديد مجموعة موارد أو إنشاؤها</em>.</li>
<li><strong>المنطقة</strong>: <em>اختر من إحدى المناطق التالية</em>*
<ul dir="rtl">
<li>شرق أستراليا</li>
<li>وسط الهند‬</li>
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
<li><strong>مستوى الأسعار</strong>: حدد <strong>F0</strong> (<em>مجاني</em>) أو <strong>S</strong> (<em>قياسي</em>) إذا لم يكن F متوفراً.</li>
<li><strong>حساب التخزين</strong>: حساب تخزين جديد
<ul dir="rtl">
<li><strong>اسم حساب التخزين</strong>: <em>أدخل اسمًا فريدًا</em>.</li>
<li><strong>نوع حساب التخزين</strong>: LRS قياسي</li>
</ul>
</li>
<li><strong>Responsible AI notice</strong>: محدد.</li>
</ul>
</li>
<li>
<p dir="auto">حدد <strong>مراجعة + إنشاء</strong>، ثم حدد <strong>إنشاء</strong> لتوفير المورد.</p>
</li>
<li>
<p dir="auto">انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</p>
</li>
<li>
<p dir="auto">اعرض صفحة <strong>المفاتيح ونقطة النهاية</strong>. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التدريب.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">أدوار مُستخدمك</h2><a id="user-content-أدوار-مُستخدمك" class="anchor" aria-label="Permalink: أدوار مُستخدمك" href="#أدوار-مُستخدمك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا تخطيت هذه الخطوة، فسوف تحصل على خطأ 403 عند محاولة الاتصال بمشروعك المخصص. من المهم أن يكون لدى مُستخدمك الحالي هذا الدور للوصول إلى بيانات الكائن الثنائي كبير الحجم لحساب التخزين، حتى إذا كنت مالك حساب التخزين.**</p>
</blockquote>
<ol dir="rtl">
<li>انتقل إلى صفحة حساب التخزين في مدخل Azure.</li>
<li>حدد <strong>التحكم في الوصول (IAM)</strong> من قائمة التنقل اليسرى.</li>
<li>حدد <strong>إضافة</strong> لإضافة واجبات الدور واختر دور <strong>مساهم بيانات الكائن الثنائي كبير الحجم للتخزين</strong> في حساب التخزين.</li>
<li>ضمن <strong>تعيين الوصول إلى</strong>، حدد <strong>المستخدم أو المجموعة أو كيان الخدمة</strong>.</li>
<li>حدد <strong>تحديد أعضاء</strong>.</li>
<li>حدد مُستخدمك. يمكنك البحث عن أسماء المستخدمين في الحقل <strong>Select</strong>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تحميل مقالات العينة</h2><a id="user-content-تحميل-مقالات-العينة" class="anchor" aria-label="Permalink: تحميل مقالات العينة" href="#تحميل-مقالات-العينة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بمجرد إنشاء خدمة اللغة وحساب التخزين، ستحتاج إلى تحميل مقالات نموذجية لتدريب نموذجك لاحقا.</p>
<ol dir="rtl">
<li>
<p dir="auto">في علامة تبويب متصفح جديدة، نزّل مقالات عادية من <code>https://aka.ms/classification-articles</code> واستخراج الملفات إلى مجلد من اختيارك.</p>
</li>
<li>
<p dir="auto">في مدخل Microsoft Azure، انتقل إلى حساب التخزين الذي أنشأته، وحدده.</p>
</li>
<li>
<p dir="auto">في حساب التخزين خاصتك، حدد <strong>تكوين</strong>، الموجود أسفل <strong>إعدادات</strong>. في شاشة التكوين، قم بتمكين الخيار** السماح بالوصول المجهول إلى كائن ثنائي الحجم** ثم حدد <strong>حفظ</strong>.</p>
</li>
<li>
<p dir="auto">حدّد <strong>الحاويات</strong> من القائمة اليمنى الموجودة أسفل <strong>تخزين البيانات</strong>. على الشاشة التي تظهر، حدد <strong>+ Container</strong>. امنح الحاوية الاسم <code>articles</code>، وحدّد <strong>مستوى الوصول المجهول</strong> إلى <strong>الحاوية (الوصول المجهول للقراءة فقط للحاويات والكائنات الثنائية كبيرة الحجم)</strong>.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: عند تكوين حساب تخزين لحلّ حقيقي، احرص على تعيين مستوى الوصول المناسب. لمعرفة المزيد حول كل مستوى وصول، راجِع <a href="https://learn.microsoft.com/azure/storage/blobs/anonymous-read-access-configure" rel="nofollow">مستندات Azure Storage</a>.</p>
</blockquote>
</li>
<li>
<p dir="auto">بعد إنشاء الحاوية، حددها ثم حدد زر <strong>تحميل</strong> . حدد <strong>استعراض بحثا عن الملفات</strong> لاستعراض المقالات العادية التي نزلتها. ثم حدد <strong>تحميل</strong>.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء مشروع تصنيف نص مخصص</h2><a id="user-content-إنشاء-مشروع-تصنيف-نص-مخصص" class="anchor" aria-label="Permalink: إنشاء مشروع تصنيف نص مخصص" href="#إنشاء-مشروع-تصنيف-نص-مخصص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بعد اكتمال التكوين، قم بإنشاء مشروع تصنيف نص مخصص. يوفر هذا المشروع مكانا للعمل لبناء نموذجك وتدريبه وتوزيعه.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: يستخدم هذا التمرين المعملي <strong>Language Studio</strong>، ولكن يمكنك أيضا إنشاء نموذجك وبنائه وتدريبه وتوزيعه من خلالREST API.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="auto">في علامة تبويب جديدة بالمتصفح، افتح مدخل « Azure AI Language Studio» في <code>https://language.cognitive.azure.com/</code>، ثم سجّل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure خاصتك.</p>
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
<li>في الشريط الموجود أعلى الصفحة، حدّد زر <strong>الإعدادات (&amp;#9881؛</strong>.</li>
<li>في الصفحة <strong>Settings</strong> اعرض علامة التبويب <strong>Resources</strong>.</li>
<li>حدد مورد language الذي أنشأته للتو، وانقر فوق <strong>Switch resource</strong>.</li>
<li>في أعلى الصفحة، انقر فوق <strong>Language Studio</strong> للعودة إلى الصفحة الرئيسية في Language Studio</li>
</ol>
</li>
<li>
<p dir="auto">في أعلى المدخل، في القائمة <strong>إنشاء جديد</strong>، حدد <strong>تصنيف النصوص المخصصة</strong>.</p>
</li>
<li>
<p dir="auto">تظهر صفحة <strong>توصيل تخزين</strong>. ستكون كافة القيم قد ملئت بالفعل. لذا حدد <strong>التالي</strong>.</p>
</li>
<li>
<p dir="auto">في صفحة <strong>تحديد نوع المشروع</strong>، حدد <strong>تصنيف ملصق مفرد</strong>. بعد ذلك حدد <strong>التالي</strong>.</p>
</li>
<li>
<p dir="auto">في جزء<strong>إدخال المعلومات الأساسية</strong>، ثم عيّن ما يلي:</p>
<ul dir="rtl">
<li><strong>الاسم:</strong> <code>ClassifyLab</code></li>
<li><strong>Text primary language</strong>: English (US)</li>
<li><strong>الوصف</strong>: <code>Custom text lab</code></li>
</ul>
</li>
<li>
<p dir="auto">حدد <strong>التالي</strong>.</p>
</li>
<li>
<p dir="auto">في صفحة <strong>اختيار حاوية</strong>، قم بتعيين القائمة المنسدلة<strong>لحاوية متجر كائن ثنائي الحجم</strong> على حاوية <em>مقالاتك</em>.</p>
</li>
<li>
<p dir="auto">حدد الخيار ** لا، أحتاج إلى تسمية ملفاتي كجزء من هذا المشروع**. بعد ذلك حدد <strong>التالي</strong>.</p>
</li>
<li>
<p dir="auto">حدد <strong>إنشاء مشروع</strong></p>
</li>
</ol>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: إذا ظهر لديك خطأ بشأن عدم تفويضك لتنفيذ هذه العملية، فستحتاج إلى إضافة تعيين دور. لتصحيح ذلك، نقوم بإضافة دور "المساهم ببيانات الكائن الثنائي كبير الحجم للتخزين" على حساب التخزين للمستخدم والذي يقوم بتشغيل النشاط العملي. يمكن العثور على مزيدٍ من التفاصيل في <a href="https://learn.microsoft.com/azure/ai-services/language-service/custom-named-entity-recognition/how-to/create-project?tabs=portal%2Clanguage-studio#enable-identity-management-for-your-resource" rel="nofollow">صفحة الوثائق</a>.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تسمية البيانات</h2><a id="user-content-تسمية-البيانات" class="anchor" aria-label="Permalink: تسمية البيانات" href="#تسمية-البيانات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن تم إنشاء مشروعك، تحتاج إلى تسمية بياناتك أو وضع علامة عليها لتدريب نموذجك على كيفية تصنيف النص.</p>
<ol dir="rtl">
<li>
<p dir="auto">على اليسار، حدد <strong>تسمية البيانات</strong>، إذا لم تكن محددة بالفعل. سترى قائمة بالملفات التي قمت بتحميلها إلى حساب التخزين الخاص بك.</p>
</li>
<li>
<p dir="auto">على الجانب الأيسر، في جزء<strong>النشاط</strong>، حدد <strong>+ إضافة فئة</strong>.  تندرج المقالات في هذا المعمل في أربع فئات ستحتاج إلى إنشائها: <code>Classifieds</code>و <code>Sports</code> و<code>News</code>و <code>Entertainment</code>.</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/tag-data-add-class-new.png#lightbox"><img src="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/tag-data-add-class-new.png#lightbox" alt="لقطة شاشة تعرض صفحة «tag data» وزر «add class»." style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="auto">بعد إنشاء الفئات الأربع، حدد <strong>مقالة 1</strong> للبدء. هنا يمكنك قراءة المقالة، وتحديد الفئة التي يمثلها هذا الملف، ومجموعة البيانات (التدريب أو الاختبار) التي تريد تخصيصها.</p>
</li>
<li>
<p dir="auto">قم بتعيين كل مقالة للفئة المناسبة ومجموعة البيانات (التدريب أو الاختبار) باستخدام جزء <strong>النشاط</strong> على اليمين.  يمكنك تحديد تسمية من قائمة التسميات على اليمين، وتعيين كل مقالة <strong>للتدريب</strong> أو <strong>الاختبار</strong> باستخدام الخيارات الموجودة أسفل جزء النشاط. يمكنك تحديد <strong>المستند التالي</strong>للانتقال إلى المستند التالي. لأغراض هذا المختبر، سنحدد ما الذي سيتم استخدامه لتدريب النموذج واختباره:</p>
<markdown-accessiblity-table data-catalyst=""><table>
<thead>
<tr>
<th>مقالة</th>
<th>الفصل</th>
<th>مجموعة البيانات</th>
</tr>
</thead>
<tbody>
<tr>
<td>Article 1</td>
<td>رياضات</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 10</td>
<td>الأخبار</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 11</td>
<td>الترفيه</td>
<td>الاختبار</td>
</tr>
<tr>
<td>Article 12</td>
<td>الأخبار</td>
<td>الاختبار</td>
</tr>
<tr>
<td>Article 13</td>
<td>رياضات</td>
<td>الاختبار</td>
</tr>
<tr>
<td>Article 2</td>
<td>رياضات</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 3</td>
<td>Classifieds</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 4</td>
<td>Classifieds</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 5</td>
<td>الترفيه</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 6</td>
<td>الترفيه</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 7</td>
<td>الأخبار</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 8</td>
<td>الأخبار</td>
<td>التدريب</td>
</tr>
<tr>
<td>Article 9</td>
<td>الترفيه</td>
<td>التدريب</td>
</tr>
</tbody>
</table></markdown-accessiblity-table>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>يتم سرد الملفات في Language Studio أبجديا، وهذا هو السبب في أن القائمة أعلاه ليست بترتيب تسلسلي. تأكد من زيارة صفحتي المستندات عند تسمية مقالاتك.</p>
</blockquote>
</li>
<li>
<p dir="auto">حدد <strong>حفظ أوصاف</strong> لحفظها.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تدريب النموذج</h2><a id="user-content-تدريب-النموذج" class="anchor" aria-label="Permalink: تدريب النموذج" href="#تدريب-النموذج"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بمجرد تسمية بياناتك، تحتاج إلى تدريب نموذجك.</p>
<ol dir="rtl">
<li>
<p dir="auto">حدد <strong>وظائف تدريب</strong> من القائمة الجانبية اليسرى.</p>
</li>
<li>
<p dir="auto">حدد ** بدء وظيفة تدريب**.</p>
</li>
<li>
<p dir="auto">تدريب نموذج جديد باسم <code>ClassifyArticles</code>.</p>
</li>
<li>
<p dir="auto">حدد <strong>استخدام تقسيم يدوي لبيانات التدريب والاختبار</strong>.</p>
<blockquote>
<p dir="auto"><strong>نصيحة</strong> في مشاريع التصنيف الخاصة بك، ستقوم خدمة Azure AI Language تلقائيا بتقسيم الاختبار الذي تم تعيينه حسب النسبة المئوية وهو أمر مفيد مع مجموعة بيانات كبيرة. مع مجموعات البيانات الأصغر، من المهم التدريب مع توزيع الفئة المناسبة.</p>
</blockquote>
</li>
<li>
<p dir="auto">حدد <strong>Train</strong></p>
</li>
</ol>
<blockquote>
<p dir="auto"><strong>مهم</strong> قد يستغرق تدريب نموذجك عدة دقائق في بعض الأحيان. ستتلقى إعلاما عند اكتماله.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تقييم نموذجك</h2><a id="user-content-تقييم-نموذجك" class="anchor" aria-label="Permalink: تقييم نموذجك" href="#تقييم-نموذجك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في تطبيقات العالم الحقيقي لتصنيف النص، من المهم تقييم نموذجك وتحسينه للتحقق من أدائه كما تتوقع.</p>
<ol dir="rtl">
<li>حدد <strong>Model performance</strong>، وحدد نموذج <strong>ClassifyArticles</strong> خاصتك. ثم يمكنك أن ترى تسجيل النموذج الخاص بك، ومقاييس الأداء، ومتى تم تدريبه. إذا لم يكن تسجيل نموذجك 100%، فهذا يعني أن أحد المستندات المستخدمة للاختبار لم يتم تقييمه إلى ما تم تسميته. يمكن أن تساعدك هذه الإخفاقات على فهم مكان التحسين.</li>
<li>حدد علامة تبويب** تفاصيل مجموعة الاختبار**. إذا كانت هناك أي أخطاء، تُمكِّنك علامة التبويب هذه من الاطّلاع على المقالات التي حددتها للاختبار وما يتوقعه النموذج وما إذا كان ذلك يتعارض مع تسمية الاختبار الخاصة بها. تعين علامة التبويب افتراضيًا لإظهار تنبؤات غير صحيحة فقط. يمكنك تبديل <strong>الخيار إظهار عدم التطابق فقط</strong> لمشاهدة جميع المقالات التي أشرت إليها للاختبار وما توقعه كل منها.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استخدام نموذجك</h2><a id="user-content-استخدام-نموذجك" class="anchor" aria-label="Permalink: استخدام نموذجك" href="#استخدام-نموذجك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بمجرد أن تكون راضيًا عن تدريب النموذج الخاص بك، فقد حان الوقت لتوزيعه والذي يسمح لك بالبدء في تصنيف النص من خلال API.</p>
<ol dir="rtl">
<li>في الجزء إلى اليسار، حدد <strong>نشر نموذج</strong>.</li>
<li>حدد <strong>إضافة نشر</strong>، ثم أدخل <code>articles</code> في <strong>حقل قم بإنشاء اسم نشر جديد</strong>، وحدد <strong>تصنيف مقالات</strong> في حقل <strong>نموذج</strong>.</li>
<li>حدد <strong>نشر</strong> لنشر نموذجك.</li>
<li>بمجرد نشر نموذجك اترك هذه الصفحة مفتوحة. ستكون بحاجة إلى اسم المشروع والنشر في الخطوة التالية.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية</h2><a id="user-content-الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية" href="#الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لاختبار قدرات تصنيف النص المخصصة لخدمةAzure AI Language، ستقوم بتطوير تطبيق وحدة تحكم بسيط في Visual Studio Code.</p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: إذا استنسخت بالفعل مستودع <strong>mslearn-ai-language</strong>، فافتحه في تعليمة Visual Studio. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.</p>
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
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تكوين تطبيقك</h2><a id="user-content-تكوين-تطبيقك" class="anchor" aria-label="Permalink: تكوين تطبيقك" href="#تكوين-تطبيقك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تم توفير تطبيقات لكل من C# وPython، وكذلك ملف نصي نموذجي ستستخدمه لاختبار التلخيص. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد Azure AI Language الخاص بك.</p>
<ol dir="rtl">
<li>
<p dir="auto">في Visual Studio Code، في جزء <strong>مستكشف</strong> ، استعرض للوصول إلى <strong>مجلد Labfiles/04-text-classification</strong> وقم بتوسيع المجلد** CSharp** أو <strong>Python</strong> استنادا إلى تفضيلات اللغة ومجلد <strong>تصنيف نص</strong> الذي يحتوي عليه. يحتوي كل مجلد على الملفات الخاصة باللغة للتطبيق الذي ستقوم بدمج وظيفة تصنيف نص Azure AI Language فيه.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن فوق مجلد <strong>تصنيف نص</strong> الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح وحدة طرفية متكاملة. ثم ثبّت حزمة Azure AI Language Text Analytics SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:</p>
</li>
<p dir="rtl"><strong>C#:</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.AI.TextAnalytics --version 5.3.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.AI.TextAnalytics --version 5.3.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>Python</strong>:</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-ai-textanalytics==5.3.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-ai-textanalytics==5.3.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">في جزء<strong>مستكشف</strong>، في مجلد<strong>تصنيف نص</strong>، افتح ملف التكوين للغة المفضلة لديك</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
</li>
<li>
<p dir="auto">قم بتحديث قيم التكوين لتضمين <strong>نقطة النهاية</strong> و<strong>مفتاح</strong> من مورد Azure Language الذي أنشأته (متوفر في صفحة <strong>المفاتيح ونقطة النهاية</strong> لمورد Azure AI Language في مدخل Microsoft Azure). يجب أن يحتوي الملف بالفعل على أسماء المشروع والنشر لنموذج تصنيف لنصك.</p>
</li>
<li>
<p dir="auto">احفظ ملف التكوين.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمة برمجية لتصنيف المستندات</h2><a id="user-content-إضافة-تعليمة-برمجية-لتصنيف-المستندات" class="anchor" aria-label="Permalink: إضافة تعليمة برمجية لتصنيف المستندات" href="#إضافة-تعليمة-برمجية-لتصنيف-المستندات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أصبحت الآن جاهزًا لاستخدام خدمة Azure AI Language لتصنيف المستندات.</p>
<ol dir="rtl">
<li>
<p dir="auto">قم بتوسيع مجلد ** المقالات** في مجلد<strong>تصنيف نص</strong> لعرض المقالات النصية التي سيصنفها التطبيق الخاص بك.</p>
</li>
<li>
<p dir="auto">في مجلد <strong>تصنيف نص</strong>، افتح ملف التعليمات البرمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: classify-text.py</li>
</ul>
</li>
<li>
<p dir="auto">ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. ومن ثم ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// import namespaces
using Azure;
using Azure.AI.TextAnalytics;</code></pre></div>
<p dir="rtl"><strong>Python</strong>: classify-text.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># import namespaces
from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient</code></pre></div>
<li>
<p dir="auto">في دالة <strong>أساسي</strong>، لاحظ أنه تم بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية خدمة Azure AI Language والمفتاح وأسماء المشروع والتوزيع من ملف التكوين. ثم ابحث عن التعليق <strong>إنشاء عميل باستخدام نقطة النهاية والمفتاح</strong>، وأضف التعليمة البرمجية التالية لإنشاء عميل لواجهة برمجة تطبيقات تحليل النص:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Create client using endpoint and key
AzureKeyCredential credentials = new AzureKeyCredential(aiSvcKey);
Uri endpoint = new Uri(aiSvcEndpoint);
TextAnalyticsClient aiClient = new TextAnalyticsClient(endpoint, credentials);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: classify-text.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-c"><pre><code># Create client using endpoint and key
credential = AzureKeyCredential(ai_key)
ai_client = TextAnalyticsClient(endpoint=ai_endpoint, credential=credential)</code></pre></div>

<li>
<p dir="auto">في الدالة <strong>أساسي</strong>، لاحظ أن التعليمات البرمجية الموجودة تقرأ جميع الملفات في مجلد ** المقالات** وتنشئ قائمة تحتوي على محتوياتها. ثم ابحث عن التعليق <strong>الحصول على تصنيفات</strong> وأضف التعليمات البرمجية التالية:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get Classifications
ClassifyDocumentOperation operation = await aiClient.SingleLabelClassifyAsync(WaitUntil.Completed, batchedDocuments, projectName, deploymentName);

int fileNo = 0;
await foreach (ClassifyDocumentResultCollection documentsInPage in operation.Value)
{
    
    foreach (ClassifyDocumentResult documentResult in documentsInPage)
    {
        Console.WriteLine(files[fileNo].Name);
        if (documentResult.HasError)
        {
            Console.WriteLine($"  Error!");
            Console.WriteLine($"  Document error code: {documentResult.Error.ErrorCode}");
            Console.WriteLine($"  Message: {documentResult.Error.Message}");
            continue;
        }

        Console.WriteLine($"  Predicted the following class:");
        Console.WriteLine();

        foreach (ClassificationCategory classification in documentResult.ClassificationCategories)
        {
            Console.WriteLine($"  Category: {classification.Category}");
            Console.WriteLine($"  Confidence score: {classification.ConfidenceScore}");
            Console.WriteLine();
        }
        fileNo++;
    }
}</code></pre></div>
<p dir="rtl"><strong>Python</strong>: classify-text.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get Classifications
operation = ai_client.begin_single_label_classify(
    batchedDocuments,
    project_name=project_name,
    deployment_name=deployment_name
)

document_results = operation.result()

for doc, classification_result in zip(files, document_results):
    if classification_result.kind == "CustomDocumentClassification":
        classification = classification_result.classifications[0]
        print("{} was classified as '{}' with confidence score {}.".format(
            doc, classification.category, classification.confidence_score)
        )
    elif classification_result.is_error is True:
        print("{} has an error with code '{}' and message '{}'".format(
            doc, classification_result.error.code, classification_result.error.message)
        )</code></pre></div>
<li>
<p dir="auto">احفظ التغييرات في ملف التعليمات البرمجية خاصتك.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">اختبار التطبيق الخاص بك</h2><a id="user-content-اختبار-التطبيق-الخاص-بك" class="anchor" aria-label="Permalink: اختبار التطبيق الخاص بك" href="#اختبار-التطبيق-الخاص-بك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أصبح الآن تطبيقك جاهزًا للاختبار.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الوحدة الطرفية المتكاملة لمجلد <strong>تصنيف نص</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
<ul dir="rtl">
<li><strong>C#:</strong> <code>dotnet run</code></li>
<li><strong>Python</strong>: <code>python classify-text.py</code></li>
</ul>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: يمكنك استخدام أيقونة <strong>تكبير حجم اللوحة</strong> (<strong>^</strong>) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.</p>
</blockquote>
</li>
<li>
<p dir="auto">مراقبة المخرجات. يجب أن يسرد التطبيق تصنيفا ودرجة ثقة لكل ملف نصي.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف</h2><a id="user-content-تنظيف" class="anchor" aria-label="Permalink: تنظيف" href="#تنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">عندما لا تحتاج إلى مشروعك بعد الآن، يمكنك حذفه من صفحة <strong>Projects</strong>الخاصة بك في Language Studio. يمكنك أيضا إزالة خدمة Azure AI Language وحساب التخزين المقترن في <a href="https://portal.azure.com" rel="nofollow">مدخل Microsoft Azure</a>.</p>
</article>
</div>
</div>
