---
lab:
  title: التعرف على الكلام وتركيبه
  module: Module 4 - Create speech-enabled apps with Azure AI services
---

# التعرف على الكلام وتجميعه

**الكلام بالذكاء الاصطناعي في Azure** هي خدمة توفر وظائف متعلقة بالكلام، بما في ذلك:

- واجهة برمجة تطبيقات *تحويل الكلام إلى نص* تمكنك من تنفيذ التعرّف على الكلام (تحويل الكلمات المنطوقة المسموعة إلى نص).
- واجهة برمجة تطبيقات *تحويل النص إلى كلام* تمكنك من تنفيذ تركيب الكلام (تحويل النص إلى كلام مسموع).

في هذا التمرين، ستستخدم كلا من واجهات برمجة التطبيقات هذه لتنفيذ تطبيق ساعة التحدث.

> **ملاحظة** يتطلب هذا التمرين استخدام كمبيوتر مزود بسماعات/سماعات رأس. للحصول على تجربة مثلى، يلزم وجود ميكروفون أيضاً. قد تتمكن بعض البيئات الظاهرية المستضافة من التقاط الصوت من الميكروفون المحلي، ولكن إذا لم ينجح ذلك (أو لم يكن لديك ميكروفون على الإطلاق)، فيمكنك استخدام ملف صوتي متوفر لإدخال الكلام. اتبع الإرشادات بعناية، حيث ستحتاج إلى تحديد خيارات مختلفة استناداً إلى ما إذا كنت تستخدم ميكروفوناً أو ملفاً صوتياً.

## توفير مورد *Azure AI Speech*

إذا لم يكن لديك بالفعل مورداً في اشتراكك، فسيتعين عليك توفير مورد **Azure AI Speech**.

1. افتح مدخل Microsoft Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
1. في حقل البحث في الأعلى، ابحث عن **خدمات الذكاء الاصطناعي في Azure** واضغط على **دخول**، ثم حدد **إنشاء** ضمن **خدمة الكلام** في النتائج.
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

## الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية

ستطور تطبيق الكلام لديك باستخدام تعليمة Visual Studio البرمجية. ملفات التعليمات البرمجية متوفرة لتطبيقك في مستودع GitHub.

> **تلميح**: إذا استنسخت بالفعل مستودع **mslearn-ai-language**، فافتحه في Visual Studio code وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.

1. ابدأ تشغيل Visual Studio Code.
1. افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-language` إلى مجلد محلي (لا يُهم أي مجلد).
1. عند استنساخ المستودع، افتح المجلد في Visual Studio Code.

    > **ملاحظة**: إذا عرضت لك Visual Studio Code رسالة منبثقة لمطالبتك بالثقة في التعليمات البرمجية التي تفتحها، فانقر فوق **نعم، أثق في خيار الكُتاب** في النافذة المنبثقة.

1. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

## تكوين تطبيقك

تم توفير تطبيقات لكل من C# وPython. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد الكلام بالذكاء الاصطناعي في Azure الخاص بك.

1. في Visual Studio Code، في جزء **Explorer**، استعرض للوصول إلى المجلد **Labfiles/07-speech** ووسع نطاق المجلد **CSharp** أو **Python** استناداً إلى تفضيلات اللغة ومجلد **الساعة الناطقة** الذي يحتوي عليها. يحتوي كل مجلد على ملفات التعليمات البرمجية الخاصة باللغة الخاصة بأحد التطبيقات الذي ستدمج وظيفة الكلام بالذكاء الاصطناعي في Azure.
1. انقر بزر الماوس الأيمن فوق مجلد **الساعة الناطقة** الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم عليك تثبيت حزمة Azure AI Vision SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#**

    ```
    dotnet add package Microsoft.CognitiveServices.Speech --version 1.30.0
    ```

    **Python**

    ```
    pip install azure-cognitiveservices-speech==1.30.0
    ```

1. في جزء **Explorer**، في مجلد **الساعة الناطقة**، افتح ملف التكوين للغتك المفضلة

    - **C#**: appsettings.json
    - **Python**: .env

1. يمكن تحديث قيم التكوين لتضمين **المنطقة** **ومفتاح** من مورد Azure AI Speech الذي أنشأته (المتوفر في صفحة **المفاتيح ونقطة النهاية** لمورد Azure AI Speech في Azure  لديك في مدخل Microsoft Azure ).

    > **ملاحظة**: تأكد من إضافة *المنطقة* لموردك، <u>وليس</u> نقطة النهاية!

1. احفظ ملف التكوين.

## إضافة تعليمات برمجية لاستخدام Azure AI Speech SDK

1. لاحظ أن مجلد **الساعة الناطقة** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: speaking-clock.py

    افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:

    **C#**: Program.cs

    ```csharp
    // Import namespaces
    using Microsoft.CognitiveServices.Speech;
    using Microsoft.CognitiveServices.Speech.Audio;
    ```

    **Python**: speaking-clock.py

    ```python
    # Import namespaces
    import azure.cognitiveservices.speech as speech_sdk
    ```

1. في الدالة **الأساسية**، لاحظ أنه جرى بالفعل توفير التعليمات البرمجية لتحميل مفتاح الخدمة والمنطقة من ملف التكوين. يجب عليك استخدام هذه المتغيرات لإنشاء **SpeechConfig** لمورد الكلام بالذكاء الاصطناعي في Azure الخاص بك. أضف التعليمات البرمجية التالية ضمن التعليق **تكوين خدمة الكلام**:

    **C#**: Program.cs

    ```csharp
    // Configure speech service
    speechConfig = SpeechConfig.FromSubscription(aiSvcKey, aiSvcRegion);
    Console.WriteLine("Ready to use speech service in " + speechConfig.Region);
    
    // Configure voice
    speechConfig.SpeechSynthesisVoiceName = "en-US-AriaNeural";
    ```

    **Python**: speaking-clock.py

    ```python
    # Configure speech service
    speech_config = speech_sdk.SpeechConfig(ai_key, ai_region)
    print('Ready to use speech service in:', speech_config.region)
    ```

1. احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد **الساعة الناطقة** وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python speaking-clock.py
    ```

1. إذا كنت تستخدم C#، فيمكنك تجاهل أي تحذيرات حول استخدام عامل **الانتظار** في الطرق غير المتزامنة - وسنصلح ذلك لاحقاً. يجب أن تعرض التعليمات البرمجية منطقة مورد خدمة الكلام الذي سيستخدمه التطبيق.

## إضافة تعليمة برمجية للتعرّف على الكلام

الآن بعد أن أصبح لديك **SpeechConfig** لخدمة الكلام في مورد الكلام بالذكاء الاصطناعي في Azure، يمكنك استخدام واجهة برمجة تطبيقات **تحويل الكلام إلى نص** للتعرّف على الكلام ونسخه إلى نص.

> **مهم**: يتضمن هذا القسم تعليمات لإجراءين بديلين. اتبع الإجراء الأول إذا كان لديك ميكروفون يعمل. اتبع الإجراء الثاني إذا كنت تريد محاكاة الإدخال المنطوق باستخدام ملف صوتي.

### إذا كان لديك ميكروفون يعمل

1. في الدالة **الأساسية** لبرنامجك، لاحظ أن التعليمات البرمجية تستخدم دالة **TranscribeCommand** لقبول الإدخال المنطوق.
1. في الدالة **TranscribeCommand**، ضمن تعليق **تكوين التعرّف على الكلام**، أضف التعليمة البرمجية المناسبة أدناه لإنشاء عميل **SpeechRecognizer** الذي يمكن استخدامه للتعرّف على الكلام ونسخه باستخدام ميكروفون النظام الافتراضي:

    **C#**

    ```csharp
    // Configure speech recognition
    using AudioConfig audioConfig = AudioConfig.FromDefaultMicrophoneInput();
    using SpeechRecognizer speechRecognizer = new SpeechRecognizer(speechConfig, audioConfig);
    Console.WriteLine("Speak now...");
    ```

    **Python**

    ```python
    # Configure speech recognition
    audio_config = speech_sdk.AudioConfig(use_default_microphone=True)
    speech_recognizer = speech_sdk.SpeechRecognizer(speech_config, audio_config)
    print('Speak now...')
    ```

1. انتقل الآن إلى قسم **إضافة تعليمة برمجية لمعالجة قسم الأوامر المكتوبة** أدناه.

---

### بدلاً من ذلك، استخدم إدخال الصوت من ملف

1. في النافذة الطرفية، أدخل الأمر التالي لتثبيت مكتبة يمكنك استخدامها لتشغيل الملف الصوتي:

    **C#**

    ```
    dotnet add package System.Windows.Extensions --version 4.6.0 
    ```

    **Python**

    ```
    pip install playsound==1.2.2
    ```

1. في ملف التعليمات البرمجية لبرنامجك، ضمن استيراد مساحة الاسم الموجودة، أضف التعليمات البرمجية التالية لاستيراد المكتبة التي ثبتها للتو:

    **C#**: Program.cs

    ```csharp
    using System.Media;
    ```

    **Python**: speaking-clock.py

    ```python
    from playsound import playsound
    ```

1. في الدالة **الأساسية**، لاحظ أن التعليمات البرمجية تستخدم دالة **TranscribeCommand** لقبول الإدخال المنطوق. ثم في دالة **TranscribeCommand**، ضمن التعليق **تكوين التعرّف على الكلام**، أضف التعليمة البرمجية المناسب أدناه لإنشاء عميل **SpeechRecognizer** الذي يمكن استخدامه للتعرّف على الكلام ونسخه من ملف صوتي:

    **C#**: Program.cs

    ```csharp
    // Configure speech recognition
    string audioFile = "time.wav";
    SoundPlayer wavPlayer = new SoundPlayer(audioFile);
    wavPlayer.Play();
    using AudioConfig audioConfig = AudioConfig.FromWavFileInput(audioFile);
    using SpeechRecognizer speechRecognizer = new SpeechRecognizer(speechConfig, audioConfig);
    ```

    **Python**: speaking-clock.py

    ```python
    # Configure speech recognition
    current_dir = os.getcwd()
    audioFile = current_dir + '\\time.wav'
    playsound(audioFile)
    audio_config = speech_sdk.AudioConfig(filename=audioFile)
    speech_recognizer = speech_sdk.SpeechRecognizer(speech_config, audio_config)
    ```

---

### إضافة تعليمة برمجية لمعالجة الأمر المكتوب

1. في الدالة **TranscribeCommand**، ضمن التعليق **معالجة إدخال الكلام**، أضف التعليمة البرمجية التالية للاستماع إلى الإدخال المنطوق، مع الحرص على عدم استبدال التعليمة البرمجية الموجودة في نهاية الدالة التي تُرجع الأمر:

    **C#**: Program.cs

    ```csharp
    // Process speech input
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

    **Python**: speaking-clock.py

    ```python
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

1. احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد **الساعة الناطقة** وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python speaking-clock.py
    ```

1. إذا استخدمت ميكروفوناً، فتحدث بوضوح وقل "كم الساعة؟". يجب أن ينسخ البرنامج الإدخال المنطوق ويعرض الوقت (استناداً إلى الوقت المحلي للكمبيوتر الذي تعمل فيه التعليمات البرمجية، والذي قد لا يكون الوقت الصحيح حيث أنت).

    يمنحك SpeechRecognizer حوالي 5 ثوانٍ للتحدث. إذا اكتشف عدم وجود إدخال منطوق، فإنه ينتج نتيجة "لا تطابق".

    إذا واجه SpeechRecognizer خطئًا، فإنه ينتج نتيجة "الإلغاء". ستعرض التعليمات البرمجية في التطبيق بعد ذلك رسالة الخطأ. السبب الأكثر احتمالاً هو مفتاح أو منطقة غير صحيحة في ملف التكوين.

## تركيب الكلام

يقبل تطبيق الساعة الناطقة الإدخال المنطوق، ولكنه لا يتحدث في الواقع! لنصلح ذلك عن طريق إضافة تعليمة برمجية لتركيب الكلام.

1. في الدالة **الأساسية** لبرنامجك، لاحظ أن التعليمات البرمجية تستخدم الدالة **TellTime** لإخبار المستخدم بالوقت الحالي.
1. في الدالة **TellTime**، ضمن التعليق **تكوين تركيب** الكلام، أضف التعليمات البرمجية التالية لإنشاء **عميل SpeechSynthesizer** الذي يمكن استخدامه لإنشاء إخراج منطوق:

    **C#**: Program.cs

    ```csharp
    // Configure speech synthesis
    speechConfig.SpeechSynthesisVoiceName = "en-GB-RyanNeural";
    using SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer(speechConfig);
    ```

    **Python**: speaking-clock.py

    ```python
    # Configure speech synthesis
    speech_config.speech_synthesis_voice_name = "en-GB-RyanNeural"
    speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config)
    ```

    > **ملاحظة** يستخدم تكوين الصوت الافتراضي جهاز صوت النظام الافتراضي للإخراج، لذلك لا تحتاج إلى توفير **AudioConfig** بشكل صريح. إذا كنت بحاجة إلى إعادة توجيه إخراج الصوت إلى ملف، يمكنك استخدام **AudioConfig** مع مسار ملف لتنفيذ ذلك.

1. في الدالة **TellTime**، ضمن التعليق **تركيب الإخراج المنطوق**، أضف التعليمات البرمجية التالية لإنشاء إخراج منطوق، مع الحرص على عدم استبدال التعليمات البرمجية في نهاية الدالة التي تطبع الاستجابة:

    **C#**: Program.cs

    ```csharp
    // Synthesize spoken output
    SpeechSynthesisResult speak = await speechSynthesizer.SpeakTextAsync(responseText);
    if (speak.Reason != ResultReason.SynthesizingAudioCompleted)
    {
        Console.WriteLine(speak.Reason);
    }
    ```

    **Python**: speaking-clock.py

    ```python
    # Synthesize spoken output
    speak = speech_synthesizer.speak_text_async(response_text).get()
    if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
        print(speak.reason)
    ```

1. احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد **الساعة الناطقة** وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python speaking-clock.py
    ```

1. عندما يُطلب منك ذلك، تحدث بوضوح في الميكروفون وقل "كم الساعة الآن؟". يجب أن يتحدث البرنامج ويخبرك بالوقت.

## استخدام صوت مختلف

يستخدم تطبيق الساعة الناطقة صوتاً افتراضياً يمكنك تغييره. تدعم خدمة الكلام مجموعة من الأصوات *القياسية* بالإضافة إلى الأصوات *العصبية* الشبيهة بالإنسان. يمكنك إنشاء أصوات *مخصصة*.

> **ملاحظة**: للحصول على قائمة بالأصوات العصبية والقياسية، راجع [معرض الصوت](https://speech.microsoft.com/portal/voicegallery) في Speech Studio.

1. في الدالة **TellTime**، ضمن التعليق **تكوين تركيب الكلام**، عدل التعليمات البرمجية كما يلي لتحديد صوت بديل قبل إنشاء عميل **SpeechSynthesizer**:

   **C#**: Program.cs

    ```csharp
    // Configure speech synthesis
    speechConfig.SpeechSynthesisVoiceName = "en-GB-LibbyNeural"; // change this
    using SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer(speechConfig);
    ```

    **Python**: speaking-clock.py

    ```python
    # Configure speech synthesis
    speech_config.speech_synthesis_voice_name = 'en-GB-LibbyNeural' # change this
    speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config)
    ```

1. احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد **الساعة الناطقة** وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python speaking-clock.py
    ```

1. عندما يُطلب منك ذلك، تحدث بوضوح في الميكروفون وقل "كم الساعة الآن؟". يجب أن يتحدث البرنامج بالصوت المحدد، ليخبرك بالوقت.

## استخدام لغة Speech Synthesis Markup (SSML)

تمكنك لغة ترميز تركيب الكلام (SSML) من تخصيص طريقة تركيب كلامك باستخدام تنسيق يستند إلى XML.

1. في الدالة **TellTime**، استبدل كافة التعليمات البرمجية الحالية ضمن التعليق **تركيب النتيجة المنطوقة** بالتعليمات البرمجية التالية (اترك التعليمات البرمجية ضمن التعليق **طباعة الاستجابة**):

   **C#**: Program.cs

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
    ```

    **Python**: speaking-clock.py

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
    ```

1. احفظ تغييراتك وارجع إلى الوحدة الطرفية المدمجة لمجلد **الساعة الناطقة** وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python speaking-clock.py
    ```

1. عندما يُطلب منك ذلك، تحدث بوضوح في الميكروفون وقل "كم الساعة الآن؟". يجب أن يتحدث البرنامج بالصوت المحدد في SSML (متجاوزاً الصوت المحدد في SpeechConfig)، ليخبرك بالوقت، ثم بعد توقف مؤقت، يخبرك أن الوقت قد حان لإنهاء هذا الدرس التطبيقي - وهو بالفعل!

## مزيد من المعلومات

لمزيد من المعلومات حول استخدام واجهات برمجة تطبيقات **تحويل الكلام إلى نص** **والنص إلى كلام**، راجع [وثائق تحويل الكلام إلى نص ووثائق](https://learn.microsoft.com/azure/ai-services/speech-service/index-speech-to-text) [وتحويل النص إلى كلام](https://learn.microsoft.com/azure/ai-services/speech-service/index-text-to-speech).
