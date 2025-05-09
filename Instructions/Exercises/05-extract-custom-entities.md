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
  <td><div dir="auto">استخراج الكيانات المخصصة</div></td>
  <td><div dir="auto">Module 3 - Getting Started with Natural Language Processing</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">استخراج الكيانات المخصصة</h1><a id="user-content-استخراج-الكيانات-المخصصة" class="anchor" aria-label="Permalink: استخراج الكيانات المخصصة" href="#استخراج-الكيانات-المخصصة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بالإضافة إلى إمكانيات معالجة اللغة الطبيعية الأخرى، تُمكّنك "خدمة لغة الذكاء الاصطناعي في Azure" من تعريف وحدات مخصصة، واستخراج مثيلات لها من النص.</p>
<p dir="auto">لاختبار استخراج الوحدة المخصصة، سنُنشئ نموذجًا ونُدربه من خلال "ستوديو لغة الذكاء الاصطناعي في Azure"، ثم نستخدم تطبيقًا لسطر الأوامر لاختباره.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">*توفير مورد *لغة الذكاء الاصطناعي في Azure</h2><a id="user-content-توفير-مورد-لغة-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: *توفير مورد *لغة الذكاء الاصطناعي في Azure" href="#توفير-مورد-لغة-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد <strong>خدمة Azure AI Language</strong>. بالإضافة إلى ذلك، لاستخدام تصنيف النص المخصص، ينبغي لك تمكين ميزة <strong>تصنيف النص المخصص واستخراجه</strong>.</p>
<ol dir="rtl">
<li>
<p dir="auto">في متصفح، افتح مدخل Microsoft Azure في ⁧<code>https://portal.azure.com</code>⁩، وسجّل الدخول باستخدام حسابك في Microsoft.</p>
</li>
<li>
<p dir="auto">حدد زر <strong>إنشاء مورد</strong>، وابحث عن <em>اللغة</em>، وأنشئ مورد <strong>خدمة اللغة</strong>. عند التواجد على صفحة <em>تحديد ميزات إضافية</em>، حدّد الميزة المخصصة التي تحتوي على <strong>استخراج التعرف على الوحدة المسماة المخصصة</strong>. إنشاء المورد بالإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>مجموعة الموارد</strong>: <em>تحديد مجموعة موارد أو إنشاؤها</em></li>
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
<li><strong>الاسم</strong>: <em>أدخل اسماً فريداً</em></li>
<li><strong>طبقة الأسعار</strong>: حدد <strong>F0</strong> (<em>مجاني</em>)، أو <strong>S</strong> (<em>قياسي</em>) إذا لم يكن F متوفراً.</li>
<li><strong>حساب التخزين</strong>: حساب تخزين جديد:
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
<p dir="auto"><strong>ملاحظة</strong>: إذا تخطيت هذه الخطوة، فسوف تحصل على خطأ 403 عند محاولة الاتصال بمشروعك المخصص. من المهم أن يكون لدى مُستخدمك الحالي هذا الدور للوصول إلى بيانات الكائن الثنائي كبير الحجم لحساب التخزين، حتى إذا كنت مالكًا لحساب التخزين.**</p>
</blockquote>
<ol dir="rtl">
<li>انتقل إلى صفحة حساب التخزين في مدخل Azure.</li>
<li>حدد <strong>التحكم في الوصول (IAM)</strong> من قائمة التنقل اليسرى.</li>
<li>حدد <strong>إضافة</strong> لإضافة واجبات الدور واختر دور <strong>مساهم بيانات الكائن الثنائي كبير الحجم للتخزين</strong> في حساب التخزين.</li>
<li>ضمن <strong>تعيين الوصول إلى</strong>، حدد <strong>المستخدم أو المجموعة أو كيان الخدمة</strong>.</li>
<li>حدد <strong>تحديد أعضاء</strong>.</li>
<li>حدد مُستخدمك. يمكنك البحث عن أسماء المستخدمين في الحقل <strong>Select</strong>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تحميل عينة إعلانات</h2><a id="user-content-تحميل-عينة-إعلانات" class="anchor" aria-label="Permalink: تحميل عينة إعلانات" href="#تحميل-عينة-إعلانات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بمجرد إنشاء "خدمة لغة الذكاء الاصطناعي في Azure" وحساب التخزين، سيتعين عليك تحميل أمثلة للإعلانات لتدريب النموذج لاحقًا.</p>
<ol dir="rtl">
<li>
<p dir="auto">في علامة تبويب جديدة بالمتصفح، قُم بتنزيل نماذج الإعلانات المصنَّفة من <code>https://aka.ms/entity-extraction-ads</code> واستخرِج الملفات إلى مجلد من اختيارك.</p>
</li>
<li>
<p dir="auto">في مدخل Microsoft Azure، انتقل إلى حساب التخزين الذي أنشأته، وحدده.</p>
</li>
<li>
<p dir="auto">في حساب التخزين الخاص بك، حدّد <strong>تكوين</strong>، الموجود أسفل <strong>الإعدادات</strong>، وظلِّل تمكين الخيار <strong>السماح بالوصول المجهول للكائن الثنائي كبير الحجم</strong> ثم حدّد <strong>حفظ</strong>.</p>
</li>
<li>
<p dir="auto">حدّد <strong>الحاويات</strong> من القائمة اليمنى، الموجودة أسفل <strong>تخزين البيانات</strong>. على الشاشة التي تظهر، حدد <strong>+ Container</strong>. امنح الحاوية الاسم <code>classifieds</code>، وحدّد <strong>مستوى الوصول المجهول</strong> إلى <strong>الحاوية (الوصول المجهول للقراءة فقط للحاويات والكائنات الثنائية كبيرة الحجم)</strong>.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: عند تكوين حساب تخزين لحلّ حقيقي، احرص على تعيين مستوى الوصول المناسب. لمعرفة المزيد حول كل مستوى وصول، راجِع <a href="https://learn.microsoft.com/azure/storage/blobs/anonymous-read-access-configure" rel="nofollow">مستندات Azure Storage</a>.</p>
</blockquote>
</li>
<li>
<p dir="auto">بعد إنشاء الحاوية، حدّدها وانقر فوق زر <strong>تحميل</strong> لتحميل نماذج الإعلانات التي قمتَ بتنزيلها.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء مشروع مخصص للتعرف على الكيان المسمى</h2><a id="user-content-إنشاء-مشروع-مخصص-للتعرف-على-الكيان-المسمى" class="anchor" aria-label="Permalink: إنشاء مشروع مخصص للتعرف على الكيان المسمى" href="#إنشاء-مشروع-مخصص-للتعرف-على-الكيان-المسمى"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أنت الآن جاهز لإنشاء مشروع تعرّف على الوحدة المسماة المخصصة. يوفر هذا المشروع مكانا للعمل لبناء نموذجك وتدريبه وتوزيعه.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: يمكنك أيضًا إنشاء نموذجك وبنائه وتدريبه ونشره من خلال واجهة برمجة تطبيقات REST.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="auto">في علامة تبويب جديدة بالمتصفح، افتح مدخل "ستوديو لغة الذكاء الاصطناعي في Azure" في <code>https://language.cognitive.azure.com/</code>، ثم سجّل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure خاصتك.</p>
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
<li>في أعلى الصفحة، انقر فوق <strong>Language Studio</strong> للعودة إلى الصفحة الرئيسية في Language Studio.</li>
</ol>
</li>
<li>
<p dir="auto">في أعلى المدخل، في قائمة <strong>إنشاء جديد</strong>، حدّد <strong>التعرّف على الوحدة المسمّاة المخصصة</strong>.</p>
</li>
<li>
<p dir="auto">إنشاء مشروع جديد بالإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>اتصال التخزين</strong>: <em>من المحتمل أن تكون هذه القيمة قد تمت تعبئتها بالفعل. قُم بتغييرها إلى حساب التخزين الخاص بك إذا لم تكن قد تمت تعبئتها سابقًا</em></li>
<li><strong>المعلومات الأساسية</strong>:</li>
<li><strong>الاسم:</strong> <code>CustomEntityLab</code>
<ul dir="rtl">
<li><strong>Text primary language</strong>: English (US)</li>
<li><strong>هل تتضمن مجموعة البيانات لديك مستندات ليست بذات اللغة؟</strong> : <em>لا</em></li>
<li><strong>الوصف</strong>: <code>Custom entities in classified ads</code></li>
</ul>
</li>
<li><strong>الحاوية:</strong>
<ul dir="rtl">
<li><strong>حاوية مخزن Blob</strong>: مصنفات</li>
<li><strong>هل ملفاتك مُسماة بفئات؟</strong>: لا، أحتاج إلى تسمية ملفاتي كجزء من هذا المشروع</li>
</ul>
</li>
</ul>
</li>
</ol>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: إذا ظهر لديك خطأ بشأن عدم تفويضك لتنفيذ هذه العملية، فستحتاج إلى إضافة تعيين دور. لتصحيح ذلك، نقوم بإضافة دور "المساهم ببيانات الكائن الثنائي كبير الحجم للتخزين" على حساب التخزين للمستخدم والذي يقوم بتشغيل النشاط العملي. يمكن العثور على مزيدٍ من التفاصيل في <a href="https://learn.microsoft.com/azure/ai-services/language-service/custom-named-entity-recognition/how-to/create-project?tabs=portal%2Clanguage-studio#enable-identity-management-for-your-resource" rel="nofollow">صفحة الوثائق</a>.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تسمية البيانات</h2><a id="user-content-تسمية-البيانات" class="anchor" aria-label="Permalink: تسمية البيانات" href="#تسمية-البيانات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن تم إنشاء مشروعك، تحتاج إلى تسمية بياناتك لتدريب النموذج على كيفية تحديد الكيانات.</p>
<ol dir="rtl">
<li>إذا لم تكن صفحة <strong>تسمية البيانات</strong> مفتوحة بالفعل، فحدد تسمية** البيانات في الجزء الموجود على اليسار**. سترى قائمة بالملفات التي قمت بتحميلها إلى حساب التخزين الخاص بك.</li>
<li>على الجانب الأيمن، في <strong>جزء النشاط</strong>، حدد <strong>إضافة كيان</strong> وأضف كيانًا جديدًا باسم <code>ItemForSale</code>.</li>
<li>كرر الخطوة السابقة لإنشاء الكيانات التالية:
<ul dir="rtl">
<li><code>Price</code></li>
<li><code>Location</code></li>
</ul>
</li>
<li>بعد إنشاء كياناتك الثلاثة، حدد <strong>Ad 1.txt</strong> حتى تتمكن من قراءتها.</li>
<li>في <em>Ad 1.txt</em>:
<ol dir="rtl">
<li>قم بتمييز نص <em>حبل من حطب الوقود</em> وحدد <strong>كيان ItemForSale</strong>.</li>
<li>قم بتمييز النص <em>دنفر في ولاية كولورادو</em> وحدد <strong>كيان الموقع</strong>.</li>
<li>قم بتمييز النص <em>90 دولارًا</em> وحدد كيان <strong>السعر</strong>.</li>
</ol>
</li>
<li>في جزء <strong>النشاط</strong>، ستلاحظ أن هذا المستند سيتم إضافته إلى مجموعة البيانات لتدريب النموذج.</li>
<li>استخدم زر <strong>المستند التالي</strong> للانتقال إلى المستند التالي، ومتابعة تعيين النص للكيانات المناسبة لمجموعة المستندات بأكملها، وإضافتها جميعًا إلى مجموعة بيانات التدريب.</li>
<li>عندما تنتهي من تسمية المستند الأخير (<em>Ad 9.txt</em>)، احفظ الأوصاف.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تدريب النموذج</h2><a id="user-content-تدريب-النموذج" class="anchor" aria-label="Permalink: تدريب النموذج" href="#تدريب-النموذج"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بمجرد تسمية بياناتك، تحتاج إلى تدريب نموذجك.</p>
<ol dir="rtl">
<li>
<p dir="auto">حدد <strong>Training jobs</strong> من الجزء الموجود على اليسار.</p>
</li>
<li>
<p dir="auto">حدد ** Start a training job**</p>
</li>
<li>
<p dir="auto">تدريب نموذج جديد باسم <code>ExtractAds</code></p>
</li>
<li>
<p dir="auto">اختر <strong>Automatically split the testing set from training data</strong></p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: في مشاريع الاستخراج، استخدم تقسيم الاختبار الذي يناسب بياناتك بشكل أفضل. للحصول على بيانات أكثر اتساقًا ومجموعات بيانات أكبر، ستقوم خدمة Azure AI Language تلقائيًا بتقسيم الاختبار المُعيّن حسب النسبة المئوية. في حالة مجموعات البيانات الأصغر، من المهم التدريب على مجموعة متنوعة صحيحة من مستندات الإدخال المحتملة.</p>
</blockquote>
</li>
<li>
<p dir="auto">انقر فوق <strong>Train</strong></p>
<blockquote>
<p dir="auto"><strong>هام</strong>: قد يستغرق تدريب النموذج الخاص بك أحيانا عدة دقائق. ستتلقى إعلاما عند اكتماله.</p>
</blockquote>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تقييم نموذجك</h2><a id="user-content-تقييم-نموذجك" class="anchor" aria-label="Permalink: تقييم نموذجك" href="#تقييم-نموذجك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في تطبيقات العالم الحقيقي، من المهم تقييم نموذجك وتحسينه للتحقق من أدائه كما تتوقع. تعرض صفحتان على اليسار تفاصيل النموذج المدرب وأي اختبار فشل.</p>
<p dir="auto">حدد <strong>Model performance</strong> في القائمة اليسرى، وحدد <code>ExtractAds</code> النموذج الخاص بك. ثم يمكنك أن ترى تسجيل النموذج الخاص بك، ومقاييس الأداء، ومتى تم تدريبه. ستتمكن من معرفة ما إذا فشلت أي مستندات اختبار، وتساعدك هذه الإخفاقات على فهم المكان الذي يحتاج إلى تحسين.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استخدام نموذجك</h2><a id="user-content-استخدام-نموذجك" class="anchor" aria-label="Permalink: استخدام نموذجك" href="#استخدام-نموذجك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">عندما تكون راضيًا عن تدريب النموذج، فقد حان الوقت لتوزيعه، ما يسمح لك بالبدء في استخراج الكيانات من خلال واجهة برمجة التطبيقات.</p>
<ol dir="rtl">
<li>في الجزء الأيسر، حدد <strong>Deploying a model</strong>.</li>
<li>حدد <strong>Add deployment</strong>، ثم أدخل الاسم <code>AdEntities</code> وحدد نموذج <strong>ExtractAds</strong>.</li>
<li>انقر فوق <strong>Deploy</strong> لتوزيع النموذج الخاص بك.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية</h2><a id="user-content-الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية" href="#الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لاختبار إمكانيات استخراج الكيان المخصص لخدمة Azure AI Language، ستقوم بتطوير تطبيق وحدة تحكم بسيط في تعليمة Visual Studio برمجية.</p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: إذا استنسخت بالفعل مستودع <strong>mslearn-ai-language</strong>، فافتحه في Visual Studio code. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.</p>
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
<p dir="auto">تم توفير تطبيقات لكل من C# وPython. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد Azure AI Language الخاص بك.</p>
<ol dir="rtl">
<li>
<p dir="auto">في Visual Studio Code، في جزء <strong>Explorer</strong>، استعرض للوصول إلى المجلد <strong>Labfiles/05-custom-entity-recognition</strong> وقم بتوسيع المجلد <strong>CSharp</strong> أو <strong>Python</strong> استناداً إلى تفضيلات اللغة ومجلد <strong>custom-entities</strong> الذي يحتوي عليه. يحتوي كل مجلد على الملفات الخاصة باللغة للتطبيق الذي ستقوم بدمج وظيفة تصنيف نص Azure AI Language فيه.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن فوق مجلد <strong>custom-entities</strong> الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة Azure AI Language Text Analytics SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:</p>
</li>
<p dir="rtl"><strong>:#C</strong></p>
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
<p dir="rtl">:<strong>Python</strong></p>
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
<p dir="auto">في جزء <strong>Explorer</strong>، في مجلد <strong>custom-entities</strong>، افتح ملف التكوين للغة المفضلة لديك</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
</li>
<li>
<p dir="auto">قم بتحديث قيم التكوين لتضمين <strong>نقطة النهاية</strong> و<strong>مفتاح</strong> من مورد Azure Language الذي أنشأته (متوفر في صفحة <strong>المفاتيح ونقطة النهاية</strong> لمورد Azure AI Language في مدخل Microsoft Azure). يجب أن يحتوي الملف بالفعل على أسماء المشروع والنشر لنموذج استخراج الكيان المخصص لديك.</p>
</li>
<li>
<p dir="auto">واحفظ ملف التكوين.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة رمز لاستخراج الكيانات</h2><a id="user-content-إضافة-رمز-لاستخراج-الكيانات" class="anchor" aria-label="Permalink: إضافة رمز لاستخراج الكيانات" href="#إضافة-رمز-لاستخراج-الكيانات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أنت الآن جاهز لاستخدام خدمة Azure AI Language لاستخراج الكيانات المخصصة من النص.</p>
<ol dir="rtl">
<li>
<p dir="auto">قم بتوسيع مجلد <strong>الإعلانات</strong> في مجلد <strong>الكيانات المخصصة</strong> لعرض الإعلانات المصنفة التي سيقوم تطبيقك بتحليلها.</p>
</li>
<li>
<p dir="auto">في مجلد <strong>custom-entities</strong>، افتح ملف التعليمات البرمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: custom-entities.py</li>
</ul>
</li>
<li>
<p dir="auto">ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. ومن ثم ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// import namespaces
using Azure;
using Azure.AI.TextAnalytics;</code></pre></div>
<p dir="rtl"><strong>Python</strong>: custom-entities.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># import namespaces
from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient</code></pre></div>
<li>
<p dir="auto">في دالة <strong>Main</strong>، لاحظ أنه تم بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية خدمة Azure AI Language والمفتاح وأسماء المشروع والتوزيع من ملف التكوين. ثم ابحث عن التعليق <strong>إنشاء عميل باستخدام نقطة النهاية والمفتاح</strong>، وأضف التعليمة البرمجية التالية لإنشاء عميل لواجهة برمجة تطبيقات تحليل النص:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Create client using endpoint and key
AzureKeyCredential credentials = new(aiSvcKey);
Uri endpoint = new(aiSvcEndpoint);
TextAnalyticsClient aiClient = new(endpoint, credentials);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: custom-entities.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Create client using endpoint and key
credential = AzureKeyCredential(ai_key)
ai_client = TextAnalyticsClient(endpoint=ai_endpoint, credential=credential)</code></pre></div>
<li>
<p dir="auto">في دالة <strong>Main</strong>، لاحظ أن التعليمة البرمجية الموجودة تقرأ جميع الملفات الموجودة في مجلد <strong>الإعلانات</strong> وتنشئ قائمة تحتوي على محتوياتها. في حالة التعليمة البرمجية C#، يتم استخدام قائمة كائنات <strong>TextDocumentInput</strong> لتضمين اسم الملف كمعرّف واللغة. في Python، يتم استخدام قائمة بسيطة لمحتويات النص.</p>
</li>
<li>
<p dir="auto">ابحث عن التعليق <strong>استخراج الكيانات</strong> وأضف التعليمة البرمجية التالية:</p>
</li>
<p dir="auto"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Extract entities
RecognizeCustomEntitiesOperation operation = await aiClient.RecognizeCustomEntitiesAsync(WaitUntil.Completed, batchedDocuments, projectName, deploymentName);
<br>
await foreach (RecognizeCustomEntitiesResultCollection documentsInPage in operation.Value)
{
    foreach (RecognizeEntitiesResult documentResult in documentsInPage)
    {
        Console.WriteLine($"Result for \"{documentResult.Id}\":");
<br>
        if (documentResult.HasError)
        {
            Console.WriteLine($"  Error!");
            Console.WriteLine($"  Document error code: {documentResult.Error.ErrorCode}");
            Console.WriteLine($"  Message: {documentResult.Error.Message}");
            Console.WriteLine();
            continue;
        }
<br>
        Console.WriteLine($"  Recognized {documentResult.Entities.Count} entities:");
<br>
        foreach (CategorizedEntity entity in documentResult.Entities)
        {
            Console.WriteLine($"  Entity: {entity.Text}");
            Console.WriteLine($"  Category: {entity.Category}");
            Console.WriteLine($"  Offset: {entity.Offset}");
            Console.WriteLine($"  Length: {entity.Length}");
            Console.WriteLine($"  ConfidenceScore: {entity.ConfidenceScore}");
            Console.WriteLine($"  SubCategory: {entity.SubCategory}");
            Console.WriteLine();
        }
<br>
        Console.WriteLine();
    }
}</code></pre></div>
<p dir="auto"><strong>Python</strong>: custom-entities.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Extract entities
operation = ai_client.begin_recognize_custom_entities(
    batchedDocuments,
    project_name=project_name,
    deployment_name=deployment_name
)
<br>
document_results = operation.result()
<br>
for doc, custom_entities_result in zip(files, document_results):
    print(doc)
    if custom_entities_result.kind == "CustomEntityRecognition":
        for entity in custom_entities_result.entities:
            print(
                "\tEntity '{}' has category '{}' with confidence score of '{}'".format(
                    entity.text, entity.category, entity.confidence_score
                )
            )
    elif custom_entities_result.is_error is True:
        print("\tError with code '{}' and message '{}'".format(
            custom_entities_result.error.code, custom_entities_result.error.message
            )
        )</code></pre></div>
<li>
<p dir="auto">احفظ التغييرات في ملف التعليمات البرمجية الخاص بك.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">اختبار التطبيق الخاص بك</h2><a id="user-content-اختبار-التطبيق-الخاص-بك" class="anchor" aria-label="Permalink: اختبار التطبيق الخاص بك" href="#اختبار-التطبيق-الخاص-بك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن التطبيق الخاص بك جاهز للاختبار.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الوحدة الطرفية المتكاملة للمجلد <strong>تصنيف النص</strong>، أدخل الأمر التالي لتشغيل البرنامج:</p>
<ul dir="rtl">
<li><strong>:#C</strong> <code>dotnet run</code></li>
<li><strong>Python</strong>: <code>python custom-entities.py</code></li>
</ul>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: يمكنك استخدام أيقونة <strong>تكبير حجم اللوحة</strong> (<strong>^</strong>) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.</p>
</blockquote>
</li>
<li>
<p dir="auto">مراقبة المخرجات. يجب أن يسرد التطبيق تفاصيل الكيانات الموجودة في كل ملف نصي.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف</h2><a id="user-content-تنظيف" class="anchor" aria-label="Permalink: تنظيف" href="#تنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">عندما لا تحتاج إلى مشروعك بعد الآن، يمكنك حذفه من صفحة <strong>Projects</strong>الخاصة بك في Language Studio. يمكنك أيضا إزالة خدمة Azure AI Language وحساب التخزين المقترن في <a href="https://portal.azure.com" rel="nofollow">مدخل Microsoft Azure</a>.</p>
</article></div></div>
