---
lab:
  title: تحليل النص
  module: Module 3 - Develop natural language processing solutions
---

# تحليل النص

**تدعم Azure Language** تحليل النص، بما في ذلك اكتشاف اللغة وتحليل التوجه واستخراج العبارة الرئيسية والتعرف على الكيان.

على سبيل المثال، لنفترض أن وكالة سفر تريد معالجة تقييمات الفنادق التي تم إرسالها إلى موقع الويب الخاص بالشركة. باستخدام Azure AI Language، يمكنها تحديد اللغة التي تتم كتابة كل تقييم بها، أو التوجه (الإيجابي أو المحايد أو السلبي) للتقييمات، والعبارات الرئيسية التي قد تشير إلى الموضوعات الرئيسية التي تمت مناقشتها في التقييم، والكيانات المسماة، مثل الأماكن أو المعالم أو الأشخاص المذكورين في التقييمات.

## توفير مورد *Azure AI Language*

إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد **خدمة Azure AI Language** في اشتراك Azure لديك.

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
1. في حقل البحث في الأعلى، ابحث عن **خدمات الذكاء الاصطناعي في Azure**. ثم، في النتائج، حدد **إنشاء** ضمن **خدمة اللغة**.
1. حدد **Continue to create your resource**.
1. توفير المورد باستخدام الإعدادات التالية:
    - **الاشتراك**: *اشتراك Azure الخاص بك*.
    - **مجموعة الموارد**: *اختيار مجموعة موارد أو إنشاءها*.
    - **المنطقة**: *اختر أي منطقة متوفرة*
    - **الاسم**: *أدخل اسمًا مميزًا*.
    - **مستوى الأسعار**: حدد **F0** (*مجاني*)، أو **S** (*قياسي*) إذا لم يكن F متوفراً.
    - **إشعار الذكاء الاصطناعي المسؤول**: أوافق.
1. حدد **مراجعة + إنشاء**، ثم حدد **إنشاء** لتوفير المورد.
1. انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.
1. اعرض صفحة **المفاتيح ونقطة النهاية**. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التمرين.

## الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية

ستقوم بتطوير تطبيق تحليلات النصور باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في مستودع GitHub.

> **تلميح**: إذا استنسخت بالفعل مستودع **mslearn-ai-language**، فافتحه في Visual Studio code وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوح الألوان (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-language` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في Visual Studio Code.

    > **ملاحظة**: إذا عرضت لك Visual Studio Code رسالة منبثقة لمطالبتك بالثقة في التعليمات البرمجية التي تفتحها، فانقر فوق **نعم، أثق في خيار الكُتاب** في النافذة المنبثقة.

4. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

## تكوين تطبيقك

تم توفير تطبيقات لكل من C# وPython، وكذلك ملف نصي نموذجي ستستخدمه لاختبار التلخيص. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد Azure AI Language الخاص بك.

1. في Visual Studio Code، في جزء **Explorer**، استعرض مجلد **Labfiles/01-analyze-text** ووسع نطاق المجلد **CSharp** أو **Python** استناداً إلى تفضيلات اللغة ومجلد **text-analysis** الذي يحتوي عليها. يحتوي كل مجلد على الملفات الخاصة باللغة للتطبيق الذي ستقوم بدمج وظيفة التحليلات لنصوص Azure AI Language فيه.
2. انقر بزر الماوس الأيمن فوق مجلد **text-analysis** الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم ثبّت حزمة Azure AI Language Text Analytics SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك. بالنسبة إلى تدريب Python، قم أيضا بتثبيت الحزمة `dotenv`:

    **C#:**

    ```
    dotnet add package Azure.AI.TextAnalytics --version 5.3.0
    ```

    **Python**:

    ```
    pip install azure-ai-textanalytics==5.3.0
    pip install python-dotenv
    ```

3. في جزء **Explorer**، في مجلد **text-analysis**، افتح ملف التكوين للغة المفضلة لديك

    - **C#**: appsettings.json
    - **Python**: .env
    
4. قم بتحديث قيم التكوين لتضمين **نقطة النهاية** و**مفتاح** من مورد Azure Language الذي أنشأته (متوفر في صفحة **المفاتيح ونقطة النهاية** لمورد Azure AI Language في مدخل Microsoft Azure)
5. احفظ ملف التكوين.

6. لاحظ أن مجلد **text-analysis** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: text-analysis.py

    افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:

    **C#**: Programs.cs

    ```csharp
    // import namespaces
    using Azure;
    using Azure.AI.TextAnalytics;
    ```

    **Python**: text-analysis.py

    ```python
    # import namespaces
    from azure.core.credentials import AzureKeyCredential
    from azure.ai.textanalytics import TextAnalyticsClient
    ```

7. في الدالة **Main**، لاحظ أنه تم بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية خدمة لغة الذكاء الاصطناعي في Azure والمفتاح من ملف التكوين. ثم ابحث عن التعليق **إنشاء عميل باستخدام نقطة النهاية والمفتاح**، وأضف التعليمة البرمجية التالية لإنشاء عميل لواجهة برمجة تطبيقات تحليل النص:

    **C#**: Programs.cs

    ```C#
    // Create client using endpoint and key
    AzureKeyCredential credentials = new AzureKeyCredential(aiSvcKey);
    Uri endpoint = new Uri(aiSvcEndpoint);
    TextAnalyticsClient aiClient = new TextAnalyticsClient(endpoint, credentials);
    ```

    **Python**: text-analysis.py

    ```Python
    # Create client using endpoint and key
    credential = AzureKeyCredential(ai_key)
    ai_client = TextAnalyticsClient(endpoint=ai_endpoint, credential=credential)
    ```

8. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **text-analysis**، وأدخل الأمر التالي لتشغيل البرنامج:

    - **C#:** `dotnet run`
    - **Python**: `python text-analysis.py`

    > **تلميح**: يمكنك استخدام أيقونة **تكبير حجم اللوحة** (**^**) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.

9. لاحظ المخرجات حيث يجب تشغيل التعليمات البرمجية دون خطأ، مع عرض محتويات كل ملف نصي للتعليقات في مجلد **التعليقات**. ينشئ التطبيق بنجاح عميلاً لواجهة برمجة تطبيقات Text Analytics ولكنه لا يستفيد منه. سنصلح ذلك في الإجراء التالي.

## إضافة تعليمة برمجية للكشف عن اللغة

الآن بعد أن قمت بإنشاء عميل لواجهة برمجة التطبيقات، دعنا نستخدمه للكشف عن اللغة التي تتم كتابة كل تقييم بها.

1. في الدالة **Main** لبرنامجك، ابحث عن التعليق **Get language**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة للكشف عن اللغة في كل مستند للتقييمات:

    **C#**: Programs.cs

    ```csharp
    // Get language
    DetectedLanguage detectedLanguage = aiClient.DetectLanguage(text);
    Console.WriteLine($"\nLanguage: {detectedLanguage.Name}");
    ```

    **Python**: text-analysis.py

    ```python
    # Get language
    detectedLanguage = ai_client.detect_language(documents=[text])[0]
    print('\nLanguage: {}'.format(detectedLanguage.primary_language.name))
    ```

     > **ملاحظة**: *في هذا المثال، يتم تحليل كل تقييم بشكل فردي، مما يؤدي إلى استدعاء منفصل للخدمة لكل ملف. يتمثل النهج البديل في إنشاء مجموعة من المستندات وتمريرها إلى الخدمة في استدعاء واحد. وفي كلا النهجين، تتكون الاستجابة من الخدمة من مجموعة من المستندات؛ ولهذا السبب تم تحديد فهرس المستند الأول (والوحيد) في الاستجابة ([0]) في تعليمة Python البرمجية أعلاه.*

1. احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد **text-analysis** وأعد تشغيل البرنامج.
1. لاحظ المخرجات، مع ملاحظة أنه يتم تحديد لغة كل تقييم في هذه المرة.

## إضافة تعليمة برمجية لتقييم التوجه

*تحليل التوجه* هو أسلوب شائع الاستخدام لتصنيف النص على أنه *إيجابي* أو *سلبي* (أو احتمالية كونه * محايد *أو* مختلط*). يتم استخدامه عادة لتحليل منشورات الوسائط الاجتماعية والتعليقات على المنتجات والعناصر الأخرى حيث قد يوفر توجه النص نتائج تحليلات مفيدة.

1. في الدالة **Main** لبرنامجك، ابحث عن التعليق **Get sentiment**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة للكشف عن التوجه في كل مستند للتقييمات:

    **C#**: Program.cs

    ```csharp
    // Get sentiment
    DocumentSentiment sentimentAnalysis = aiClient.AnalyzeSentiment(text);
    Console.WriteLine($"\nSentiment: {sentimentAnalysis.Sentiment}");
    ```

    **Python**: text-analysis.py

    ```python
    # Get sentiment
    sentimentAnalysis = ai_client.analyze_sentiment(documents=[text])[0]
    print("\nSentiment: {}".format(sentimentAnalysis.sentiment))
    ```

1. احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد **text-analysis** وأعد تشغيل البرنامج.
1. لاحظ المخرجات، مع ملاحظة أنه تم الكشف عن توجه التعليقات.

## إضافة تعليمة برمجية لتحديد العبارات الرئيسية

قد يكون من المفيد تحديد العبارات الرئيسية في نص أساسي للمساعدة في تحديد الموضوعات الرئيسية التي يناقشها.

1. في الدالة **Main** لبرنامجك، ابحث عن التعليق **Get key phrases**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة للكشف عن العبارات الرئيسية في كل مستند للتقييمات:

    **C#**: Program.cs

    ```csharp
    // Get key phrases
    KeyPhraseCollection phrases = aiClient.ExtractKeyPhrases(text);
    if (phrases.Count > 0)
    {
        Console.WriteLine("\nKey Phrases:");
        foreach(string phrase in phrases)
        {
            Console.WriteLine($"\t{phrase}");
        }
    }
    ```

    **Python**: text-analysis.py

    ```python
    # Get key phrases
    phrases = ai_client.extract_key_phrases(documents=[text])[0].key_phrases
    if len(phrases) > 0:
        print("\nKey Phrases:")
        for phrase in phrases:
            print('\t{}'.format(phrase))
    ```

1. احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد **text-analysis** وأعد تشغيل البرنامج.
1. لاحظ المخرجات، مع ملاحظة أن كل مستند يحتوي على عبارات رئيسية تعطي بعض نتائج التحليلات حول ما يتعلق به التعليقات.

## إضافة رمز لاستخراج الكيانات

في كثير من الأحيان، تشير المستندات أو النصوص الأخرى إلى الأشخاص أو الأماكن أو الفترات الزمنية أو الكيانات الأخرى. يمكن لواجهة برمجة تطبيقات  text Analytics الكشف عن فئات متعددة (وفئات فرعية) للكيان في النص الخاص بك.

1. في الدالة **Main** لبرنامجك، ابحث عن التعليق **Get entities**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة لتحديد الكيانات المذكورة في كل تقييم:

    **C#**: Program.cs

    ```csharp
    // Get entities
    CategorizedEntityCollection entities = aiClient.RecognizeEntities(text);
    if (entities.Count > 0)
    {
        Console.WriteLine("\nEntities:");
        foreach(CategorizedEntity entity in entities)
        {
            Console.WriteLine($"\t{entity.Text} ({entity.Category})");
        }
    }
    ```

    **Python**: text-analysis.py

    ```python
    # Get entities
    entities = ai_client.recognize_entities(documents=[text])[0].entities
    if len(entities) > 0:
        print("\nEntities")
        for entity in entities:
            print('\t{} ({})'.format(entity.text, entity.category))
    ```

1. احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد **text-analysis** وأعد تشغيل البرنامج.
1. لاحظ المخرجات، مع ملاحظة الكيانات التي تم الكشف عنها في النص.

## إضافة تعليمة برمجية لاستخراج الكيانات المرتبطة

بالإضافة إلى الكيانات المصنفة، يمكن لواجهة برمجة تطبيقات Text Analytics الكشف عن الكيانات التي توجد لها ارتباطات معروفة بمصادر البيانات، مثل ويكيبيديا.

1. في الدالة **Main** لبرنامجك، ابحث عن التعليق **Get linked entities**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية اللازمة لتحديد الكيانات المرتبطة المذكورة في كل تقييم:

    **C#**: Program.cs

    ```csharp
    // Get linked entities
    LinkedEntityCollection linkedEntities = aiClient.RecognizeLinkedEntities(text);
    if (linkedEntities.Count > 0)
    {
        Console.WriteLine("\nLinks:");
        foreach(LinkedEntity linkedEntity in linkedEntities)
        {
            Console.WriteLine($"\t{linkedEntity.Name} ({linkedEntity.Url})");
        }
    }
    ```

    **Python**: text-analysis.py

    ```python
    # Get linked entities
    entities = ai_client.recognize_linked_entities(documents=[text])[0].entities
    if len(entities) > 0:
        print("\nLinks")
        for linked_entity in entities:
            print('\t{} ({})'.format(linked_entity.name, linked_entity.url))
    ```

1. احفظ تغييراتك. ثم ارجع إلى الوحدة الطرفية المتكاملة لمجلد **text-analysis** وأعد تشغيل البرنامج.
1. لاحظ المخرجات، مع ملاحظة الكيانات المرتبطة التي تم تحديدها.

## تنظيف الموارد

إذا انتهيت من استكشاف خدمة Azure AI Language، فيمكنك حذف الموارد التي قمت بإنشائها في هذا التمرين. وإليك الطريقة:

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.

2. استعرض للوصول إلى مورد Azure AI Language الذي أنشأته في هذا المختبر.

3. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## مزيد من المعلومات

لمزيد من المعلومات حول استخدام **Azure AI Language**، راجع [وثائق](https://learn.microsoft.com/azure/ai-services/language-service/).
