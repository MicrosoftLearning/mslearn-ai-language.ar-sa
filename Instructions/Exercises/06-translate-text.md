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
  <td><div dir="auto">ترجمة النص</div></td>
  <td><div dir="auto">Module 3 - Getting Started with Natural Language Processing</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<p dir="auto">{% assign site.title = page.lab.title %}</p>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">ترجمة النص</h1><a id="user-content-ترجمة-النص" class="anchor" aria-label="Permalink: ترجمة النص" href="#ترجمة-النص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><strong>Azure AI Translator</strong> هو خدمة تمكّنك من ترجمة النص بين اللغات. في هذا التمرين، ستستخدمه لإنشاء تطبيق بسيط يترجم الإدخال بأي لغة مدعومة إلى اللغة المستهدفة التي تختارها.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تزويد مورد <em>Azure AI Translator</em></h2><a id="user-content-تزويد-مورد-azure-ai-translator" class="anchor" aria-label="Permalink: تزويد مورد Azure AI Translator" href="#تزويد-مورد-azure-ai-translator"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد <strong>Azure AI Translator</strong>.</p>
<ol dir="rtl">
<li>افتح مدخل Azure على <code>https://portal.azure.com</code>، وقم بتسجيل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</li>
<li>في حقل البحث في الأعلى، ابحث عن <strong>خدمات الذكاء الاصطناعي في Azure</strong> واضغط على <strong>Enter</strong>، ثم حدد <strong>Create</strong> ضمن <strong>Translator</strong> في النتائج.</li>
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
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في Visual Studio Code</h2><a id="user-content-الاستعداد-لتطوير-تطبيق-في-visual-studio-code" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في Visual Studio Code" href="#الاستعداد-لتطوير-تطبيق-في-visual-studio-code"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">ستقوم بتطوير تطبيق الترجمة النصية باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في مستودع GitHub.</p>
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
<p dir="auto">تم توفير تطبيقات لكل من C# وPython. يتميز كلا التطبيقين بنفس الوظيفة. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد Azure AI Translator الخاص بك.</p>
<ol dir="rtl">
<li>
<p dir="auto">في Visual Studio Code، في جزء <strong>Explorer</strong>، استعرض للوصول إلى المجلد <strong>Labfiles/06b-translator-sdk</strong> وقم بتوسيع المجلد <strong>CSharp</strong> أو <strong>Python</strong> استناداً إلى تفضيلات اللغة ومجلد <strong>translate-text</strong> الذي يحتوي عليه. يحتوي كل مجلد على ملفات التعليمات البرمجية الخاصة باللغة الخاصة بأحد التطبيقات الذي ستقوم بدمج وظيفة Azure AI Translator فيه.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن فوق مجلد <strong>translate-text</strong> الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة Azure AI Translator SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة:</p>
</li>
<p dir="rtl"><strong>:#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.AI.Translation.Text --version 1.0.0-beta.1
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.AI.Translation.Text --version 1.0.0-beta.1" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl">:<strong>Python</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-ai-translation-text==1.0.0b1
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-ai-translation-text==1.0.0b1" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<li>
<p dir="auto">في جزء <strong>Explorer</strong>، في مجلد <strong>translate-text</strong>، افتح ملف التكوين للغة المفضلة لديك</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
</li>
<li>
<p dir="auto">قم بتحديث قيم التكوين لتضمين <strong>المنطقة</strong> و<strong>مفتاح</strong> من مورد Azure AI Translator الذي أنشأته (متوفر في صفحة <strong>المفاتيح ونقطة النهاية</strong> لمورد Azure AI Translator في مدخل Microsoft Azure).</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: تأكد من إضافة <em>المنطقة</em> لموردك، وليس نقطة النهاية!</p>
</blockquote>
</li>
<li>
<p dir="auto">واحفظ ملف التكوين.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إضافة تعليمة برمجية لترجمة النص</h2><a id="user-content-إضافة-تعليمة-برمجية-لترجمة-النص" class="anchor" aria-label="Permalink: إضافة تعليمة برمجية لترجمة النص" href="#إضافة-تعليمة-برمجية-لترجمة-النص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أنت الآن جاهز لاستخدام Azure AI Translator لترجمة النص.</p>
<ol dir="rtl">
<li>
<p dir="auto">لاحظ أن مجلد <strong>ترجمة النص</strong> يحتوي على ملف تعليمات برمجية لتطبيق العميل:</p>
<ul dir="rtl">
    <li><strong>C#</strong>: Program.cs</li>
    <li><strong>Python</strong>: translate.py</li>
</ul>
<p dir="auto">افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// import namespaces
using Azure;
using Azure.AI.Translation.Text;</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translate.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># import namespaces
from azure.ai.translation.text import *
from azure.ai.translation.text.models import InputTextItem</code></pre></div>
<li>
<p dir="auto">في الدالة <strong>Main</strong> ، لاحظ أن التعليمات البرمجية الموجودة تقرأ إعدادات التكوين.</p>
</li>
<li>
<p dir="auto">ابحث عن التعليق <strong>إنشاء عميل باستخدام نقطة النهاية والمفتاح</strong> وأضف التعليمات البرمجية التالية:</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Create client using endpoint and key
AzureKeyCredential credential = new(translatorKey);
TextTranslationClient client = new(credential, translatorRegion);</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translate.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Create client using endpoint and key
credential = TranslatorCredential(translatorKey, translatorRegion)
client = TextTranslationClient(credential)</code></pre></div>

<li>
<p dir="auto">ابحث عن التعليق <strong>اختر اللغة الهدف</strong> وأضف التعليمات البرمجية التالية، والتي تستخدم خدمة Text Translator لإرجاع قائمة اللغات المعتمدة للترجمة، وتطالب المستخدم بتحديد رمز لغة للغة الهدف.</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Choose target language
Response<GetLanguagesResult> languagesResponse = await client.GetLanguagesAsync(scope:"translation").ConfigureAwait(false);
GetLanguagesResult languages = languagesResponse.Value;
Console.WriteLine($"{languages.Translation.Count} languages available.\n(See https://learn.microsoft.com/azure/ai-services/translator/language-support#translation)");
Console.WriteLine("Enter a target language code for translation (for example, 'en'):");
string targetLanguage = "xx";
bool languageSupported = false;
while (!languageSupported)
{
    targetLanguage = Console.ReadLine();
    if (languages.Translation.ContainsKey(targetLanguage))
    {
        languageSupported = true;
    }
    else
    {
        Console.WriteLine($"{targetLanguage} is not a supported language.");
    }
<br>
}</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translate.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Choose target language
languagesResponse = client.get_languages(scope="translation")
print("{} languages supported.".format(len(languagesResponse.translation)))
print("(See https://learn.microsoft.com/azure/ai-services/translator/language-support#translation)")
print("Enter a target language code for translation (for example, 'en'):")
targetLanguage = "xx"
supportedLanguage = False
while supportedLanguage == False:
    targetLanguage = input()
    if  targetLanguage in languagesResponse.translation.keys():
        supportedLanguage = True
    else:
        print("{} is not a supported language.".format(targetLanguage))</code></pre></div>

<li>
<p dir="auto">ابحث عن التعليق <strong>ترجمة النص</strong> وأضف التعليمات البرمجية التالية، التي تطالب المستخدم بشكل متكرر بترجمة النص، وتستخدم خدمة Azure AI Translator لترجمتها إلى اللغة الهدف (الكشف عن اللغة المصدر تلقائياً)، وتعرض النتائج حتى يدخل المستخدم <em>إنهاء</em>.</p>
</li>
<p dir="rtl"><strong>C#</strong>: Programs.cs</p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Translate text
string inputText = "";
while (inputText.ToLower() != "quit")
{
    Console.WriteLine("Enter text to translate ('quit' to exit)");
    inputText = Console.ReadLine();
    if (inputText.ToLower() != "quit")
    {
        Response<IReadOnlyList<TranslatedTextItem>> translationResponse = await client.TranslateAsync(targetLanguage, inputText).ConfigureAwait(false);
        IReadOnlyList<TranslatedTextItem> translations = translationResponse.Value;
        TranslatedTextItem translation = translations[0];
        string sourceLanguage = translation?.DetectedLanguage?.Language;
        Console.WriteLine($"'{inputText}' translated from {sourceLanguage} to {translation?.Translations[0].To} as '{translation?.Translations?[0]?.Text}'.");
    }
}</code></pre></div>
<p dir="rtl"><strong>Python</strong>: translate.py</p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Translate text
inputText = ""
while inputText.lower() != "quit":
    inputText = input("Enter text to translate ('quit' to exit):")
    if inputText != "quit":
        input_text_elements = [InputTextItem(text=inputText)]
        translationResponse = client.translate(content=input_text_elements, to=[targetLanguage])
        translation = translationResponse[0] if translationResponse else None
        if translation:
            sourceLanguage = translation.detected_language
            for translated_text in translation.translations:
                print(f"'{inputText}' was translated from {sourceLanguage.language} to {translated_text.to} as '{translated_text.text}'.")</code></pre></div>

<li>
<p dir="auto">احفظ التغييرات في ملف التعليمات البرمجية الخاص بك.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">اختبار التطبيق الخاص بك</h2><a id="user-content-اختبار-التطبيق-الخاص-بك" class="anchor" aria-label="Permalink: اختبار التطبيق الخاص بك" href="#اختبار-التطبيق-الخاص-بك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن التطبيق الخاص بك جاهز للاختبار.</p>
<ol dir="rtl">
<li>
<p dir="auto">في الوحدة الطرفية المتكاملة للمجلد <strong>ترجمة النص</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
<ul dir="rtl">
<li><strong>:#C</strong> <code>dotnet run</code></li>
<li><strong>Python</strong>: <code>python translate.py</code></li>
</ul>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: يمكنك استخدام أيقونة <strong>تكبير حجم اللوحة</strong> (<strong>^</strong>) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.</p>
</blockquote>
</li>
<li>
<p dir="auto">عند المطالبة، أدخِل لغة هدف صالحة من القائمة المعروضة.</p>
</li>
<li>
<p dir="auto">أدخِل عبارة لترجمتها (على سبيل المثال <code>This is a test</code> أو <code>C'est un test</code>) واعرض النتائج، والتي يجب أن تكتشف اللغة المصدر وتترجم النص إلى اللغة الهدف.</p>
</li>
<li>
<p dir="auto">عند الانتهاء، أدخِل <code>quit</code>. يمكنك تشغيل التطبيق مرة أخرى واختيار لغة هدف مختلفة.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف</h2><a id="user-content-تنظيف" class="anchor" aria-label="Permalink: تنظيف" href="#تنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">عندما لا تحتاج إلى مشروعك بعد الآن، يمكنك حذف مورد Azure AI Translator في <a href="https://portal.azure.com" rel="nofollow">مدخل Azure</a>.</p>
</article></div></div>
