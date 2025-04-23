---
lab:
  title: التعرف على الكلام وتجميعه (إصدار Azure AI Foundry)
  module: Module 4 - Create speech-enabled apps with Azure AI services
---

<!--
Possibly update to use standalone AI Service instead of Foundry?
-->

# التعرف على الكلام وتجميعه

**الكلام بالذكاء الاصطناعي في Azure** هي خدمة توفر وظائف متعلقة بالكلام، بما في ذلك:

- واجهة برمجة تطبيقات *تحويل الكلام إلى نص* تمكنك من تنفيذ التعرّف على الكلام (تحويل الكلمات المنطوقة المسموعة إلى نص).
- واجهة برمجة تطبيقات *تحويل النص إلى كلام* تمكنك من تنفيذ تركيب الكلام (تحويل النص إلى كلام مسموع).

في هذا التمرين، ستستخدم كلا من واجهات برمجة التطبيقات هذه لتنفيذ تطبيق ساعة التحدث.

> **ملاحظة** تم تصميم هذا التدريب لإكماله في Azure cloud shell، حيث لا يتم دعم الوصول المباشر إلى الأجهزة الصوتية لجهاز الكمبيوتر الخاص بك. لذلك سيستخدم النشاط العملي ملفات الصوت لعمليات دفق مدخلات ومخرجات الكلام. يتم توفير التعليمات البرمجية لتحقيق نفس النتائج باستخدام ميكروفون ومكبر صوت كمرجع.

## إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure

دعنا نبدأ بإنشاء مشروع في مصنع الذكاء الاصطناعي في Azure.

1. في متصفح الويب، افتح [مدخل Azure AI Foundry](https://ai.azure.com) على `https://ai.azure.com` وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك. أغلق أية تلميحات أو أجزاء تشغيل سريع يتم فتحها عندما تقوم بتسجيل الدخول، وإذا لزم الأمر، استخدم شعار **مصنع الذكاء الاصطناعي في Azure** في أعلى اليسار للانتقال إلى الصفحة الرئيسية، والتي تبدو مشابهة للصورة التالية:

    ![لقطة شاشة لمدخل Azure AI Foundry.](./ai-foundry/media/ai-foundry-home.png)

1. في الصفحة الرئيسية، حدد **+ إنشاء مشروع**.
1. في معالج **إنشاء مشروع**، أدخل اسمًا صالحًا لمشروعك، وإذا تم اقتراح مركز موجود، فاختر خيار إنشاء مركز جديد. ثم راجع موارد Azure التي سيتم إنشاؤها تلقائيًا لدعم مركزك ومشروعك.
1. حدد **تخصيص** وحدد الإعدادات التالية لمركزك:
    - **اسم المركز**: *اسم صالح لمركزك*
    - **Subscription**: *اشتراكك في Azure*
    - **Resource group**: *إنشاء مجموعة موارد أو تحديدها*
    - **الموقع**: اختر أي منطقة متاحة
    - **اتصال خدمات الذكاء الاصطناعي في Azure أو Azure OpenAI**: *إنشاء مورد جديد لخدمات الذكاء الاصطناعي*
    - **ربط Azure AI Search**: *أنشئ مورد Azure AI Search جديد باسم فريد*

1. حدد **التالي** لمراجعة التكوين الخاص بك. ثم حدد **إنشاء** وانتظر حتى تكتمل العملية.
1. عند إنشاء مشروعك، أغلق أي تلميحات يتم عرضها وراجع صفحة المشروع في مدخل مصنع الذكاء الاصطناعي في Azure، والذي يجب أن يبدو مشابهة للصورة التالية:

    ![لقطة شاشة توضح تفاصيل مشروع ذكاء اصطناعي في Azure في مدخل مصنع الذكاء الاصطناعي في Azure.](./ai-foundry/media/ai-foundry-project.png)

## إعداد وتكوين تطبيق الساعة الناطقة

1. في مدخل مصنع الذكاء الاصطناعي في Azure، اعرض صفحة **النظرة العامة** لمشروعك.
1. في منطقة **تفاصيل المشروع**، لاحظ **سلسلة الاتصال الخاصة بالمشروع**و **موقعه** لمشروعك. ستستخدم سلسلة الاتصال للاتصال بمشروعك في تطبيق عميل، وستحتاج إلى الموقع للاتصال بنقطة نهاية Azure AI Services Speech.
1. افتح علامة تبويب جديدة للمتصفح (مع إبقاء مدخل مصنع الذكاء الاصطناعي في Azure مفتوحًا في علامة التبويب الموجودة). بعد ذلك في علامة التبويب الجديدة، انتقل إلى [بوابة Azure](https://portal.azure.com) على `https://portal.azure.com`؛ وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك إذا طُلب منك ذلك.
1. استخدم الزر **[\>_]** الموجود على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة ***PowerShell***. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    > **تلميح**: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.

1. في جزء PowerShell، أدخل الأوامر التالية لاستنساخ مستودع GitHub لهذا التمرين:

    ```
   rm -r mslearn-ai-language -f
   git clone https://github.com/microsoftlearning/mslearn-ai-language mslearn-ai-language
    ```

    ***الآن اتبع الخطوات الخاصة بلغة البرمجة التي اخترتها.***

1. بعد استنساخ مخزن البيانات الخاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الساعة الناطقة:  

    **Python**

    ```
   cd mslearn-ai-language/labfiles/07b-speech/python/speaking-clock
    ```

    **C#**

    ```
   cd mslearn-ai-language/labfiles/07b-speech/c-sharp/speaking-clock
    ```

1. في جزء سطر أوامر Cloud Shell، أدخل الأمر التالي لتثبيت المكتبات التي ستستخدمها:

    **Python**

    ```
   python -m venv labenv
   ./labenv/bin/Activate.ps1
   pip install python-dotenv azure-identity azure-ai-projects azure-cognitiveservices-speech==1.42.0
    ```

    **C#**

    ```
   dotnet add package Azure.Identity
   dotnet add package Azure.AI.Projects --prerelease
   dotnet add package Microsoft.CognitiveServices.Speech --version 1.42.0
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

    يتم فتح الملف في محرر التعليمات البرمجية.

1. ملف التعليمات البرمجية، استبدل أماكن وضع** your_project_endpoint** و**your_location**بسلسلة الاتصال والموقع الخاص بمشروعك (تم نسخها من صفحة **نظرة عامة** على المشروع في البوابة الإلكترونية الخاصة بـ Azure AI Foundry)
1. بعد استبدال العناصر النائبة، استخدم الأمر **CTRL+S** لحفظ التغييرات ثم استخدم الأمر **CTRL+Q** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحWا.

## إضافة تعليمات برمجية لاستخدام Azure AI Speech SDK

> **تلميح**: عند إضافة التعليمات البرمجية، تأكد من الحفاظ على المسافة البادئة الصحيحة.

1. أدخل الأمر التالي لتحرير ملف التعليمات البرمجية الذي تم توفيره:

    **Python**

    ```
   code speaking-clock.py
    ```

    **C#**

    ```
   code Program.cs
    ```

1. في أعلى ملف التعليمات البرمجية، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، وضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Speech SDK بواسطة مورد Azure AI Services في مشروع Azure AI Foundry الخاص بك. 

    **Python**

    ```python
   # Import namespaces
   from dotenv import load_dotenv
   from azure.ai.projects.models import ConnectionType
   from azure.identity import DefaultAzureCredential
   from azure.core.credentials import AzureKeyCredential
   from azure.ai.projects import AIProjectClient
   import azure.cognitiveservices.speech as speech_sdk
    ```

    **C#**

    ```csharp
   // Import namespaces
   using Azure.Identity;
   using Azure.AI.Projects;
   using Microsoft.CognitiveServices.Speech;
   using Microsoft.CognitiveServices.Speech.Audio;
    ```

1. في الوظيفة **الرئيسية**، تحت التعليق **الحصول على إعدادات التكوين**، لاحظ أن التعليمات البرمجية تقوم بتحميل قيم سلسلة الاتصال وموقع المشروع اللذين قمت بتحديدهم في ملف التكوين.

1. أضف التعليمات البرمجية التالية ضمن التعليق **Get AI Speech الخاص بنقطة النهاية والمفتاح من المشروع**:

    **Python**

    ```python
   # Get AI Services key from the project
   project_client = AIProjectClient.from_connection_string(
        conn_str=project_connection,
        credential=DefaultAzureCredential())

   ai_svc_connection = project_client.connections.get_default(
      connection_type=ConnectionType.AZURE_AI_SERVICES,
      include_credentials=True, 
    )

   ai_svc_key = ai_svc_connection.key

    ```

    **C#**

    ```csharp
   // Get AI Services key from the project
   var projectClient = new AIProjectClient(project_connection,
                        new DefaultAzureCredential());

   ConnectionResponse aiSvcConnection = projectClient.GetConnectionsClient().GetDefaultConnection(ConnectionType.AzureAIServices, true);

   var apiKeyAuthProperties = aiSvcConnection.Properties as ConnectionPropertiesApiKeyAuth;

   var aiSvcKey = apiKeyAuthProperties.Credentials.Key;
    ```

    تتصل هذه التعليمات البرمجية بمشروع Azure AI Foundry الخاص بك، وتحصل على المورد الافتراضي لـ AI Services المتصل، وتسترد مفتاح المصادقة المطلوب لاستخدامه.

1. ضمن تعليق**تكوين خدمة الكلام**، أضف التعليمات البرمجية التالية لاستخدام مفتاح AI Services ومنطقة المشروع الخاصة بك لتكوين اتصالك بنقطة نهاية Azure AI Services Speech

   **Python**

    ```python
   # Configure speech service
   speech_config = speech_sdk.SpeechConfig(ai_svc_key, location)
   print('Ready to use speech service in:', speech_config.region)
    ```

    **C#**

    ```csharp
   // Configure speech service
   speechConfig = SpeechConfig.FromSubscription(aiSvcKey, location);
   Console.WriteLine("Ready to use speech service in " + speechConfig.Region);
    ```

1. احفظ التغييرات (*CTRL+S*)، ولكن اترك محرر التعليمات البرمجية مفتوحا.

## تشغيل التطبيق

حتى الآن، لا يقوم التطبيق بأي شيء آخر غير الاتصال بمشروع Azure AI Foundry لاسترداد التفاصيل اللازمة لاستخدام خدمة الكلام، ولكن من المفيد تشغيلها والتحقق من أنها تعمل قبل إضافة وظيفة الكلام.

1. في سطر الأوامر أسفل محرر التعليمات البرمجية، أدخل أمر Azure CLI التالي لتحديد حساب Azure الذي تم تسجيل الدخول إليه لجلسة العمل:

    ```
   az account show
    ```

    يجب أن تتضمن نواتج JSON تفاصيل حساب Azure والاشتراك الذي تعمل فيه (والذي يجب أن يكون نفس الاشتراك الذي أنشأت فيه مشروع Azure AI Foundry.)

    يستخدم تطبيقك بيانات اعتماد Azure للسياق الذي يتم تشغيله فيه لمصادقة الاتصال بمشروعك. في بيئة الإنتاج، قد يتم تكوين التطبيق للتشغيل باستخدام هوية مدارة. في بيئة التطوير هذه، سيستخدم بيانات اعتماد جلسة عمل cloud shell المصادق عليها.

    > **ملاحظة**: يمكنك تسجيل الدخول إلى Azure في بيئة التطوير باستخدام `az login` الأمر Azure CLI. في هذه الحالة، تكون cloud shell قد سجلت الدخول بالفعل باستخدام بيانات اعتماد Azure التي قمت بتسجيل الدخول إلى البوابة الإلكترونية بها؛ لذا، فإن تسجيل الدخول بشكل صريح غير ضروري. لمعرفة المزيد حول استخدام Azure CLI للمصادقة على Azure، راجع [المصادقة على Azure باستخدام Azure CLI](https://learn.microsoft.com/cli/azure/authenticate-azure-cli).

1. في سطر الأوامر، أدخل الأمر التالي الخاص باللغة لتشغيل تطبيق الساعة الناطقة:

    **Python**

    ```
   python speaking-clock.py
    ```

    **C#**

    ```
   dotnet run
    ```

1. إذا كنت تستخدم C#، فيمكنك تجاهل أي تحذيرات حول استخدام عامل **الانتظار** في الطرق غير المتزامنة - وسنصلح ذلك لاحقاً. يجب أن تعرض التعليمات البرمجية منطقة مورد خدمة الكلام الذي سيستخدمه التطبيق. يشير التشغيل الناجح إلى أن التطبيق قد اتصل بمشروع Azure AI Foundry واسترد المفتاح الذي يحتاجه لاستخدام خدمة Azure AI Speech service.

## إضافة تعليمة برمجية للتعرّف على الكلام

الآن بعد أن أصبح لديك **SpeechConfig** لخدمة الكلام في مورد Azure AI Services، يمكنك استخدام واجهة برمجة تطبيقات **تحويل الكلام إلى نص** للتعرّف على الكلام ونسخه إلى نص.

في هذا الإجراء، يتم التقاط مدخلات الكلام من ملف صوتي، والذي يمكنك تشغيله هنا:

<video controls src="ai-foundry/media/Time.mp4" title="كم الساعة؟" width="150"></video>

1. في الدالة **الأساسية**، لاحظ أن التعليمات البرمجية تستخدم دالة **TranscribeCommand** لقبول الإدخال المنطوق. ثم في دالة **TranscribeCommand**، ضمن التعليق **تكوين التعرّف على الكلام**، أضف التعليمة البرمجية المناسب أدناه لإنشاء عميل **SpeechRecognizer** الذي يمكن استخدامه للتعرّف على الكلام ونسخه من ملف صوتي:

    **Python**

    ```python
   # Configure speech recognition
   current_dir = os.getcwd()
   audioFile = current_dir + '/time.wav'
   audio_config = speech_sdk.AudioConfig(filename=audioFile)
   speech_recognizer = speech_sdk.SpeechRecognizer(speech_config, audio_config)
    ```

    **C#**

    ```csharp
   // Configure speech recognition
   string audioFile = "time.wav";
   using AudioConfig audioConfig = AudioConfig.FromWavFileInput(audioFile);
   using SpeechRecognizer speechRecognizer = new SpeechRecognizer(speechConfig, audioConfig);
    ```

1. في الدالة **TranscribeCommand**، ضمن التعليق **معالجة إدخال الكلام**، أضف التعليمة البرمجية التالية للاستماع إلى الإدخال المنطوق، مع الحرص على عدم استبدال التعليمة البرمجية الموجودة في نهاية الدالة التي تُرجع الأمر:

    **Python**

    ```python
   # Process speech input
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
           print(cancellation.error_details)
    ```

    **C#**

    ```csharp
   // Process speech input
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
   }
    ```

1. احفظ التغييرات (*CTRL+S*)، ثم في سطر الأوامر أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل البرنامج:

    **Python**

    ```
   python speaking-clock.py
    ```

    **C#**

    ```
   dotnet run
    ```

1. راجع المخرجات من التطبيق، الذي يجب أن "يسمع" الكلام بنجاح في الملف الصوتي وإرجاع استجابة مناسبة (لاحظ أن Azure cloud shell قد يكون قيد التشغيل على خادم في منطقة زمنية مختلفة عن منطقتك!)

    > **تلميح**: إذا واجه SpeechRecognizer خطئًا، فإنه يكون نتيجة "الإلغاء". ستعرض التعليمات البرمجية في التطبيق بعد ذلك رسالة الخطأ. السبب الأكثر احتمالاً هو مفتاح غير صحيح أو منطقة غير صحيحة في ملف التكوين.

## تركيب الكلام

يقبل تطبيق الساعة الناطقة الإدخال المنطوق، ولكنه لا يتحدث في الواقع! لنصلح ذلك عن طريق إضافة تعليمة برمجية لتركيب الكلام.

مرة أخرى، نظرًا لقيود الأجهزة الخاصة بـ cloud shell سنوجه مخرجات الكلام المركبة إلى ملف.

1. في الدالة **الأساسية** لبرنامجك، لاحظ أن التعليمات البرمجية تستخدم الدالة **TellTime** لإخبار المستخدم بالوقت الحالي.
1. في الدالة **TellTime**، ضمن التعليق **تكوين تركيب** الكلام، أضف التعليمات البرمجية التالية لإنشاء **عميل SpeechSynthesizer** الذي يمكن استخدامه لإنشاء إخراج منطوق:

    **Python**

    ```python
   # Configure speech synthesis
   output_file = "output.wav"
   speech_config.speech_synthesis_voice_name = "en-GB-RyanNeural"
   audio_config = speech_sdk.audio.AudioConfig(filename=output_file)
   speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config, audio_config,)
    ```

    **C#**

    ```csharp
   // Configure speech synthesis
   var outputFile = "output.wav";
   speechConfig.SpeechSynthesisVoiceName = "en-GB-RyanNeural";
   using var audioConfig = AudioConfig.FromWavFileOutput(outputFile);
   using SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer(speechConfig, audioConfig);
    ```

1. في الدالة **TellTime**، ضمن التعليق **تركيب الإخراج المنطوق**، أضف التعليمات البرمجية التالية لإنشاء إخراج منطوق، مع الحرص على عدم استبدال التعليمات البرمجية في نهاية الدالة التي تطبع الاستجابة:

    **Python**

    ```python
   # Synthesize spoken output
   speak = speech_synthesizer.speak_text_async(response_text).get()
   if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
       print(speak.reason)
   else:
       print("Spoken output saved in " + outputFile)
    ```

    **C#**

    ```csharp
   // Synthesize spoken output
   SpeechSynthesisResult speak = await speechSynthesizer.SpeakTextAsync(responseText);
   if (speak.Reason != ResultReason.SynthesizingAudioCompleted)
   {
       Console.WriteLine(speak.Reason);
   }
   else
   {
       Console.WriteLine("Spoken output saved in " + outputFile);
   }
    ```

1. احفظ التغييرات (*CTRL+S*)، ثم في سطر الأوامر أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل البرنامج:

   **Python**

    ```
   python speaking-clock.py
    ```

    **C#**

    ```
   dotnet run
    ```

1. راجع المخرجات من التطبيق، والذي يجب أن يشير إلى أنه تم حفظ المخرجات المنطوقة في ملف.
1. إذا كان لديك مشغل وسائط قادر على تشغيل الملفات الصوتية .wav، ففي شريط الأدوات لجزء cloud shell، استخدم **الزر Upload/Download files** لتنزيل الملف الصوتي من مجلد التطبيق، ثم قم بتشغيله:

    **Python**

    /home/*user*`/mslearn-ai-language/Labfiles/07b-speech/Python/speaking-clock/output.wav`

    **C#**

    /home/*user*`/mslearn-ai-language/Labfiles/07b-speech/C-Sharp/speaking-clock/output.wav`

    يجب أن يكون صوت الملف النهائي مشابهًا لهذا:

    <video controls src="./ai-foundry/media/Output.mp4" title="الوقت هو 2:15" width="150"></video>

## استخدام لغة Speech Synthesis Markup (SSML)

تمكنك لغة ترميز تركيب الكلام (SSML) من تخصيص طريقة تركيب كلامك باستخدام تنسيق يستند إلى XML.

1. في الدالة **TellTime**، استبدل كافة التعليمات البرمجية الحالية ضمن التعليق **تركيب النتيجة المنطوقة** بالتعليمات البرمجية التالية (اترك التعليمات البرمجية ضمن التعليق **طباعة الاستجابة**):

    **Python**

    ```python
   # Synthesize spoken output
   responseSsml = " \
       <speak version='1.0' xmlns='http://www.w3.org/2001/10/synthesis' xml:lang='en-US'> \
           <voice name='en-GB-LibbyNeural'> \
               {} \
               <break strength='weak'/> \
               Time to end this lab! \
           </voice> \
       </speak>".format(response_text)
   speak = speech_synthesizer.speak_ssml_async(responseSsml).get()
   if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
       print(speak.reason)
   else:
       print("Spoken output saved in " + outputFile)
    ```

   **C#**

    ```csharp
   // Synthesize spoken output
   string responseSsml = $@"
       <speak version='1.0' xmlns='http://www.w3.org/2001/10/synthesis' xml:lang='en-US'>
           <voice name='en-GB-LibbyNeural'>
               {responseText}
               <break strength='weak'/>
               Time to end this lab!
           </voice>
       </speak>";
   SpeechSynthesisResult speak = await speechSynthesizer.SpeakSsmlAsync(responseSsml);
   if (speak.Reason != ResultReason.SynthesizingAudioCompleted)
   {
       Console.WriteLine(speak.Reason);
   }
   else
   {
        Console.WriteLine("Spoken output saved in " + outputFile);
   }
    ```

1. احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد **الساعة الناطقة** وأدخل الأمر التالي لتشغيل البرنامج:

    **Python**

    ```
   python speaking-clock.py
    ```

    **C#**

    ```
   dotnet run
    ```

1. راجع المخرجات من التطبيق، والذي يجب أن يشير إلى أنه تم حفظ المخرجات المنطوقة في ملف.
1. مرة أخرى، إذا كان لديك مشغل وسائط قادر على تشغيل الملفات الصوتية .wav، في شريط الأدوات لجزء cloud shell، فاستخدم **الزر Upload/Download files** لتنزيل الملف الصوتي من مجلد التطبيق، ثم قم بتشغيله:

    **Python**

    /home/*user*`/mslearn-ai-language/Labfiles/07b-speech/Python/speaking-clock/output.wav`

    **C#**

    /home/*user*`/mslearn-ai-language/Labfiles/07b-speech/C-Sharp/speaking-clock/output.wav`

    يجب أن يكون صوت الملف النهائي مشابهًا لهذا:
    
    <video controls src="./ai-foundry/media/Output2.mp4" title="الوقت هو 5:30. حان الوقت لإنهاء هذا النشاط العملي." width="150"></video>

## تنظيف

إذا انتهيت من استكشاف Azure AI Speech فيجب عليك حذف الموارد التي قمت بإنشائها في هذا التدريب لتجنب تكبد تكاليف Azure غير ضرورية.

1. ارجع إلى علامة تبويب المتصفح التي تحتوي على بوابة Azure (أو أعد فتح [بوابة Azure](https://portal.azure.com) في `https://portal.azure.com` في علامة تبويب متصفح جديدة) واعرض محتويات مجموعة الموارد التي نشرت فيها الموارد المستخدمة في هذا التدريب.
1. على شريط الأدوات، حدد **حذف مجموعة الموارد**.
1. أدخل اسم مجموعة الموارد وأكّد أنك تريد حذفها.

## ماذا لو كان لديك ميكروفون ومكبر صوت؟

سوف تستخدم ملفات صوتية لمدخلات ومخرجات الكلام في هذا التدريب. دعونا نرى كيف يمكن تعديل التعليمات البرمجية لاستخدام الأجهزة الصوتية.

### استخدام التعرف على الكلام من خلال ميكروفون

إذا كان لديك ميكروفون، يمكنك استخدام التعليمات البرمجية التالية لالتقاط المدخلات المنطوقة للتعرف على الكلام:

**Python**

```python
# Configure speech recognition
audio_config = speech_sdk.AudioConfig(use_default_microphone=True)
speech_recognizer = speech_sdk.SpeechRecognizer(speech_config, audio_config)
print('Speak now...')

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
        print(cancellation.error_details)

```

**C#**

```csharp
// Configure speech recognition
using AudioConfig audioConfig = AudioConfig.FromDefaultMicrophoneInput();
using SpeechRecognizer speechRecognizer = new SpeechRecognizer(speechConfig, audioConfig);
Console.WriteLine("Speak now...");

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
}
```

> **ملاحظة**: الميكروفون الافتراضي للنظام هو مدخل الصوت الافتراضي، لذلك يمكنك أيضا حذف AudioConfig تمامًا!

### استخدام تركيب الكلام بواسطة مكبر صوت

إذا كان لديك مكبر صوت، يمكنك استخدام التعليمات البرمجية التالية لتجميع الكلام.

**Python**

```python
response_text = 'The time is {}:{:02d}'.format(now.hour,now.minute)

# Configure speech synthesis
speech_config.speech_synthesis_voice_name = "en-GB-RyanNeural"
audio_config = speech_sdk.audio.AudioOutputConfig(use_default_speaker=True)
speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config, audio_config)

# Synthesize spoken output
speak = speech_synthesizer.speak_text_async(response_text).get()
if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
    print(speak.reason)
```

**C#**

```csharp
var now = DateTime.Now;
string responseText = "The time is " + now.Hour.ToString() + ":" + now.Minute.ToString("D2");

// Configure speech synthesis
speechConfig.SpeechSynthesisVoiceName = "en-GB-RyanNeural";
using var audioConfig = AudioConfig.FromDefaultSpeakerOutput();
using SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer(speechConfig, audioConfig);

// Synthesize spoken output
SpeechSynthesisResult speak = await speechSynthesizer.SpeakTextAsync(responseText);
if (speak.Reason != ResultReason.SynthesizingAudioCompleted)
{
    Console.WriteLine(speak.Reason);
}
```

> **ملاحظة**: مكبر الصوت الافتراضي للنظام هي مُخرج الصوت الافتراضي، لذلك يمكنك أيضا حذف AudioConfig تمامًا!

## مزيد من المعلومات

لمزيد من المعلومات حول استخدام واجهات برمجة تطبيقات **تحويل الكلام إلى نص** **والنص إلى كلام**، راجع [وثائق تحويل الكلام إلى نص ووثائق](https://learn.microsoft.com/azure/ai-services/speech-service/index-speech-to-text) [وتحويل النص إلى كلام](https://learn.microsoft.com/azure/ai-services/speech-service/index-text-to-speech).
