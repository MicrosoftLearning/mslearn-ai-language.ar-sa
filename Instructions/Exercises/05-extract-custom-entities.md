---
lab:
  title: استخراج الكيانات المخصصة
  module: Module 3 - Getting Started with Natural Language Processing
---

# استخراج الكيانات المخصصة

بالإضافة إلى إمكانيات معالجة اللغة الطبيعية الأخرى، تُمكّنك "خدمة لغة الذكاء الاصطناعي في Azure" من تعريف وحدات مخصصة، واستخراج مثيلات لها من النص.

لاختبار استخراج الوحدة المخصصة، سنُنشئ نموذجًا ونُدربه من خلال "ستوديو لغة الذكاء الاصطناعي في Azure"، ثم نستخدم تطبيقًا لسطر الأوامر لاختباره.

## *توفير مورد *لغة الذكاء الاصطناعي في Azure

إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد **خدمة لغة الذكاء الاصطناعي في Azure**. بالإضافة إلى ذلك، لاستخدام تصنيف النص المخصص، يتعين عليك تمكين ميزة **تصنيف النص المخصص واستخراجه**.

1. في متصفح، افتح مدخل Microsoft Azure في ⁧`https://portal.azure.com`⁩، وسجّل الدخول باستخدام حسابك في Microsoft.
1. حدد زر **إنشاء مورد**، وابحث عن *اللغة*، وأنشئ مورد **خدمة اللغة**. عند التواجد على صفحة *تحديد ميزات إضافية*، حدّد الميزة المخصصة التي تحتوي على **استخراج التعرف على الوحدة المسماة المخصصة**. إنشاء المورد بالإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *تحديد مجموعة موارد أو إنشاؤها*
    - **المنطقة**: *اختر أي منطقة متوفرة*
    - **الاسم**: *أدخل اسماً فريداً*
    - **طبقة الأسعار**: حدد **F0** (*مجاني*)، أو **S** (*قياسي*) إذا لم يكن F متوفراً.
    - **حساب التخزين**: حساب تخزين جديد:
      - **اسم حساب التخزين**: *أدخل اسمًا فريدًا*.
      - **نوع حساب التخزين**: LRS قياسي
    - **Responsible AI notice**: محدد.

1. حدّد **مراجعة + إنشاء**، ثم حدّد **إنشاء** لتوفير المورد.
1. انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.
1. اعرض صفحة **المفاتيح ونقطة النهاية**. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقًا في التمرين.

## تحميل عينة إعلانات

بمجرد إنشاء "خدمة لغة الذكاء الاصطناعي في Azure" وحساب التخزين، سيتعين عليك تحميل أمثلة للإعلانات لتدريب النموذج لاحقًا.

1. في علامة تبويب جديدة بالمتصفح، قُم بتنزيل نماذج الإعلانات المصنَّفة من `https://aka.ms/entity-extraction-ads` واستخرِج الملفات إلى مجلد من اختيارك.

2. في مدخل Microsoft Azure، انتقل إلى حساب التخزين الذي أنشأته، وحدده.

3. في حساب التخزين الخاص بك، حدّد **تكوين**، الموجود أسفل **الإعدادات**، وظلِّل تمكين الخيار **السماح بالوصول المجهول للكائن الثنائي كبير الحجم** ثم حدّد **حفظ**.

4. حدّد **الحاويات** من القائمة اليمنى، الموجودة أسفل **تخزين البيانات**. على الشاشة التي تظهر، حدد **+ Container**. امنح الحاوية الاسم `classifieds`، وقُم بتعيين **مستوى الوصول العام** إلى **الحاوية (الوصول المجهول للقراءة فقط للحاويات والكائنات الثنائية كبيرة الحجم)**.

    > **ملاحظة**: عند تكوين حساب تخزين لحلّ حقيقي، احرص على تعيين مستوى الوصول المناسب. لمعرفة المزيد حول كل مستوى وصول، راجِع [مستندات Azure Storage](https://learn.microsoft.com/azure/storage/blobs/anonymous-read-access-configure).

5. بعد إنشاء الحاوية، حدّدها وانقر فوق زر **تحميل** لتحميل نماذج الإعلانات التي قمتَ بتنزيلها.

## إنشاء مشروع مخصص للتعرف على الكيان المسمى

أنت الآن جاهز لإنشاء مشروع تعرّف على الوحدة المسماة المخصصة. يوفر هذا المشروع مكانا للعمل لبناء نموذجك وتدريبه وتوزيعه.

> **ملاحظة**: يمكنك أيضًا إنشاء نموذجك وبنائه وتدريبه ونشره من خلال واجهة برمجة تطبيقات REST.

1. في علامة تبويب جديدة بالمتصفح، افتح مدخل "ستوديو لغة الذكاء الاصطناعي في Azure" في `https://language.cognitive.azure.com/`، ثم سجّل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure خاصتك.
1. إذا طلب منك اختيار مورد Language، حدد الإعدادات التالية:

    - **Azure Directory**: دليل Azure الذي يحتوي على اشتراكك.
    - **Azure subscription**: اشتراك Azure الخاص بك.
    - **نوع المورد**: اللغة.
    - **مورد اللغة**: مورد "لغة الذكاء الاصطناعي في Azure" الذي أنشأتَه سابقًا.

    إذا <u>لم</u> تتم مطالبتك باختيار مورد language، فقد يرجع ذلك إلى وجود موارد Language متعددة في اشتراكك؛ وفي هذه الحالة:

    1. في الشريط الموجود أعلى الصفحة، حدّد زر **الإعدادات (&#9881;)**.
    2. في الصفحة **Settings** اعرض علامة التبويب **Resources**.
    3. حدد مورد language الذي أنشأته للتو، وانقر فوق **Switch resource**.
    4. في أعلى الصفحة، انقر فوق **Language Studio** للعودة إلى الصفحة الرئيسية في Language Studio.

1. في أعلى المدخل، في قائمة **إنشاء جديد**، حدّد **التعرّف على الوحدة المسمّاة المخصصة**.

1. إنشاء مشروع جديد بالإعدادات التالية:
    - **اتصال التخزين**: *من المحتمل أن تكون هذه القيمة قد تمت تعبئتها بالفعل. قُم بتغييرها إلى حساب التخزين الخاص بك إذا لم تكن قد تمت تعبئتها سابقًا*
    - **المعلومات الأساسية**:
    - **الاسم:** `CustomEntityLab`
        - **Text primary language**: English (US)
        - **هل تتضمن مجموعة البيانات لديك مستندات ليست بذات اللغة؟** : *لا*
        - **الوصف**: `Custom entities in classified ads`
    - **الحاوية:**
        - **حاوية مخزن Blob**: مصنفات
        - **هل ملفاتك مُسماة بفئات؟**: لا، أحتاج إلى تسمية ملفاتي كجزء من هذا المشروع

## تسمية البيانات

الآن بعد أن تم إنشاء مشروعك، تحتاج إلى تسمية بياناتك لتدريب النموذج على كيفية تحديد الكيانات.

1. إذا لم تكن صفحة **تسمية البيانات** مفتوحة بالفعل، فحدد تسمية** البيانات في الجزء الموجود على اليسار**. سترى قائمة بالملفات التي قمت بتحميلها إلى حساب التخزين الخاص بك.
1. على الجانب الأيمن، في **جزء النشاط**، حدد **إضافة كيان** وأضف كيانًا جديدًا باسم `ItemForSale`.
1.  كرر الخطوة السابقة لإنشاء الكيانات التالية:
    - `Price`
    - `Location`
1. بعد إنشاء كياناتك الثلاثة، حدد **Ad 1.txt** حتى تتمكن من قراءتها.
1. في *Ad 1.txt*: 
    1. قم بتمييز نص *حبل من حطب الوقود* وحدد **كيان ItemForSale**.
    1. قم بتمييز النص *دنفر في ولاية كولورادو* وحدد **كيان الموقع**.
    1. قم بتمييز النص *90 دولارًا* وحدد كيان **السعر**.
في جزء **النشاط**، ستلاحظ أن هذه الوثيقة سيتم إضافتها إلى مجموعة البيانات لتدريب النموذج.
1. استخدم زر **المستند التالي** للانتقال إلى المستند التالي، ومتابعة تعيين النص للكيانات المناسبة لمجموعة المستندات بأكملها، وإضافتها جميعًا إلى مجموعة بيانات التدريب.
1. عندما تنتهي من تسمية المستند الأخير (*Ad 9.txt*)، احفظ الأوصاف.

## تدريب النموذج

بمجرد تسمية بياناتك، تحتاج إلى تدريب نموذجك.

1. حدد **Training jobs** من الجزء الموجود على اليسار.
2. حدد ** Start a training job**
3. تدريب نموذج جديد باسم `ExtractAds`
4. اختر **Automatically split the testing set from training data**

    > **تلميح**: في مشاريع الاستخراج، استخدم تقسيم الاختبار الذي يناسب بياناتك بشكل أفضل. للحصول على بيانات أكثر اتساقًا ومجموعات بيانات أكبر، ستقوم خدمة Azure AI Language تلقائيًا بتقسيم الاختبار المُعيّن حسب النسبة المئوية. في حالة مجموعات البيانات الأصغر، من المهم التدريب على مجموعة متنوعة صحيحة من مستندات الإدخال المحتملة.

5. انقر فوق **Train**

    > **هام**: قد يستغرق تدريب النموذج الخاص بك أحيانا عدة دقائق. ستتلقى إعلاما عند اكتماله.

## تقييم نموذجك

في تطبيقات العالم الحقيقي، من المهم تقييم نموذجك وتحسينه للتحقق من أدائه كما تتوقع. تعرض صفحتان على اليسار تفاصيل النموذج المدرب وأي اختبار فشل.

حدد **Model performance** في القائمة اليسرى، وحدد `ExtractAds` النموذج الخاص بك. ثم يمكنك أن ترى تسجيل النموذج الخاص بك، ومقاييس الأداء، ومتى تم تدريبه. ستتمكن من معرفة ما إذا فشلت أي مستندات اختبار، وتساعدك هذه الإخفاقات على فهم المكان الذي يحتاج إلى تحسين.

## استخدام نموذجك

عندما تكون راضيًا عن تدريب النموذج، فقد حان الوقت لتوزيعه، ما يسمح لك بالبدء في استخراج الكيانات من خلال واجهة برمجة التطبيقات.

1. في الجزء الأيسر، حدد **Deploying a model**.
2. حدد **Add deployment**، ثم أدخل الاسم `AdEntities` وحدد نموذج **ExtractAds**.
3. انقر فوق **Deploy** لتوزيع النموذج الخاص بك.

## الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية

لاختبار إمكانيات استخراج الكيان المخصص لخدمة Azure AI Language، ستقوم بتطوير تطبيق وحدة تحكم بسيط في تعليمة Visual Studio برمجية.

> **تلميح**: إذا استنسخت بالفعل مستودع **mslearn-ai-language**، فافتحه في Visual Studio code. وإلا اتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوح الألوان (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-language` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في Visual Studio Code.

    > **ملاحظة**: إذا عرض لك Visual Studio Code رسالة منبثقة لمطالبتك بالثقة في التعليمات البرمجية التي تفتحها، فانقر فوق **نعم، أثق في خيار الكُتاب** في النافذة المنبثقة.

4. انتظر حتى يتم تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: إذا تمت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

## تكوين تطبيقك

تم توفير تطبيقات لكل من C# وPython. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد Azure AI Language الخاص بك.

1. في Visual Studio Code، في جزء **Explorer**، استعرض للوصول إلى المجلد **Labfiles/05-custom-entity-recognition** وقم بتوسيع المجلد **CSharp** أو **Python** استناداً إلى تفضيلات اللغة ومجلد **custom-entities** الذي يحتوي عليه. يحتوي كل مجلد على الملفات الخاصة باللغة للتطبيق الذي ستقوم بدمج وظيفة تصنيف نص Azure AI Language فيه.
1. انقر بزر الماوس الأيمن فوق مجلد **custom-entities** الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة Azure AI Language Text Analytics SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#:**

    ```
    dotnet add package Azure.AI.TextAnalytics --version 5.3.0
    ```

    **Python**:

    ```
    pip install azure-ai-textanalytics==5.3.0
    ```

1. في جزء **Explorer**، في مجلد **custom-entities**، افتح ملف التكوين للغة المفضلة لديك

    - **C#**: appsettings.json
    - **Python**: .env
    
1. قم بتحديث قيم التكوين لتضمين **نقطة النهاية** و**مفتاح** من مورد Azure Language الذي أنشأته (متوفر في صفحة **المفاتيح ونقطة النهاية** لمورد Azure AI Language في مدخل Microsoft Azure). يجب أن يحتوي الملف بالفعل على أسماء المشروع والنشر لنموذج استخراج الكيان المخصص لديك.
1. واحفظ ملف التكوين.

## إضافة رمز لاستخراج الكيانات

أنت الآن جاهز لاستخدام خدمة Azure AI Language لاستخراج الكيانات المخصصة من النص.

1. قم بتوسيع مجلد **الإعلانات** في مجلد **الكيانات المخصصة** لعرض الإعلانات المصنفة التي سيقوم تطبيقك بتحليلها.
1. في مجلد **custom-entities**، افتح ملف التعليمات البرمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: custom-entities.py

1. ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:

    **C#**: Programs.cs

    ```csharp
    // import namespaces
    using Azure;
    using Azure.AI.TextAnalytics;
    ```

    **Python**: custom-entities.py

    ```python
    # import namespaces
    from azure.core.credentials import AzureKeyCredential
    from azure.ai.textanalytics import TextAnalyticsClient
    ```

1. في دالة **Main**، لاحظ أنه تم بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية خدمة Azure AI Language والمفتاح وأسماء المشروع والتوزيع من ملف التكوين. ثم ابحث عن التعليق **إنشاء عميل باستخدام نقطة النهاية والمفتاح**، وأضف التعليمة البرمجية التالية لإنشاء عميل لواجهة برمجة تطبيقات تحليل النص:

    **C#**: Programs.cs

    ```csharp
    // Create client using endpoint and key
    AzureKeyCredential credentials = new(aiSvcKey);
    Uri endpoint = new(aiSvcEndpoint);
    TextAnalyticsClient aiClient = new(endpoint, credentials);
    ```

    **Python**: custom-entities.py

    ```Python
    # Create client using endpoint and key
    credential = AzureKeyCredential(ai_key)
    ai_client = TextAnalyticsClient(endpoint=ai_endpoint, credential=credential)
    ```

1. في دالة **Main**، لاحظ أن التعليمة البرمجية الموجودة تقرأ جميع الملفات الموجودة في مجلد **الإعلانات** وتنشئ قائمة تحتوي على محتوياتها. في حالة التعليمة البرمجية C#، يتم استخدام قائمة كائنات **TextDocumentInput** لتضمين اسم الملف كمعرّف واللغة. في Python، يتم استخدام قائمة بسيطة لمحتويات النص.
1. ابحث عن التعليق **استخراج الكيانات** وأضف التعليمة البرمجية التالية:

    **C#**: Program.cs

    ```csharp
    // Extract entities
    RecognizeCustomEntitiesOperation operation = await aiClient.RecognizeCustomEntitiesAsync(WaitUntil.Completed, batchedDocuments, projectName, deploymentName);

    await foreach (RecognizeCustomEntitiesResultCollection documentsInPage in operation.Value)
    {
        foreach (RecognizeEntitiesResult documentResult in documentsInPage)
        {
            Console.WriteLine($"Result for \"{documentResult.Id}\":");

            if (documentResult.HasError)
            {
                Console.WriteLine($"  Error!");
                Console.WriteLine($"  Document error code: {documentResult.Error.ErrorCode}");
                Console.WriteLine($"  Message: {documentResult.Error.Message}");
                Console.WriteLine();
                continue;
            }

            Console.WriteLine($"  Recognized {documentResult.Entities.Count} entities:");

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

            Console.WriteLine();
        }
    }
    ```

    **Python**: custom-entities.py

    ```Python
    # Extract entities
    operation = ai_client.begin_recognize_custom_entities(
        batchedDocuments,
        project_name=project_name,
        deployment_name=deployment_name
    )

    document_results = operation.result()

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
            )
    ```

1. احفظ التغييرات في ملف التعليمات البرمجية الخاص بك.

## اختبار التطبيق الخاص بك

الآن التطبيق الخاص بك جاهز للاختبار.

1. في الوحدة الطرفية المتكاملة للمجلد **تصنيف النص**، أدخل الأمر التالي لتشغيل البرنامج:

    - **C#:** `dotnet run`
    - **Python**: `python custom-entities.py`

    > **تلميح**: يمكنك استخدام أيقونة **تكبير حجم اللوحة** (**^**) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.

1. مراقبة المخرجات. يجب أن يسرد التطبيق تفاصيل الكيانات الموجودة في كل ملف نصي.

## تنظيف

عندما لا تحتاج إلى مشروعك بعد الآن، يمكنك حذفه من صفحة **Projects**الخاصة بك في Language Studio. يمكنك أيضا إزالة خدمة Azure AI Language وحساب التخزين المقترن في [Azure portal](https://portal.azure.com).
