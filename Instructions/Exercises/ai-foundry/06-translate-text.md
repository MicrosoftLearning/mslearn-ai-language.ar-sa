---
lab:
  title: ترجمة النص
  module: Module 3 - Getting Started with Natural Language Processing
---
{٪ assign site.title = page.lab.title ٪}

# ترجمة النص

**Azure AI Translator** هو خدمة تمكّنك من ترجمة النص بين اللغات. في هذا التمرين، ستستخدمه لإنشاء تطبيق بسيط يترجم الإدخال بأي لغة مدعومة إلى اللغة المستهدفة التي تختارها.

## تزويد مورد *Azure AI Translator*

إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد **Azure AI Translator**.

1. افتح مدخل Azure على `https://portal.azure.com`، وقم بتسجيل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
1. في حقل البحث في الأعلى، ابحث عن **خدمات الذكاء الاصطناعي في Azure** واضغط على **Enter**، ثم حدد **Create** ضمن **Translator** في النتائج.
1. إنشاء المورد بالإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختيار مجموعة موارد أو إنشاءها*
    - **المنطقة**: *اختر أي منطقة متوفرة*
    - **الاسم**: *أدخل اسماً فريداً*
    - **طبقة الأسعار**: حدد **F0** (*مجاني*)، أو **S** (*قياسي*) إذا لم يكن F متوفراً.
    - **إشعار الذكاء الاصطناعي المسؤول**: أوافق.
1. حدد **مراجعة + إنشاء**، ثم حدد **إنشاء** لتوفير المورد.
1. انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.
1. اعرض صفحة **المفاتيح ونقطة النهاية**. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التمرين.

## الاستعداد لتطوير تطبيق في Visual Studio Code

ستقوم بتطوير تطبيق الترجمة النصية باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في مستودع GitHub.

> **تلميح**: إذا استنسخت بالفعل مستودع **mslearn-ai-language**، فافتحه في Visual Studio code وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-language` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في Visual Studio Code.

    > **ملاحظة**: إذا عرضت لك Visual Studio Code رسالة منبثقة لمطالبتك بالثقة في التعليمات البرمجية التي تفتحها، فانقر فوق **نعم، أثق في خيار الكُتاب** في النافذة المنبثقة.

4. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

## تكوين تطبيقك

تم توفير تطبيقات لكل من C# وPython. يتميز كلا التطبيقين بنفس الوظيفة. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد Azure AI Translator الخاص بك.

1. في Visual Studio Code، في جزء **Explorer**، استعرض للوصول إلى المجلد **Labfiles/06b-translator-sdk** وقم بتوسيع المجلد **CSharp** أو **Python** استناداً إلى تفضيلات اللغة ومجلد **translate-text** الذي يحتوي عليه. يحتوي كل مجلد على ملفات التعليمات البرمجية الخاصة باللغة الخاصة بأحد التطبيقات الذي ستقوم بدمج وظيفة Azure AI Translator فيه.
2. انقر بزر الماوس الأيمن فوق مجلد **translate-text** الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة Azure AI Translator SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة:

    **C#:**

    ```
    dotnet add package Azure.AI.Translation.Text --version 1.0.0-beta.1
    ```

    **Python**:

    ```
    pip install azure-ai-translation-text==1.0.0b1
    ```

3. في جزء **Explorer**، في مجلد **translate-text**، افتح ملف التكوين للغة المفضلة لديك

    - **C#**: appsettings.json
    - **Python**: .env
    
4. قم بتحديث قيم التكوين لتضمين **المنطقة** و**مفتاح** من مورد Azure AI Translator الذي أنشأته (متوفر في صفحة **المفاتيح ونقطة النهاية** لمورد Azure AI Translator في مدخل Microsoft Azure).

    > **ملاحظة**: تأكد من إضافة *المنطقة* لموردك، <u>وليس</u> نقطة النهاية!

5. واحفظ ملف التكوين.

## إضافة تعليمة برمجية لترجمة النص

أنت الآن جاهز لاستخدام Azure AI Translator لترجمة النص.

1. لاحظ أن مجلد **ترجمة النص** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: translate.py

    افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:

    **C#**: Programs.cs

    ```csharp
    // import namespaces
    using Azure;
    using Azure.AI.Translation.Text;
    ```

    **Python**: translate.py

    ```python
    # import namespaces
    from azure.ai.translation.text import *
    from azure.ai.translation.text.models import InputTextItem
    ```

1. في الدالة **Main** ، لاحظ أن التعليمات البرمجية الموجودة تقرأ إعدادات التكوين.
1. ابحث عن التعليق **إنشاء عميل باستخدام نقطة النهاية والمفتاح** وأضف التعليمات البرمجية التالية:

    **C#**: Programs.cs

    ```csharp
    // Create client using endpoint and key
    AzureKeyCredential credential = new(translatorKey);
    TextTranslationClient client = new(credential, translatorRegion);
    ```

    **Python**: translate.py

    ```python
    # Create client using endpoint and key
    credential = TranslatorCredential(translatorKey, translatorRegion)
    client = TextTranslationClient(credential)
    ```

1. ابحث عن التعليق **اختر اللغة الهدف** وأضف التعليمات البرمجية التالية، والتي تستخدم خدمة Text Translator لإرجاع قائمة اللغات المعتمدة للترجمة، وتطالب المستخدم بتحديد رمز لغة للغة الهدف.

    **C#**: Programs.cs

    ```csharp
    // Choose target language
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

    }
    ```

    **Python**: translate.py

    ```python
    # Choose target language
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
            print("{} is not a supported language.".format(targetLanguage))
    ```

1. ابحث عن التعليق **ترجمة النص** وأضف التعليمات البرمجية التالية، التي تطالب المستخدم بشكل متكرر بترجمة النص، وتستخدم خدمة Azure AI Translator لترجمتها إلى اللغة الهدف (الكشف عن اللغة المصدر تلقائياً)، وتعرض النتائج حتى يدخل المستخدم *إنهاء*.

    **C#**: Programs.cs

    ```csharp
    // Translate text
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
    } 
    ```

    **Python**: translate.py

    ```python
    # Translate text
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
                    print(f"'{inputText}' was translated from {sourceLanguage.language} to {translated_text.to} as '{translated_text.text}'.")
    ```

1. احفظ التغييرات في ملف التعليمات البرمجية الخاص بك.

## اختبار التطبيق الخاص بك

الآن التطبيق الخاص بك جاهز للاختبار.

1. في الوحدة الطرفية المتكاملة للمجلد **ترجمة النص**، وأدخل الأمر التالي لتشغيل البرنامج:

    - **C#:** `dotnet run`
    - **Python**: `python translate.py`

    > **تلميح**: يمكنك استخدام أيقونة **تكبير حجم اللوحة** (**^**) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.

1. عند المطالبة، أدخِل لغة هدف صالحة من القائمة المعروضة.
1. أدخِل عبارة لترجمتها (على سبيل المثال `This is a test` أو `C'est un test`) واعرض النتائج، والتي يجب أن تكتشف اللغة المصدر وتترجم النص إلى اللغة الهدف.
1. عند الانتهاء، أدخِل `quit`. يمكنك تشغيل التطبيق مرة أخرى واختيار لغة هدف مختلفة.

## تنظيف

عندما لا تحتاج إلى مشروعك بعد الآن، يمكنك حذف مورد Azure AI Translator في [مدخل Azure](https://portal.azure.com).
