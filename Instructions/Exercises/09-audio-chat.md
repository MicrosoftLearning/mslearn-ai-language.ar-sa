<div class="Box-sc-g0xbh4-0 eoaCFS js-snippet-clipboard-copy-unpositioned undefined" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div dir="rtl"><markdown-accessiblity-table data-catalyst=""><table>
  <thead>
  <tr>
  <th>lab</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="rtl"><table>
  <thead>
  <tr>
  <th>title</th>
  <th>description</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="rtl">تطوير تطبيق دردشة يدعم الصوت</div></td>
  <td><div dir="rtl">تعرّف على كيفية استخدام Azure AI Foundry لبناء تطبيق ذكاء اصطناعي توليدي يدعم إدخال الصوت.</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="rtl"><h1 tabindex="-1" class="heading-element" dir="rtl">تطوير تطبيق دردشة يدعم الصوت</h1><a id="user-content-تطوير-تطبيق-دردشة-يدعم-الصوت" class="anchor" aria-label="Permalink: تطوير تطبيق دردشة يدعم الصوت" href="#تطوير-تطبيق-دردشة-يدعم-الصوت"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">في هذا التمرين، يمكنك استخدام نموذج الذكاء الاصطناعي التوليدي <em>Phi-4-multimodal-instruct</em> لتوليد ردود للمطالبات التي تتضمن ملفات صوتية. ستطوّر تطبيقًا يقدّم مساعدات ذكاء اصطناعي تتعلق بالمنتجات الطازجة في متجر بقالة باستخدام Azure AI Foundry وخدمة استدلال نماذج Azure AI.</p>
<p dir="rtl">سيستغرق هذا التدريب حوالي <strong>30</strong> دقيقة.</p>
<div class="markdown-heading" dir="rtl"><h2 tabindex="-1" class="heading-element" dir="rtl">إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure</h2><a id="user-content-إنشاء-مشروع-في-مصنع-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure" href="#إنشاء-مشروع-في-مصنع-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">دعنا نبدأ بإنشاء مشروع في مصنع الذكاء الاصطناعي في Azure.</p>
<ol dir="rtl">
<li>
<p dir="rtl">في متصفح الويب، افتح <a href="https://ai.azure.com" rel="nofollow">مدخل Azure AI Foundry</a> على <code>https://ai.azure.com</code> وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك. أغلق أية تلميحات أو أجزاء تشغيل سريع يتم فتحها عندما تقوم بتسجيل الدخول، وإذا لزم الأمر، استخدم شعار <strong>مصنع الذكاء الاصطناعي في Azure</strong> في أعلى اليسار للانتقال إلى الصفحة الرئيسية، والتي تبدو مشابهة للصورة التالية:</p>
<p dir="rtl"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/ai-foundry-home.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/ai-foundry-home.png" alt="لقطة شاشة لمدخل Azure AI Foundry." style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="rtl">في الصفحة الرئيسية، حدد <strong>+ إنشاء مشروع</strong>.</p>
</li>
<li>
<p dir="rtl">في معالج** إنشاء مشروع**، أدخل اسمًا مناسبًا لمشروعك وإذا تم اقتراح مركز موجود، فحدد خيار إنشاء مركز جديد. ثم راجع موارد Azure التي سيتم إنشاؤها تلقائيًا لدعم مركزك ومشروعك.</p>
</li>
<li>
<p dir="rtl">حدد <strong>تخصيص</strong> وحدد الإعدادات التالية لمركزك:</p>
<ul dir="rtl">
<li><strong>اسم المركز</strong>: <em>اسم صالح لمركزك</em></li>
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>Resource group</strong>: <em>إنشاء مجموعة موارد أو تحديدها</em></li>
<li><strong>الموقع</strong>: حدد أيًا من المناطق التالية*:
<ul dir="rtl">
<li>شرق الولايات المتحدة</li>
<li>East US 2</li>
<li>وسط شمال الولايات المتحدة</li>
<li>South Central US</li>
<li>منطقة السويد الوسطى</li>
<li>غرب الولايات المتحدة</li>
<li>غرب الولايات المتحدة الأمريكية 3</li>
</ul>
</li>
<li><strong>توصيل خدمات Azure AI أو Azure OpenAI</strong>: <em>إنشاء مورد جديد لخدمات الذكاء الاصطناعي</em></li>
<li><strong>الاتصال بـ Azure AI Search</strong>: تخطي الاتصال</li>
</ul>
<blockquote>
<p dir="rtl">* في وقت كتابة هذا الدليل، يتوفر نموذج Microsoft <em>Phi-4-multimodal-instruct</em> الذي سنستخدمه في هذا التمرين في هذه المناطق. يمكنك التحقق من أحدث توفر إقليمي لنماذج معينة في <a href="https://learn.microsoft.com/azure/ai-foundry/how-to/deploy-models-serverless-availability#region-availability" rel="nofollow">وثائق Azure AI Foundry</a>. في حال تم الوصول إلى الحد الأقصى للحصة الإقليمية لاحقًا في التمرين، قد تحتاج إلى إنشاء مورد آخر في منطقة مختلفة.</p>
</blockquote>
</li>
<li>
<p dir="rtl">حدد <strong>التالي</strong> لمراجعة التكوين الخاص بك. ثم حدد <strong>إنشاء</strong> وانتظر حتى تكتمل العملية.</p>
</li>
<li>
<p dir="rtl">عند إنشاء مشروعك، أغلق أي تلميحات يتم عرضها وراجع صفحة المشروع في مدخل مصنع الذكاء الاصطناعي في Azure، والذي يجب أن يبدو مشابهة للصورة التالية:</p>
<p dir="rtl"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/ai-foundry-project.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/ai-foundry-project.png" alt="لقطة شاشة توضح تفاصيل مشروع ذكاء اصطناعي في Azure في مدخل مصنع الذكاء الاصطناعي في Azure." style="max-width: 100%;"></a></p>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h2 tabindex="-1" class="heading-element" dir="rtl">توزيع نموذج متعدد الوسائط</h2><a id="user-content-توزيع-نموذج-متعدد-الوسائط" class="anchor" aria-label="Permalink: توزيع نموذج متعدد الوسائط" href="#توزيع-نموذج-متعدد-الوسائط"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">أنت الآن جاهز لنشر نموذج متعدد الوسائط يمكنه دعم الإدخال المستند إلى الصوت. هناك العديد من النماذج التي يمكنك الاختيار من بينها، بما في ذلك نموذج OpenAI <em>gpt-4o</em>. في هذا التمرين، سنستخدم نموذج <em>Phi-4-multimodal-instruct</em>.</p>
<ol dir="rtl">
<li>في شريط الأدوات الموجود في أعلى يمين من صفحة مشروع مصنع الذكاء الاصطناعي في Azure، استخدم أيقونة** ميزات المعاينة**(<strong>⏿</strong>) للتأكد من تمكين ميزة <strong>نشر النماذج في خدمة استنتاج نموذج Azure AI</strong>. تضمن هذه الميزة توفّر توزيع النموذج الخاص بك لخدمة الاستدلال بالذكاء الاصطناعي في Azure، والتي ستستخدمها في كود التطبيق الخاص بك.</li>
<li>في الجزء الموجود على يسار مشروعك، في قسم <strong>أصولي</strong>، حدد صفحة <strong>النماذج + نقاط النهاية</strong>.</li>
<li>في صفحة <strong>النماذج + نقاط النهاية</strong>، في علامة التبويب <strong>عمليات توزيع النماذج</strong>، في القائمة <strong>+ نشر النموذج</strong>، حدّد <strong>توزيع النموذج الأساسي</strong>.</li>
<li>ابحث عن نموذج <strong>Phi-4-multimodal-instruct</strong> في القائمة، ثم حدده وأكّده.</li>
<li>وافق على اتفاقية الترخيص إذا طلب منك ذلك، ثم وزّع النموذج بالإعدادات التالية عن طريق تحديد <strong>تخصيص</strong> في تفاصيل التوزيع:
<ul dir="rtl">
<li><strong>اسم التوزيع</strong>: <em>اسم صالح توزيع نموذجك</em></li>
<li><strong>نوع النشر</strong>: معيار عالمي</li>
<li><strong>تفاصيل التوزيع</strong>: <em>استخدام الإعدادات الافتراضية</em></li>
</ul>
</li>
<li>انتظر حتى تصبح حالة التزويد للتوزيع <strong>مكتملة</strong>.</li>
</ol>
<div class="markdown-heading" dir="rtl"><h2 tabindex="-1" class="heading-element" dir="rtl">أنشئ تطبيق عميل</h2><a id="user-content-أنشئ-تطبيق-عميل" class="anchor" aria-label="Permalink: أنشئ تطبيق عميل" href="#أنشئ-تطبيق-عميل"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">الآن بعد أن نشرت النموذج، يمكنك استخدام النشر في تطبيق عميل.</p>
<blockquote>
<p dir="rtl"><strong>تلميح</strong>: يمكنك اختيار تطوير الحل الخاص بك باستخدام Python أو Microsoft C#. اتبع الإرشادات في القسم المناسب للغة التي اخترتها.</p>
</blockquote>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">إعداد تكوين التطبيق</h3><a id="user-content-إعداد-تكوين-التطبيق" class="anchor" aria-label="Permalink: إعداد تكوين التطبيق" href="#إعداد-تكوين-التطبيق"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="rtl">في مدخل مصنع الذكاء الاصطناعي في Azure، اعرض صفحة <strong>النظرة العامة</strong> لمشروعك.</p>
</li>
<li>
<p dir="rtl">في منطقة <strong>تفاصيل المشروع</strong>، لاحظ <strong>سلسلة الاتصال للمشروع</strong>. ستستخدم سلسلة الاتصال هذه للاتصال بمشروعك في تطبيق العميل.</p>
</li>
<li>
<p dir="rtl">افتح علامة تبويب جديدة للمتصفح (مع إبقاء مدخل مصنع الذكاء الاصطناعي في Azure مفتوحًا في علامة التبويب الموجودة). بعد ذلك في علامة التبويب الجديدة، انتقل إلى <a href="https://portal.azure.com" rel="nofollow">بوابة Azure</a> على <code>https://portal.azure.com</code>؛ وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك إذا طُلب منك ذلك.</p>
<p dir="rtl">أغلق أي إشعارات ترحيبية لرؤية الصفحة الرئيسية لبوابة Azure.</p>
</li>
<li>
<p dir="rtl">استخدم الزر <strong>[&gt;_]</strong> الموجود على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة <em><strong>PowerShell</strong></em> بدون مساحة تخزين في اشتراكك.</p>
<p dir="rtl">يوفّر Cloud Shell واجهة سطر الأوامر في الجزء الموجود في أسفل بوابة Azure. يمكنك تغيير حجم هذا الجزء أو تكبيره لتسهيل العمل فيه.</p>
<blockquote>
<p dir="rtl"><strong>ملاحظة</strong>: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة <em>معالج Bash</em>، فبدّل إلى <em><strong>PowerShell</strong></em>.</p>
</blockquote>
</li>
<li>
<p dir="rtl">في شريط أدوات Cloud Shell، في قائمة <strong>الإعدادات</strong>، حدد <strong>الانتقال إلى الإصدار الكلاسيكي</strong> (هذا مطلوب لاستخدام محرر التعليمات البرمجية).</p>
<p dir="rtl"><strong>تأكد من التبديل إلى الإصدار الكلاسيكي من cloud shell قبل المتابعة.</strong></p>
</li>
<li>
<p dir="rtl">في جزء Cloud Shell، أدخل الأوامر التالية لاستنساخ مستودع GitHub الذي يحتوي على ملفات التعليمات البرمجية لهذا التمرين (اكتب الأمر أو انسخه إلى الحافظة ثم انقر بزر الماوس الأيمن في سطر الأوامر وقم بلصقه كنص عادي):</p>
</li>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>rm -r mslearn-ai-audio -f
git clone https://github.com/MicrosoftLearning/mslearn-ai-language mslearn-ai-audio
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="rm -r mslearn-ai-audio -f
git clone https://github.com/MicrosoftLearning/mslearn-ai-language mslearn-ai-audio" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<blockquote>
<p dir="rtl"><strong>تلميح</strong>: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر <code>cls</code> لتسهيل التركيز على كل مهمة.</p>
</blockquote>
</li>
<li>
<p dir="rtl">بعد استنساخ مخزن بيانات خاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الدردشة:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>cd mslearn-ai-audio/Labfiles/09-audio-chat/python
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="cd mslearn-ai-audio/Labfiles/09-audio-chat/python" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>cd mslearn-ai-audio/Labfiles/09-audio-chat/c-sharp
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="cd mslearn-ai-audio/Labfiles/09-audio-chat/c-sharp" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">في جزء سطر أوامر Cloud Shell، أدخل الأمر التالي لتثبيت المكتبات التي ستستخدمها:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python -m venv labenv
./labenv/bin/Activate.ps1
pip install python-dotenv azure-identity azure-ai-projects azure-ai-inference
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python -m venv labenv
./labenv/bin/Activate.ps1
pip install python-dotenv azure-identity azure-ai-projects azure-ai-inference" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.Identity
dotnet add package Azure.AI.Inference --version 1.0.0-beta.3
dotnet add package Azure.AI.Projects --version 1.0.0-beta.3
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.Identity
dotnet add package Azure.AI.Inference --version 1.0.0-beta.3
dotnet add package Azure.AI.Projects --version 1.0.0-beta.3" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code .env
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code .env" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code appsettings.json
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code appsettings.json" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl">ينبغي أن يفتح الملف في محرر التعليمات البرمجية.</p>
</li>
<li>
<p dir="rtl">في ملف التعليمات البرمجية، استبدل العنصر النائب <strong>your_project_connection_string</strong> بسلسلة الاتصال الخاصة بمشروعك (المنسوخة من صفحة <strong>نظرة عامة</strong> على المشروع في بوابة Azure AI Foundry)، واستبدل العنصر النائب <strong>your_model_deployment</strong> بالاسم الذي قمت بتعيينه لتوزيع نموذج Phi-4-multimodal-instruct الخاص بك.</p>
</li>
<li>
<p dir="rtl">بعد استبدال العناصر النائبة، في محرر التعليمات البرمجية، استخدم الأمر <strong>CTRL+S</strong> أو <strong>انقر بزر الماوس الأيمن &gt; حفظ</strong> لحفظ التغييرات، ثم استخدم الأمر <strong>CTRL+Q</strong> أو <strong>انقر بزر الماوس الأيمن &gt; إنهاء</strong> لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحًا.</p>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">اكتب التعليمة البرمجية للاتصال بمشروعك والحصول على عميل دردشة لنموذجك</h3><a id="user-content-اكتب-التعليمة-البرمجية-للاتصال-بمشروعك-والحصول-على-عميل-دردشة-لنموذجك" class="anchor" aria-label="Permalink: اكتب التعليمة البرمجية للاتصال بمشروعك والحصول على عميل دردشة لنموذجك" href="#اكتب-التعليمة-البرمجية-للاتصال-بمشروعك-والحصول-على-عميل-دردشة-لنموذجك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<blockquote>
<p dir="rtl"><strong>تلميح</strong>: عند إضافة التعليمات البرمجية، تأكد من الحفاظ على المسافة البادئة الصحيحة.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="rtl">أدخل الأمر التالي لتحرير ملف التعليمات البرمجية الذي تم توفيره:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code audio-chat.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code audio-chat.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code Program.cs
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code Program.cs" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">في ملف التعليمات البرمجية، لاحظ العبارات الموجودة في أعلى الملف والتي تمت إضافتها لاستيراد مساحات الأسماء (Namespaces) الضرورية لـ (SDK). بعد ذلك، ابحث عن التعليق <strong>إضافة المراجع</strong>، وأضف التعليمة البرمجية التالية للإشارة إلى المساحات الأساسية في المكتبات التي قمت بتثبيتها مسبقًا:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c"># Add references</span>
<span class="pl-k">from</span> <span class="pl-s1">dotenv</span> <span class="pl-k">import</span> <span class="pl-s1">load_dotenv</span>
<span class="pl-k">from</span> <span class="pl-s1">azure</span>.<span class="pl-s1">identity</span> <span class="pl-k">import</span> <span class="pl-v">DefaultAzureCredential</span>
<span class="pl-k">from</span> <span class="pl-s1">azure</span>.<span class="pl-s1">ai</span>.<span class="pl-s1">projects</span> <span class="pl-k">import</span> <span class="pl-v">AIProjectClient</span>
<span class="pl-k">from</span> <span class="pl-s1">azure</span>.<span class="pl-s1">ai</span>.<span class="pl-s1">inference</span>.<span class="pl-s1">models</span> <span class="pl-k">import</span> (
    <span class="pl-v">SystemMessage</span>,
    <span class="pl-v">UserMessage</span>,
    <span class="pl-v">TextContentItem</span>,
    <span class="pl-v">AudioContentItem</span>,
    <span class="pl-v">InputAudio</span>,
    <span class="pl-v">AudioContentFormat</span>,
)</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="# Add references
from dotenv import load_dotenv
from azure.identity import DefaultAzureCredential
from azure.ai.projects import AIProjectClient
from azure.ai.inference.models import (
    SystemMessage,
    UserMessage,
    TextContentItem,
    AudioContentItem,
    InputAudio,
    AudioContentFormat,
)" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c">// Add references</span>
<span class="pl-k">using</span> <span class="pl-s1">Azure</span><span class="pl-kos">.</span><span class="pl-s1">Identity</span><span class="pl-kos">;</span>
<span class="pl-k">using</span> <span class="pl-s1">Azure</span><span class="pl-kos">.</span><span class="pl-s1">AI</span><span class="pl-kos">.</span><span class="pl-s1">Projects</span><span class="pl-kos">;</span>
<span class="pl-k">using</span> <span class="pl-s1">Azure</span><span class="pl-kos">.</span><span class="pl-s1">AI</span><span class="pl-kos">.</span><span class="pl-s1">Inference</span><span class="pl-kos">;</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="// Add references
using Azure.Identity;
using Azure.AI.Projects;
using Azure.AI.Inference;" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">في الوظيفة <strong>الرئيسية</strong>، تحت التعليق <strong>الحصول على إعدادات التكوين</strong>، لاحظ أن التعليمة البرمجية تقوم بتحميل قيم سلسلة الاتصال بالمشروع واسم نشر النموذج التي قمت بتحديدها في ملف التكوين.</p>
</li>
<li>
<p dir="rtl">ابحث عن التعليق <strong>تهيئة عميل المشروع</strong>، وأضف التعليمة البرمجية التالية للاتصال بمشروع Azure AI Foundry الخاص بك باستخدام بيانات اعتماد Azure التي قمت بتسجيل الدخول بها حاليًا:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c"># Initialize the project client</span>
<span class="pl-s1">project_client</span> <span class="pl-c1">=</span> <span class="pl-v">AIProjectClient</span>.<span class="pl-c1">from_connection_string</span>(
    <span class="pl-s1">conn_str</span><span class="pl-c1">=</span><span class="pl-s1">project_connection</span>,
    <span class="pl-s1">credential</span><span class="pl-c1">=</span><span class="pl-en">DefaultAzureCredential</span>())</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="# Initialize the project client
project_client = AIProjectClient.from_connection_string(
    conn_str=project_connection,
    credential=DefaultAzureCredential())" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c">// Initialize the project client</span>
<span class="pl-k">var</span> <span class="pl-s1">projectClient</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-smi">AIProjectClient</span><span class="pl-kos">(</span><span class="pl-s1">project_connection</span><span class="pl-kos">,</span>
                    <span class="pl-k">new</span> <span class="pl-smi">DefaultAzureCredential</span><span class="pl-kos">(</span><span class="pl-kos">)</span><span class="pl-kos">)</span><span class="pl-kos">;</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="// Initialize the project client
var projectClient = new AIProjectClient(project_connection,
                    new DefaultAzureCredential());" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">ابحث عن التعليق <strong>الحصول على عميل دردشة</strong>، وأضف التعليمة البرمجية التالية لإنشاء عنصر عميل للدردشة مع النموذج الخاص بك:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c"># Get a chat client</span>
<span class="pl-s1">chat_client</span> <span class="pl-c1">=</span> <span class="pl-s1">project_client</span>.<span class="pl-c1">inference</span>.<span class="pl-c1">get_chat_completions_client</span>(<span class="pl-s1">model</span><span class="pl-c1">=</span><span class="pl-s1">model_deployment</span>)</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="# Get a chat client
chat_client = project_client.inference.get_chat_completions_client(model=model_deployment)" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c">// Get a chat client</span>
<span class="pl-smi">ChatCompletionsClient</span> <span class="pl-s1">chat</span> <span class="pl-c1">=</span> <span class="pl-s1">projectClient</span><span class="pl-kos">.</span><span class="pl-en">GetChatCompletionsClient</span><span class="pl-kos">(</span><span class="pl-kos">)</span><span class="pl-kos">;</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="// Get a chat client
ChatCompletionsClient chat = projectClient.GetChatCompletionsClient();" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">اكتب تعليمة برمجية لإرسال مطالبة صوتية تعتمد على عنوان URL</h3><a id="user-content-اكتب-تعليمة-برمجية-لإرسال-مطالبة-صوتية-تعتمد-على-عنوان-url" class="anchor" aria-label="Permalink: اكتب تعليمة برمجية لإرسال مطالبة صوتية تعتمد على عنوان URL" href="#اكتب-تعليمة-برمجية-لإرسال-مطالبة-صوتية-تعتمد-على-عنوان-url"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="rtl">في محرر التعليمات البرمجية لملف <strong>audio-chat.py</strong>، في قسم التكرار، أسفل التعليق <strong>الحصول على رد لإدخال الصوت</strong>، أضف التعليمة البرمجية التالية لإرسال مطالبة تتضمن الصوت التالي:</p>
</li>
<p dir="rtl"></p>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c"># Get a response to audio input</span>
<span class="pl-s1">file_path</span> <span class="pl-c1">=</span> <span class="pl-s">"https://github.com/microsoftlearning/mslearn-ai-language/raw/refs/heads/main/labfiles/09-audio-chat/data/manzanas.mp3"</span>
<span class="pl-s1">response</span> <span class="pl-c1">=</span> <span class="pl-s1">chat_client</span>.<span class="pl-c1">complete</span>(
    <span class="pl-s1">messages</span><span class="pl-c1">=</span>[
        <span class="pl-en">SystemMessage</span>(<span class="pl-s1">system_message</span>),
        <span class="pl-en">UserMessage</span>(
            [
                <span class="pl-en">TextContentItem</span>(<span class="pl-s1">text</span><span class="pl-c1">=</span><span class="pl-s1">prompt</span>),
                {
                    <span class="pl-s">"type"</span>: <span class="pl-s">"audio_url"</span>,
                    <span class="pl-s">"audio_url"</span>: {<span class="pl-s">"url"</span>: <span class="pl-s1">file_path</span>}
                }
            ]
        )
    ]
)
<span class="pl-en">print</span>(<span class="pl-s1">response</span>.<span class="pl-c1">choices</span>[<span class="pl-c1">0</span>].<span class="pl-c1">message</span>.<span class="pl-c1">content</span>)</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="# Get a response to audio input
file_path = &quot;https://github.com/microsoftlearning/mslearn-ai-language/raw/refs/heads/main/labfiles/09-audio-chat/data/manzanas.mp3&quot;
response = chat_client.complete(
    messages=[
        SystemMessage(system_message),
        UserMessage(
            [
                TextContentItem(text=prompt),
                {
                    &quot;type&quot;: &quot;audio_url&quot;,
                    &quot;audio_url&quot;: {&quot;url&quot;: file_path}
                }
            ]
        )
    ]
)
print(response.choices[0].message.content)" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c">// Get a response to audio input</span>
<span class="pl-smi">string</span> <span class="pl-s1">audioUrl</span> <span class="pl-c1">=</span> <span class="pl-s">"https://github.com/microsoftlearning/mslearn-ai-language/raw/refs/heads/main/labfiles/09-audio-chat/data/manzanas.mp3"</span><span class="pl-kos">;</span>
<span class="pl-k">var</span> <span class="pl-s1">requestOptions</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-smi">ChatCompletionsOptions</span><span class="pl-kos">(</span><span class="pl-kos">)</span>
<span class="pl-kos">{</span>
    <span class="pl-s1">Messages</span> <span class="pl-c1">=</span>
    <span class="pl-kos">{</span>
        <span class="pl-k">new</span> <span class="pl-smi">ChatRequestSystemMessage</span><span class="pl-kos">(</span><span class="pl-s1">system_message</span><span class="pl-kos">)</span><span class="pl-kos">,</span>
        <span class="pl-k">new</span> <span class="pl-smi">ChatRequestUserMessage</span><span class="pl-kos">(</span>
            <span class="pl-k">new</span> <span class="pl-smi">ChatMessageTextContentItem</span><span class="pl-kos">(</span><span class="pl-s1">prompt</span><span class="pl-kos">)</span><span class="pl-kos">,</span>
            <span class="pl-k">new</span> <span class="pl-smi">ChatMessageAudioContentItem</span><span class="pl-kos">(</span><span class="pl-k">new</span> <span class="pl-smi">Uri</span><span class="pl-kos">(</span><span class="pl-s1">audioUrl</span><span class="pl-kos">)</span><span class="pl-kos">)</span><span class="pl-kos">)</span><span class="pl-kos">,</span>
    <span class="pl-kos">}</span><span class="pl-kos">,</span>
    <span class="pl-s1">Model</span> <span class="pl-c1">=</span> <span class="pl-s1">model_deployment</span>
<span class="pl-kos">}</span><span class="pl-kos">;</span>
<span class="pl-k">var</span> <span class="pl-s1">response</span> <span class="pl-c1">=</span> <span class="pl-s1">chat</span><span class="pl-kos">.</span><span class="pl-en">Complete</span><span class="pl-kos">(</span><span class="pl-s1">requestOptions</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-s1">Console</span><span class="pl-kos">.</span><span class="pl-en">WriteLine</span><span class="pl-kos">(</span><span class="pl-s1">response</span><span class="pl-kos">.</span><span class="pl-s1">Value</span><span class="pl-kos">.</span><span class="pl-s1">Content</span><span class="pl-kos">)</span><span class="pl-kos">;</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="// Get a response to audio input
string audioUrl = &quot;https://github.com/microsoftlearning/mslearn-ai-language/raw/refs/heads/main/labfiles/09-audio-chat/data/manzanas.mp3&quot;;
var requestOptions = new ChatCompletionsOptions()
{
    Messages =
    {
        new ChatRequestSystemMessage(system_message),
        new ChatRequestUserMessage(
            new ChatMessageTextContentItem(prompt),
            new ChatMessageAudioContentItem(new Uri(audioUrl))),
    },
    Model = model_deployment
};
var response = chat.Complete(requestOptions);
Console.WriteLine(response.Value.Content);" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">استخدم الأمر <strong>CTRL+S</strong> لحفظ التغييرات في ملف التعليمات البرمجية. يمكنك أيضًا إغلاق محرر التعليمات البرمجية باستخدام (<strong>CTRL+Q</strong>) إذا رغبت في ذلك.</p>
</li>
<li>
<p dir="rtl">في جزء سطر أوامر Cloud Shell أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل التطبيق:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python audio-chat.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python audio-chat.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet run" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">عند طلب بذلك، أدخل المطالبة <code>What is this customer saying in English?</code></p>
</li>
<li>
<p dir="rtl">راجع الاستجابة.</p>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">استخدم مطالبة مختلفة</h3><a id="user-content-استخدم-مطالبة-مختلفة" class="anchor" aria-label="Permalink: استخدم مطالبة مختلفة" href="#استخدم-مطالبة-مختلفة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="rtl">في محرر التعليمات البرمجية الخاص بتطبيقك، ابحث عن التعليمة البرمجية التي أضفتها مسبقًا أسفل التعليق <strong>الحصول على رد لإدخال الصوت</strong>. ثم عدّل التعليمات البرمجية كما يلي لتحديد ملف صوتي مختلف:</p>
</li>
<p dir="rtl"></p>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c"># Get a response to audio input</span>
<span class="pl-s1">file_path</span> <span class="pl-c1">=</span> <span class="pl-s">"https://github.com/microsoftlearning/mslearn-ai-language/raw/refs/heads/main/labfiles/09-audio-chat/data/caomei.mp3"</span>
<span class="pl-s1">response</span> <span class="pl-c1">=</span> <span class="pl-s1">chat_client</span>.<span class="pl-c1">complete</span>(
    <span class="pl-s1">messages</span><span class="pl-c1">=</span>[
        <span class="pl-en">SystemMessage</span>(<span class="pl-s1">system_message</span>),
        <span class="pl-en">UserMessage</span>(
            [
                <span class="pl-en">TextContentItem</span>(<span class="pl-s1">text</span><span class="pl-c1">=</span><span class="pl-s1">prompt</span>),
                {
                    <span class="pl-s">"type"</span>: <span class="pl-s">"audio_url"</span>,
                    <span class="pl-s">"audio_url"</span>: {<span class="pl-s">"url"</span>: <span class="pl-s1">file_path</span>}
                }
            ]
        )
    ]
)
<span class="pl-en">print</span>(<span class="pl-s1">response</span>.<span class="pl-c1">choices</span>[<span class="pl-c1">0</span>].<span class="pl-c1">message</span>.<span class="pl-c1">content</span>)</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="# Get a response to audio input
file_path = &quot;https://github.com/microsoftlearning/mslearn-ai-language/raw/refs/heads/main/labfiles/09-audio-chat/data/caomei.mp3&quot;
response = chat_client.complete(
    messages=[
        SystemMessage(system_message),
        UserMessage(
            [
                TextContentItem(text=prompt),
                {
                    &quot;type&quot;: &quot;audio_url&quot;,
                    &quot;audio_url&quot;: {&quot;url&quot;: file_path}
                }
            ]
        )
    ]
)
print(response.choices[0].message.content)" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-c">// Get a response to audio input</span>
<span class="pl-smi">string</span> <span class="pl-s1">audioUrl</span> <span class="pl-c1">=</span> <span class="pl-s">"https://github.com/microsoftlearning/mslearn-ai-language/raw/refs/heads/main/labfiles/09-audio-chat/data/caomei.mp3"</span><span class="pl-kos">;</span>
<span class="pl-k">var</span> <span class="pl-s1">requestOptions</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-smi">ChatCompletionsOptions</span><span class="pl-kos">(</span><span class="pl-kos">)</span>
<span class="pl-kos">{</span>
    <span class="pl-s1">Messages</span> <span class="pl-c1">=</span>
    <span class="pl-kos">{</span>
        <span class="pl-k">new</span> <span class="pl-smi">ChatRequestSystemMessage</span><span class="pl-kos">(</span><span class="pl-s1">system_message</span><span class="pl-kos">)</span><span class="pl-kos">,</span>
        <span class="pl-k">new</span> <span class="pl-smi">ChatRequestUserMessage</span><span class="pl-kos">(</span>
            <span class="pl-k">new</span> <span class="pl-smi">ChatMessageTextContentItem</span><span class="pl-kos">(</span><span class="pl-s1">prompt</span><span class="pl-kos">)</span><span class="pl-kos">,</span>
            <span class="pl-k">new</span> <span class="pl-smi">ChatMessageAudioContentItem</span><span class="pl-kos">(</span><span class="pl-k">new</span> <span class="pl-smi">Uri</span><span class="pl-kos">(</span><span class="pl-s1">audioUrl</span><span class="pl-kos">)</span><span class="pl-kos">)</span><span class="pl-kos">)</span><span class="pl-kos">,</span>
    <span class="pl-kos">}</span><span class="pl-kos">,</span>
    <span class="pl-s1">Model</span> <span class="pl-c1">=</span> <span class="pl-s1">model_deployment</span>
<span class="pl-kos">}</span><span class="pl-kos">;</span>
<span class="pl-k">var</span> <span class="pl-s1">response</span> <span class="pl-c1">=</span> <span class="pl-s1">chat</span><span class="pl-kos">.</span><span class="pl-en">Complete</span><span class="pl-kos">(</span><span class="pl-s1">requestOptions</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-s1">Console</span><span class="pl-kos">.</span><span class="pl-en">WriteLine</span><span class="pl-kos">(</span><span class="pl-s1">response</span><span class="pl-kos">.</span><span class="pl-s1">Value</span><span class="pl-kos">.</span><span class="pl-s1">Content</span><span class="pl-kos">)</span><span class="pl-kos">;</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="// Get a response to audio input
string audioUrl = &quot;https://github.com/microsoftlearning/mslearn-ai-language/raw/refs/heads/main/labfiles/09-audio-chat/data/caomei.mp3&quot;;
var requestOptions = new ChatCompletionsOptions()
{
    Messages =
    {
        new ChatRequestSystemMessage(system_message),
        new ChatRequestUserMessage(
            new ChatMessageTextContentItem(prompt),
            new ChatMessageAudioContentItem(new Uri(audioUrl))),
    },
    Model = model_deployment
};
var response = chat.Complete(requestOptions);
Console.WriteLine(response.Value.Content);" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">استخدم الأمر <strong>CTRL+S</strong> لحفظ التغييرات في ملف التعليمات البرمجية. يمكنك أيضًا إغلاق محرر التعليمات البرمجية باستخدام (<strong>CTRL+Q</strong>) إذا رغبت في ذلك.</p>
</li>
<li>
<p dir="rtl">في جزء سطر أوامر Cloud Shell أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل التطبيق:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python audio-chat.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python audio-chat.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet run" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">عند طلب بذلك، أدخل المطالبة التالية:</p>
</li>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>A customer left this voice message, can you summarize it?
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="A customer left this voice message, can you summarize it?" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">راجع الاستجابة. ثم أدخل <code>quit</code> للخروج من البرنامج.</p>
<blockquote>
<p dir="rtl"><strong>ملاحظة</strong>: في هذا التطبيق البسيط، لم ننفّذ منطق للاحتفاظ بسجل المحادثة؛ لذلك سيعامل النموذج كل مطالبة على أنها طلب جديد دون أي سياق للمطالبة السابقة.</p>
</blockquote>
</li>
<li>
<p dir="rtl">يمكنك الاستمرار في تشغيل التطبيق، واختيار أنواع مختلفة من المطالبات وتجربة مطالبات متنوعة. عند الانتهاء، أدخل <code>quit</code> للخروج من البرنامج.</p>
<p dir="rtl">إذا كان لديك الوقت، فيمكنك تعديل التعليمة البرمجية لاستخدام مطالبة نظام مختلفة وملفات صوتية خاصة بك يمكن الوصول إليها عبر الإنترنت.</p>
<blockquote>
<p dir="rtl"><strong>ملاحظة</strong>: في هذا التطبيق البسيط، لم ننفّذ منطق للاحتفاظ بسجل المحادثة؛ لذلك سيعامل النموذج كل مطالبة على أنها طلب جديد دون أي سياق للمطالبة السابقة.</p>
</blockquote>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h2 tabindex="-1" class="heading-element" dir="rtl">الملخص</h2><a id="user-content-الملخص" class="anchor" aria-label="Permalink: الملخص" href="#الملخص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">في هذا التمرين، استخدمت Azure AI Foundry وAzure AI Inference SDK لإنشاء تطبيق عميل يستخدم نموذجًا متعدد الوسائط لتوليد الردود للصوت.</p>
<div class="markdown-heading" dir="rtl"><h2 tabindex="-1" class="heading-element" dir="rtl">تنظيف</h2><a id="user-content-تنظيف" class="anchor" aria-label="Permalink: تنظيف" href="#تنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">إذا كنت قد أنهيت استكشاف Azure AI Foundry، يجب عليك حذف الموارد التي أنشأتها في هذا التمرين لتجنب تكاليف Azure غير الضرورية.</p>
<ol dir="rtl">
<li>ارجع إلى علامة تبويب المتصفح التي تحتوي على بوابة Azure (أو أعد فتح <a href="https://portal.azure.com" rel="nofollow">بوابة Azure</a> في <code>https://portal.azure.com</code> في علامة تبويب متصفح جديدة) واعرض محتويات مجموعة الموارد التي نشرت فيها الموارد المستخدمة في هذا التدريب.</li>
<li>على شريط الأدوات، حدد <strong>حذف مجموعة الموارد</strong>.</li>
<li>أدخل اسم مجموعة الموارد وأكّد أنك تريد حذفها.</li>
</ol>
</article></div>
