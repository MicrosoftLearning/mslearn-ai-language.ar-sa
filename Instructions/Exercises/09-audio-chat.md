---
lab:
  title: تطوير تطبيق دردشة يدعم الصوت
  description: تعرّف على كيفية استخدام Azure AI Foundry لبناء تطبيق ذكاء اصطناعي توليدي يدعم إدخال الصوت.
---

# تطوير تطبيق دردشة يدعم الصوت

في هذا التمرين، يمكنك استخدام نموذج الذكاء الاصطناعي التوليدي *Phi-4-multimodal-instruct* لتوليد ردود للمطالبات التي تتضمن ملفات صوتية. ستُطوّر تطبيقًا يوفر مساعدة الذكاء الاصطناعي لشركة توريد المنتجات باستخدام Azure AI Foundry وخدمة استدلال نموذج الذكاء الاصطناعي في Azure لتلخيص الرسائل الصوتية التي يتركها العملاء.

سيستغرق هذا التدريب حوالي **30** دقيقة.

## إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure

دعنا نبدأ بإنشاء مشروع في مصنع الذكاء الاصطناعي في Azure.

1. في متصفح الويب، افتح [مدخل Azure AI Foundry](https://ai.azure.com) على `https://ai.azure.com` وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك. أغلق أية تلميحات أو أجزاء تشغيل سريع يتم فتحها عندما تقوم بتسجيل الدخول، وإذا لزم الأمر، استخدم شعار **مصنع الذكاء الاصطناعي في Azure** في أعلى اليسار للانتقال إلى الصفحة الرئيسية، والتي تبدو مشابهة للصورة التالية:

    ![لقطة شاشة لمدخل Azure AI Foundry.](../media/ai-foundry-home.png)

1. في الصفحة الرئيسية، حدد **+ إنشاء مشروع**.
1. في معالج** إنشاء مشروع**، أدخل اسمًا مناسبًا لمشروعك وإذا تم اقتراح مركز موجود، فحدد خيار إنشاء مركز جديد. ثم راجع موارد Azure التي سيتم إنشاؤها تلقائيًا لدعم مركزك ومشروعك.
1. حدد **تخصيص** وحدد الإعدادات التالية لمركزك:
    - **اسم المركز**: *اسم صالح لمركزك*
    - **Subscription**: *اشتراكك في Azure*
    - **Resource group**: *إنشاء مجموعة موارد أو تحديدها*
    - **الموقع**: حدد أيًا من المناطق التالية\*:
        - شرق الولايات المتحدة
        - East US 2
        - وسط شمال الولايات المتحدة
        - South Central US
        - منطقة السويد الوسطى
        - غرب الولايات المتحدة
        - غرب الولايات المتحدة الأمريكية 3
    - **توصيل خدمات Azure AI أو Azure OpenAI**: *إنشاء مورد جديد لخدمات الذكاء الاصطناعي*
    - **الاتصال بـ Azure AI Search**: تخطي الاتصال

    > \* في وقت كتابة هذا الدليل، يتوفر نموذج Microsoft *Phi-4-multimodal-instruct* الذي سنستخدمه في هذا التمرين في هذه المناطق. يمكنك التحقق من أحدث توفر إقليمي لنماذج معينة في [وثائق Azure AI Foundry](https://learn.microsoft.com/azure/ai-foundry/how-to/deploy-models-serverless-availability#region-availability). في حال تم الوصول إلى الحد الأقصى للحصة الإقليمية لاحقًا في التمرين، قد تحتاج إلى إنشاء مورد آخر في منطقة مختلفة.

1. حدد **التالي** لمراجعة التكوين الخاص بك. ثم حدد **إنشاء** وانتظر حتى تكتمل العملية.
1. عند إنشاء مشروعك، أغلق أي تلميحات يتم عرضها وراجع صفحة المشروع في مدخل مصنع الذكاء الاصطناعي في Azure، والذي يجب أن يبدو مشابهة للصورة التالية:

    ![لقطة شاشة توضح تفاصيل مشروع ذكاء اصطناعي في Azure في مدخل مصنع الذكاء الاصطناعي في Azure.](../media/ai-foundry-project.png)

## توزيع نموذج متعدد الوسائط

أنت الآن جاهز لنشر نموذج متعدد الوسائط يمكنه دعم الإدخال المستند إلى الصوت. هناك العديد من النماذج التي يمكنك الاختيار من بينها، بما في ذلك نموذج OpenAI *gpt-4o*. في هذا التمرين، سنستخدم نموذج *Phi-4-multimodal-instruct*.

1. في شريط الأدوات الموجود في أعلى يمين من صفحة مشروع مصنع الذكاء الاصطناعي في Azure، استخدم أيقونة** ميزات المعاينة**(**&#9215;**) للتأكد من تمكين ميزة **نشر النماذج في خدمة استنتاج نموذج Azure AI**. تضمن هذه الميزة توفّر توزيع النموذج الخاص بك لخدمة الاستدلال بالذكاء الاصطناعي في Azure، والتي ستستخدمها في كود التطبيق الخاص بك.
1. في الجزء الموجود على يسار مشروعك، في قسم **أصولي**، حدد صفحة **النماذج + نقاط النهاية**.
1. في صفحة **النماذج + نقاط النهاية**، في علامة التبويب **عمليات توزيع النماذج**، في القائمة **+ نشر النموذج**، حدّد **توزيع النموذج الأساسي**.
1. ابحث عن نموذج **Phi-4-multimodal-instruct** في القائمة، ثم حدده وأكّده.
1. وافق على اتفاقية الترخيص إذا طلب منك ذلك، ثم وزّع النموذج بالإعدادات التالية عن طريق تحديد **تخصيص** في تفاصيل التوزيع:
    - **اسم التوزيع**: *اسم صالح توزيع نموذجك*
    - **نوع النشر**: معيار عالمي
    - **تفاصيل التوزيع**: *استخدام الإعدادات الافتراضية*
1. انتظر حتى تصبح حالة التزويد للتوزيع **مكتملة**.

## أنشئ تطبيق عميل

الآن بعد أن نشرت النموذج، يمكنك استخدام النشر في تطبيق عميل.

> **تلميح**: يمكنك اختيار تطوير الحل الخاص بك باستخدام Python أو Microsoft C#. اتبع الإرشادات في القسم المناسب للغة التي اخترتها.

### إعداد تكوين التطبيق

1. في مدخل مصنع الذكاء الاصطناعي في Azure، اعرض صفحة **النظرة العامة** لمشروعك.
1. في منطقة **تفاصيل المشروع**، لاحظ **سلسلة الاتصال للمشروع**. ستستخدم سلسلة الاتصال هذه للاتصال بمشروعك في تطبيق العميل.
1. افتح علامة تبويب جديدة للمتصفح (مع إبقاء مدخل مصنع الذكاء الاصطناعي في Azure مفتوحًا في علامة التبويب الموجودة). بعد ذلك في علامة التبويب الجديدة، انتقل إلى [بوابة Azure](https://portal.azure.com) على `https://portal.azure.com`؛ وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك إذا طُلب منك ذلك.

    أغلق أي إشعارات ترحيبية لرؤية الصفحة الرئيسية لبوابة Azure.

1. استخدم الزر **[\>_]** الموجود على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة ***PowerShell*** بدون مساحة تخزين في اشتراكك.

    يوفّر Cloud Shell واجهة سطر الأوامر في الجزء الموجود في أسفل بوابة Azure. يمكنك تغيير حجم هذا الجزء أو تكبيره لتسهيل العمل فيه.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    **<font color="red">تأكد من التبديل إلى الإصدار الكلاسيكي من cloud shell قبل المتابعة.</font>**

1. في جزء Cloud Shell، أدخل الأوامر التالية لاستنساخ مستودع GitHub الذي يحتوي على ملفات التعليمات البرمجية لهذا التمرين (اكتب الأمر أو انسخه إلى الحافظة ثم انقر بزر الماوس الأيمن في سطر الأوامر وقم بلصقه كنص عادي):


    ```
    rm -r mslearn-ai-audio -f
    git clone https://github.com/MicrosoftLearning/mslearn-ai-language mslearn-ai-audio
    ```

    > **تلميح**: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.

1. بعد استنساخ مخزن بيانات خاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الدردشة:  

    **Python**

    ```
    cd mslearn-ai-audio/Labfiles/09-audio-chat/Python
    ```

    **C#**

    ```
    cd mslearn-ai-audio/Labfiles/09-audio-chat/C-sharp
    ```

1. في جزء سطر أوامر Cloud Shell، أدخل الأمر التالي لتثبيت المكتبات التي ستستخدمها:

    **Python**

    ```
    python -m venv labenv
    ./labenv/bin/Activate.ps1
    pip install -r requirements.txt azure-identity azure-ai-projects azure-ai-inference
    ```

    **C#**

    ```
    dotnet add package Azure.Identity
    dotnet add package Azure.AI.Inference --version 1.0.0-beta.3
    dotnet add package Azure.AI.Projects --version 1.0.0-beta.3
    ```

1. أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:

    **Python**

    ```
    code .env
    ```

    **C#**

    ```
    code appsettings.json
    ```

    ينبغي أن يفتح الملف في محرر التعليمات البرمجية.

1. في ملف التعليمات البرمجية، استبدل العنصر النائب **your_project_connection_string** بسلسلة الاتصال الخاصة بمشروعك (المنسوخة من صفحة **نظرة عامة** على المشروع في بوابة Azure AI Foundry)، واستبدل العنصر النائب **your_model_deployment** بالاسم الذي قمت بتعيينه لتوزيع نموذج Phi-4-multimodal-instruct الخاص بك.

1. بعد استبدال العناصر النائبة، في محرر التعليمات البرمجية، استخدم الأمر **CTRL+S** أو **انقر بزر الماوس الأيمن > حفظ** لحفظ التغييرات، ثم استخدم الأمر **CTRL+Q** أو **انقر بزر الماوس الأيمن > إنهاء** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحًا.

### اكتب التعليمة البرمجية للاتصال بمشروعك والحصول على عميل دردشة لنموذجك

> **تلميح**: عند إضافة التعليمات البرمجية، تأكد من الحفاظ على المسافة البادئة الصحيحة.

1. أدخل الأمر التالي لتحرير ملف التعليمات البرمجية الذي تم توفيره:

    **Python**

    ```
    code audio-chat.py
    ```

    **C#**

    ```
    code Program.cs
    ```

1. في ملف التعليمات البرمجية، لاحظ العبارات الموجودة في أعلى الملف والتي تمت إضافتها لاستيراد مساحات الأسماء (Namespaces) الضرورية لـ (SDK). بعد ذلك، ابحث عن التعليق **إضافة المراجع**، وأضف التعليمة البرمجية التالية للإشارة إلى المساحات الأساسية في المكتبات التي قمت بتثبيتها مسبقًا:

    **Python**

    ```python
    # Add references
    from dotenv import load_dotenv
    from azure.identity import DefaultAzureCredential
    from azure.ai.projects import AIProjectClient
    from azure.ai.inference.models import (
        SystemMessage,
        UserMessage,
        TextContentItem,
    )
    ```

    **C#**

    ```csharp
    // Add references
    using Azure.Identity;
    using Azure.AI.Projects;
    using Azure.AI.Inference;
    ```

1. في الوظيفة **الرئيسية**، تحت التعليق **الحصول على إعدادات التكوين**، لاحظ أن التعليمة البرمجية تقوم بتحميل قيم سلسلة الاتصال بالمشروع واسم نشر النموذج التي قمت بتحديدها في ملف التكوين.

1. ابحث عن التعليق **تهيئة عميل المشروع**، وأضف التعليمة البرمجية التالية للاتصال بمشروع Azure AI Foundry الخاص بك باستخدام بيانات اعتماد Azure التي قمت بتسجيل الدخول بها حاليًا:

    **Python**

    ```python
    # Initialize the project client
    project_client = AIProjectClient.from_connection_string(
        conn_str=project_connection,
        credential=DefaultAzureCredential())
    ```

    **C#**

    ```csharp
    // Initialize the project client
    var projectClient = new AIProjectClient(project_connection,
                        new DefaultAzureCredential());
    ```

1. ابحث عن التعليق **الحصول على عميل دردشة**، وأضف التعليمة البرمجية التالية لإنشاء عنصر عميل للدردشة مع النموذج الخاص بك:

    **Python**

    ```python
    # Get a chat client
    chat_client = project_client.inference.get_chat_completions_client(model=model_deployment)
    ```

    **C#**

    ```csharp
    // Get a chat client
    ChatCompletionsClient chat = projectClient.GetChatCompletionsClient();
    ```
    

### اكتب تعليمة برمجية لإرسال مطالبة صوتية تعتمد على عنوان URL

1. في محرر التعليمات البرمجية لملف **audio-chat.py**، في قسم التكرار، أسفل التعليق **الحصول على رد لإدخال الصوت**، أضف التعليمة البرمجية التالية لإرسال مطالبة تتضمن الصوت التالي:

    <video controls src="../media/avocados.mp4" title="طلب الأفوكادو" width="150"></video>

    **Python**

    ```python
    # Get a response to audio input
    file_path = "https://github.com/MicrosoftLearning/mslearn-ai-language/raw/refs/heads/main/Labfiles/09-audio-chat/data/avocados.mp3"
    response = chat_client.complete(
        messages=[
            SystemMessage(system_message),
            UserMessage(
                [
                    TextContentItem(text=prompt),
                    {
                        "type": "audio_url",
                        "audio_url": {"url": file_path}
                    }
                ]
            )
        ]
    )
    print(response.choices[0].message.content)
    ```

    **C#**

    ```csharp
    // Get a response to audio input
    string audioUrl = "https://github.com/MicrosoftLearning/mslearn-ai-language/raw/refs/heads/main/Labfiles/09-audio-chat/data/avocados.mp3";
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
    Console.WriteLine(response.Value.Content);
    ```

1. استخدم الأمر **CTRL+S** لحفظ التغييرات في ملف التعليمات البرمجية. يمكنك أيضًا إغلاق محرر التعليمات البرمجية باستخدام (**CTRL+Q**) إذا رغبت في ذلك.

1. في جزء سطر أوامر Cloud Shell أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل التطبيق:

    **Python**

    ```
    python audio-chat.py
    ```

    **C#**

    ```
    dotnet run
    ```

1. عند طلب ذلك، أدخل المطالبة 

    ```
    Can you summarize this customer's voice message?
    ```

1. راجع الاستجابة.

### استخدم ملفًا صوتيًا مختلفًا

1. في محرر التعليمات البرمجية الخاص بتطبيقك، ابحث عن التعليمة البرمجية التي أضفتها مسبقًا أسفل التعليق **الحصول على رد لإدخال الصوت**. ثم عدّل التعليمات البرمجية كما يلي لتحديد ملف صوتي مختلف:

    <video controls src="../media/fresas.mp4" title="طلب فراولة" width="150"></video>

    **Python**

    ```python
    # Get a response to audio input
    file_path = "https://github.com/MicrosoftLearning/mslearn-ai-language/raw/refs/heads/main/Labfiles/09-audio-chat/data/fresas.mp3"
    response = chat_client.complete(
        messages=[
            SystemMessage(system_message),
            UserMessage(
                [
                    TextContentItem(text=prompt),
                    {
                        "type": "audio_url",
                        "audio_url": {"url": file_path}
                    }
                ]
            )
        ]
    )
    print(response.choices[0].message.content)
    ```

    **C#**

    ```csharp
    // Get a response to audio input
    string audioUrl = "https://github.com/MicrosoftLearning/mslearn-ai-language/raw/refs/heads/main/Labfiles/09-audio-chat/data/fresas.mp3";
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
    Console.WriteLine(response.Value.Content);
    ```

1. استخدم الأمر **CTRL+S** لحفظ التغييرات في ملف التعليمات البرمجية. يمكنك أيضًا إغلاق محرر التعليمات البرمجية باستخدام (**CTRL+Q**) إذا رغبت في ذلك.

1. في جزء سطر أوامر Cloud Shell أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل التطبيق:

    **Python**

    ```
    python audio-chat.py
    ```

    **C#**

    ```
    dotnet run
    ```

1. عند طلب بذلك، أدخل المطالبة التالية: 
    
    ```
    Can you summarize this customer's voice message? Is it time-sensitive?
    ```

1. راجع الاستجابة. ثم أدخل `quit` للخروج من البرنامج.

    > **ملاحظة**: في هذا التطبيق البسيط، لم ننفّذ منطق للاحتفاظ بسجل المحادثة؛ لذلك سيعامل النموذج كل مطالبة على أنها طلب جديد دون أي سياق للمطالبة السابقة.

1. يمكنك الاستمرار في تشغيل التطبيق، واختيار أنواع مختلفة من المطالبات وتجربة مطالبات متنوعة. عند الانتهاء، أدخل `quit` للخروج من البرنامج.

    إذا كان لديك الوقت، فيمكنك تعديل التعليمة البرمجية لاستخدام مطالبة نظام مختلفة وملفات صوتية خاصة بك يمكن الوصول إليها عبر الإنترنت.

    > **ملاحظة**: في هذا التطبيق البسيط، لم ننفّذ منطق للاحتفاظ بسجل المحادثة؛ لذلك سيعامل النموذج كل مطالبة على أنها طلب جديد دون أي سياق للمطالبة السابقة.

## الملخص

في هذا التمرين، استخدمت Azure AI Foundry وAzure AI Inference SDK لإنشاء تطبيق عميل يستخدم نموذجًا متعدد الوسائط لتوليد الردود للصوت.

## تنظيف

إذا كنت قد أنهيت استكشاف Azure AI Foundry، يجب عليك حذف الموارد التي أنشأتها في هذا التمرين لتجنب تكاليف Azure غير الضرورية.

1. ارجع إلى علامة تبويب المتصفح التي تحتوي على بوابة Azure (أو أعد فتح [بوابة Azure](https://portal.azure.com) في `https://portal.azure.com` في علامة تبويب متصفح جديدة) واعرض محتويات مجموعة الموارد التي نشرت فيها الموارد المستخدمة في هذا التدريب.
1. على شريط الأدوات، حدد **حذف مجموعة الموارد**.
1. أدخل اسم مجموعة الموارد وأكّد أنك تريد حذفها.
