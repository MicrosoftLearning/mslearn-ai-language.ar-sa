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
  <td><div dir="auto">تحليل النص</div></td>
  <td><div dir="auto">Module 3 - Develop natural language processing solutions</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">تحليل النص</h1><a id="user-content-تحليل-النص" class="anchor" aria-label="Permalink: تحليل النص" href="#تحليل-النص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><strong>تدعم Azure Language</strong> تحليل النص، بما في ذلك اكتشاف اللغة وتحليل التوجه واستخراج العبارة الرئيسية والتعرف على الكيان.</p>
<p dir="auto">على سبيل المثال، لنفترض أن وكالة سفر تريد معالجة تقييمات الفنادق التي تم إرسالها إلى موقع الويب الخاص بالشركة. باستخدام Azure AI Language، يمكنها تحديد اللغة التي تتم كتابة كل تقييم بها، أو التوجه (الإيجابي أو المحايد أو السلبي) للتقييمات، والعبارات الرئيسية التي قد تشير إلى الموضوعات الرئيسية التي تمت مناقشتها في التقييم، والكيانات المسماة، مثل الأماكن أو المعالم أو الأشخاص المذكورين في التقييمات.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">توفير مورد <em>Azure AI Language</em></h2><a id="user-content-توفير-مورد-azure-ai-language" class="anchor" aria-label="Permalink: توفير مورد Azure AI Language" href="#توفير-مورد-azure-ai-language"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد <strong>خدمة Azure AI Language</strong> في اشتراك Azure لديك.</p>
<ol dir="rtl">
<li>افتح مدخل Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</li>
<li>حدد <strong>Create a resource.</strong></li>
<li>في حقل البحث، ابحث عن <strong>خدمة اللغة</strong>. ثم، في النتائج، حدد <strong>إنشاء</strong> ضمن <strong>خدمة اللغة</strong>.</li>
<li>حدد <strong>Continue to create your resource</strong>.</li>
<li>توفير المورد باستخدام الإعدادات التالية:
<ul dir="rtl">
<li><strong>الاشتراك</strong>: <em>اشتراك Azure الخاص بك</em>.</li>
<li><strong>مجموعة الموارد</strong>: <em>اختيار مجموعة موارد أو إنشاءها</em>.</li>
<li><strong>المنطقة</strong>: <em>اختر أي منطقة متوفرة</em></li>
<li><strong>الاسم</strong>: <em>أدخل اسمًا مميزًا</em>.</li>
<li><strong>مستوى الأسعار</strong>: حدد <strong>F0</strong> (<em>مجاني</em>)، أو <strong>S</strong> (<em>قياسي</em>) إذا لم يكن F متوفراً.</li>
<li><strong>إشعار الذكاء الاصطناعي المسؤول</strong>: أوافق.</li>
</ul>
</li>
<li>حدد <strong>مراجعة + إنشاء</strong>، ثم حدد <strong>إنشاء</strong> لتوفير المورد.</li>
<li>انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</li>
<li>اعرض صفحة <strong>المفاتيح ونقطة النهاية</strong> في قسم <strong>إدارة الموارد</strong>. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التمرين.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية</h2><a id="user-content-الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية" href="#الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">ستقوم بتطوير تطبيق تحليلات النصور باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في مستودع GitHub.</p>
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
<p dir="auto">تم توفير تطبيقات لكل من C# وPython، وكذلك ملف نصي نموذجي ستستخدمه لاختبار التلخيص. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد Azure AI Language الخاص بك.</p>
<ol dir="rtl">
<li>
<p dir="auto">في Visual Studio Code، في جزء <strong>Explorer</strong>، استعرض مجلد <strong>Labfiles/01-analyze-text</strong> ووسع نطاق المجلد <strong>CSharp</strong> أو <strong>Python</strong> استناداً إلى تفضيلات اللغة ومجلد <strong>text-analysis</strong> الذي يحتوي عليها. يحتوي كل مجلد على الملفات الخاصة باللغة للتطبيق الذي ستقوم بدمج وظيفة التحليلات لنصوص Azure AI Language فيه.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن فوق مجلد <strong>text-analysis</strong> الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم ثبّت حزمة Azure AI Language Text Analytics SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك. بالنسبة إلى تدريب Python، قم أيضا بتثبيت الحزمة <code>dotenv</code>:</p>
</li>
<p dir="rtl"><strong>:#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto text-left" ><pre class="notranslate"><code>dotnet add package Azure.AI.TextAnalytics --version 5.3.0
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
pip install python-dotenv
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-ai-textanalytics==5.3.0
pip install python-dotenv" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<li>
<p dir="auto">في جزء <strong>Explorer</strong>، في مجلد <strong>text-analysis</strong>، افتح ملف التكوين للغة المفضلة لديك</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
</li>
<li>
<p dir="auto">قم بتحديث قيم التكوين لتضمين <strong>نقطة النهاية</strong> و<strong>مفتاح</strong> من مورد Azure Language الذي أنشأته (متوفر في صفحة <strong>المفاتيح ونقطة النهاية</strong> لمورد Azure AI Language في مدخل Microsoft Azure)</p>
</li>
<li>
<p dir="auto">احفظ ملف التكوين.</p>
</li>
<li>
<p dir="auto">لاحظ أن مجلد <strong>text-analysis</strong> يحتوي على ملف تعليمات برمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: text-analysis.py</li>
</ul>
<p dir="auto">افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// import namespaces
using Azure;
using Azure.AI.TextAnalytics;</code></pre></div>
<p dir="rtl"><strong>Python</strong>: text-analysis.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># import namespaces
from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient</code></pre></div>
<li>
<p dir="auto">في الدالة <strong>Main</strong>، لاحظ أنه تم بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية خدمة لغة الذكاء الاصطناعي في Azure والمفتاح من ملف التكوين. ثم ابحث عن التعليق <strong>إنشاء عميل باستخدام نقطة النهاية والمفتاح</strong>، وأضف التعليمة البرمجية التالية لإنشاء عميل لواجهة برمجة تطبيقات تحليل النص:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Create client using endpoint and key
AzureKeyCredential credentials = new AzureKeyCredential(aiSvcKey);
Uri endpoint = new Uri(aiSvcEndpoint);
TextAnalyticsClient aiClient = new TextAnalyticsClient(endpoint, credentials);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: text-analysis.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Create client using endpoint and key
credential = AzureKeyCredential(ai_key)
ai_client = TextAnalyticsClient(endpoint=ai_endpoint, credential=credential)</code></pre></div>
<li>
<p dir="auto">احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>text-analysis</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
<ul dir="rtl">
<li><strong>:#C</strong> <code>dotnet run</code></li>
<li><strong>Python</strong>: <code>python text-analysis.py</code></li>
</ul>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: يمكنك استخدام أيقونة <strong>تكبير حجم اللوحة</strong> (<strong>^</strong>) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.</p>
</blockquote>
</li>
<li>
<p dir="auto">لاحظ المخرجات حيث يجب تشغيل التعليمات البرمجية دون خطأ، مع عرض محتويات كل ملف نصي للتعليقات في مجلد <strong>التعليقات</strong>. ينشئ التطبيق بنجاح عميلاً لواجهة برمجة تطبيقات Text Analytics ولكنه لا يستفيد منه. سنصلح ذلك في الإجراء التالي.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمة برمجية للكشف عن اللغة</h2><a id="user-content-إضافة-تعليمة-برمجية-للكشف-عن-اللغة" class="anchor" aria-label="Permalink: إضافة تعليمة برمجية للكشف عن اللغة" href="#إضافة-تعليمة-برمجية-للكشف-عن-اللغة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن قمت بإنشاء عميل لواجهة برمجة التطبيقات، دعنا نستخدمه للكشف عن اللغة التي تتم كتابة كل تقييم بها.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>Main</strong> لبرنامجك، ابحث عن التعليق <strong>Get language</strong>. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة للكشف عن اللغة في كل مستند للتقييمات:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get language
DetectedLanguage detectedLanguage = aiClient.DetectLanguage(text);
Console.WriteLine($"\nLanguage: {detectedLanguage.Name}");</code></pre></div>
<p dir="rtl"><strong>Python</strong>: text-analysis.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get language
detectedLanguage = ai_client.detect_language(documents=[text])[0]
print('\nLanguage: {}'.format(detectedLanguage.primary_language.name))</code></pre></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: <em>في هذا المثال، يتم تحليل كل تقييم بشكل فردي، مما يؤدي إلى استدعاء منفصل للخدمة لكل ملف. يتمثل النهج البديل في إنشاء مجموعة من المستندات وتمريرها إلى الخدمة في استدعاء واحد. وفي كلا النهجين، تتكون الاستجابة من الخدمة من مجموعة من المستندات؛ ولهذا السبب تم تحديد فهرس المستند الأول (والوحيد) في الاستجابة ([0]) في تعليمة Python البرمجية أعلاه.</em></p>
</blockquote>
<li>
<p dir="auto">احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>text-analysis</strong> وأعد تشغيل البرنامج.</p>
</li>
<li>
<p dir="auto">لاحظ المخرجات، مع ملاحظة أنه يتم تحديد لغة كل تقييم في هذه المرة.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمة برمجية لتقييم التوجه</h2><a id="user-content-إضافة-تعليمة-برمجية-لتقييم-التوجه" class="anchor" aria-label="Permalink: إضافة تعليمة برمجية لتقييم التوجه" href="#إضافة-تعليمة-برمجية-لتقييم-التوجه"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><em>تحليل التوجه</em> هو أسلوب شائع الاستخدام لتصنيف النص على أنه <em>إيجابي</em> أو <em>سلبي</em> (أو احتمالية كونه * محايد <em>أو</em> مختلط*). يتم استخدامه عادة لتحليل منشورات الوسائط الاجتماعية والتعليقات على المنتجات والعناصر الأخرى حيث قد يوفر توجه النص نتائج تحليلات مفيدة.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>Main</strong> لبرنامجك، ابحث عن التعليق <strong>Get sentiment</strong>. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة للكشف عن التوجه في كل مستند للتقييمات:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get sentiment
DocumentSentiment sentimentAnalysis = aiClient.AnalyzeSentiment(text);
Console.WriteLine($"\nSentiment: {sentimentAnalysis.Sentiment}");</code></pre></div>
<p dir="rtl"><strong>Python</strong>: text-analysis.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get sentiment
sentimentAnalysis = ai_client.analyze_sentiment(documents=[text])[0]
print("\nSentiment: {}".format(sentimentAnalysis.sentiment))</code></pre></div>
<li>
<p dir="auto">احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>text-analysis</strong> وأعد تشغيل البرنامج.</p>
</li>
<li>
<p dir="auto">لاحظ المخرجات، مع ملاحظة أنه تم الكشف عن توجه التعليقات.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمة برمجية لتحديد العبارات الرئيسية</h2><a id="user-content-إضافة-تعليمة-برمجية-لتحديد-العبارات-الرئيسية" class="anchor" aria-label="Permalink: إضافة تعليمة برمجية لتحديد العبارات الرئيسية" href="#إضافة-تعليمة-برمجية-لتحديد-العبارات-الرئيسية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">قد يكون من المفيد تحديد العبارات الرئيسية في نص أساسي للمساعدة في تحديد الموضوعات الرئيسية التي يناقشها.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>Main</strong> لبرنامجك، ابحث عن التعليق <strong>Get key phrases</strong>. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة للكشف عن العبارات الرئيسية في كل مستند للتقييمات:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get key phrases
KeyPhraseCollection phrases = aiClient.ExtractKeyPhrases(text);
if (phrases.Count > 0)
{
  Console.WriteLine("\nKey Phrases:");
  foreach(string phrase in phrases)
  {
    Console.WriteLine($"\t{phrase}");
  }
}
</code></pre></div>
<p dir="rtl"><strong>Python</strong>: text-analysis.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get key phrases
phrases = ai_client.extract_key_phrases(documents=[text])[0].key_phrases
if len(phrases) > 0:
  print("\nKey Phrases:")
  for phrase in phrases:
    print('\t{}'.format(phrase))</code></pre></div>
<li>
<p dir="auto">احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>text-analysis</strong> وأعد تشغيل البرنامج.</p>
</li>
<li>
<p dir="auto">لاحظ المخرجات، مع ملاحظة أن كل مستند يحتوي على عبارات رئيسية تعطي بعض نتائج التحليلات حول ما يتعلق به التعليقات.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة رمز لاستخراج الكيانات</h2><a id="user-content-إضافة-رمز-لاستخراج-الكيانات" class="anchor" aria-label="Permalink: إضافة رمز لاستخراج الكيانات" href="#إضافة-رمز-لاستخراج-الكيانات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في كثير من الأحيان، تشير المستندات أو النصوص الأخرى إلى الأشخاص أو الأماكن أو الفترات الزمنية أو الكيانات الأخرى. يمكن لواجهة برمجة تطبيقات  text Analytics الكشف عن فئات متعددة (وفئات فرعية) للكيان في النص الخاص بك.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>Main</strong> لبرنامجك، ابحث عن التعليق <strong>Get entities</strong>. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة لتحديد الكيانات المذكورة في كل تقييم:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get entities
CategorizedEntityCollection entities = aiClient.RecognizeEntities(text);
if (entities.Count > 0)
{
  Console.WriteLine("\nEntities:");
  foreach(CategorizedEntity entity in entities)
  {
    Console.WriteLine($"\t{entity.Text} ({entity.Category})");
  }
}</code></pre></div>
<p dir="rtl"><strong>Python</strong>: text-analysis.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get entities
entities = ai_client.recognize_entities(documents=[text])[0].entities
if len(entities) > 0:
  print("\nEntities")
  for entity in entities:
    print('\t{} ({})'.format(entity.text, entity.category))</code></pre></div>
<li>
<p dir="auto">احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>text-analysis</strong> وأعد تشغيل البرنامج.</p>
</li>
<li>
<p dir="auto">لاحظ المخرجات، مع ملاحظة الكيانات التي تم الكشف عنها في النص.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمة برمجية لاستخراج الكيانات المرتبطة</h2><a id="user-content-إضافة-تعليمة-برمجية-لاستخراج-الكيانات-المرتبطة" class="anchor" aria-label="Permalink: إضافة تعليمة برمجية لاستخراج الكيانات المرتبطة" href="#إضافة-تعليمة-برمجية-لاستخراج-الكيانات-المرتبطة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بالإضافة إلى الكيانات المصنفة، يمكن لواجهة برمجة تطبيقات Text Analytics الكشف عن الكيانات التي توجد لها ارتباطات معروفة بمصادر البيانات، مثل ويكيبيديا.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>Main</strong> لبرنامجك، ابحث عن التعليق <strong>Get linked entities</strong>. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة لتحديد الكيانات المرتبطة المذكورة في كل تقييم:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get linked entities
LinkedEntityCollection linkedEntities = aiClient.RecognizeLinkedEntities(text);
if (linkedEntities.Count > 0)
{
  Console.WriteLine("\nLinks:");
  foreach(LinkedEntity linkedEntity in linkedEntities)
  {
    Console.WriteLine($"\t{linkedEntity.Name} ({linkedEntity.Url})");
  }
}</code></pre></div>
<p dir="rtl"><strong>Python</strong>: text-analysis.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get linked entities
entities = ai_client.recognize_linked_entities(documents=[text])[0].entities
if len(entities) > 0:
  print("\nLinks")
  for linked_entity in entities:
    print('\t{} ({})'.format(linked_entity.name, linked_entity.url))</code></pre></div>
<li>
<p dir="auto">احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>text-analysis</strong> وأعد تشغيل البرنامج.</p>
</li>
<li>
<p dir="auto">لاحظ المخرجات، مع ملاحظة الكيانات المرتبطة التي تم تحديدها.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف الموارد</h2><a id="user-content-تنظيف-الموارد" class="anchor" aria-label="Permalink: تنظيف الموارد" href="#تنظيف-الموارد"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا انتهيت من استكشاف خدمة Azure AI Language، فيمكنك حذف الموارد التي قمت بإنشائها في هذا التمرين. وإليك الطريقة:</p>
<ol dir="rtl">
<li>
<p dir="auto">افتح مدخل Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</p>
</li>
<li>
<p dir="auto">استعرض للوصول إلى مورد Azure AI Language الذي أنشأته في هذا المختبر.</p>
</li>
<li>
<p dir="auto">في صفحة المورد، حدد <strong>حذف</strong> واتبع الإرشادات لحذف المورد.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لمزيد من المعلومات حول استخدام <strong>Azure AI Language</strong>، راجع <a href="https://learn.microsoft.com/azure/ai-services/language-service/" rel="nofollow">وثائق</a>.</p>
</article></div></div>
