---
lab:
  title: التعرف على الكلام وتركيبه
  description: قُم بإنشاء ساعة ناطقة تقوم بتحويل الكلام إلى نص والعكس.
---

# التعرف على الكلام وتجميعه

**الكلام بالذكاء الاصطناعي في Azure** هي خدمة توفر وظائف متعلقة بالكلام، بما في ذلك:

- واجهة برمجة تطبيقات *تحويل الكلام إلى نص* تمكنك من تنفيذ التعرّف على الكلام (تحويل الكلمات المنطوقة المسموعة إلى نص).
- واجهة برمجة تطبيقات *تحويل النص إلى كلام* تمكنك من تنفيذ تركيب الكلام (تحويل النص إلى كلام مسموع).

في هذا التمرين، ستستخدم كلا من واجهات برمجة التطبيقات هذه لتنفيذ تطبيق ساعة التحدث.

يستند هذا التمرين إلى لغة Python، لكن يمكنك تطوير تطبيقات الكلام باستخدام عِدد تطوير برامج (SDK) خاصة بلغات متعددة، منها:

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

## إعداد وتكوين تطبيق الساعة الناطقة

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

1. بعد استنساخ مخزن البيانات الخاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الساعة الناطقة:  

    ```
   cd mslearn-ai-language/Labfiles/07-speech/Python/speaking-clock
    ```

1. في جزء سطر الأوامر، نفّذ الأمر التالي لعرض ملفات التعليمات البرمجية في مجلد **speaking-clock**:

    ```
   ls -a -l
    ```

    تتضمن الملفات ملف تكوين (**.env**) وملف تعليمات برمجية (**speaking-clock.py**). ملفات الصوت التي سيستخدمها تطبيقك موجودة في المجلد الفرعي **الصوت**.

1. قُم بإنشاء بيئة افتراضية للغة Python وتثبيت حزمة عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Speech والحزم المطلوبة الأخرى عبر تنفيذ الأمر التالي:

    ```
   python -m venv labenv
   ./labenv/bin/Activate.ps1
   pip install -r requirements.txt azure-cognitiveservices-speech==1.42.0
    ```

1. أدخِل الأمر التالي لتحرير ملف التكوين:

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
   code speaking-clock.py
    ```

1. في أعلى ملف التعليمات البرمجية، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:

    ```python
   # Import namespaces
   from azure.core.credentials import AzureKeyCredential
   import azure.cognitiveservices.speech as speech_sdk
    ```

1. في الدالة **Main**، ضمن التعليق **Get config settings**، لاحظ أن التعليمات البرمجية تقوم بتحميل المفتاح والمنطقة التي عرّفتها في ملف التكوين.

1. ابحث عن التعليق **Configure speech service**، وأضِف التعليمات البرمجية التالية لاستخدام مفتاح AI Services والمنطقة الخاصة بك لتكوين الاتصال بنقطة نهاية Azure AI Services Speech:

    ```python
   # Configure speech service
   speech_config = speech_sdk.SpeechConfig(speech_key, speech_region)
   print('Ready to use speech service in:', speech_config.region)
    ```

1. احفظ التغييرات (*CTRL+S*)، ولكن اترك محرر التعليمات البرمجية مفتوحا.

## تشغيل التطبيق

حتى الآن، التطبيق لا يقوم بأي شيء سوى الاتصال بخدمة Azure AI Speech الخاصة بك، ولكن من المفيد تشغيله والتحقق من أنه يعمل قبل إضافة وظائف الكلام.

1. في سطر الأوامر، أدخِل الأمر التالي لتشغيل تطبيق الساعة الناطقة:

    ```
   python speaking-clock.py
    ```

    يجب أن تعرض التعليمات البرمجية منطقة مورد خدمة الكلام الذي سيستخدمه التطبيق. يشير التشغيل الناجح إلى أن التطبيق متصل بمورد Azure AI Speech.

## إضافة تعليمة برمجية للتعرّف على الكلام

الآن بعد أن أصبح لديك **SpeechConfig** لخدمة الكلام في مورد Azure AI Services، يمكنك استخدام واجهة برمجة تطبيقات **تحويل الكلام إلى نص** للتعرّف على الكلام ونسخه إلى نص.

في هذا الإجراء، يتم التقاط مدخلات الكلام من ملف صوتي، والذي يمكنك تشغيله هنا:

<video controls src="https://github.com/MicrosoftLearning/mslearn-ai-language/raw/refs/heads/main/Instructions/media/Time.mp4" title="كم الساعة؟" width="150"></video>

1. في ملف التعليمات البرمجية، لاحظ أن التعليمات البرمجية تستخدم الدالة **TranscribeCommand** لقبول المدخلات الصوتية. بعد ذلك، في الدالة **TranscribeCommand**، ابحث عن التعليق **Configure speech recognition** وأضِف التعليمات البرمجية المناسبة أدناه لإنشاء عميل **SpeechRecognizer** يمكن استخدامه للتعرّف على الكلام من ملف صوتي ونسخه:

    ```python
   # Configure speech recognition
   current_dir = os.getcwd()
   audioFile = current_dir + '/time.wav'
   audio_config = speech_sdk.AudioConfig(filename=audioFile)
   speech_recognizer = speech_sdk.SpeechRecognizer(speech_config, audio_config)
    ```

1. في الدالة **TranscribeCommand**، ضمن التعليق **معالجة إدخال الكلام**، أضف التعليمة البرمجية التالية للاستماع إلى الإدخال المنطوق، مع الحرص على عدم استبدال التعليمة البرمجية الموجودة في نهاية الدالة التي تُرجع الأمر:

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

1. احفظ التغييرات (*CTRL+S*)، ثم في سطر الأوامر أسفل محرر التعليمات البرمجية ، أعِد تشغيل البرنامج:
1. راجع الناتج، والذي يجب أن يلتقط الكلام في الملف الصوتي بنجاح ويعيد الاستجابة المناسبة (لاحظ أن Cloud Shell الخاص بك قد يكون يعمل على خادم في منطقة زمنية مختلفة عن منطقتك!)

    > **تلميح**: إذا واجه SpeechRecognizer خطئًا، فإنه يكون نتيجة "الإلغاء". ستعرض التعليمات البرمجية في التطبيق بعد ذلك رسالة الخطأ. السبب الأكثر احتمالاً هو مفتاح غير صحيح أو منطقة غير صحيحة في ملف التكوين.

## تركيب الكلام

يقبل تطبيق الساعة الناطقة الإدخال المنطوق، ولكنه لا يتحدث في الواقع! لنصلح ذلك عن طريق إضافة تعليمة برمجية لتركيب الكلام.

مرة أخرى، نظرًا لقيود الأجهزة الخاصة بـ cloud shell سنوجه مخرجات الكلام المركبة إلى ملف.

1. في ملف التعليمات البرمجية، لاحظ أن التعليمات البرمجية تستخدم الدالة **TellTime** لإخبار المستخدم بالوقت الحالي.
1. في الدالة **TellTime**، ضمن التعليق **تكوين تركيب** الكلام، أضف التعليمات البرمجية التالية لإنشاء **عميل SpeechSynthesizer** الذي يمكن استخدامه لإنشاء إخراج منطوق:

    ```python
   # Configure speech synthesis
   output_file = "output.wav"
   speech_config.speech_synthesis_voice_name = "en-GB-RyanNeural"
   audio_config = speech_sdk.audio.AudioConfig(filename=output_file)
   speech_synthesizer = speech_sdk.SpeechSynthesizer(speech_config, audio_config,)
    ```

1. في الدالة **TellTime**، ضمن التعليق **تركيب الإخراج المنطوق**، أضف التعليمات البرمجية التالية لإنشاء إخراج منطوق، مع الحرص على عدم استبدال التعليمات البرمجية في نهاية الدالة التي تطبع الاستجابة:

    ```python
   # Synthesize spoken output
   speak = speech_synthesizer.speak_text_async(response_text).get()
   if speak.reason != speech_sdk.ResultReason.SynthesizingAudioCompleted:
        print(speak.reason)
   else:
        print("Spoken output saved in " + output_file)
    ```

1. احفظ التغييرات (*CTRL+S*) وأعِد تشغيل البرنامج، والذي يجب أن يشير إلى أن المخرجات الصوتية قد تم حفظها في ملف.

1. إذا كان لديك مشغّل وسائط قادر على تشغيل ملفات بصيغة .wav، يمكنك تنزيل الملف الذي تم إنشاؤه عن طريق إدخال الأمر التالي:

    ```
   download ./output.wav
    ```

    ينشئ أمر التنزيل رابطًا منبثقًا في أسفل يمين متصفحك، والذي يمكنك تحديده لتنزيل الملف وفتحه.

    يجب أن يكون صوت الملف النهائي مشابهًا لهذا:

    <video controls src="https://github.com/MicrosoftLearning/mslearn-ai-language/raw/refs/heads/main/Instructions/media/Output.mp4" title="الوقت هو 2:15" width="150"></video>

## استخدام لغة Speech Synthesis Markup (SSML)

تمكنك لغة ترميز تركيب الكلام (SSML) من تخصيص طريقة تركيب كلامك باستخدام تنسيق يستند إلى XML.

1. في الدالة **TellTime**، استبدل كافة التعليمات البرمجية الحالية ضمن التعليق **تركيب النتيجة المنطوقة** بالتعليمات البرمجية التالية (اترك التعليمات البرمجية ضمن التعليق **طباعة الاستجابة**):

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
       print("Spoken output saved in " + output_file)
    ```

1. احفظ التغييرات وأعِد تشغيل البرنامج، والذي يجب أن يشير مرة أخرى إلى أن المخرجات الصوتية قد تم حفظها في ملف.
1. قُم بتنزيل الملف الذي تم إنشاؤه وتشغيله، والذي يجب أن يكون الصوت مشابهًا لما يلي:
    
    <video controls src="https://github.com/MicrosoftLearning/mslearn-ai-language/raw/refs/heads/main/Instructions/media/Output2.mp4" title="الوقت هو 5:30. حان الوقت لإنهاء هذا النشاط العملي." width="150"></video>

## (اختياري) ماذا لو كان لديك ميكروفون ومكبر صوت؟

سوف تستخدم ملفات صوتية لمدخلات ومخرجات الكلام في هذا التدريب. دعونا نرى كيف يمكن تعديل التعليمات البرمجية لاستخدام الأجهزة الصوتية.

### استخدام التعرف على الكلام من خلال ميكروفون

إذا كان لديك ميكروفون، يمكنك استخدام التعليمات البرمجية التالية لالتقاط المدخلات المنطوقة للتعرف على الكلام:

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

> **ملاحظة**: الميكروفون الافتراضي للنظام هو مدخل الصوت الافتراضي، لذلك يمكنك أيضا حذف AudioConfig تمامًا!

### استخدام تركيب الكلام بواسطة مكبر صوت

إذا كان لديك مكبر صوت، يمكنك استخدام التعليمات البرمجية التالية لتجميع الكلام.

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

> **ملاحظة**: مكبر الصوت الافتراضي للنظام هي مُخرج الصوت الافتراضي، لذلك يمكنك أيضا حذف AudioConfig تمامًا!

## تنظيف

إذا انتهيت من استكشاف Azure AI Speech فيجب عليك حذف الموارد التي قمت بإنشائها في هذا التدريب لتجنب تكبد تكاليف Azure غير ضرورية.

1. يمكنك إغلاق جزء Azure Cloud Shell
1. في مدخل Microsoft Azure، انتقل إلى مورد Azure AI Speech الذي أنشأته في هذا التدريب العملي.
1. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## مزيد من المعلومات

لمزيد من المعلومات حول استخدام واجهات برمجة تطبيقات **تحويل الكلام إلى نص** **والنص إلى كلام**، راجع [وثائق تحويل الكلام إلى نص ووثائق](https://learn.microsoft.com/azure/ai-services/speech-service/index-speech-to-text) [وتحويل النص إلى كلام](https://learn.microsoft.com/azure/ai-services/speech-service/index-text-to-speech).
