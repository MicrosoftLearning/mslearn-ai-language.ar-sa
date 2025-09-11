---
lab:
  title: ترجمة النص
  description: قُم بترجمة النصوص المقدمة بين أي لغات مدعومة باستخدام Azure AI Translator.
---

# ترجمة النص

**Azure AI Translator** هو خدمة تمكّنك من ترجمة النص بين اللغات. في هذا التمرين، ستستخدمه لإنشاء تطبيق بسيط يترجم الإدخال بأي لغة مدعومة إلى اللغة المستهدفة التي تختارها.

يستند هذا التمرين إلى لغة Python، لكن يمكنك تطوير تطبيقات ترجمة النصوص باستخدام عِدد تطوير برامج (SDK) خاصة بلغات متعددة، منها:

- [مكتبة عميل Azure AI Translation للغة Python](https://pypi.org/project/azure-ai-translation-text/)
- [مكتبة عميل Azure AI Translation للغة NET.](https://www.nuget.org/packages/Azure.AI.Translation.Text)
- [مكتبة عميل Azure AI Translation للغة JavaScript](https://www.npmjs.com/package/@azure-rest/ai-translation-text)

سيستغرق هذا التدريب حوالي **30** دقيقة.

## تزويد مورد *Azure AI Translator*

إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد **Azure AI Translator**.

1. افتح مدخل Azure على `https://portal.azure.com`، وقم بتسجيل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
1. في حقل البحث العلوي، ابحث عن **المترجمون** ثم حدّد **المترجمون** من النتائج.
1. إنشاء المورد بالإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختيار مجموعة موارد أو إنشاءها*
    - **المنطقة**: *اختر أي منطقة متوفرة*
    - **الاسم**: *أدخل اسماً فريداً*
    - **طبقة الأسعار**: حدد **F0** (*مجاني*)، أو **S** (*قياسي*) إذا لم يكن F متوفراً.
1. حدد **مراجعة + إنشاء**، ثم حدد **إنشاء** لتوفير المورد.
1. انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.
1. اعرض صفحة **المفاتيح ونقطة النهاية**. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التدريب.

## الإعداد لتطوير تطبيق في Cloud Shell

لاختبار قدرات ترجمة النصوص في Azure AI Translator، ستقوم بتطوير تطبيق وحدة تحكم بسيط في Azure Cloud Shell.

1. في بوابة Azure، استخدم الزر **[\>_]** على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة ***PowerShell***. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    **<font color="red">تأكد من التبديل إلى الإصدار الكلاسيكي من cloud shell قبل المتابعة.</font>**

1. في جزء PowerShell، أدخل الأوامر التالية لاستنساخ مستودع GitHub لهذا التمرين:

    ```
   rm -r mslearn-ai-language -f
   git clone https://github.com/microsoftlearning/mslearn-ai-language
    ```

    > **تلميح**: عند إدخال الأوامر في Cloudshell، قد يحتل الناتج مساحة كبيرة من ذاكرة الشاشة المؤقتة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.

1. بعد استنساخ مخزن بيانات خاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الدردشة:  

    ```
   cd mslearn-ai-language/Labfiles/06-translator-sdk/Python/translate-text
    ```

## تكوين تطبيقك

1. في جزء سطر الأوامر، نفّذ الأمر التالي لعرض ملفات التعليمات البرمجية في مجلد **translate-text**:

    ```
   ls -a -l
    ```

    تتضمن الملفات ملف تكوين (**.env**) وملف تعليمات برمجية (**translate.py**).

1. قُم بإنشاء بيئة افتراضية للغة Python وتثبيت حزمة عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Translation والحزم المطلوبة الأخرى عبر تنفيذ الأمر التالي:

    ```
   python -m venv labenv
   ./labenv/bin/Activate.ps1
   pip install -r requirements.txt azure-ai-translation-text==1.0.1
    ```

1. أدخِل الأمر التالي لتحرير ملف تكوين التطبيق:

    ```
   code .env
    ```

    يتم فتح الملف في محرر التعليمات البرمجية.

1. قم بتحديث قيم التكوين لتضمين **المنطقة** و**مفتاح** من مورد Azure AI Translator الذي أنشأته (متوفر في صفحة **المفاتيح ونقطة النهاية** لمورد Azure AI Translator في مدخل Microsoft Azure).

    > **ملاحظة**: تأكد من إضافة *المنطقة* لموردك، <u>وليس</u> نقطة النهاية!

1. بعد استبدال العناصر النائبة، استخدم الأمر **CTRL+S** أو **Right-click > Save** لحفظ التغييرات ثم استخدم الأمر **CTRL+Q** أو **Right-click > Quit** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحًا.

## إضافة تعليمة برمجية لترجمة النص

1. أدخِل الأمر التالي لفتح ملف التعليمات البرمجية الخاص بالتطبيق وتحريره:

    ```
   code translate.py
    ```

1. راجع التعليمات البرمجية الموجودة حاليًا. عليك إضافة التعليمات البرمجية لاستخدام عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Translation.

    > **تلميح**: خلال إضافة التعليمات البرمجية إلى ملف التعليمات البرمجية، تأكد من الحفاظ على المسافة البادئة الصحيحة.

1. في أعلى ملف التعليمات البرمجية، ضمن مراجع المساحات الاسمية الموجودة، ابحث عن التعليق **Import namespaces** وأضِف التعليمات البرمجية التالية لاستيراد المساحات الاسمية التي ستحتاج إلى استخدامها في عدة تطوير البرامج (SDK) الخاصة بالترجمة:

    ```python
   # import namespaces
   from azure.core.credentials import AzureKeyCredential
   from azure.ai.translation.text import *
   from azure.ai.translation.text.models import InputTextItem
    ```

1. في الدالة **Main**، لاحظ أن التعليمات البرمجية الحالية تقرأ إعدادات التكوين.
1. ابحث عن التعليق **إنشاء عميل باستخدام نقطة النهاية والمفتاح** وأضف التعليمات البرمجية التالية:

    ```python
   # Create client using endpoint and key
   credential = AzureKeyCredential(translatorKey)
   client = TextTranslationClient(credential=credential, region=translatorRegion)
    ```

1. ابحث عن التعليق **Choose target language** وأضِف التعليمات البرمجية التالية، التي تستخدم خدمة Text Translator لإرجاع قائمة اللغات المدعومة للترجمة، ويطلب من المستخدم اختيار رمز اللغة المستهدفة:

    ```python
   # Choose target language
   languagesResponse = client.get_supported_languages(scope="translation")
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
            print("{} is not a supported language.".format(targetLanguage))
    ```

1. ابحث عن التعليق **Translate text** وأضِف التعليمات البرمجية التالية، والتي تقوم باستمرار بطلب النصوص المراد ترجمتها من المستخدم، وتستخدم خدمة Azure AI Translator لترجمتها إلى اللغة المستهدفة (مع التعرّف التلقائي على لغة المصدر)، وتعرض النتائج حتى يقوم المستخدم بإدخال كلمة *quit*:

    ```python
   # Translate text
   inputText = ""
   while inputText.lower() != "quit":
        inputText = input("Enter text to translate ('quit' to exit):")
        if inputText != "quit":
            input_text_elements = [InputTextItem(text=inputText)]
            translationResponse = client.translate(body=input_text_elements, to_language=[targetLanguage])
            translation = translationResponse[0] if translationResponse else None
            if translation:
                sourceLanguage = translation.detected_language
                for translated_text in translation.translations:
                    print(f"'{inputText}' was translated from {sourceLanguage.language} to {translated_text.to} as '{translated_text.text}'.")
    ```

1. احفظ تغييراتك باستخدام (CTRL+S)، بعدها نفذ الأمر التالي لتشغيل البرنامج (قُم بتكبير جزء cloud shell وتعديل حجم الألواح لمشاهدة المزيد من النص في جزء سطر الأوامر):

    ```
   python translate.py
    ```

1. عند المطالبة، أدخِل لغة هدف صالحة من القائمة المعروضة.
1. أدخِل عبارة لترجمتها (على سبيل المثال `This is a test` أو `C'est un test`) واعرض النتائج، والتي يجب أن تكتشف اللغة المصدر وتترجم النص إلى اللغة الهدف.
1. عند الانتهاء، أدخِل `quit`. يمكنك تشغيل التطبيق مرة أخرى واختيار لغة هدف مختلفة.

## تنظيف الموارد

إذا انتهيت من استكشاف خدمة Azure AI Translator، يمكنك حذف الموارد التي أنشأتها في هذا التمرين. وإليك الطريقة:

1. يمكنك إغلاق جزء Azure Cloud Shell
1. في مدخل Microsoft Azure، انتقل إلى مورد Azure AI Translator الذي أنشأته في هذا التدريب العملي.
1. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## مزيد من المعلومات

للمزيد من المعلومات حول استخدام **Azure AI Translator**، يُرجى مراجعة [وثائق Azure AI Translator](https://learn.microsoft.com/azure/ai-services/translator/).
