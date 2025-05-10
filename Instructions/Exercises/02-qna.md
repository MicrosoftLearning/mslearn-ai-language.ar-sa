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
  <td><div dir="auto">إنشاء حل للإجابة على الأسئلة</div></td>
  <td><div dir="auto">Module 6 - Create question answering solutions with Azure AI Language</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">إنشاء حل للإجابة على الأسئلة</h1><a id="user-content-إنشاء-حل-للإجابة-على-الأسئلة" class="anchor" aria-label="Permalink: إنشاء حل للإجابة على الأسئلة" href="#إنشاء-حل-للإجابة-على-الأسئلة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أحد أكثر سيناريوهات المحادثة شيوعا هو توفير الدعم من خلال قاعدة المعارف (KB) من الأسئلة المتداولة (FAQs). تنشر العديد من المؤسسات الأسئلة الشائعة كمستندات أو صفحات ويب، وهو ما يعمل بشكل جيد مع مجموعة صغيرة من أزواج الأسئلة والأجوبة، ولكن قد يكون من الصعب البحث في المستندات الكبيرة ويستغرق وقتاً طويلاً.</p>
<p dir="auto"><strong>تتضمن لغة الذكاء الاصطناعي في Azure</strong> <em>إمكانية الإجابة على الأسئلة</em> التي تمكنك من إنشاء قاعدة المعارف (KB) من أزواج الأسئلة والأجوبة التي يمكن الاستعلام عنها باستخدام إدخال اللغة الطبيعية، وهي الأكثر شيوعا كمورد يمكن للروبوت استخدامه للبحث عن إجابات للأسئلة المقدمة من المستخدمين.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">توفير مورد <em>لغة الذكاء الاصطناعي في Azure</em></h2><a id="user-content-توفير-مورد-لغة-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: توفير مورد لغة الذكاء الاصطناعي في Azure" href="#توفير-مورد-لغة-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك واحدًا بالفعل في اشتراكك، فستحتاج إلى توفير مورد <strong>خدمة لغة الذكاء الاصطناعي في Azure</strong>. بالإضافة إلى ذلك، لإنشاء واستضافة قاعدة معرفية للإجابة على الأسئلة، تحتاج إلى تمكين ميزة <strong>الإجابة على الأسئلة</strong>.</p>
<ol dir="rtl">
<li>
<p dir="auto">افتح مدخل Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</p>
</li>
<li>
<p dir="auto">حدد <strong>Create a resource.</strong></p>
</li>
<li>
<p dir="auto">في حقل البحث، ابحث عن <strong>خدمة اللغة</strong>. ثم، في النتائج، حدد <strong>إنشاء</strong> ضمن <strong>خدمة اللغة</strong>.</p>
</li>
<li>
<p dir="auto">حدد كتلة <strong>الإجابة على الأسئلة المخصصة</strong>. ثم حدد <strong>متابعة لإنشاء المورد الخاص بك</strong>. ستحتاج إلى إدخال الإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>مجموعة الموارد</strong>: <em>اختيار مجموعة موارد أو إنشاءها</em>.</li>
<li><strong>المنطقة</strong>: <em>اختر أي موقع متاح</em></li>
<li><strong>الاسم</strong>: <em>أدخل اسماً فريداً</em></li>
<li><strong>طبقة الأسعار</strong>: حدد <strong>F0</strong> (<em>مجاني</em>)، أو <strong>S</strong> (<em>قياسي</em>) إذا لم يكن F متوفراً.</li>
<li><strong>منطقة البحث في Azure</strong>: <em>اختر موقعاً في نفس المنطقة العالمية التي يوجد بها مصدر اللغة الخاص بك</em></li>
<li><strong>مستوى الأسعار الخاص ببحث Azure</strong>: مجاني (F) (<em>إذا لم يكن هذا المستوى متاحاً، فاختر Basic (B)</em>)</li>
<li><strong>Responsible AI Notice</strong>: <em>Agree</em></li>
</ul>
</li>
<li>
<p dir="auto">حدد <strong>إنشاء + مراجعة</strong>، ثم حدد <strong>إنشاء</strong>.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong> تستخدم الإجابة على الأسئلة المخصصة Azure Search لفهرسة قاعدة المعارف (KB) الأسئلة والأجوبة والاستعلام عنها.</p>
</blockquote>
</li>
<li>
<p dir="auto">انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</p>
</li>
<li>
<p dir="auto">اعرض صفحة <strong>المفاتيح ونقطة النهاية</strong>. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التمرين.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء مشروع للإجابة على الأسئلة</h2><a id="user-content-إنشاء-مشروع-للإجابة-على-الأسئلة" class="anchor" aria-label="Permalink: إنشاء مشروع للإجابة على الأسئلة" href="#إنشاء-مشروع-للإجابة-على-الأسئلة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لإنشاء قاعدة المعارف (KB) للإجابة على الأسئلة في مورد لغة الذكاء الاصطناعي في Azure، يمكنك استخدام مدخل Language Studio لإنشاء مشروع إجابة على الأسئلة. في هذه الحالة، ستقوم بإنشاء قاعدة المعارف (KB) يحتوي على أسئلة وإجابات حول <a href="https://docs.microsoft.com/learn" rel="nofollow">Microsoft Learn</a>.</p>
<ol dir="rtl">
<li>
<p dir="auto">في علامة تبويب مستعرض جديدة، افتح مدخل Language Studio في <a href="https://language.cognitive.azure.com/" rel="nofollow">https://language.cognitive.azure.com/</a>، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure خاصتك.</p>
</li>
<li>
<p dir="auto">إذا طلب منك اختيار مورد اللغة، حدد الإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>Azure Directory</strong>: دليل Azure الذي يحتوي على اشتراكك.</li>
<li><strong>Azure subscription</strong>: اشتراك Azure الخاص بك.</li>
<li><strong>نوع المورد</strong>: اللغة</li>
<li><strong>اسم المورد</strong>. مورد "لغة الذكاء الاصطناعي في Azure" الذي أنشأتَه سابقًا.</li>
</ul>
<p dir="auto">إذا لم تتم مطالبتك باختيار مورد language، فقد يرجع ذلك إلى وجود موارد Language متعددة في اشتراكك؛ وفي هذه الحالة:</p>
<ol dir="rtl">
<li>في الشريط الموجود أعلى الصفحة، حدّد زر <strong>الإعدادات (&amp;#9881؛</strong>.</li>
<li>في الصفحة <strong>Settings</strong> اعرض علامة التبويب <strong>Resources</strong>.</li>
<li>حدد مورد language الذي أنشأته للتو، وانقر فوق <strong>Switch resource</strong>.</li>
<li>في أعلى الصفحة، انقر فوق <strong>Language Studio</strong> للعودة إلى الصفحة الرئيسية في Language Studio.</li>
</ol>
</li>
<li>
<p dir="auto">في أعلى مدخل، في القائمة <strong>إنشاء جديد</strong>، حدد <strong>الإجابة على الأسئلة المخصصة</strong>.</p>
</li>
<li>
<p dir="auto">في معالج *<strong>إنشاء مشروع</strong>، في صفحة <strong>اختيار إعداد اللغة</strong>، حدد الخيار <strong>تحديد اللغة لجميع المشاريع</strong>، ثم حدد <strong>الإنجليزية</strong> كلغة. بعد ذلك حدد <strong>التالي</strong>.</p>
</li>
<li>
<p dir="auto">في صفحة <strong>إدخال المعلومات الأساسية</strong> أدخل التفاصيل التالية:</p>
<ul dir="rtl">
<li><strong>الاسم</strong> <code>LearnFAQ</code></li>
<li><strong>الوصف</strong>: <code>FAQ for Microsoft Learn</code></li>
<li><strong>الإجابة الافتراضية عند عدم إرجاع أي إجابة</strong>: <code>Sorry, I don't understand the question</code></li>
</ul>
</li>
<li>
<p dir="auto">حدد <strong>التالي</strong>.</p>
</li>
<li>
<p dir="auto">في صفحة <strong>مراجعة وإنهاء</strong>، حدد <strong>إنشاء مشروع</strong>.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة مصادر إلى قاعدة المعارف (KB)</h2><a id="user-content-إضافة-مصادر-إلى-قاعدة-المعارف-kb" class="anchor" aria-label="Permalink: إضافة مصادر إلى قاعدة المعارف (KB)" href="#إضافة-مصادر-إلى-قاعدة-المعارف-kb"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يمكنك إنشاء قاعدة المعارف (KB) من البداية، ولكن من الشائع البدء باستيراد الأسئلة والأجوبة من صفحة أو مستند الأسئلة المتداولة الموجود. في هذه الحالة، ستقوم باستيراد البيانات من صفحة الأسئلة الشائعة الموجودة على Microsoft Learn، كما ستقوم أيضًا باستيراد بعض أسئلة وأجوبة "المحادثة" المحددة مسبقًا لدعم تبادلات المحادثة الشائعة.</p>
<ol dir="rtl">
<li>في <strong>صفحة إدارة المصادر</strong> لمشروع الإجابة على سؤالك، في <strong>&amp;9547; أضف قائمة المصدر</strong>، وحدد <strong>عناوين URL</strong>. ثم في <strong>مربع الحوار إضافة عناوين URL</strong>، حدد <strong>╋ أضف url</strong> وقم بتعيين الاسم وعنوان URL التاليين قبل تحديد <strong>إضافة الكل</strong> لإضافته إلى قاعدة المعارف (KB):
<ul dir="rtl">
<li><strong>الاسم:</strong> <code>Learn FAQ Page</code></li>
<li><strong>URL</strong>: <code>https://docs.microsoft.com/en-us/learn/support/faq</code></li>
</ul>
</li>
<li>في <strong>صفحة إدارة المصادر</strong> لمشروع الإجابة على سؤالك، في <strong>╋ أضف قائمة المصدر</strong>، وحدد <strong>عناوين URL</strong>. في مربع الحوار <strong>إضافة الدردشة التلقائية</strong>، حدد <strong>Friendly</strong> وحدد <strong>Add chit chat</strong>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تحرير قاعدة المعرفة</h2><a id="user-content-تحرير-قاعدة-المعرفة" class="anchor" aria-label="Permalink: تحرير قاعدة المعرفة" href="#تحرير-قاعدة-المعرفة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تم ملء قاعدة المعارف (KB) بأزواج الأسئلة والأجوبة من الأسئلة المتداولة حول Microsoft Learn، وملحقة بمجموعة من أزواج الأسئلة والأجوبة الخاصة <em>بالدردشة التلقائية</em>. يمكنك توسيع قاعدة المعارف (KB) عن طريق إضافة أزواج إضافية من الأسئلة والأجوبة.</p>
<ol dir="rtl">
<li>
<p dir="auto">في مشروع <strong>LearnFAQ</strong> في Language Studio، حدد صفحة <strong>تحرير قاعدة المعارف (KB)</strong> لمشاهدة أزواج الأسئلة والأجوبة الموجودة (إذا تم عرض بعض التلميحات، فاقرأها واختر <strong>حسناً</strong> لتجاهلها، أو حدد <strong>تخطي الكل</strong>)</p>
</li>
<li>
<p dir="auto">في قاعدة المعارف (KB)، في علامة التبويب <strong>إجابات الأسئلة</strong>، حدد <strong>＋</strong>، وأنشئ زوجا جديدا من إجابات الأسئلة بالإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>المصدر</strong>: <code>https://docs.microsoft.com/en-us/learn/support/faq</code></li>
<li><strong>السؤال</strong>: <code>What are Microsoft credentials?</code></li>
<li><strong>الإجابة</strong>: <code>Microsoft credentials enable you to validate and prove your skills with Microsoft technologies.</code></li>
</ul>
</li>
<li>
<p dir="auto">حدد <strong>تم</strong>.</p>
</li>
<li>
<p dir="auto">في صفحة <strong>السؤال ما هي بيانات اعتماد Microsoft؟</strong> التي تم إنشاؤها، قم بتوسيع <strong>الأسئلة البديلة</strong>. ثم أضف السؤال <code>How can I demonstrate my Microsoft technology skills?</code> البديل.</p>
<p dir="auto">في بعض الحالات، من المنطقي تمكين المستخدم من متابعة إجابة عن طريق إنشاء <em>محادثة متعددة الأدوار</em> تمكن المستخدم من تحسين السؤال بشكل متكرر للوصول إلى الإجابة التي يحتاجها.</p>
</li>
<li>
<p dir="auto">ضمن الإجابة التي أدخلتها لسؤال الشهادة، قم بتوسيع <strong>مطالبات المتابعة</strong> وأضف مطالبة المتابعة التالية:</p>
<ul dir="rtl">
<li><strong>النص المعروض في المطالبة للمستخدم</strong>: <code>Learn more about credentials</code>.</li>
<li>حدد علامة التبويب <strong>إنشاء ارتباط إلى زوج جديد</strong>، وأدخل هذا النص: <code>You can learn more about credentials on the [Microsoft credentials page](https://docs.microsoft.com/learn/credentials/).</code></li>
<li>حدد <strong>إظهار في التدفق السياقي فقط</strong>. يضمن هذا الخيار أن يتم إرجاع الإجابة فقط في سياق سؤال متابعة من سؤال الشهادة الأصلي.</li>
</ul>
</li>
<li>
<p dir="auto">حدد <strong>إضافة مطالبة</strong>.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تدريب واختبار قاعدة المعارف</h2><a id="user-content-تدريب-واختبار-قاعدة-المعارف" class="anchor" aria-label="Permalink: تدريب واختبار قاعدة المعارف" href="#تدريب-واختبار-قاعدة-المعارف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن، وبعد أن أصبحت لديك قاعدة معارف؛ فإنه يمكنك اختبارها في مدخل Language Studio.</p>
<ol dir="rtl">
<li>احفظ التغييرات على قاعدة المعارف (KB) عن طريق تحديد الزر <strong>حفظ</strong> ضمن <strong>علامة التبويب أزواج الأسئلة والإجابات</strong> على اليسار.</li>
<li>بعد حفظ التغييرات، حدد الزر <strong>اختبار</strong> لفتح جزء الاختبار.</li>
<li>في جزء الاختبار، في الأعلى، قم بإلغاء تحديد <strong>تضمين استجابة الإجابة القصيرة</strong> (إذا لم يكن محددا بالفعل). ثم في الأسفل أدخل الرسالة <code>Hello</code>. وينبغي إرجاع استجابة مناسبة.</li>
<li>في جزء الاختبار، أدخل في الجزء السفلي رسالة تقول <code>What is Microsoft Learn?</code>. يجب إرجاع رد مناسب من الأسئلة الشائعة.</li>
<li>أدخل الرسالة <code>Thanks!</code> يجب إرجاع استجابة المحادثات التلقائية المناسبة.</li>
<li>إدخال الرسالة <code>Tell me about Microsoft credentials</code>. يجب أن يتم إرجاع الإجابة التي قمت بإنشائها مع رابط المتابعة السريع.</li>
<li>حدد الارتباط <strong>تعرّف على المزيد حول متابعة بيانات الاعتماد</strong>. يجب إرجاع إجابة المتابعة مع ارتباط إلى صفحة الشهادة.</li>
<li>عند الانتهاء من اختبار قاعدة المعرفة، قم بإغلاق جزء الاختبار.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">نشر قاعدة المعرفة</h2><a id="user-content-نشر-قاعدة-المعرفة" class="anchor" aria-label="Permalink: نشر قاعدة المعرفة" href="#نشر-قاعدة-المعرفة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">توفر قاعدة المعرفة خدمة خلفية يمكن لتطبيقات العميل استخدامها للإجابة على الأسئلة. أنت الآن جاهز لنشر قاعدة المعارف (KB) والوصول إلى واجهة REST الخاصة به من عميل.</p>
<ol dir="rtl">
<li>في مشروع <strong>LearnFAQ</strong> في استوديو اللغة، حدد صفحة <strong>نشر قاعدة المعرفة</strong> من قائمة التنقل الموجودة على اليسار.</li>
<li>في أعلى الصفحة، حدد <strong>نشر</strong>. ثم حدد <strong>نشر</strong> لتأكيد رغبتك في نشر قاعدة المعارف (KB).</li>
<li>عند اكتمال النشر، حدد <strong>الحصول على عنوان URL للتنبؤ</strong> لعرض نقطة نهاية REST لقاعدة المعرفة الخاصة بك ولاحظ أن نموذج الطلب يتضمن معلمات لـ:
<ul dir="rtl">
<li><strong>projectName</strong>: اسم مشروعك (الذي ينبغي أن يكون <em>LearnFAQ</em>)</li>
<li><strong>deploymentName</strong>: اسم النشر الخاص بك (والذي يجب أن يكون <em>إنتاجاً</em>)</li>
</ul>
</li>
<li>أغلق مربع حوار عنوان URL للتنبؤ.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في Visual Studio Code</h2><a id="user-content-الاستعداد-لتطوير-تطبيق-في-visual-studio-code" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في Visual Studio Code" href="#الاستعداد-لتطوير-تطبيق-في-visual-studio-code"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">ستقوم بتطوير تطبيق الإجابة على أسئلتك باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.</p>
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
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تكوين تطبيقك</h2><a id="user-content-تكوين-تطبيقك" class="anchor" aria-label="Permalink: تكوين تطبيقك" href="#تكوين-تطبيقك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تم توفير تطبيقات لكل من C# وPython، وكذلك ملف نصي نموذجي ستستخدمه لاختبار التلخيص. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد لغة الذكاء الاصطناعي في Azure الخاص بك.</p>
<ol dir="rtl">
<li>
<p dir="auto">في Visual Studio Code، في جزء <strong>Explorer</strong>، استعرض للوصول إلى المجلد <strong>Labfiles/02-qna</strong> ووسع نطاق المجلد <strong>CSharp</strong> أو <strong>Python</strong> استناداً إلى تفضيلات اللغة ومجلد <strong>الساعة الناطقة</strong> الذي يحتوي عليها. يحتوي كل مجلد على الملفات الخاصة باللغة الخاصة بالتطبيق الذي ستقوم بدمج وظيفة الإجابة على أسئلة لغة الذكاء الاصطناعي في Azure فيه.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن فوق مجلد <strong>qna-app</strong> الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة SDK للإجابة على أسئلة لغة الذكاء الاصطناعي في Azure عن طريق تشغيل الأمر المناسب لتفضيلات اللغة الخاصة بك:</p>
</li>
<p dir="rtl"><strong>:#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.AI.Language.QuestionAnswering
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.AI.Language.QuestionAnswering" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>لغة Python</strong>:</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-ai-language-questionanswering
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-ai-language-questionanswering" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<li>
<p dir="auto">في جزء <strong>Explorer</strong>، في مجلد <strong>qna-app</strong>، افتح ملف التكوين للغتك المفضلة</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
</li>
<li>
<p dir="auto">قم بتحديث قيم التكوين لتضمين <strong>نقطة النهاية</strong> و<strong>مفتاح</strong> من مورد Azure Language الذي أنشأته (متوفر في صفحة <strong>المفاتيح ونقطة النهاية</strong> لمورد Azure AI Language في مدخل Microsoft Azure). يجب أن يكون اسم المشروع واسم النشر قاعدة المعارف (KB) المنشورة أيضا في هذا الملف.</p>
</li>
<li>
<p dir="auto">احفظ ملف التكوين.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمية برمجية إلى التطبيق</h2><a id="user-content-إضافة-تعليمية-برمجية-إلى-التطبيق" class="anchor" aria-label="Permalink: إضافة تعليمية برمجية إلى التطبيق" href="#إضافة-تعليمية-برمجية-إلى-التطبيق"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أنت الآن جاهز لإضافة التعليمة البرمجية اللازمة لاستيراد مكتبات SDK المطلوبة، وإنشاء اتصال مصادق عليه بمشروعك المنشور، وإرسال الأسئلة.</p>
<ol dir="rtl">
<li>
<p dir="auto">لاحظ أن مجلد <strong>qna-app</strong> يحتوي على ملف تعليمات برمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: qna-app.py</li>
</ul>
<p dir="auto">افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// import namespaces
using Azure;
using Azure.AI.Language.QuestionAnswering;</code></pre></div>
<p dir="rtl"><strong>Python</strong>: qna-app.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># import namespaces
from azure.core.credentials import AzureKeyCredential
from azure.ai.language.questionanswering import QuestionAnsweringClient</code></pre></div>
<li>
<p dir="auto">في الدالة <strong>Main</strong>، لاحظ أنه تم بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية خدمة لغة الذكاء الاصطناعي في Azure والمفتاح من ملف التكوين. ثم ابحث عن التعليق <strong>إنشاء عميل باستخدام نقطة النهاية والمفتاح</strong>، وأضف التعليمة البرمجية التالية لإنشاء عميل لواجهة برمجة تطبيقات تحليل النص:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Create client using endpoint and key
AzureKeyCredential credentials = new AzureKeyCredential(aiSvcKey);
Uri endpoint = new Uri(aiSvcEndpoint);
QuestionAnsweringClient aiClient = new QuestionAnsweringClient(endpoint, credentials);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: qna-app.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Create client using endpoint and key
credential = AzureKeyCredential(ai_key)
ai_client = QuestionAnsweringClient(endpoint=ai_endpoint, credential=credential)</code></pre></div>
<li>
<p dir="auto">في الدالة <strong>Main</strong> ، ابحث عن التعليق <strong>إرسال سؤال وعرض الإجابة</strong>، وأضف التعليمات البرمجية التالية لقراءة الأسئلة بشكل متكرر من سطر الأوامر، وإرسالها إلى الخدمة، وعرض تفاصيل الإجابات:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Submit a question and display the answer
string user_question = "";
while (true)
    {
        Console.Write("Question: ");
        user_question = Console.ReadLine();
        if (user_question.ToLower() == "quit")
            break;
        QuestionAnsweringProject project = new QuestionAnsweringProject(projectName, deploymentName);
        Response<AnswersResult> response = aiClient.GetAnswers(user_question, project);
        foreach (KnowledgeBaseAnswer answer in response.Value.Answers)
        {
            Console.WriteLine(answer.Answer);
            Console.WriteLine($"Confidence: {answer.Confidence:P2}");
            Console.WriteLine($"Source: {answer.Source}");
            Console.WriteLine();
        }
    }</code></pre></div>
<p dir="rtl"><strong>Python</strong>: qna-app.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Submit a question and display the answer
user_question = ''
while True:
    user_question = input('\nQuestion:\n')
    if user_question.lower() == "quit":                
        break
    response = ai_client.get_answers(question=user_question,
                                    project_name=ai_project_name,
                                    deployment_name=ai_deployment_name)
    for candidate in response.answers:
        print(candidate.answer)
        print("Confidence: {}".format(candidate.confidence))
        print("Source: {}".format(candidate.source))</code></pre></div>
<li>
<p dir="auto">احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>qna-app</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
<ul dir="rtl">
<li><strong>:#C</strong> <code>dotnet run</code></li>
<li><strong>Python</strong>: <code>python qna-app.py</code></li>
</ul>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: يمكنك استخدام أيقونة <strong>تكبير حجم اللوحة</strong> (<strong>^</strong>) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.</p>
</blockquote>
</li>
<li>
<p dir="auto">عند المطالبة، أدخل سؤالا لإرساله إلى مشروع الإجابة على سؤالك؛ على سبيل المثال <code>What is a learning path?</code>.</p>
</li>
<li>
<p dir="auto">راجع الإجابة التي يتم إرجاعها.</p>
</li>
<li>
<p dir="auto">اطرح المزيد من الأسئلة. عند الانتهاء، أدخِل <code>quit</code>.</p>
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
<p dir="auto">للتعرّف على المزيد حول الإجابة على الأسئلة في لغة الذكاء الاصطناعي في Azure، راجع <a href="https://learn.microsoft.com/azure/ai-services/language-service/question-answering/overview" rel="nofollow">وثائق</a> لغة الذكاء الاصطناعي في Azure.</p>
</article></div></div>
