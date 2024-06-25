---
lab:
  title: ترجمة الكلام
  module: Module 8 - Translate speech with Azure AI Speech
---

# ترجمة الكلام

يتضمن Azure AI Speech واجهة برمجة تطبيقات لترجمة الكلام يمكنك استخدامها لترجمة اللغة المنطوقة. على سبيل المثال، افترض أنك تريد إعداد تطبيق مترجم يمكن للأشخاص استخدامه عند السفر في أماكن لا يتحدثون فيها اللغة المحلية. سيكون بإمكانهم قول عبارات مثل «أين المحطة؟» أو «أحتاج الوصول إلى صيدلية» بلغتهم الخاصة، وترجمتها إلى اللغة المحلية.

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

> **تلميح**: إذا استنسخت بالفعل مستودع **mslearn-ai-language**، فافتحه في تعليمة Visual Studio البرمجية. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.

1. ابدأ تشغيل Visual Studio Code.
1. افتح لوح الألوان (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-language` إلى مجلد محلي (لا يُهم أي مجلد).
1. عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.

    > **ملاحظة**: إذا عرضت لك تعليمة Visual Studio البرمجية رسالة منبثقة لمطالبتك بالثقة في التعليمات البرمجية التي تفتحها، فانقر فوق **نعم، أثق في خيار الكُتاب** في النافذة المنبثقة.

1. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

## تكوين تطبيقك

تم توفير تطبيقات لكل من C# وPython. يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد الكلام بالذكاء الاصطناعي في Azure الخاص بك.

1. في تعليمة Visual Studio البرمجية في جزء **مستكشف**، استعرض للوصول إلى مجلد **Labfiles/08-speech-translation** وقم بتوسيع المجلد ** CSharp** أو **Python** استنادًا إلى تفضيلات اللغة ومجلد **المترجم** الذي يحتوي عليه. يحتوي كل مجلد على ملفات التعليمات البرمجية الخاصة باللغة الخاصة بأحد التطبيقات الذي ستدمج وظيفة Azure AI Speech.
1. انقر بزر الماوس الأيمن فوق مجلد **المترجم** الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم عليك تثبيت حزمة Azure AI Vision SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#**

    ```
    dotnet add package Microsoft.CognitiveServices.Speech --version 1.30.0
    ```

    **Python**

    ```
    pip install azure-cognitiveservices-speech==1.30.0
    ```

1. في جزء **مستكشف**، في مجلد **المترجم**، افتح ملف التكوين للغة المفضلة لديك

    - **C#**: appsettings.json
    - **Python**: .env

1. يمكن تحديث قيم التكوين لتضمين **المنطقة** **ومفتاح** من مورد Azure AI Speech الذي أنشأته (المتوفر في صفحة **المفاتيح ونقطة النهاية** لمورد Azure AI Speech في Azure  لديك في مدخل Microsoft Azure ).

    > **ملاحظة**: تأكد من إضافة *المنطقة* لموردك، <u>وليس</u> نقطة النهاية!

1. احفظ ملف التكوين.

## إضافة تعليمة برمجية لاستخدام Speech SDK

1. لاحظ أن مجلد**المترجم** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: translator.py

    افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:

    **C#**: Program.cs

    ```csharp
    // Import namespaces
    using Microsoft.CognitiveServices.Speech;
    using Microsoft.CognitiveServices.Speech.Audio;
    using Microsoft.CognitiveServices.Speech.Translation;
    ```

    **Python**: translator.py

    ```python
    # Import namespaces
    import azure.cognitiveservices.speech as speech_sdk
    ```

1. في الدالة **الرئيسية**، لاحظ أن التعليمات البرمجية لتحميل مفتاح خدمةAzure AI Speec والمنطقة من ملف التكوين قد تم توفيرها بالفعل. يجب استخدام هذه المتغيرات لإنشاء **SpeechTranslationConfig** لمورد Azure AI Speec، والذي ستستخدمه لترجمة الإدخال المنطوق. أضف التعليمات البرمجية التالية ضمن التعليق **تكوين الترجمة**:

    **C#**: Program.cs

    ```csharp
    // Configure translation
    translationConfig = SpeechTranslationConfig.FromSubscription(aiSvcKey, aiSvcRegion);
    translationConfig.SpeechRecognitionLanguage = "en-US";
    translationConfig.AddTargetLanguage("fr");
    translationConfig.AddTargetLanguage("es");
    translationConfig.AddTargetLanguage("hi");
    Console.WriteLine("Ready to translate from " + translationConfig.SpeechRecognitionLanguage);
    ```

    **Python**: translator.py

    ```python
    # Configure translation
    translation_config = speech_sdk.translation.SpeechTranslationConfig(ai_key, ai_region)
    translation_config.speech_recognition_language = 'en-US'
    translation_config.add_target_language('fr')
    translation_config.add_target_language('es')
    translation_config.add_target_language('hi')
    print('Ready to translate from',translation_config.speech_recognition_language)
    ```

1. ستستخدم **SpeechTranslationConfig** لترجمة الكلام إلى نص، ولكنك ستستخدم أيضًا **SpeechConfig** لتجميع الترجمات في الكلام. أضف التعليمات البرمجية التالية ضمن التعليق **تكوين الكلام**:

    **C#**: Program.cs

    ```csharp
    // Configure speech
    speechConfig = SpeechConfig.FromSubscription(aiSvcKey, aiSvcRegion);
    ```

    **Python**: translator.py

    ```python
    # Configure speech
    speech_config = speech_sdk.SpeechConfig(ai_key, ai_region)
    ```

1. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **لمترجم**، وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python translator.py
    ```

1. إذا كنت تستخدم C#، فيمكنك تجاهل أي تحذيرات بشأن استخدام عامل **الانتظار** في الطرق غير المتزامنة - وسنصلح ذلك لاحقاً. يجب أن تعرض التعليمات البرمجية رسالة تفيد بأنها جاهزة للترجمة من en-US ومطالبتك بلغة مستهدفة. اضغط على دخول لإنهاء البرنامج.

## تنفيذ ترجمة الكلام

الآن بعد أن أصبح لديك **تكوين ترجمة كلام** لخدمة Azure AI Speech، يمكنك استخدام واجهة برمجة التطبيقات ترجمة Azure AI Speech للتعرف على الكلام وترجمته.

> **مهم**: يتضمن هذا القسم تعليمات لإجراءين بديلين. اتبع الإجراء الأول إذا كان لديك ميكروفون يعمل. اتبع الإجراء الثاني إذا كنت تريد محاكاة الإدخال المنطوق باستخدام ملف صوتي.

### إذا كان لديك ميكروفون يعمل

1. في الدالة **الأساسية** لبرنامجك، لاحظ أن التعليمات البرمجية تستخدم الدالة **ترجمة** لترجمة الإدخال المنطوق.
1. في الدالة **ترجمة** ، ضمن التعليق **ترجمة الكلام**، أضف التعليمات البرمجية التالية لإنشاء عميل**منظم الترجمة** الذي يمكن استخدامه للتعرف على الكلام وترجمته باستخدام ميكروفون النظام الافتراضي للإدخال.

    **C#**: Program.cs

    ```csharp
    // Translate speech
    using AudioConfig audioConfig = AudioConfig.FromDefaultMicrophoneInput();
    using TranslationRecognizer translator = new TranslationRecognizer(translationConfig, audioConfig);
    Console.WriteLine("Speak now...");
    TranslationRecognitionResult result = await translator.RecognizeOnceAsync();
    Console.WriteLine($"Translating '{result.Text}'");
    translation = result.Translations[targetLanguage];
    Console.OutputEncoding = Encoding.UTF8;
    Console.WriteLine(translation);
    ```

    **Python**: translator.py

    ```python
    # Translate speech
    audio_config = speech_sdk.AudioConfig(use_default_microphone=True)
    translator = speech_sdk.translation.TranslationRecognizer(translation_config, audio_config = audio_config)
    print("Speak now...")
    result = translator.recognize_once_async().get()
    print('Translating "{}"'.format(result.text))
    translation = result.translations[targetLanguage]
    print(translation)
    ```

    > **ملاحظة** التعليمات البرمجية في تطبيقك تترجم الإدخال إلى جميع اللغات الثلاث في مكالمة واحدة. يتم عرض الترجمة للغة معينة فقط، ولكن يمكنك استرداد أي من الترجمات عن طريق تحديد رمز اللغة الهدف في مجموعة **الترجمات** للنتيجة.

1. انتقل الآن إلى قسم**تشغيل البرنامج** أدناه.

---

### بدلاً من ذلك، استخدم إدخال الصوت من ملف

1. في النافذة الطرفية، أدخل الأمر التالي لتثبيت مكتبة يمكنك استخدامها لتشغيل الملف الصوتي:

    **C#**: Program.cs

    ```csharp
    dotnet add package System.Windows.Extensions --version 4.6.0 
    ```

    **Python**: translator.py

    ```python
    pip install playsound==1.3.0
    ```

1. في ملف التعليمات البرمجية لبرنامجك، ضمن استيراد مساحة الاسم الموجودة، أضف التعليمات البرمجية التالية لاستيراد المكتبة التي ثبتها للتو:

    **C#**: Program.cs

    ```csharp
    using System.Media;
    ```

    **Python**: translator.py

    ```python
    from playsound import playsound
    ```

1. في الدالة **الأساسية** لبرنامجك، لاحظ أن التعليمات البرمجية تستخدم الدالة **ترجمة** لترجمة الإدخال المنطوق. ثم في الدالة **ترجمة** ، ضمن التعليق **ترجمة كلام**، أضف التعليمات البرمجية التالية لإنشاء عميل**منظم ترجمة** الذي يمكن استخدامه للتعرف على الكلام وترجمته من ملف.

    **C#**: Program.cs

    ```csharp
    // Translate speech
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
    Console.WriteLine(translation);
    ```

    **Python**: translator.py

    ```python
    # Translate speech
    audioFile = 'station.wav'
    playsound(audioFile)
    audio_config = speech_sdk.AudioConfig(filename=audioFile)
    translator = speech_sdk.translation.TranslationRecognizer(translation_config, audio_config = audio_config)
    print("Getting speech from file...")
    result = translator.recognize_once_async().get()
    print('Translating "{}"'.format(result.text))
    translation = result.translations[targetLanguage]
    print(translation)
    ```

---

### قم بتشغيل البرنامج.

1. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **لمترجم**، وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python translator.py
    ```

1. عند المطالبة، أدخل رمز لغة صالحا (*fr*أو *es*أو *hi*)، ثم إذا كنت تستخدم ميكروفونا، فتحدث بوضوح وقل « أين المحطة؟» أو بعض العبارات الأخرى التي قد تستخدمها عند السفر إلى الخارج. ينبغي نسخ البرنامج إدخالك المنطوق ويترجمه إلى اللغة التي حددتها (الفرنسية أو الإسبانية أو الهندية). كرر هذه العملية، مع تجربة كل لغة يدعمها التطبيق. عند الانتهاء، اضغط على دخول لإنهاء البرنامج.

    يمنحك منظم الترجمة حوالي 5 ثوان للتحدث. في حالة اكتشاف عدم وجود إدخال منطوق، فإنه ينتج نتيجة "لا تطابق". قد لا تعرض دائمًا الترجمة إلى الهندية على نحوٍ صحيحٍ في نافذة وحدة التحكم بسبب مشكلات ترميز الأحرف.

> **ملاحظة**: تترجم التعليمات البرمجية في تطبيقك الإدخال إلى جميع اللغات الثلاث في مكالمة واحدة. يتم عرض الترجمة للغة معينة فقط، ولكن يمكنك استرداد أي من الترجمات عن طريق تحديد رمز اللغة الهدف في مجموعة **الترجمات** للنتيجة.

## تجميع الترجمة إلى كلام

يترجم تطبيقك الآن الإدخال المنطوق إلى نص؛ والتي قد تكون كافية إذا كنت بحاجة إلى طلب المساعدة من شخص ما أثناء السفر. ولكن من المفضل أن تكون الترجمة منطوقة بصوت مناسب.

1. في الدالة **ترجمة**، ضمن التعليق **تركيب الترجمة**، أضف التعليمات البرمجية التالية لاستخدام عميل **المركب الكلامي** لتجميع الترجمة ككلمة من خلال السماعة الافتراضية:

    **C#**: Program.cs

    ```csharp
    // Synthesize translation
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
    }
    ```

    **Python**: translator.py

    ```python
    # Synthesize translation
    voices = {
            "fr": "fr-FR-HenriNeural",
            "es": "es-ES-ElviraNeural",
            "hi": "hi-IN-MadhurNeural"
    }
    speech_config.speech_synthesis_voice_name = voices.get(targetLanguage)
    speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config)
    speak = speech_synthesizer.speak_text_async(translation).get()
    if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
        print(speak.reason)
    ```

1. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **لمترجم**، وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python translator.py
    ```

1. عند المطالبة، أدخل رمز لغة صالحًا (*fr*أو *es*أو *hi*)، ثم تحدث بوضوح في الميكروفون وقل عبارة قد تستخدمها عند السفر إلى الخارج.  ينسخ البرنامج إدخالك المنطوق ويستجيب باستخدام ترجمة منطوقة. كرر هذه العملية، مع تجربة كل لغة يدعمها التطبيق. عند الانتهاء، اضغط على**دخول** لإنهاء البرنامج.

> **ملاحظة**
> *في هذا المثال، لقد استخدمت **تكوين ترجمة الكلام** لترجمة الكلام إلى نص، ثم استخدمت **تكوين الكلام** لتجميع الترجمة باعتبارها كلام. يمكنك في الواقع استخدام **تكوين ترجمة الكلام** لتجميع الترجمة مباشرة، ولكن هذا يعمل فقط عند الترجمة إلى لغة واحدة، ويؤدي إلى دفق صوتي يتم حفظه عادة كملف بدلا من إرساله مباشرة إلى مكبر الصوت.*

## مزيد من المعلومات

لمزيد من المعلومات حول استخدام واجهة برمجة تطبيقات ترجمة Azure AI Speech، راجع [وثائق ترجمة الكلام](https://learn.microsoft.com/azure/ai-services/speech-service/speech-translation).
