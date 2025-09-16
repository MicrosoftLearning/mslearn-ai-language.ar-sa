---
lab:
  title: استخراج الكيانات المخصصة
  description: قُم بتدريب نموذج لاستخراج الكيانات المخصصة من مدخلات النص باستخدام Azure AI Language.
---

# استخراج الكيانات المخصصة

بالإضافة إلى إمكانيات معالجة اللغة الطبيعية الأخرى، تُمكّنك "خدمة لغة الذكاء الاصطناعي في Azure" من تعريف وحدات مخصصة، واستخراج مثيلات لها من النص.

لاختبار استخراج الكيانات المخصصة، سنقوم بإنشاء نموذج وتدريبه عبر Azure AI Language Studio، ثم استخدام تطبيق Python لاختباره.

يستند هذا التمرين إلى لغة Python، لكن يمكنك تطوير تطبيقات تصنيف النصوص باستخدام عِدد تطوير برامج (SDK) خاصة بلغات متعددة، منها:

- [مكتبة عميل Azure AI Text Analytics للغة Python](https://pypi.org/project/azure-ai-textanalytics/)
- [مكتبة عميل Azure AI Text Analytics للغة NET.](https://www.nuget.org/packages/Azure.AI.TextAnalytics)
- [مكتبة عميل Azure AI Text Analytics للغة JavaScript](https://www.npmjs.com/package/@azure/ai-text-analytics)

سيستغرق هذا التمرين حوالي **35** دقيقة.

## توفير مورد *Azure AI Language*

إذا لم يكن لديك بالفعل واحد في اشتراكك، فسيتعين عليك توفير مورد **خدمة Azure AI Language**. بالإضافة إلى ذلك، لاستخدام تصنيف النص المخصص، ينبغي لك تمكين ميزة **تصنيف النص المخصص واستخراجه**.

1. في متصفح، افتح مدخل Microsoft Azure في ⁧`https://portal.azure.com`⁩، وسجّل الدخول باستخدام حسابك في Microsoft.
1. حدد زر **إنشاء مورد**، وابحث عن *اللغة*، وأنشئ مورد **خدمة اللغة**. عند التواجد على صفحة *تحديد ميزات إضافية*، حدّد الميزة المخصصة التي تحتوي على **استخراج التعرف على الوحدة المسماة المخصصة**. إنشاء المورد بالإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *تحديد مجموعة موارد أو إنشاؤها*
    - **المنطقة**: *اختر من إحدى المناطق التالية*\*
        - شرق أستراليا
        - وسط الهند‬
        - شرق الولايات المتحدة
        - East US 2
        - أوروبا الشمالية
        - South Central US
        - شمال سويسرا
        - جنوب المملكة المتحدة
        - أوروبا الغربية
        - West US 2
        - غرب الولايات المتحدة الأمريكية 3
    - **الاسم**: *أدخل اسماً فريداً*
    - **طبقة الأسعار**: حدد **F0** (*مجاني*)، أو **S** (*قياسي*) إذا لم يكن F متوفراً.
    - **حساب التخزين**: حساب تخزين جديد:
      - **اسم حساب التخزين**: *أدخل اسمًا فريدًا*.
      - **نوع حساب التخزين**: LRS قياسي
    - **Responsible AI notice**: محدد.

1. حدد **مراجعة + إنشاء**، ثم حدد **إنشاء** لتوفير المورد.
1. انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.
1. اعرض صفحة **المفاتيح ونقطة النهاية**. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التدريب.

## قُم بتكوين الوصول بناءً على الأدوار للمستخدم الخاص بك

> **ملاحظة**: إذا تخطيت هذه الخطوة، فسوف تحصل على خطأ 403 عند محاولة الاتصال بمشروعك المخصص. من الضروري أن يتم تعيين هذا الدور للمستخدم الحالي للوصول إلى البيانات الثنائية الكبيرة في حساب التخزين، حتى وإن كنت مالك حساب التخزين.

1. انتقل إلى صفحة حساب التخزين في مدخل Azure.
2. حدد **التحكم في الوصول (IAM)** من قائمة التنقل اليسرى.
3. حدد **إضافة** لإضافة واجبات الدور واختر دور **مساهم بيانات الكائن الثنائي كبير الحجم للتخزين** في حساب التخزين.
4. ضمن **تعيين الوصول إلى**، حدد **المستخدم أو المجموعة أو كيان الخدمة**.
5. حدد **تحديد أعضاء**.
6. حدد مُستخدمك. يمكنك البحث عن أسماء المستخدمين في الحقل **Select**.

## تحميل عينة إعلانات

بمجرد إنشاء "خدمة لغة الذكاء الاصطناعي في Azure" وحساب التخزين، سيتعين عليك تحميل أمثلة للإعلانات لتدريب النموذج لاحقًا.

1. في علامة تبويب جديدة بالمتصفح، قُم بتنزيل نماذج الإعلانات المصنَّفة من `https://aka.ms/entity-extraction-ads` واستخرِج الملفات إلى مجلد من اختيارك.

2. في مدخل Microsoft Azure، انتقل إلى حساب التخزين الذي أنشأته، وحدده.

3. في حساب التخزين الخاص بك، حدّد **تكوين**، الموجود أسفل **الإعدادات**، وظلِّل تمكين الخيار **السماح بالوصول المجهول للكائن الثنائي كبير الحجم** ثم حدّد **حفظ**.

4. حدّد **الحاويات** من القائمة اليمنى، الموجودة أسفل **تخزين البيانات**. على الشاشة التي تظهر، حدد **+ Container**. امنح الحاوية الاسم `classifieds`، وحدّد **مستوى الوصول المجهول** إلى **الحاوية (الوصول المجهول للقراءة فقط للحاويات والكائنات الثنائية كبيرة الحجم)**.

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
    - **مورد اللغة**: مورد Azure AI Language الذي أنشأتَه سابقًا.

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

> **تلميح**: إذا ظهر لديك خطأ بشأن عدم تفويضك لتنفيذ هذه العملية، فستحتاج إلى إضافة تعيين دور. لتصحيح ذلك، نقوم بإضافة دور "المساهم ببيانات الكائن الثنائي كبير الحجم للتخزين" على حساب التخزين للمستخدم والذي يقوم بتشغيل النشاط العملي. يمكن العثور على مزيدٍ من التفاصيل في [صفحة الوثائق](https://learn.microsoft.com/azure/ai-services/language-service/custom-named-entity-recognition/how-to/create-project?tabs=portal%2Clanguage-studio#enable-identity-management-for-your-resource).

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
1. في جزء **النشاط**، ستلاحظ أن هذا المستند سيتم إضافته إلى مجموعة البيانات لتدريب النموذج.
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

## الإعداد لتطوير تطبيق في Cloud Shell

لاختبار إمكانيات استخراج الوحدات المخصصة في خدمة Azure AI Language، ستقوم بتطوير تطبيق بسيط يعمل عبر وحدة تحكم في Azure Cloud Shell.

1. في بوابة Azure، استخدم الزر **[\>_]** على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة ***PowerShell***. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    **<font color="red">تأكد من التبديل إلى الإصدار الكلاسيكي من cloud shell قبل المتابعة.</font>**

1. في جزء PowerShell، أدخل الأوامر التالية لاستنساخ مستودع GitHub لهذا التمرين:

    ```
   rm -r mslearn-ai-language -f
   git clone https://github.com/microsoftlearning/mslearn-ai-language
    ```

    > **تلميح**: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.
    ```

1. After the repo has been cloned, navigate to the folder containing the application code files:  

    ```
    cd mslearn-ai-language/Labfiles/05-custom-entity-recognition/Python/custom-entities
    ```

## Configure your application

1. In the command line pane, run the following command to view the code files in the **custom-entities** folder:

    ```
   ls -a -l
    ```

    The files include a configuration file (**.env**) and a code file (**custom-entities.py**). The text your application will analyze is in the **ads** subfolder.

1. Create a Python virtual environment and install the Azure AI Language Text Analytics SDK package and other required packages by running the following command:

    ```
   python -m venv labenv ./labenv/bin/Activate.ps1 pip install -r requirements.txt azure-ai-textanalytics==5.3.0
    ```

1. Enter the following command to edit the application configuration file:

    ```
   code .env
    ```

    The file is opened in a code editor.

1. Update the configuration values to include the  **endpoint** and a **key** from the Azure Language resource you created (available on the **Keys and Endpoint** page for your Azure AI Language resource in the Azure portal).The file should already contain the project and deployment names for your custom entity extraction model.
1. After you've replaced the placeholders, within the code editor, use the **CTRL+S** command or **Right-click > Save** to save your changes and then use the **CTRL+Q** command or **Right-click > Quit** to close the code editor while keeping the cloud shell command line open.

## Add code to extract entities

1. Enter the following command to edit the application code file:

    ```
    code custom-entities.py
    ```

1. Review the existing code. You will add code to work with the AI Language Text Analytics SDK.

    > **Tip**: As you add code to the code file, be sure to maintain the correct indentation.

1. At the top of the code file, under the existing namespace references, find the comment **Import namespaces** and add the following code to import the namespaces you will need to use the Text Analytics SDK:

    ```python
   # import namespaces
   from azure.core.credentials import AzureKeyCredential
   from azure.ai.textanalytics import TextAnalyticsClient
    ```

1. في الدالة **Main**، لاحظ أن التعليمات البرمجية الخاصة بتحميل نقطة النهاية وخاصية المفتاح لخدمة Azure AI Language وكذلك أسماء المشروع والتوزيع من ملف الإعدادات متوفر مسبقًا. بعد ذلك، ابحث عن التعليق **Create client using endpoint and key**، وأضِف التعليمات البرمجية التالية لإنشاء عميل تحليلات النصوص:

    ```Python
   # Create client using endpoint and key
   credential = AzureKeyCredential(ai_key)
   ai_client = TextAnalyticsClient(endpoint=ai_endpoint, credential=credential)
    ```

1. يُرجى ملاحظة أن التعليمات البرمجية الحالية تقرأ جميع الملفات في مجلد **الإعلانات** وتنشئ قائمة بالمحتويات. بعد ذلك، ابحث عن التعليق **Extract entities** وأضِف التعليمات البرمجية التالية:

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

1. احفظ تغييراتك باستخدام (CTRL+S)، بعدها نفذ الأمر التالي لتشغيل البرنامج (قُم بتكبير جزء cloud shell وتعديل حجم الألواح لمشاهدة المزيد من النص في جزء سطر الأوامر):

    ```
   python custom-entities.py
    ```

1. مراقبة المخرجات. يجب أن يسرد التطبيق تفاصيل الكيانات الموجودة في كل ملف نصي.

## تنظيف

عندما لا تحتاج إلى مشروعك بعد الآن، يمكنك حذفه من صفحة **Projects**الخاصة بك في Language Studio. يمكنك أيضا إزالة خدمة Azure AI Language وحساب التخزين المقترن في [مدخل Microsoft Azure](https://portal.azure.com).
