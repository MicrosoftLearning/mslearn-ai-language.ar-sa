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
  <td><div dir="auto">التعرف على الكلام وتجميعه (إصدار Azure AI Foundry)</div></td>
  <td><div dir="auto">Module 4 - Create speech-enabled apps with Azure AI services</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>


<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">التعرف على الكلام وتجميعه</h1><a id="user-content-التعرف-على-الكلام-وتجميعه" class="anchor" aria-label="Permalink: التعرف على الكلام وتجميعه" href="#التعرف-على-الكلام-وتجميعه"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><strong>الكلام بالذكاء الاصطناعي في Azure</strong> هي خدمة توفر وظائف متعلقة بالكلام، بما في ذلك:</p>
<ul dir="rtl">
<li>واجهة برمجة تطبيقات <em>تحويل الكلام إلى نص</em> تمكنك من تنفيذ التعرّف على الكلام (تحويل الكلمات المنطوقة المسموعة إلى نص).</li>
<li>واجهة برمجة تطبيقات <em>تحويل النص إلى كلام</em> تمكنك من تنفيذ تركيب الكلام (تحويل النص إلى كلام مسموع).</li>
</ul>
<p dir="auto">في هذا التمرين، ستستخدم كلا من واجهات برمجة التطبيقات هذه لتنفيذ تطبيق ساعة التحدث.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong> تم تصميم هذا التدريب لإكماله في Azure cloud shell، حيث لا يتم دعم الوصول المباشر إلى الأجهزة الصوتية لجهاز الكمبيوتر الخاص بك. لذلك سيستخدم النشاط العملي ملفات الصوت لعمليات دفق مدخلات ومخرجات الكلام. يتم توفير التعليمات البرمجية لتحقيق نفس النتائج باستخدام ميكروفون ومكبر صوت كمرجع.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure</h2><a id="user-content-إنشاء-مشروع-في-مصنع-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure" href="#إنشاء-مشروع-في-مصنع-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">دعنا نبدأ بإنشاء مشروع في مصنع الذكاء الاصطناعي في Azure.</p>
<ol dir="rtl">
<li>
<p dir="auto">في متصفح الويب، افتح <a href="https://ai.azure.com" rel="nofollow">مدخل Azure AI Foundry</a> على <code>https://ai.azure.com</code> وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك. أغلق أية تلميحات أو أجزاء تشغيل سريع يتم فتحها عندما تقوم بتسجيل الدخول، وإذا لزم الأمر، استخدم شعار <strong>مصنع الذكاء الاصطناعي في Azure</strong> في أعلى اليسار للانتقال إلى الصفحة الرئيسية، والتي تبدو مشابهة للصورة التالية:</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/ai-foundry-home.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/ai-foundry-home.png" alt="لقطة شاشة لمدخل Azure AI Foundry." style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="auto">في الصفحة الرئيسية، حدد <strong>+ إنشاء مشروع</strong>.</p>
</li>
<li>
<p dir="auto">في معالج <strong>إنشاء مشروع</strong>، أدخل اسمًا صالحًا لمشروعك، وإذا تم اقتراح مركز موجود، فاختر خيار إنشاء مركز جديد. ثم راجع موارد Azure التي سيتم إنشاؤها تلقائيًا لدعم مركزك ومشروعك.</p>
</li>
<li>
<p dir="auto">حدد <strong>تخصيص</strong> وحدد الإعدادات التالية لمركزك:</p>
<ul dir="rtl">
<li><strong>اسم المركز</strong>: <em>اسم صالح لمركزك</em></li>
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>Resource group</strong>: <em>إنشاء مجموعة موارد أو تحديدها</em></li>
<li><strong>الموقع</strong>: اختر أي منطقة متاحة</li>
<li><strong>اتصال خدمات الذكاء الاصطناعي في Azure أو Azure OpenAI</strong>: <em>إنشاء مورد جديد لخدمات الذكاء الاصطناعي</em></li>
<li><strong>ربط Azure AI Search</strong>: <em>أنشئ مورد Azure AI Search جديد باسم فريد</em></li>
</ul>
</li>
<li>
<p dir="auto">حدد <strong>التالي</strong> لمراجعة التكوين الخاص بك. ثم حدد <strong>إنشاء</strong> وانتظر حتى تكتمل العملية.</p>
</li>
<li>
<p dir="auto">عند إنشاء مشروعك، أغلق أي تلميحات يتم عرضها وراجع صفحة المشروع في مدخل مصنع الذكاء الاصطناعي في Azure، والذي يجب أن يبدو مشابهة للصورة التالية:</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/ai-foundry-project.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-language.ar-sa/blob/main/Instructions/media/ai-foundry-project.png" alt="لقطة شاشة توضح تفاصيل مشروع ذكاء اصطناعي في Azure في مدخل مصنع الذكاء الاصطناعي في Azure." style="max-width: 100%;"></a></p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إعداد وتكوين تطبيق الساعة الناطقة</h2><a id="user-content-إعداد-وتكوين-تطبيق-الساعة-الناطقة" class="anchor" aria-label="Permalink: إعداد وتكوين تطبيق الساعة الناطقة" href="#إعداد-وتكوين-تطبيق-الساعة-الناطقة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="auto">في مدخل مصنع الذكاء الاصطناعي في Azure، اعرض صفحة <strong>النظرة العامة</strong> لمشروعك.</p>
</li>
<li>
<p dir="auto">في منطقة <strong>تفاصيل المشروع</strong>، لاحظ <strong>سلسلة الاتصال الخاصة بالمشروع</strong>و <strong>موقعه</strong> لمشروعك. ستستخدم سلسلة الاتصال للاتصال بمشروعك في تطبيق عميل، وستحتاج إلى الموقع للاتصال بنقطة نهاية Azure AI Services Speech.</p>
</li>
<li>
<p dir="auto">افتح علامة تبويب جديدة للمتصفح (مع إبقاء مدخل مصنع الذكاء الاصطناعي في Azure مفتوحًا في علامة التبويب الموجودة). بعد ذلك في علامة التبويب الجديدة، انتقل إلى <a href="https://portal.azure.com" rel="nofollow">بوابة Azure</a> على <code>https://portal.azure.com</code>؛ وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك إذا طُلب منك ذلك.</p>
</li>
<li>
<p dir="auto">استخدم الزر <strong>[&gt;_]</strong> الموجود على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة <em><strong>PowerShell</strong></em>. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة <em>معالج Bash</em>، فبدّل إلى <em><strong>PowerShell</strong></em>.</p>
</blockquote>
</li>
<li>
<p dir="auto">في شريط أدوات Cloud Shell، في قائمة <strong>الإعدادات</strong>، حدد <strong>الانتقال إلى الإصدار الكلاسيكي</strong> (هذا مطلوب لاستخدام محرر التعليمات البرمجية).</p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر <code>cls</code> لتسهيل التركيز على كل مهمة.</p>
</blockquote>
</li>
<li>
<p dir="auto">في جزء PowerShell، أدخل الأوامر التالية لاستنساخ مستودع GitHub لهذا التمرين:</p>
</li>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>rm -r mslearn-ai-language -f
git clone https://github.com/microsoftlearning/mslearn-ai-language mslearn-ai-language
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="rm -r mslearn-ai-language -f
git clone https://github.com/microsoftlearning/mslearn-ai-language mslearn-ai-language" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><em><strong>الآن اتبع الخطوات الخاصة بلغة البرمجة التي اخترتها.</strong></em></p>

<li>
<p dir="auto">بعد استنساخ مخزن البيانات الخاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الساعة الناطقة:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>cd mslearn-ai-language/labfiles/07b-speech/python/speaking-clock
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="cd mslearn-ai-language/labfiles/07b-speech/python/speaking-clock" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>cd mslearn-ai-language/labfiles/07b-speech/c-sharp/speaking-clock
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="cd mslearn-ai-language/labfiles/07b-speech/c-sharp/speaking-clock" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">في جزء سطر أوامر Cloud Shell، أدخل الأمر التالي لتثبيت المكتبات التي ستستخدمها:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python -m venv labenv
./labenv/bin/Activate.ps1
pip install python-dotenv azure-identity azure-ai-projects azure-cognitiveservices-speech==1.42.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python -m venv labenv
./labenv/bin/Activate.ps1
pip install python-dotenv azure-identity azure-ai-projects azure-cognitiveservices-speech==1.42.0" tabindex="0" role="button">
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
dotnet add package Azure.AI.Projects --prerelease
dotnet add package Microsoft.CognitiveServices.Speech --version 1.42.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.Identity
dotnet add package Azure.AI.Projects --prerelease
dotnet add package Microsoft.CognitiveServices.Speech --version 1.42.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:</p>
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
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code appsettings.json
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
<p dir="auto">يتم فتح الملف في محرر التعليمات البرمجية.</p>

<li>
<p dir="auto">ملف التعليمات البرمجية، استبدل أماكن وضع** your_project_endpoint** و<strong>your_location</strong>بسلسلة الاتصال والموقع الخاص بمشروعك (تم نسخها من صفحة <strong>نظرة عامة</strong> على المشروع في البوابة الإلكترونية الخاصة بـ Azure AI Foundry)</p>
</li>
<li>
<p dir="auto">بعد استبدال العناصر النائبة، استخدم الأمر <strong>CTRL+S</strong> لحفظ التغييرات ثم استخدم الأمر <strong>CTRL+Q</strong> لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحWا.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمات برمجية لاستخدام Azure AI Speech SDK</h2><a id="user-content-إضافة-تعليمات-برمجية-لاستخدام-azure-ai-speech-sdk" class="anchor" aria-label="Permalink: إضافة تعليمات برمجية لاستخدام Azure AI Speech SDK" href="#إضافة-تعليمات-برمجية-لاستخدام-azure-ai-speech-sdk"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: عند إضافة التعليمات البرمجية، تأكد من الحفاظ على المسافة البادئة الصحيحة.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="auto">أدخل الأمر التالي لتحرير ملف التعليمات البرمجية الذي تم توفيره:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code speaking-clock.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code speaking-clock.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code Program.cs
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

<li>
<p dir="auto">في أعلى ملف التعليمات البرمجية، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. بعد ذلك، وضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Speech SDK بواسطة مورد Azure AI Services في مشروع Azure AI Foundry الخاص بك.</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Import namespaces
from dotenv import load_dotenv
from azure.ai.projects.models import ConnectionType
from azure.identity import DefaultAzureCredential
from azure.core.credentials import AzureKeyCredential
from azure.ai.projects import AIProjectClient
import azure.cognitiveservices.speech as speech_sdk</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Import namespaces
using Azure.Identity;
using Azure.AI.Projects;
using Microsoft.CognitiveServices.Speech;
using Microsoft.CognitiveServices.Speech.Audio;</code></pre></div>

<li>
<p dir="auto">في الوظيفة <strong>الرئيسية</strong>، تحت التعليق <strong>الحصول على إعدادات التكوين</strong>، لاحظ أن التعليمات البرمجية تقوم بتحميل قيم سلسلة الاتصال وموقع المشروع اللذين قمت بتحديدهم في ملف التكوين.</p>
</li>
<li>
<p dir="auto">أضف التعليمات البرمجية التالية ضمن التعليق <strong>Get AI Speech الخاص بنقطة النهاية والمفتاح من المشروع</strong>:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get AI Services key from the project
project_client = AIProjectClient.from_connection_string(
    conn_str=project_connection,
    credential=DefaultAzureCredential())
<br>
ai_svc_connection = project_client.connections.get_default(
  connection_type=ConnectionType.AZURE_AI_SERVICES,
  include_credentials=True, 
)
<br>
ai_svc_key = ai_svc_connection.key</code></pre></div>
<p dir="dir"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>/ Get AI Services key from the project
var projectClient = new AIProjectClient(project_connection,
                    new DefaultAzureCredential());
<br>
ConnectionResponse aiSvcConnection = projectClient.GetConnectionsClient().GetDefaultConnection(ConnectionType.AzureAIServices, true);
<br>
var apiKeyAuthProperties = aiSvcConnection.Properties as ConnectionPropertiesApiKeyAuth;
<br>
var aiSvcKey = apiKeyAuthProperties.Credentials.Key;</code></pre></div>
<p dir="auto">تتصل هذه التعليمات البرمجية بمشروع Azure AI Foundry الخاص بك، وتحصل على المورد الافتراضي لـ AI Services المتصل، وتسترد مفتاح المصادقة المطلوب لاستخدامه.</p>

<li>
<p dir="auto">ضمن تعليق<strong>تكوين خدمة الكلام</strong>، أضف التعليمات البرمجية التالية لاستخدام مفتاح AI Services ومنطقة المشروع الخاصة بك لتكوين اتصالك بنقطة نهاية Azure AI Services Speech</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Configure speech service
speech_config = speech_sdk.SpeechConfig(ai_svc_key, location)
print('Ready to use speech service in:', speech_config.region)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Configure speech service
speechConfig = SpeechConfig.FromSubscription(aiSvcKey, location);
Console.WriteLine("Ready to use speech service in " + speechConfig.Region);</code></pre></div>
<li>
<p dir="auto">احفظ التغييرات (<em>CTRL+S</em>)، ولكن اترك محرر التعليمات البرمجية مفتوحا.</p>
</li>s
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تشغيل التطبيق</h2><a id="user-content-تشغيل-التطبيق" class="anchor" aria-label="Permalink: تشغيل التطبيق" href="#تشغيل-التطبيق"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">حتى الآن، لا يقوم التطبيق بأي شيء آخر غير الاتصال بمشروع Azure AI Foundry لاسترداد التفاصيل اللازمة لاستخدام خدمة الكلام، ولكن من المفيد تشغيلها والتحقق من أنها تعمل قبل إضافة وظيفة الكلام.</p>
<ol dir="rtl">
<li>
<p dir="auto">في سطر الأوامر أسفل محرر التعليمات البرمجية، أدخل أمر Azure CLI التالي لتحديد حساب Azure الذي تم تسجيل الدخول إليه لجلسة العمل:</p>
</li>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>az account show
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="az account show" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto">يجب أن تتضمن نواتج JSON تفاصيل حساب Azure والاشتراك الذي تعمل فيه (والذي يجب أن يكون نفس الاشتراك الذي أنشأت فيه مشروع Azure AI Foundry.)</p>
<p dir="auto">يستخدم تطبيقك بيانات اعتماد Azure للسياق الذي يتم تشغيله فيه لمصادقة الاتصال بمشروعك. في بيئة الإنتاج، قد يتم تكوين التطبيق للتشغيل باستخدام هوية مدارة. في بيئة التطوير هذه، سيستخدم بيانات اعتماد جلسة عمل cloud shell المصادق عليها.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: يمكنك تسجيل الدخول إلى Azure في بيئة التطوير باستخدام <code>az login</code> الأمر Azure CLI. في هذه الحالة، تكون cloud shell قد سجلت الدخول بالفعل باستخدام بيانات اعتماد Azure التي قمت بتسجيل الدخول إلى البوابة الإلكترونية بها؛ لذا، فإن تسجيل الدخول بشكل صريح غير ضروري. لمعرفة المزيد حول استخدام Azure CLI للمصادقة على Azure، راجع <a href="https://learn.microsoft.com/cli/azure/authenticate-azure-cli" rel="nofollow">المصادقة على Azure باستخدام Azure CLI</a>.</p>
</blockquote>

<li>
<p dir="auto">في سطر الأوامر، أدخل الأمر التالي الخاص باللغة لتشغيل تطبيق الساعة الناطقة:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python speaking-clock.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python speaking-clock.py" tabindex="0" role="button">
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

<li>
<p dir="auto">إذا كنت تستخدم C#، فيمكنك تجاهل أي تحذيرات حول استخدام عامل <strong>الانتظار</strong> في الطرق غير المتزامنة - وسنصلح ذلك لاحقاً. يجب أن تعرض التعليمات البرمجية منطقة مورد خدمة الكلام الذي سيستخدمه التطبيق. يشير التشغيل الناجح إلى أن التطبيق قد اتصل بمشروع Azure AI Foundry واسترد المفتاح الذي يحتاجه لاستخدام خدمة Azure AI Speech service.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمة برمجية للتعرّف على الكلام</h2><a id="user-content-إضافة-تعليمة-برمجية-للتعرّف-على-الكلام" class="anchor" aria-label="Permalink: إضافة تعليمة برمجية للتعرّف على الكلام" href="#إضافة-تعليمة-برمجية-للتعرّف-على-الكلام"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك <strong>SpeechConfig</strong> لخدمة الكلام في مورد Azure AI Services، يمكنك استخدام واجهة برمجة تطبيقات <strong>تحويل الكلام إلى نص</strong> للتعرّف على الكلام ونسخه إلى نص.</p>
<p dir="auto">في هذا الإجراء، يتم التقاط مدخلات الكلام من ملف صوتي، والذي يمكنك تشغيله هنا:</p>
<p dir="auto"></p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>الأساسية</strong>، لاحظ أن التعليمات البرمجية تستخدم دالة <strong>TranscribeCommand</strong> لقبول الإدخال المنطوق. ثم في دالة <strong>TranscribeCommand</strong>، ضمن التعليق <strong>تكوين التعرّف على الكلام</strong>، أضف التعليمة البرمجية المناسب أدناه لإنشاء عميل <strong>SpeechRecognizer</strong> الذي يمكن استخدامه للتعرّف على الكلام ونسخه من ملف صوتي:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Configure speech recognition
current_dir = os.getcwd()
audioFile = current_dir + '/time.wav'
audio_config = speech_sdk.AudioConfig(filename=audioFile)
speech_recognizer = speech_sdk.SpeechRecognizer(speech_config, audio_config)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Configure speech recognition
string audioFile = "time.wav";
using AudioConfig audioConfig = AudioConfig.FromWavFileInput(audioFile);
using SpeechRecognizer speechRecognizer = new SpeechRecognizer(speechConfig, audioConfig);</code></pre></div>

<li>
<p dir="auto">في الدالة <strong>TranscribeCommand</strong>، ضمن التعليق <strong>معالجة إدخال الكلام</strong>، أضف التعليمة البرمجية التالية للاستماع إلى الإدخال المنطوق، مع الحرص على عدم استبدال التعليمة البرمجية الموجودة في نهاية الدالة التي تُرجع الأمر:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Process speech input
print("Listening...")
speech = speech_recognizer.recognize_once_async().get()
if speech.reason == speech_sdk.ResultReason.RecognizedSpeech:
   command = speech.text
   print(command)
else:
   print(speech.reason)
   if speech.reason == speech_sdk.ResultReason.Canceled:
       cancellation = speech.cancellation_details
       print(cancellation.reason)
       print(cancellation.error_details)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Process speech input
Console.WriteLine("Listening...");
SpeechRecognitionResult speech = await speechRecognizer.RecognizeOnceAsync();
if (speech.Reason == ResultReason.RecognizedSpeech)
{
   command = speech.Text;
   Console.WriteLine(command);
}
else
{
   Console.WriteLine(speech.Reason);
   if (speech.Reason == ResultReason.Canceled)
   {
       var cancellation = CancellationDetails.FromResult(speech);
       Console.WriteLine(cancellation.Reason);
       Console.WriteLine(cancellation.ErrorDetails);
   }
}</code></pre></div>

<li>
<p dir="auto">احفظ التغييرات (<em>CTRL+S</em>)، ثم في سطر الأوامر أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل البرنامج:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python speaking-clock.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python speaking-clock.py" tabindex="0" role="button">
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

<li>
<p dir="auto">راجع المخرجات من التطبيق، الذي يجب أن "يسمع" الكلام بنجاح في الملف الصوتي وإرجاع استجابة مناسبة (لاحظ أن Azure cloud shell قد يكون قيد التشغيل على خادم في منطقة زمنية مختلفة عن منطقتك!)</p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: إذا واجه SpeechRecognizer خطئًا، فإنه يكون نتيجة "الإلغاء". ستعرض التعليمات البرمجية في التطبيق بعد ذلك رسالة الخطأ. السبب الأكثر احتمالاً هو مفتاح غير صحيح أو منطقة غير صحيحة في ملف التكوين.</p>
</blockquote>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تركيب الكلام</h2><a id="user-content-تركيب-الكلام" class="anchor" aria-label="Permalink: تركيب الكلام" href="#تركيب-الكلام"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يقبل تطبيق الساعة الناطقة الإدخال المنطوق، ولكنه لا يتحدث في الواقع! لنصلح ذلك عن طريق إضافة تعليمة برمجية لتركيب الكلام.</p>
<p dir="auto">مرة أخرى، نظرًا لقيود الأجهزة الخاصة بـ cloud shell سنوجه مخرجات الكلام المركبة إلى ملف.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>الأساسية</strong> لبرنامجك، لاحظ أن التعليمات البرمجية تستخدم الدالة <strong>TellTime</strong> لإخبار المستخدم بالوقت الحالي.</p>
</li>
<li>
<p dir="auto">في الدالة <strong>TellTime</strong>، ضمن التعليق <strong>تكوين تركيب</strong> الكلام، أضف التعليمات البرمجية التالية لإنشاء <strong>عميل SpeechSynthesizer</strong> الذي يمكن استخدامه لإنشاء إخراج منطوق:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Configure speech synthesis
output_file = "output.wav"
speech_config.speech_synthesis_voice_name = "en-GB-RyanNeural"
audio_config = speech_sdk.audio.AudioConfig(filename=output_file)
speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config, audio_config,)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Configure speech synthesis
var outputFile = "output.wav";
speechConfig.SpeechSynthesisVoiceName = "en-GB-RyanNeural";
using var audioConfig = AudioConfig.FromWavFileOutput(outputFile);
using SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer(speechConfig, audioConfig);</code></pre></div>

<li>
<p dir="auto">في الدالة <strong>TellTime</strong>، ضمن التعليق <strong>تركيب الإخراج المنطوق</strong>، أضف التعليمات البرمجية التالية لإنشاء إخراج منطوق، مع الحرص على عدم استبدال التعليمات البرمجية في نهاية الدالة التي تطبع الاستجابة:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Synthesize spoken output
speak = speech_synthesizer.speak_text_async(response_text).get()
if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
   print(speak.reason)
else:
   print("Spoken output saved in " + outputFile)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Synthesize spoken output
SpeechSynthesisResult speak = await speechSynthesizer.SpeakTextAsync(responseText);
if (speak.Reason != ResultReason.SynthesizingAudioCompleted)
{
   Console.WriteLine(speak.Reason);
}
else
{
   Console.WriteLine("Spoken output saved in " + outputFile);
}</code></pre></div>

<li>
<p dir="auto">احفظ التغييرات (<em>CTRL+S</em>)، ثم في سطر الأوامر أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل البرنامج:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python speaking-clock.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python speaking-clock.py" tabindex="0" role="button">
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

<li>
<p dir="auto">راجع المخرجات من التطبيق، والذي يجب أن يشير إلى أنه تم حفظ المخرجات المنطوقة في ملف.</p>
</li>
<li>
<p dir="auto">إذا كان لديك مشغل وسائط قادر على تشغيل الملفات الصوتية .wav، ففي شريط الأدوات لجزء cloud shell، استخدم <strong>الزر Upload/Download files</strong> لتنزيل الملف الصوتي من مجلد التطبيق، ثم قم بتشغيله:</p>
<p dir="auto"><strong>Python</strong></p>
<p dir="auto">/home/<em>user</em><code>/mslearn-ai-language/Labfiles/07b-speech/Python/speaking-clock/output.wav</code></p>
<p dir="auto"><strong>#C</strong></p>
<p dir="auto">/home/<em>user</em><code>/mslearn-ai-language/Labfiles/07b-speech/C-Sharp/speaking-clock/output.wav</code></p>
<p dir="auto">يجب أن يكون صوت الملف النهائي مشابهًا لهذا:</p>
<p dir="auto"></p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استخدام لغة Speech Synthesis Markup (SSML)</h2><a id="user-content-استخدام-لغة-speech-synthesis-markup-ssml" class="anchor" aria-label="Permalink: استخدام لغة Speech Synthesis Markup (SSML)" href="#استخدام-لغة-speech-synthesis-markup-ssml"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تمكنك لغة ترميز تركيب الكلام (SSML) من تخصيص طريقة تركيب كلامك باستخدام تنسيق يستند إلى XML.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>TellTime</strong>، استبدل كافة التعليمات البرمجية الحالية ضمن التعليق <strong>تركيب النتيجة المنطوقة</strong> بالتعليمات البرمجية التالية (اترك التعليمات البرمجية ضمن التعليق <strong>طباعة الاستجابة</strong>):</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Synthesize spoken output<br>
responseSsml = &quot; &#92;<br>
    &lt;speak version='1.0' xmlns='http://www.w3.org/2001/10/synthesis' xml:lang='en-US'&gt; &#92;<br>
        &lt;voice name='en-GB-LibbyNeural'&gt; &#92;<br>
            &#123;&#125; &#92;<br>
            &lt;break strength='weak'/&gt; &#92;<br>
            Time to end this lab! &#92;<br>
        &lt;/voice&gt; &#92;<br>
    &lt;/speak&gt;&quot;.format(response_text)<br>
speak = speech_synthesizer.speak_ssml_async(responseSsml).get()<br>
if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:<br>
    print(speak.reason)<br>
else:<br>
    print(&quot;Spoken output saved in &quot; + outputFile)<br></code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Synthesize spoken output<br>
string responseSsml = $@&quot;<br>
   &lt;speak version='1.0' xmlns='http://www.w3.org/2001/10/synthesis' xml:lang='en-US'&gt;<br>
       &lt;voice name='en-GB-LibbyNeural'&gt;<br>
           &#123;responseText&#125;<br>
           &lt;break strength='weak'/&gt;<br>
           Time to end this lab!<br>
       &lt;/voice&gt;<br>
   &lt;/speak&gt;&quot;;<br>
SpeechSynthesisResult speak = await speechSynthesizer.SpeakSsmlAsync(responseSsml);<br>
if (speak.Reason != ResultReason.SynthesizingAudioCompleted)<br>
&#123;<br>
   Console.WriteLine(speak.Reason);<br>
&#125;<br>
else<br>
&#123;<br>
    Console.WriteLine(&quot;Spoken output saved in &quot; + outputFile);<br>
&#125;</code></pre></div>

<li>
<p dir="auto">احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد <strong>الساعة الناطقة</strong> وأدخل الأمر التالي لتشغيل البرنامج:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python speaking-clock.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python speaking-clock.py" tabindex="0" role="button">
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

<li>
<p dir="auto">راجع المخرجات من التطبيق، والذي يجب أن يشير إلى أنه تم حفظ المخرجات المنطوقة في ملف.</p>
</li>
<li>
<p dir="auto">مرة أخرى، إذا كان لديك مشغل وسائط قادر على تشغيل الملفات الصوتية .wav، في شريط الأدوات لجزء cloud shell، فاستخدم <strong>الزر Upload/Download files</strong> لتنزيل الملف الصوتي من مجلد التطبيق، ثم قم بتشغيله:</p>
<p dir="auto"><strong>Python</strong></p>
<p dir="auto">/home/<em>user</em><code>/mslearn-ai-language/Labfiles/07b-speech/Python/speaking-clock/output.wav</code></p>
<p dir="auto"><strong>#C</strong></p>
<p dir="auto">/home/<em>user</em><code>/mslearn-ai-language/Labfiles/07b-speech/C-Sharp/speaking-clock/output.wav</code></p>
<p dir="auto">يجب أن يكون صوت الملف النهائي مشابهًا لهذا:</p>
<p dir="auto"></p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف</h2><a id="user-content-تنظيف" class="anchor" aria-label="Permalink: تنظيف" href="#تنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا انتهيت من استكشاف Azure AI Speech فيجب عليك حذف الموارد التي قمت بإنشائها في هذا التدريب لتجنب تكبد تكاليف Azure غير ضرورية.</p>
<ol dir="rtl">
<li>ارجع إلى علامة تبويب المتصفح التي تحتوي على بوابة Azure (أو أعد فتح <a href="https://portal.azure.com" rel="nofollow">بوابة Azure</a> في <code>https://portal.azure.com</code> في علامة تبويب متصفح جديدة) واعرض محتويات مجموعة الموارد التي نشرت فيها الموارد المستخدمة في هذا التدريب.</li>
<li>على شريط الأدوات، حدد <strong>حذف مجموعة الموارد</strong>.</li>
<li>أدخل اسم مجموعة الموارد وأكّد أنك تريد حذفها.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">ماذا لو كان لديك ميكروفون ومكبر صوت؟</h2><a id="user-content-ماذا-لو-كان-لديك-ميكروفون-ومكبر-صوت" class="anchor" aria-label="Permalink: ماذا لو كان لديك ميكروفون ومكبر صوت؟" href="#ماذا-لو-كان-لديك-ميكروفون-ومكبر-صوت"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">سوف تستخدم ملفات صوتية لمدخلات ومخرجات الكلام في هذا التدريب. دعونا نرى كيف يمكن تعديل التعليمات البرمجية لاستخدام الأجهزة الصوتية.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">استخدام التعرف على الكلام من خلال ميكروفون</h3><a id="user-content-استخدام-التعرف-على-الكلام-من-خلال-ميكروفون" class="anchor" aria-label="Permalink: استخدام التعرف على الكلام من خلال ميكروفون" href="#استخدام-التعرف-على-الكلام-من-خلال-ميكروفون"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا كان لديك ميكروفون، يمكنك استخدام التعليمات البرمجية التالية لالتقاط المدخلات المنطوقة للتعرف على الكلام:</p>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Configure speech recognition
audio_config = speech_sdk.AudioConfig(use_default_microphone=True)
speech_recognizer = speech_sdk.SpeechRecognizer(speech_config, audio_config)
print('Speak now...')
<br>
# Process speech input
speech = speech_recognizer.recognize_once_async().get()
if speech.reason == speech_sdk.ResultReason.RecognizedSpeech:
    command = speech.text
    print(command)
else:
    print(speech.reason)
    if speech.reason == speech_sdk.ResultReason.Canceled:
        cancellation = speech.cancellation_details
        print(cancellation.reason)
        print(cancellation.error_details)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Configure speech recognition
using AudioConfig audioConfig = AudioConfig.FromDefaultMicrophoneInput();
using SpeechRecognizer speechRecognizer = new SpeechRecognizer(speechConfig, audioConfig);
Console.WriteLine("Speak now...");
<br>
SpeechRecognitionResult speech = await speechRecognizer.RecognizeOnceAsync();
if (speech.Reason == ResultReason.RecognizedSpeech)
{
    command = speech.Text;
    Console.WriteLine(command);
}
else
{
    Console.WriteLine(speech.Reason);
    if (speech.Reason == ResultReason.Canceled)
    {
        var cancellation = CancellationDetails.FromResult(speech);
        Console.WriteLine(cancellation.Reason);
        Console.WriteLine(cancellation.ErrorDetails);
    }
}</code></pre></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: الميكروفون الافتراضي للنظام هو مدخل الصوت الافتراضي، لذلك يمكنك أيضا حذف AudioConfig تمامًا!</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">استخدام تركيب الكلام بواسطة مكبر صوت</h3><a id="user-content-استخدام-تركيب-الكلام-بواسطة-مكبر-صوت" class="anchor" aria-label="Permalink: استخدام تركيب الكلام بواسطة مكبر صوت" href="#استخدام-تركيب-الكلام-بواسطة-مكبر-صوت"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا كان لديك مكبر صوت، يمكنك استخدام التعليمات البرمجية التالية لتجميع الكلام.</p>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code>response_text = 'The time is {}:{:02d}'.format(now.hour,now.minute)
<br>
# Configure speech synthesis
speech_config.speech_synthesis_voice_name = "en-GB-RyanNeural"
audio_config = speech_sdk.audio.AudioOutputConfig(use_default_speaker=True)
speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config, audio_config)
<br>
# Synthesize spoken output
speak = speech_synthesizer.speak_text_async(response_text).get()
if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
    print(speak.reason)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>var now = DateTime.Now;
string responseText = "The time is " + now.Hour.ToString() + ":" + now.Minute.ToString("D2");
<br>
// Configure speech synthesis
speechConfig.SpeechSynthesisVoiceName = "en-GB-RyanNeural";
using var audioConfig = AudioConfig.FromDefaultSpeakerOutput();
using SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer(speechConfig, audioConfig);
<br>
// Synthesize spoken output
SpeechSynthesisResult speak = await speechSynthesizer.SpeakTextAsync(responseText);
if (speak.Reason != ResultReason.SynthesizingAudioCompleted)
{
    Console.WriteLine(speak.Reason);
}</code></pre></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: مكبر الصوت الافتراضي للنظام هي مُخرج الصوت الافتراضي، لذلك يمكنك أيضا حذف AudioConfig تمامًا!</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لمزيد من المعلومات حول استخدام واجهات برمجة تطبيقات <strong>تحويل الكلام إلى نص</strong> <strong>والنص إلى كلام</strong>، راجع <a href="https://learn.microsoft.com/azure/ai-services/speech-service/index-speech-to-text" rel="nofollow">وثائق تحويل الكلام إلى نص ووثائق</a> <a href="https://learn.microsoft.com/azure/ai-services/speech-service/index-text-to-speech" rel="nofollow">وتحويل النص إلى كلام</a>.</p>
</article></div></div>
