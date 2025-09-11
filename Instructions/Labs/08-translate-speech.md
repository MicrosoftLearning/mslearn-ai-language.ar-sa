---
lab:
  title: ترجمة الكلام
  description: قُم بترجمة الكلام من لغة إلى لغة أخرى وطبقها في تطبيقك الخاص.
---

# ترجمة الكلام

يتضمن Azure AI Speech واجهة برمجة تطبيقات لترجمة الكلام يمكنك استخدامها لترجمة اللغة المنطوقة. على سبيل المثال، افترض أنك تريد إعداد تطبيق مترجم يمكن للأشخاص استخدامه عند السفر في أماكن لا يتحدثون فيها اللغة المحلية. سيكون بإمكانهم قول عبارات مثل «أين المحطة؟» أو «أحتاج الوصول إلى صيدلية» بلغتهم الخاصة، وترجمتها إلى اللغة المحلية. في هذا التمرين، ستستخدم عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Speech للغة Python لإنشاء تطبيق بسيط بناءً على المثال المرفق.

يستند هذا التمرين إلى لغة Python، لكن يمكنك تطوير تطبيقات ترجمة الكلام باستخدام عِدد تطوير برامج (SDK) خاصة بلغات متعددة، منها:

- [عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Speech للغة Python](https://pypi.org/project/azure-cognitiveservices-speech/)
- [عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Speech للغة NET.](https://www.nuget.org/packages/Microsoft.CognitiveServices.Speech)
- [عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Speech للغة JavaScript](https://www.npmjs.com/package/microsoft-cognitiveservices-speech-sdk)

سيستغرق هذا التدريب حوالي **30** دقيقة.

> **ملاحظة** تم تصميم هذا التدريب لإكماله في Azure cloud shell، حيث لا يتم دعم الوصول المباشر إلى الأجهزة الصوتية لجهاز الكمبيوتر الخاص بك. لذلك سيستخدم النشاط العملي ملفات الصوت لعمليات دفق مدخلات ومخرجات الكلام. يتم توفير التعليمات البرمجية لتحقيق نفس النتائج باستخدام ميكروفون ومكبر صوت كمرجع.

## إنشاء مورد Azure AI Speech

لنبدأ بإنشاء مورد Azure AI Speech.

1. افتح [مدخل Microsoft Azure](https://portal.azure.com) على `https://portal.azure.com`، وسجّل الدخول باستخدام حساب Microsoft المرتبط باشتراك Azure الخاص بك.
1. في حقل البحث العلوي، ابحث عن **خدمة الكلام**. حدّدها من القائمة، ثم حدّد **إنشاء**.
1. توفير المورد باستخدام الإعدادات التالية:
    - **الاشتراك**: *اشتراك Azure الخاص بك*.
    - **مجموعة الموارد**: *اختيار مجموعة موارد أو إنشاءها*.
    - **المنطقة**: *اختر أي منطقة متوفرة*
    - **الاسم**: *أدخل اسمًا مميزًا*.
    - **مستوى الأسعار**: حدد **F0** (*مجاني*) أو **S** (*قياسي*) إذا لم يكن F متوفراً.
1. حدد **مراجعة + إنشاء**، ثم حدد **إنشاء** لتوفير المورد.
1. انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.
1. اعرض صفحة **المفاتيح ونقطة النهاية** في قسم **إدارة الموارد**. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التدريب.

## الإعداد لتطوير تطبيق في Cloud Shell

1. مع إبقاء صفحة **المفاتيح ونقطة النهاية** مفتوحة، استخدم الزرّ **[\>_]** الموجود على يمين شريط البحث في أعلى الصفحة لإنشاء Cloud Shell جديد في مدخل Microsoft Azure، مع تحديد بيئة ***PowerShell***. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    **<font color="red">تأكد من التبديل إلى الإصدار الكلاسيكي من cloud shell قبل المتابعة.</font>**

1. في جزء PowerShell، أدخل الأوامر التالية لاستنساخ مستودع GitHub لهذا التمرين:

    ```
   rm -r mslearn-ai-language -f
   git clone https://github.com/microsoftlearning/mslearn-ai-language
    ```

    > **تلميح**: عند إدخال الأوامر في Cloudshell، قد يحتل الناتج مساحة كبيرة من ذاكرة الشاشة المؤقتة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.

1. بعد استنساخ المستودع، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية:

    ```
   cd mslearn-ai-language/Labfiles/08-speech-translation/Python/translator
    ```

1. في جزء سطر الأوامر، نفّذ الأمر التالي لعرض ملفات التعليمات البرمجية في مجلد **المترجم**:

    ```
   ls -a -l
    ```

    تتضمن الملفات ملف تكوين (**.env**) وملف تعليمات برمجية (**translator.py**).

1. قُم بإنشاء بيئة افتراضية للغة Python وتثبيت حزمة عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Speech والحزم المطلوبة الأخرى عبر تنفيذ الأمر التالي:

    ```
    python -m venv labenv
    ./labenv/bin/Activate.ps1
    pip install -r requirements.txt azure-cognitiveservices-speech==1.42.0
    ```

1. أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:

    ```
   code .env
    ```

    يتم فتح الملف في محرر التعليمات البرمجية.

1. قُم بتحديث قيم الإعدادات لتشمل **المنطقة** و**المفتاح** من مورد Azure AI Speech الذي أنشأته (متاح في صفحة **المفاتيح ونقطة النهاية** لمورد Azure AI Translator في مدخل Microsoft Azure).
1. بعد استبدال العناصر النائبة، استخدم الأمر **CTRL+S** لحفظ التغييرات ثم استخدم الأمر **CTRL+Q** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحWا.

## إضافة تعليمات برمجية لاستخدام Azure AI Speech SDK

> **تلميح**: عند إضافة التعليمات البرمجية، تأكد من الحفاظ على المسافة البادئة الصحيحة.

1. أدخل الأمر التالي لتحرير ملف التعليمات البرمجية الذي تم توفيره:

    ```
   code translator.py
    ```

1. في أعلى ملف التعليمات البرمجية، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:

    ```python
   # Import namespaces
   from azure.core.credentials import AzureKeyCredential
   import azure.cognitiveservices.speech as speech_sdk
    ```

1. في الدالة **Main**، ضمن التعليق **Get config settings**، لاحظ أن التعليمات البرمجية تقوم بتحميل المفتاح والمنطقة التي عرّفتها في ملف التكوين.

1. ابحث عن التعليمات البرمجية التالية ضمن التعليق **Configure translation**، وأضِف التعليمات البرمجية التالية لتكوين اتصالك بنقطة نهاية خدمات Azure AI Speech:

    ```python
   # Configure translation
   translation_config = speech_sdk.translation.SpeechTranslationConfig(speech_key, speech_region)
   translation_config.speech_recognition_language = 'en-US'
   translation_config.add_target_language('fr')
   translation_config.add_target_language('es')
   translation_config.add_target_language('hi')
   print('Ready to translate from',translation_config.speech_recognition_language)
    ```

1. ستستخدم **SpeechTranslationConfig** لترجمة الكلام إلى نص، ولكنك ستستخدم أيضًا **SpeechConfig** لتجميع الترجمات في الكلام. أضف التعليمات البرمجية التالية ضمن التعليق **تكوين الكلام**:

    ```python
   # Configure speech
   speech_config = speech_sdk.SpeechConfig(speech_key, speech_region)
   print('Ready to use speech service in:', speech_config.region)
    ```

1. احفظ التغييرات (*CTRL+S*)، ولكن اترك محرر التعليمات البرمجية مفتوحا.

## تشغيل التطبيق

حتى الآن، التطبيق لا يقوم بأي شيء سوى الاتصال بمورد Azure AI Speech الخاص بك، ولكن من المفيد تشغيله والتحقق من أنه يعمل قبل إضافة وظيفة الكلام.

1. في سطر الأوامر، أدخِل الأمر التالي لتشغيل تطبيق المترجم:

    ```
   python translator.py
    ```

    يجب أن تعرض التعليمات البرمجية منطقة مورد خدمة الكلام التي سيستخدمها التطبيق، ورسالة تفيد بأنه جاهز للترجمة من اللغة الإنجليزية (en-US) ويطلب منك إدخال اللغة المستهدفة. يشير التشغيل الناجح إلى أن التطبيق متصل بخدمة Azure AI Speech. اضغط على دخول لإنهاء البرنامج.

## تنفيذ ترجمة الكلام

الآن بعد أن أصبح لديك **تكوين ترجمة كلام** لخدمة Azure AI Speech، يمكنك استخدام واجهة برمجة التطبيقات ترجمة Azure AI Speech للتعرف على الكلام وترجمته.

1. في ملف التعليمات البرمجية، لاحظ أن التعليمات البرمجية تستخدم الدالة **Translate** لترجمة المدخلات الصوتية. ثم في الدالة **ترجمة** ، ضمن التعليق **ترجمة كلام**، أضف التعليمات البرمجية التالية لإنشاء عميل**منظم ترجمة** الذي يمكن استخدامه للتعرف على الكلام وترجمته من ملف.

    ```python
   # Translate speech
   current_dir = os.getcwd()
   audioFile = current_dir + '/station.wav'
   audio_config_in = speech_sdk.AudioConfig(filename=audioFile)
   translator = speech_sdk.translation.TranslationRecognizer(translation_config, audio_config = audio_config_in)
   print("Getting speech from file...")
   result = translator.recognize_once_async().get()
   print('Translating "{}"'.format(result.text))
   translation = result.translations[targetLanguage]
   print(translation)
    ```

1. احفظ التغييرات (*CTRL+S*)، وأعِد تشغيل البرنامج:

    ```
   python translator.py
    ```

1. عند الطلب، أدخِل رمز لغة صالحًا (*fr*، أو *es*، أو *hi*). يجب أن يقوم البرنامج بنسخ ملف الإدخال الخاص بك وترجمته إلى اللغة التي حددتها (الفرنسية، أو الإسبانية، أو الهندية). كرر هذه العملية، مع تجربة كل لغة يدعمها التطبيق.

    > **ملاحظة**: قد لا تعرض دائمًا الترجمة إلى الهندية على نحوٍ صحيحٍ في نافذة وحدة التحكم بسبب مشكلات ترميز الأحرف.

1. عند الانتهاء، اضغط علىدخول لإنهاء البرنامج.

> **ملاحظة**: تترجم التعليمات البرمجية في تطبيقك الإدخال إلى جميع اللغات الثلاث في مكالمة واحدة. يتم عرض الترجمة للغة معينة فقط، ولكن يمكنك استرداد أي من الترجمات عن طريق تحديد رمز اللغة الهدف في مجموعة **الترجمات** للنتيجة.

## تجميع الترجمة إلى كلام

يترجم تطبيقك الآن الإدخال المنطوق إلى نص؛ والتي قد تكون كافية إذا كنت بحاجة إلى طلب المساعدة من شخص ما أثناء السفر. ولكن من المفضل أن تكون الترجمة منطوقة بصوت مناسب.

> **ملاحظة**: نظرًا لقيود الأجهزة في Cloud Shell، سنوجه مخرجات الكلام المولّد إلى ملف.

1. في الدالة **Translate**، ابحث عن التعليق **Synthesize translation**، وأضِف التعليمات البرمجية التالية لاستخدام عميل **SpeechSynthesizer** لتوليد الترجمة على شكل كلام وحفظها كملف بصيغة .wav:

    ```python
   # Synthesize translation
   output_file = "output.wav"
   voices = {
            "fr": "fr-FR-HenriNeural",
            "es": "es-ES-ElviraNeural",
            "hi": "hi-IN-MadhurNeural"
   }
   speech_config.speech_synthesis_voice_name = voices.get(targetLanguage)
   audio_config_out = speech_sdk.audio.AudioConfig(filename=output_file)
   speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config, audio_config_out)
   speak = speech_synthesizer.speak_text_async(translation).get()
   if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
        print(speak.reason)
   else:
        print("Spoken output saved in " + output_file)
    ```

1. احفظ التغييرات (*CTRL+S*)، وأعِد تشغيل البرنامج:

    ```
   python translator.py
    ```

1. راجع ناتج التطبيق، والذي يجب أن يشير إلى أن الترجمة الصوتية قد تم حفظها في ملف. عند الانتهاء، اضغط على**دخول** لإنهاء البرنامج.
1. إذا كان لديك مشغّل وسائط قادر على تشغيل ملفات بصيغة .wav، يمكنك تنزيل الملف الذي تم إنشاؤه عن طريق إدخال الأمر التالي:

    ```
   download ./output.wav
    ```

    ينشئ أمر التنزيل رابطًا منبثقًا في أسفل يمين متصفحك، والذي يمكنك تحديده لتنزيل الملف وفتحه.

> **ملاحظة**
> *في هذا المثال، لقد استخدمت **تكوين ترجمة الكلام** لترجمة الكلام إلى نص، ثم استخدمت **تكوين الكلام** لتجميع الترجمة باعتبارها كلام. في الواقع، يمكنك استخدام **SpeechTranslationConfig** لتوليد الترجمة مباشرةً ككلام، ولكن هذا يعمل فقط عند الترجمة إلى لغة واحدة، وينتج عنه تدفق صوتي يتم حفظه عادةً كملف.*

## تنظيف الموارد

إذا انتهيت من استكشاف خدمة Azure AI Speech، يمكنك حذف الموارد التي أنشأتها في هذا التمرين. وإليك الطريقة:

1. يمكنك إغلاق جزء Azure Cloud Shell
1. في مدخل Microsoft Azure، انتقل إلى مورد Azure AI Speech الذي أنشأته في هذا التدريب العملي.
1. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## ماذا لو كان لديك ميكروفون ومكبر صوت؟

سوف تستخدم ملفات صوتية لمدخلات ومخرجات الكلام في هذا التدريب. دعونا نرى كيف يمكن تعديل التعليمات البرمجية لاستخدام الأجهزة الصوتية.

### استخدام الترجمة الصوتية مع الميكروفون

1. إذا كان لديك ميكروفون، يمكنك استخدام التعليمات البرمجية التالية لالتقاط المدخلات الصوتية للترجمة:

    ```python
   # Translate speech
   audio_config_in = speech_sdk.AudioConfig(use_default_microphone=True)
   translator = speech_sdk.translation.TranslationRecognizer(translation_config, audio_config = audio_config_in)
   print("Speak now...")
   result = translator.recognize_once_async().get()
   print('Translating "{}"'.format(result.text))
   translation = result.translations[targetLanguage]
   print(translation)
    ```

> **ملاحظة**: الميكروفون الافتراضي للنظام هو مدخل الصوت الافتراضي، لذلك يمكنك أيضا حذف AudioConfig تمامًا!

### استخدام تركيب الكلام بواسطة مكبر صوت

1. إذا كان لديك مكبر صوت، يمكنك استخدام التعليمات البرمجية التالية لتجميع الكلام.
    
    ```python
   # Synthesize translation
   voices = {
            "fr": "fr-FR-HenriNeural",
            "es": "es-ES-ElviraNeural",
            "hi": "hi-IN-MadhurNeural"
   }
   speech_config.speech_synthesis_voice_name = voices.get(targetLanguage)
   audio_config_out = speech_sdk.audio.AudioConfig(use_default_speaker=True)
   speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config, audio_config_out)
   speak = speech_synthesizer.speak_text_async(translation).get()
   if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
        print(speak.reason)
    ```

> **ملاحظة**: مكبر الصوت الافتراضي للنظام هي مُخرج الصوت الافتراضي، لذلك يمكنك أيضا حذف AudioConfig تمامًا!

## مزيد من المعلومات

لمزيد من المعلومات حول استخدام واجهة برمجة تطبيقات ترجمة Azure AI Speech، راجع [وثائق ترجمة الكلام](https://learn.microsoft.com/azure/ai-services/speech-service/speech-translation).
