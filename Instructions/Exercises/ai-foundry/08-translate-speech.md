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
  <td><div dir="auto">ترجمة الكلام</div></td>
  <td><div dir="auto">Module 8 - Translate speech with Azure AI Speech</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">ترجمة الكلام</h1><a id="user-content-ترجمة-الكلام" class="anchor" aria-label="Permalink: ترجمة الكلام" href="#ترجمة-الكلام"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يتضمن Azure AI Speech واجهة برمجة تطبيقات لترجمة الكلام يمكنك استخدامها لترجمة اللغة المنطوقة. على سبيل المثال، افترض أنك تريد إعداد تطبيق مترجم يمكن للأشخاص استخدامه عند السفر في أماكن لا يتحدثون فيها اللغة المحلية. سيكون بإمكانهم قول عبارات مثل «أين المحطة؟» أو «أحتاج الوصول إلى صيدلية» بلغتهم الخاصة، وترجمتها إلى اللغة المحلية.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong> يتطلب هذا التمرين استخدام كمبيوتر مزود بسماعات/سماعات رأس. للحصول على تجربة مثلى، يلزم وجود ميكروفون أيضاً. قد تتمكن بعض البيئات الظاهرية المستضافة من التقاط الصوت من الميكروفون المحلي، ولكن إذا لم ينجح ذلك (أو لم يكن لديك ميكروفون على الإطلاق)، فيمكنك استخدام ملف صوتي متوفر لإدخال الكلام. اتبع الإرشادات بعناية، حيث ستحتاج إلى تحديد خيارات مختلفة استناداً إلى ما إذا كنت تستخدم ميكروفوناً أو ملفاً صوتياً.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">توفير مورد <em>Azure AI Speech</em></h2><a id="user-content-توفير-مورد-azure-ai-speech" class="anchor" aria-label="Permalink: توفير مورد Azure AI Speech" href="#توفير-مورد-azure-ai-speech"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل مورداً في اشتراكك، فسيتعين عليك توفير مورد <strong>Azure AI Speech</strong>.</p>
<ol dir="rtl">
<li>افتح مدخل Microsoft Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</li>
<li>في حقل البحث في الأعلى، ابحث عن <strong>خدمات الذكاء الاصطناعي في Azure</strong> واضغط على <strong>دخول</strong>، ثم حدد <strong>إنشاء</strong> ضمن <strong>خدمة الكلام</strong> في النتائج.</li>
<li>إنشاء المورد بالإعدادات التالية:
<ul dir="rtl">
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>مجموعة الموارد</strong>: <em>اختيار مجموعة موارد أو إنشاءها</em></li>
<li><strong>المنطقة</strong>: <em>اختر أي منطقة متوفرة</em></li>
<li><strong>الاسم</strong>: <em>أدخل اسماً فريداً</em></li>
<li><strong>طبقة الأسعار</strong>: حدد <strong>F0</strong> (<em>مجاني</em>)، أو <strong>S</strong> (<em>قياسي</em>) إذا لم يكن F متوفراً.</li>
<li><strong>إشعار الذكاء الاصطناعي المسؤول</strong>: أوافق.</li>
</ul>
</li>
<li>حدد <strong>مراجعة + إنشاء</strong>، ثم حدد <strong>إنشاء</strong> لتوفير المورد.</li>
<li>انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</li>
<li>اعرض صفحة <strong>المفاتيح ونقطة النهاية</strong>. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التمرين.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية</h2><a id="user-content-الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية" href="#الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">ستطور تطبيق الكلام لديك باستخدام تعليمة Visual Studio البرمجية. ملفات التعليمات البرمجية متوفرة لتطبيقك في مستودع GitHub.</p>
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
<p dir="auto">تم توفير تطبيقات لكل من C# وPython. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد الكلام بالذكاء الاصطناعي في Azure الخاص بك.</p>
<ol dir="rtl">
<li>
<p dir="auto">في تعليمة Visual Studio البرمجية في جزء <strong>مستكشف</strong>، استعرض للوصول إلى مجلد <strong>Labfiles/08-speech-translation</strong> وقم بتوسيع المجلد ** CSharp** أو <strong>Python</strong> استنادًا إلى تفضيلات اللغة ومجلد <strong>المترجم</strong> الذي يحتوي عليه. يحتوي كل مجلد على ملفات التعليمات البرمجية الخاصة باللغة الخاصة بأحد التطبيقات الذي ستدمج وظيفة Azure AI Speech.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن فوق مجلد <strong>المترجم</strong> الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم عليك تثبيت حزمة Azure AI Vision SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:</p>
</li>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Microsoft.CognitiveServices.Speech --version 1.30.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Microsoft.CognitiveServices.Speech --version 1.30.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-cognitiveservices-speech==1.30.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-cognitiveservices-speech==1.30.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">في جزء <strong>مستكشف</strong>، في مجلد <strong>المترجم</strong>، افتح ملف التكوين للغة المفضلة لديك</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
</li>
<li>
<p dir="auto">يمكن تحديث قيم التكوين لتضمين <strong>المنطقة</strong> <strong>ومفتاح</strong> من مورد Azure AI Speech الذي أنشأته (المتوفر في صفحة <strong>المفاتيح ونقطة النهاية</strong> لمورد Azure AI Speech في Azure  لديك في مدخل Microsoft Azure ).</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: تأكد من إضافة <em>المنطقة</em> لموردك، وليس نقطة النهاية!</p>
</blockquote>
</li>
<li>
<p dir="auto">احفظ ملف التكوين.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمة برمجية لاستخدام Speech SDK</h2><a id="user-content-إضافة-تعليمة-برمجية-لاستخدام-speech-sdk" class="anchor" aria-label="Permalink: إضافة تعليمة برمجية لاستخدام Speech SDK" href="#إضافة-تعليمة-برمجية-لاستخدام-speech-sdk"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="auto">لاحظ أن مجلد<strong>المترجم</strong> يحتوي على ملف تعليمات برمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: translator.py</li>
</ul>
<p dir="auto">افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Import namespaces
using Microsoft.CognitiveServices.Speech;
using Microsoft.CognitiveServices.Speech.Audio;
using Microsoft.CognitiveServices.Speech.Translation;</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translator.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Import namespaces
import azure.cognitiveservices.speech as speech_sdk</code></pre></div>

<li>
<p dir="auto">في الدالة <strong>الرئيسية</strong>، لاحظ أن التعليمات البرمجية لتحميل مفتاح خدمةAzure AI Speec والمنطقة من ملف التكوين قد تم توفيرها بالفعل. يجب استخدام هذه المتغيرات لإنشاء <strong>SpeechTranslationConfig</strong> لمورد Azure AI Speec، والذي ستستخدمه لترجمة الإدخال المنطوق. أضف التعليمات البرمجية التالية ضمن التعليق <strong>تكوين الترجمة</strong>:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Configure translation
translationConfig = SpeechTranslationConfig.FromSubscription(aiSvcKey, aiSvcRegion);
translationConfig.SpeechRecognitionLanguage = "en-US";
translationConfig.AddTargetLanguage("fr");
translationConfig.AddTargetLanguage("es");
translationConfig.AddTargetLanguage("hi");
Console.WriteLine("Ready to translate from " + translationConfig.SpeechRecognitionLanguage);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translator.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Configure translation
translation_config = speech_sdk.translation.SpeechTranslationConfig(ai_key, ai_region)
translation_config.speech_recognition_language = 'en-US'
translation_config.add_target_language('fr')
translation_config.add_target_language('es')
translation_config.add_target_language('hi')
print('Ready to translate from',translation_config.speech_recognition_language)</code></pre></div>

<li>
<p dir="auto">ستستخدم <strong>SpeechTranslationConfig</strong> لترجمة الكلام إلى نص، ولكنك ستستخدم أيضًا <strong>SpeechConfig</strong> لتجميع الترجمات في الكلام. أضف التعليمات البرمجية التالية ضمن التعليق <strong>تكوين الكلام</strong>:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Configure speech
speechConfig = SpeechConfig.FromSubscription(aiSvcKey, aiSvcRegion);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translator.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Configure speech
speech_config = speech_sdk.SpeechConfig(ai_key, ai_region)</code></pre></div>

<li>
<p dir="auto">احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>لمترجم</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
</li>
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
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python translator.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python translator.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">إذا كنت تستخدم C#، فيمكنك تجاهل أي تحذيرات بشأن استخدام عامل <strong>الانتظار</strong> في الطرق غير المتزامنة - وسنصلح ذلك لاحقاً. يجب أن تعرض التعليمات البرمجية رسالة تفيد بأنها جاهزة للترجمة من en-US ومطالبتك بلغة مستهدفة. اضغط على دخول لإنهاء البرنامج.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنفيذ ترجمة الكلام</h2><a id="user-content-تنفيذ-ترجمة-الكلام" class="anchor" aria-label="Permalink: تنفيذ ترجمة الكلام" href="#تنفيذ-ترجمة-الكلام"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك <strong>تكوين ترجمة كلام</strong> لخدمة Azure AI Speech، يمكنك استخدام واجهة برمجة التطبيقات ترجمة Azure AI Speech للتعرف على الكلام وترجمته.</p>
<blockquote>
<p dir="auto"><strong>مهم</strong>: يتضمن هذا القسم تعليمات لإجراءين بديلين. اتبع الإجراء الأول إذا كان لديك ميكروفون يعمل. اتبع الإجراء الثاني إذا كنت تريد محاكاة الإدخال المنطوق باستخدام ملف صوتي.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إذا كان لديك ميكروفون يعمل</h3><a id="user-content-إذا-كان-لديك-ميكروفون-يعمل" class="anchor" aria-label="Permalink: إذا كان لديك ميكروفون يعمل" href="#إذا-كان-لديك-ميكروفون-يعمل"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>الأساسية</strong> لبرنامجك، لاحظ أن التعليمات البرمجية تستخدم الدالة <strong>ترجمة</strong> لترجمة الإدخال المنطوق.</p>
</li>
<li>
<p dir="auto">في الدالة <strong>ترجمة</strong> ، ضمن التعليق <strong>ترجمة الكلام</strong>، أضف التعليمات البرمجية التالية لإنشاء عميل<strong>منظم الترجمة</strong> الذي يمكن استخدامه للتعرف على الكلام وترجمته باستخدام ميكروفون النظام الافتراضي للإدخال.</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Translate speech
using AudioConfig audioConfig = AudioConfig.FromDefaultMicrophoneInput();
using TranslationRecognizer translator = new TranslationRecognizer(translationConfig, audioConfig);
Console.WriteLine("Speak now...");
TranslationRecognitionResult result = await translator.RecognizeOnceAsync();
Console.WriteLine($"Translating '{result.Text}'");
translation = result.Translations[targetLanguage];
Console.OutputEncoding = Encoding.UTF8;
Console.WriteLine(translation);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translator.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Translate speech
audio_config = speech_sdk.AudioConfig(use_default_microphone=True)
translator = speech_sdk.translation.TranslationRecognizer(translation_config, audio_config = audio_config)
print("Speak now...")
result = translator.recognize_once_async().get()
print('Translating "{}"'.format(result.text))
translation = result.translations[targetLanguage]
print(translation)</code></pre></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong> التعليمات البرمجية في تطبيقك تترجم الإدخال إلى جميع اللغات الثلاث في مكالمة واحدة. يتم عرض الترجمة للغة معينة فقط، ولكن يمكنك استرداد أي من الترجمات عن طريق تحديد رمز اللغة الهدف في مجموعة <strong>الترجمات</strong> للنتيجة.</p>
</blockquote>

<li>
<p dir="auto">انتقل الآن إلى قسم<strong>تشغيل البرنامج</strong> أدناه.</p>
</li>
</ol>
<hr>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">بدلاً من ذلك، استخدم إدخال الصوت من ملف</h3><a id="user-content-بدلاً-من-ذلك-استخدم-إدخال-الصوت-من-ملف" class="anchor" aria-label="Permalink: بدلاً من ذلك، استخدم إدخال الصوت من ملف" href="#بدلاً-من-ذلك-استخدم-إدخال-الصوت-من-ملف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="auto">في النافذة الطرفية، أدخل الأمر التالي لتثبيت مكتبة يمكنك استخدامها لتشغيل الملف الصوتي:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>dotnet add package System.Windows.Extensions --version 4.6.0</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translator.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code>pip install playsound==1.3.0</code></pre></div>

<li>
<p dir="auto">في ملف التعليمات البرمجية لبرنامجك، ضمن استيراد مساحة الاسم الموجودة، أضف التعليمات البرمجية التالية لاستيراد المكتبة التي ثبتها للتو:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>using System.Media;</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translator.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code>from playsound import playsound</code></pre></div>

<li>
<p dir="auto">في الدالة <strong>الأساسية</strong> لبرنامجك، لاحظ أن التعليمات البرمجية تستخدم الدالة <strong>ترجمة</strong> لترجمة الإدخال المنطوق. ثم في الدالة <strong>ترجمة</strong> ، ضمن التعليق <strong>ترجمة كلام</strong>، أضف التعليمات البرمجية التالية لإنشاء عميل<strong>منظم ترجمة</strong> الذي يمكن استخدامه للتعرف على الكلام وترجمته من ملف.</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Translate speech
string audioFile = "station.wav";
SoundPlayer wavPlayer = new SoundPlayer(audioFile);
wavPlayer.Play();
using AudioConfig audioConfig = AudioConfig.FromWavFileInput(audioFile);
using TranslationRecognizer translator = new TranslationRecognizer(translationConfig, audioConfig);
Console.WriteLine("Getting speech from file...");
TranslationRecognitionResult result = await translator.RecognizeOnceAsync();
Console.WriteLine($"Translating '{result.Text}'");
translation = result.Translations[targetLanguage];
Console.OutputEncoding = Encoding.UTF8;
Console.WriteLine(translation);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translator.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Translate speech
audioFile = 'station.wav'
playsound(audioFile)
audio_config = speech_sdk.AudioConfig(filename=audioFile)
translator = speech_sdk.translation.TranslationRecognizer(translation_config, audio_config = audio_config)
print("Getting speech from file...")
result = translator.recognize_once_async().get()
print('Translating "{}"'.format(result.text))
translation = result.translations[targetLanguage]
print(translation)</code></pre></div>

</ol>
<hr>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">قم بتشغيل البرنامج.</h3><a id="user-content-قم-بتشغيل-البرنامج" class="anchor" aria-label="Permalink: قم بتشغيل البرنامج." href="#قم-بتشغيل-البرنامج"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="auto">احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>لمترجم</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
</li>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
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
<p dir="rtl"><strong>Python</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python translator.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python translator.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">عند المطالبة، أدخل رمز لغة صالحا (<em>fr</em>أو <em>es</em>أو <em>hi</em>)، ثم إذا كنت تستخدم ميكروفونا، فتحدث بوضوح وقل « أين المحطة؟» أو بعض العبارات الأخرى التي قد تستخدمها عند السفر إلى الخارج. ينبغي نسخ البرنامج إدخالك المنطوق ويترجمه إلى اللغة التي حددتها (الفرنسية أو الإسبانية أو الهندية). كرر هذه العملية، مع تجربة كل لغة يدعمها التطبيق. عند الانتهاء، اضغط على دخول لإنهاء البرنامج.</p>
<p dir="auto">يمنحك منظم الترجمة حوالي 5 ثوان للتحدث. في حالة اكتشاف عدم وجود إدخال منطوق، فإنه ينتج نتيجة "لا تطابق". قد لا تعرض دائمًا الترجمة إلى الهندية على نحوٍ صحيحٍ في نافذة وحدة التحكم بسبب مشكلات ترميز الأحرف.</p>
</li>
</ol>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: تترجم التعليمات البرمجية في تطبيقك الإدخال إلى جميع اللغات الثلاث في مكالمة واحدة. يتم عرض الترجمة للغة معينة فقط، ولكن يمكنك استرداد أي من الترجمات عن طريق تحديد رمز اللغة الهدف في مجموعة <strong>الترجمات</strong> للنتيجة.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تجميع الترجمة إلى كلام</h2><a id="user-content-تجميع-الترجمة-إلى-كلام" class="anchor" aria-label="Permalink: تجميع الترجمة إلى كلام" href="#تجميع-الترجمة-إلى-كلام"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يترجم تطبيقك الآن الإدخال المنطوق إلى نص؛ والتي قد تكون كافية إذا كنت بحاجة إلى طلب المساعدة من شخص ما أثناء السفر. ولكن من المفضل أن تكون الترجمة منطوقة بصوت مناسب.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الدالة <strong>ترجمة</strong>، ضمن التعليق <strong>تركيب الترجمة</strong>، أضف التعليمات البرمجية التالية لاستخدام عميل <strong>المركب الكلامي</strong> لتجميع الترجمة ككلمة من خلال السماعة الافتراضية:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Program.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Synthesize translation
var voices = new Dictionary<string, string>
                {
                    ["fr"] = "fr-FR-HenriNeural",
                    ["es"] = "es-ES-ElviraNeural",
                    ["hi"] = "hi-IN-MadhurNeural"
                };
speechConfig.SpeechSynthesisVoiceName = voices[targetLanguage];
using SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer(speechConfig);
SpeechSynthesisResult speak = await speechSynthesizer.SpeakTextAsync(translation);
if (speak.Reason != ResultReason.SynthesizingAudioCompleted)
{
    Console.WriteLine(speak.Reason);
}</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translator.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Synthesize translation
voices = {
        "fr": "fr-FR-HenriNeural",
        "es": "es-ES-ElviraNeural",
        "hi": "hi-IN-MadhurNeural"
}
speech_config.speech_synthesis_voice_name = voices.get(targetLanguage)
speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config)
speak = speech_synthesizer.speak_text_async(translation).get()
if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
    print(speak.reason)</code></pre></div>

<li>
<p dir="auto">احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>لمترجم</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
</li>
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
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python translator.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python translator.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">عند المطالبة، أدخل رمز لغة صالحًا (<em>fr</em>أو <em>es</em>أو <em>hi</em>)، ثم تحدث بوضوح في الميكروفون وقل عبارة قد تستخدمها عند السفر إلى الخارج.  ينسخ البرنامج إدخالك المنطوق ويستجيب باستخدام ترجمة منطوقة. كرر هذه العملية، مع تجربة كل لغة يدعمها التطبيق. عند الانتهاء، اضغط على<strong>دخول</strong> لإنهاء البرنامج.</p>
</li>
</ol>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>
في هذا المثال، لقد استخدمت <strong>تكوين ترجمة الكلام</strong> لترجمة الكلام إلى نص، ثم استخدمت <strong>تكوين الكلام</strong> لتجميع الترجمة باعتبارها كلام. يمكنك في الواقع استخدام <strong>تكوين ترجمة الكلام</strong> لتجميع الترجمة مباشرة، ولكن هذا يعمل فقط عند الترجمة إلى لغة واحدة، ويؤدي إلى دفق صوتي يتم حفظه عادة كملف بدلا من إرساله مباشرة إلى مكبر الصوت.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لمزيد من المعلومات حول استخدام واجهة برمجة تطبيقات ترجمة Azure AI Speech، راجع <a href="https://learn.microsoft.com/azure/ai-services/speech-service/speech-translation" rel="nofollow">وثائق ترجمة الكلام</a>.</p>
</article></div></div>
