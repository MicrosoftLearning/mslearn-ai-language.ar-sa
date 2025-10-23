---
lab:
  title: تطوير وكيل Voice Live صوتي مدعوم بالذكاء الاصطناعي في Azure
  description: تعرّف على كيفية إنشاء تطبيق ويب لتمكين التفاعلات الصوتية في الوقت الحقيقي باستخدام وكيل Voice Live مدعوم بالذكاء الاصطناعي في Azure.
---

# تطوير وكيل Voice Live صوتي مدعوم بالذكاء الاصطناعي في Azure

في هذا التمرين، يمكنك إكمال تطبيق ويب Python مستند إلى Flask يتيح تفاعلات صوتية في الوقت الحقيقي باستخدام وكيل. يمكنك إضافة التعليمات البرمجية لتهيئة الجلسة ومعالجة أحداثها. يمكنك استخدام برنامج نصي للنشر يقوم بنشر نموذج الذكاء الاصطناعي، وإنشاء صورة للتطبيق في Azure Container Registry (ACR) باستخدام مهام ACR، ثم إنشاء مثيل Azure App Service الذي يسحب الصورة. لاختبار التطبيق، ستحتاج إلى جهاز صوت مزوّد بقدرتَي الميكروفون والسماعة.

على الرغم من أن هذا التمرين يستند إلى Python، يمكنك تطوير تطبيقات مماثلة باستخدام حزم SDK مخصصة للغات برمجة أخرى، منها:

- [مكتبة عميل Azure VoiceLive لـ .NET](https://www.nuget.org/packages/Azure.AI.VoiceLive/)

المهام المنفَّذة في هذا التمرين:

* تنزيل الملفات الأساسية للتطبيق
* إضافة تعليمة برمجية لإكمال تطبيق الويب
* مراجعة قاعدة التعليمات البرمجية الإجمالية
* تحديث البرنامج النصي للنشر وتشغيله
* عرض التطبيق واختباره

يستغرق هذا التمرين حوالي **30** دقيقة لإكماله.

## تشغيل Azure Cloud Shell وتنزيل الملفات

في هذا القسم من التمرين، يمكنك تنزيل ملف مضغوط يحتوي على الملفات الأساسية للتطبيق.

1. في المستعرض الخاص بك، انتقل إلى مدخل Microsoft Azure[https://portal.azure.com](https://portal.azure.com)، وسجِّل الدخول باستخدام بيانات اعتماد Azure إذا تمت مطالبتك بها.

1. استخدم الزر **[\>_]** الموجود على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في مدخل Microsoft Azure، وتحديد بيئة ***Bash***. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *PowerShell*، فبدّل إلى ***Bash***.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

1. قُم بتشغيل الأمر التالي في **Bash** shell لتنزيل ملفات التمرين وفك ضغطها. سيتغير الأمر الثاني أيضًا إلى دليل ملفات التمرين.

    ```bash
    wget https://github.com/MicrosoftLearning/mslearn-ai-language/raw/refs/heads/main/downloads/python/voice-live-web.zip
    ```

    ```
    unzip voice-live-web.zip && cd voice-live-web
    ```

## إضافة تعليمة برمجية لإكمال تطبيق الويب

الآن بعد أن تم تنزيل ملفات التمرين، فإن الخطوة التالية هي إضافة تعليمة برمجية لإكمال التطبيق. يتم تنفيذ الخطوات التالية في cloud shell. 

>**Tip:** قُم بتغيير حجم cloud shell لعرض المزيد من المعلومات والتعليمات البرمجية عن طريق سحب الحد العلوي. يمكنك أيضًا استخدام زرَّي التصغير والتكبير للتبديل بين cloud shell والواجهة الرئيسية للمدخل.

قُم بتشغيل الأمر التالي للتغيير إلى دليل *src* قبل متابعة التمرين.

```bash
cd src
```

### قُم بإضافة تعليمة برمجية لتنفيذ المساعد الصوتي المباشر

في هذا القسم، يمكنك إضافة تعليمة برمجية لتنفيذ المساعد الصوتي المباشر. يقوم أسلوب **\_\_init\_\_** بتهيئة المساعد الصوتي عن طريق تخزين مَعلمات اتصال Azure VoiceLive (نقطة النهاية وبيانات الاعتماد والنموذج والصوت وإرشادات النظام) وإعداد متغيرات حالة وقت التشغيل لإدارة دورة حياة الاتصال ومعالجة انقطاعات المستخدم في أثناء المحادثات. يستورد أسلوب **البدء** مكونات Azure VoiceLive SDK الضرورية التي سيتم استخدامها لإنشاء اتصال WebSocket وتكوين جلسة الصوت في الوقت الحقيقي.

1. قُم بتشغيل الأمر التالي لفتح ملف *flask_app.py* للتحرير.

    ```bash
    code flask_app.py
    ```

1. ابحث عن التعليق **# BEGIN VOICE LIVE ASSISTANT IMPLEMENTATION - ALIGN CODE WITH COMMENT** في التعليمات البرمجية. انسخ التعليمات البرمجية أدناه وأدخِلها أسفل التعليق. تأكد من التحقق من المسافة البادئة.

    ```python
    def __init__(
        self,
        endpoint: str,
        credential,
        model: str,
        voice: str,
        instructions: str,
        state_callback=None,
    ):
        # Store Azure Voice Live connection and configuration parameters
        self.endpoint = endpoint
        self.credential = credential
        self.model = model
        self.voice = voice
        self.instructions = instructions
        
        # Initialize runtime state - connection established in start()
        self.connection = None
        self._response_cancelled = False  # Used to handle user interruptions
        self._stopping = False  # Signals graceful shutdown
        self.state_callback = state_callback or (lambda *_: None)

    async def start(self):
        # Import Voice Live SDK components needed for establishing connection and configuring session
        from azure.ai.voicelive.aio import connect  # type: ignore
        from azure.ai.voicelive.models import (
            RequestSession,
            ServerVad,
            AzureStandardVoice,
            Modality,
            InputAudioFormat,
            OutputAudioFormat,
        )  # type: ignore
    ```

1. أدخِل **ctrl+s** لحفظ التغييرات وإبقاء المحرر مفتوحًا للقسم التالي.

### قُم بإضافة تعليمة برمجية لتنفيذ المساعد الصوتي المباشر

في هذا القسم، يمكنك إضافة تعليمة برمجية لتكوين جلسة الصوت المباشرة. يحدد هذا الإجراء الأساليب (الصوت فقط غير مدعوم من قِبل واجهة برمجة التطبيقات)، وإرشادات النظام التي تحدد سلوك المساعد، وصوت Azure TTS للاستجابات، وتنسيق الصوت لكلٍ من تدفقات الإدخال والإخراج، والكشف عن النشاط الصوتي من جانب الخادم (VAD) الذي يحدد كيفية اكتشاف النموذج عندما يبدأ المستخدمون التحدث ويتوقفون عنه.

1. ابحث عن التعليق **# BEGIN CONFIGURE VOICE LIVE SESSION - ALIGN CODE WITH COMMENT** في التعليمات البرمجية. انسخ التعليمات البرمجية أدناه وأدخِلها أسفل التعليق. تأكد من التحقق من المسافة البادئة.

    ```python
    # Configure VoiceLive session with audio/text modalities and voice activity detection
    session_config = RequestSession(
        modalities=[Modality.TEXT, Modality.AUDIO],
        instructions=self.instructions,
        voice=voice_cfg,
        input_audio_format=InputAudioFormat.PCM16,
        output_audio_format=OutputAudioFormat.PCM16,
        turn_detection=ServerVad(threshold=0.5, prefix_padding_ms=300, silence_duration_ms=500),
    )
    await conn.session.update(session=session_config)
    ```

1. أدخِل **ctrl+s** لحفظ التغييرات وإبقاء المحرر مفتوحًا للقسم التالي.

### أضِف تعليمة برمجية لمعالجة أحداث الجلسة

في هذا القسم، يمكنك إضافة تعليمة برمجية لإضافة معالجات الأحداث لجلسة الصوت المباشرة. تستجيب معالجات الأحداث لأحداث جلسة VoiceLive الرئيسية في أثناء دورة حياة المحادثة: **_handle_session_updated** يرسل إشارة عندما تكون الجلسة جاهزة لإدخال المستخدم، و **_handle_speech_started** يكتشف متى يبدأ المستخدم في التحدث وينفّذ منطق المقاطعة عن طريق إيقاف تشغيل أي مساعد صوت مستمر وإلغاء الاستجابات قيد التقدم للسماح بتدفق المحادثة الطبيعية، و **_handle_speech_stopped** يعالج عندما ينتهي المستخدم من التحدث ويبدأ المساعد في معالجة الإدخال.

1. ابحث عن التعليق **# BEGIN HANDLE SESSION EVENTS - ALIGN CODE WITH COMMENT** في التعليمات البرمجية. انسخ التعليمات البرمجية أدناه وأدخِلها أسفل التعليق، وتأكد من التحقق من المسافة البادئة.

    ```python
    async def _handle_event(self, event, conn, verbose=False):
        """Handle Voice Live events with clear separation by event type."""
        # Import event types for processing different Voice Live server events
        from azure.ai.voicelive.models import ServerEventType
        
        event_type = event.type
        if verbose:
            _broadcast({"type": "log", "level": "debug", "event_type": str(event_type)})
        
        # Route Voice Live server events to appropriate handlers
        if event_type == ServerEventType.SESSION_UPDATED:
            await self._handle_session_updated()
        elif event_type == ServerEventType.INPUT_AUDIO_BUFFER_SPEECH_STARTED:
            await self._handle_speech_started(conn)
        elif event_type == ServerEventType.INPUT_AUDIO_BUFFER_SPEECH_STOPPED:
            await self._handle_speech_stopped()
        elif event_type == ServerEventType.RESPONSE_AUDIO_DELTA:
            await self._handle_audio_delta(event)
        elif event_type == ServerEventType.RESPONSE_AUDIO_DONE:
            await self._handle_audio_done()
        elif event_type == ServerEventType.RESPONSE_DONE:
            # Reset cancellation flag but don't change state - _handle_audio_done already did
            self._response_cancelled = False
        elif event_type == ServerEventType.ERROR:
            await self._handle_error(event)

    async def _handle_session_updated(self):
        """Session is ready for conversation."""
        self.state_callback("ready", "Session ready. You can start speaking now.")

    async def _handle_speech_started(self, conn):
        """User started speaking - handle interruption if needed."""
        self.state_callback("listening", "Listening… speak now")
        
        try:
            # Stop any ongoing audio playback on the client side
            _broadcast({"type": "control", "action": "stop_playback"})
            
            # If assistant is currently speaking or processing, cancel the response to allow interruption
            current_state = assistant_state.get("state")
            if current_state in {"assistant_speaking", "processing"}:
                self._response_cancelled = True
                await conn.response.cancel()
                _broadcast({"type": "log", "level": "debug", 
                          "msg": f"Interrupted assistant during {current_state}"})
            else:
                _broadcast({"type": "log", "level": "debug", 
                          "msg": f"User speaking during {current_state} - no cancellation needed"})
        except Exception as e:
            _broadcast({"type": "log", "level": "debug", 
                      "msg": f"Exception in speech handler: {e}"})

    async def _handle_speech_stopped(self):
        """User stopped speaking - processing input."""
        self.state_callback("processing", "Processing your input…")

    async def _handle_audio_delta(self, event):
        """Stream assistant audio to clients."""
        if self._response_cancelled:
            return  # Skip cancelled responses
            
        # Update state when assistant starts speaking
        if assistant_state.get("state") != "assistant_speaking":
            self.state_callback("assistant_speaking", "Assistant speaking…")
        
        # Extract and broadcast Voice Live audio delta as base64 to WebSocket clients
        audio_data = getattr(event, "delta", None)
        if audio_data:
            audio_b64 = base64.b64encode(audio_data).decode("utf-8")
            _broadcast({"type": "audio", "audio": audio_b64})

    async def _handle_audio_done(self):
        """Assistant finished speaking."""
        self._response_cancelled = False
        self.state_callback("ready", "Assistant finished. You can speak again.")

    async def _handle_error(self, event):
        """Handle Voice Live errors."""
        error = getattr(event, "error", None)
        message = getattr(error, "message", "Unknown error") if error else "Unknown error"
        self.state_callback("error", f"Error: {message}")

    def request_stop(self):
        self._stopping = True
    ```

1. أدخِل **ctrl+s** لحفظ التغييرات وإبقاء المحرر مفتوحًا للقسم التالي.

### راجع التعليمات البرمجية في التطبيق

حتى الآن، أضفت تعليمة برمجية إلى التطبيق لتنفيذ الوكيل ومعالجة أحداثه. استقطع بضع دقائق لمراجعة التعليمات البرمجية الكاملة والتعليقات للحصول على فهم أفضل لكيفية تعامل التطبيق مع حالة العميل وعملياته.

1. عند الانتهاء، أدخِل **ctrl+q** للخروج من المحرر. 

## تحديث البرنامج النصي للنشر وتشغيله

في هذا القسم، يمكنك إجراء تغيير صغير على برنامج **azdeploy.sh** النصي للنشر، ثم تشغيل النشر. 

### قُم بتحديث البرنامج النصي للنشر

هناك قيمتان فقط يجب تغييرهما في أعلى برنامج **azdeploy.sh** النصي للنشر. 

* تحدد قيمة **rg** مجموعة الموارد لاحتواء النشر. يمكنك قبول القيمة الافتراضية، أو إدخال القيمة الخاصة بك إذا كنت بحاجة إلى النشر إلى مجموعة موارد معيّنة.

* تعيّن قيمة **الموقع** منطقة النشر. يمكن نشر نموذج *gpt-4o* المستخدم في التمرين في مناطق أخرى، ولكن يمكن أن تكون هناك حدود في أي منطقة معيّنة. إذا فشل النشر في المنطقة التي اخترتها، فجرب **eastus2** أو **swedencentral**. 

    ```
    rg="rg-voicelive" # Replace with your resource group
    location="eastus2" # Or a location near you
    ```

1. قُم بتشغيل الأوامر التالية في Cloud Shell لبدء تحرير البرنامج النصي للنشر.

    ```bash
    cd ~/01-voice-live-web
    ```
    
    ```bash
    code azdeploy.sh
    ```

1. قُم بتحديث قيم **rg** و**الموقع** لتلبية احتياجاتك ثم أدخِل **ctrl+s** لحفظ التغييرات و**ctrl+q** للخروج من المحرر.

### تشغيل البرنامج النصي للتوزيع

ينشر البرنامج النصي للنشر نموذج الذكاء الاصطناعي وينشئ الموارد الضرورية في Azure لتشغيل تطبيق مُحزَّم في حاوية في App Service.

1. قُم بتشغيل الأمر التالي في Cloud Shell لبدء نشر موارد Azure والتطبيق.

    ```bash
    bash azdeploy.sh
    ```

1. حدد **الخيار 1** للنشر الأوّلي.

    يجب أن يكتمل النشر في 5-10 دقائق. في أثناء النشر، قد تتم مطالبتك بالمعلومات/الإجراءات التالية:
    
    * إذا تمت مطالبتك بالمصادقة على Azure، فاتبع التوجيهات المقدمة لك.
    * إذا تمت مطالبتك بتحديد اشتراك، فاستخدم مفاتيح الأسهم لتمييز اشتراكك واضغط على مفتاح الإدخال **Enter**. 
    * من المحتمل أن تشاهد بعض التحذيرات في أثناء النشر ويمكن تجاهلها.
    * إذا فشل النشر في أثناء نشر نموذج الذكاء الاصطناعي، فقُم بتغيير المنطقة في البرنامج النصي للنشر وحاول مرة أخرى. 
    * يمكن أن تنشغل المناطق في Azure في بعض الأحيان وتقاطع توقيت عمليات النشر. إذا فشل النشر بعد نشر النموذج، فأعِد تشغيل البرنامج النصي للنشر.

## عرض التطبيق واختباره

عند اكتمال النشر ستكون رسالة "اكتمل النشر!" في shell مع رابط إلى تطبيق الويب. يمكنك تحديد هذا الرابط أو الانتقال إلى مورد App Service وتشغيل التطبيق من هناك. قد يستغرق تحميل التطبيق بضع دقائق. 

1. حدد الزر **بدء جلسة** للاتصال بالنموذج.
1. ستتم مطالبتك بمنح التطبيق حق الوصول إلى أجهزة الصوت لديك.
1. ابدأ التحدث مع النموذج عندما يطالبك التطبيق ببدء التحدث.

استكشاف الأخطاء وإصلاحها:

* إذا أبلغ التطبيق عن متغيرات بيئة مفقودة، فأعِد تشغيل التطبيق في App Service.
* إذا رأيت رسائل *مقطع صوتي* زائدة في السجل المعروض في التطبيق، فحدد **إيقاف الجلسة** ثم ابدأ الجلسة مرة أخرى. 
* إذا فشل التطبيق في العمل على الإطلاق، فتحقق مرة أخرى من إضافة جميع التعليمات البرمجية ومن المسافة البادئة المناسبة. إذا كنت بحاجة إلى إجراء أي تغييرات، فأعِد تشغيل النشر وحدد **الخيار 2** لتحديث الصورة فقط.

## تنظيف الموارد

قُم بتشغيل الأمر التالي في Cloud Shell لإزالة جميع الموارد المنشورة لهذا التمرين. ستتم مطالبتك بتأكيد حذف المورد.

```
azd down --purge
```