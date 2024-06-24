---
lab:
  title: إنشاء حل للإجابة على الأسئلة
  module: Module 6 - Create question answering solutions with Azure AI Language
---

# إنشاء حل للإجابة على الأسئلة

أحد أكثر سيناريوهات المحادثة شيوعا هو توفير الدعم من خلال قاعدة المعارف (KB) من الأسئلة المتداولة (FAQs). تنشر العديد من المؤسسات الأسئلة الشائعة كمستندات أو صفحات ويب، وهو ما يعمل بشكل جيد مع مجموعة صغيرة من أزواج الأسئلة والأجوبة، ولكن قد يكون من الصعب البحث في المستندات الكبيرة ويستغرق وقتاً طويلاً.

**تتضمن لغة الذكاء الاصطناعي في Azure** *إمكانية الإجابة على الأسئلة* التي تمكنك من إنشاء قاعدة المعارف (KB) من أزواج الأسئلة والأجوبة التي يمكن الاستعلام عنها باستخدام إدخال اللغة الطبيعية، وهي الأكثر شيوعا كمورد يمكن للروبوت استخدامه للبحث عن إجابات للأسئلة المقدمة من المستخدمين.

## توفير مورد *لغة الذكاء الاصطناعي في Azure*

إذا لم يكن لديك واحدًا بالفعل في اشتراكك، فستحتاج إلى توفير مورد **خدمة لغة الذكاء الاصطناعي في Azure**. بالإضافة إلى ذلك، لإنشاء واستضافة قاعدة معرفية للإجابة على الأسئلة، تحتاج إلى تمكين ميزة **الإجابة على الأسئلة**.

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
1. في حقل البحث بالأعلى، أدخل **خدمات الذكاء الاصطناعي في Azure**، ثم اضغط على **Enter**.
1. حدد **إنشاء** ضمن **مورد خدمة اللغة** في النتائج.
1. **حدد** كتلة **الإجابة على الأسئلة** المخصصة. ثم حدد **متابعة لإنشاء المورد الخاص بك**. ستحتاج إلى إدخال الإعدادات التالية:

    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختيار مجموعة موارد أو إنشاءها*.
    - **المنطقة**: *اختر أي موقع متاح*
    - **الاسم**: *أدخل اسماً فريداً*
    - **طبقة الأسعار**: حدد **F0** (*مجاني*)، أو **S** (*قياسي*) إذا لم يكن F متوفراً.
    - **منطقة البحث في Azure**: *اختر موقعاً في نفس المنطقة العالمية التي يوجد بها مصدر اللغة الخاص بك*
    - **مستوى الأسعار الخاص ببحث Azure**: مجاني (F) (*إذا لم يكن هذا المستوى متاحاً، فاختر Basic (B)*)
    - **Responsible AI Notice**: *Agree*

1. حدد **إنشاء + مراجعة**، ثم حدد **إنشاء**.

    > **ملاحظة** تستخدم الإجابة على الأسئلة المخصصة Azure Search لفهرسة قاعدة المعارف (KB) الأسئلة والأجوبة والاستعلام عنها.

1. انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.
1. اعرض صفحة **المفاتيح ونقطة النهاية**. ستحتاج إلى المعلومات الموجودة في هذه الصفحة لاحقاً في التمرين.

## إنشاء مشروع للإجابة على الأسئلة

لإنشاء قاعدة المعارف (KB) للإجابة على الأسئلة في مورد لغة الذكاء الاصطناعي في Azure، يمكنك استخدام مدخل Language Studio لإنشاء مشروع إجابة على الأسئلة. في هذه الحالة، ستقوم بإنشاء قاعدة المعارف (KB) يحتوي على أسئلة وإجابات حول [Microsoft Learn](https://docs.microsoft.com/learn).

1. في علامة تبويب مستعرض جديدة، افتح مدخل Language Studio في [https://language.cognitive.azure.com/](https://language.cognitive.azure.com/)، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure خاصتك.
1. إذا طلب منك اختيار مورد اللغة، حدد الإعدادات التالية:
    - **Azure Directory**: دليل Azure الذي يحتوي على اشتراكك.
    - **Azure subscription**: اشتراك Azure الخاص بك.
    - **نوع المورد**: اللغة
    - **اسم المورد**. مورد "لغة الذكاء الاصطناعي في Azure" الذي أنشأتَه سابقًا.

    إذا <u>لم</u> تتم مطالبتك باختيار مورد language، فقد يرجع ذلك إلى وجود موارد Language متعددة في اشتراكك؛ وفي هذه الحالة:

    1. في الشريط الموجود أعلى الصفحة، حدّد زر **الإعدادات (&#9881;)**.
    2. في الصفحة **Settings** اعرض علامة التبويب **Resources**.
    3. حدد مورد language الذي أنشأته للتو، وانقر فوق **Switch resource**.
    4. في أعلى الصفحة، انقر فوق **Language Studio** للعودة إلى الصفحة الرئيسية في Language Studio.

1. في أعلى مدخل، في القائمة **إنشاء جديد**، حدد **الإجابة على الأسئلة المخصصة**.
1. في معالج ***إنشاء مشروع**، في **صفحة اختيار إعداد** اللغة، حدد الخيار لتعيين **اللغة لكافة المشاريع في هذا المورد**، وحدد **اللغة الإنجليزية** كلغة. بعد ذلك حدد **التالي**.
1. في صفحة **إدخال المعلومات الأساسية** أدخل التفاصيل التالية:
    - **الاسم** `LearnFAQ`
    - **الوصف**: `FAQ for Microsoft Learn`
    - **الإجابة الافتراضية عند عدم إرجاع أي إجابة**: `Sorry, I don't understand the question`
1. حدد **التالي**.
1. في صفحة **مراجعة وإنهاء**، حدد **إنشاء مشروع**.

## إضافة مصادر إلى قاعدة المعارف (KB)

يمكنك إنشاء قاعدة المعارف (KB) من البداية، ولكن من الشائع البدء باستيراد الأسئلة والأجوبة من صفحة أو مستند الأسئلة المتداولة الموجود. في هذه الحالة، ستقوم باستيراد البيانات من صفحة ويب الأسئلة المتداولة الموجودة لـ Microsoft learn، وستستورد أيضا بعض الأسئلة والأجوبة المحددة مسبقا حول "الدردشة التلقائية" لدعم تبادل المحادثات الشائعة.

1. في **صفحة إدارة المصادر** لمشروع الإجابة على سؤالك، في **&9547; أضف قائمة المصدر**، وحدد **عناوين URL**. ثم في **مربع الحوار إضافة عناوين URL**، حدد **&#9547; أضف url** وقم بتعيين الاسم وعنوان URL التاليين قبل تحديد **إضافة الكل** لإضافته إلى قاعدة المعارف (KB):
    - **الاسم:** `Learn FAQ Page`
    - **URL**: `https://docs.microsoft.com/en-us/learn/support/faq`
1. في **صفحة إدارة المصادر** لمشروع الإجابة على سؤالك، في **&#9547; أضف قائمة المصدر**، وحدد **عناوين URL**. في مربع الحوار **إضافة الدردشة التلقائية**، حدد **Friendly** وحدد **Add chit chat**.

## تحرير قاعدة المعرفة

تم ملء قاعدة المعارف (KB) بأزواج الأسئلة والأجوبة من الأسئلة المتداولة حول Microsoft Learn، وملحقة بمجموعة من أزواج الأسئلة والأجوبة الخاصة *بالدردشة التلقائية*. يمكنك توسيع قاعدة المعارف (KB) عن طريق إضافة أزواج إضافية من الأسئلة والأجوبة.

1. في مشروع **LearnFAQ** في Language Studio، حدد صفحة **تحرير قاعدة المعارف (KB)** لمشاهدة أزواج الأسئلة والأجوبة الموجودة (إذا تم عرض بعض التلميحات، فاقرأها واختر **حسناً** لتجاهلها، أو حدد **تخطي الكل**)
1. في قاعدة المعارف (KB)، في علامة التبويب **إجابات الأسئلة**، حدد **&#65291;**، وأنشئ زوجا جديدا من إجابات الأسئلة بالإعدادات التالية:
    - **المصدر**: `https://docs.microsoft.com/en-us/learn/support/faq`
    - **السؤال**: `What are Microsoft credentials?`
    - **الإجابة**: `Microsoft credentials enable you to validate and prove your skills with Microsoft technologies.`
1. حدد **تم**.
1. في صفحة **السؤال ما هي بيانات اعتماد Microsoft؟** التي تم إنشاؤها، قم بتوسيع **الأسئلة البديلة**. ثم أضف السؤال `How can I demonstrate my Microsoft technology skills?` البديل.

    في بعض الحالات، من المنطقي تمكين المستخدم من متابعة إجابة عن طريق إنشاء *محادثة متعددة الأدوار* تمكن المستخدم من تحسين السؤال بشكل متكرر للوصول إلى الإجابة التي يحتاجها.

1. ضمن الإجابة التي أدخلتها لسؤال الشهادة، قم بتوسيع **مطالبات المتابعة** وأضف مطالبة المتابعة التالية:
    - **النص المعروض في المطالبة للمستخدم**: `Learn more about credentials`.
    - حدد علامة التبويب **إنشاء ارتباط إلى زوج جديد**، وأدخل هذا النص: `You can learn more about credentials on the [Microsoft credentials page](https://docs.microsoft.com/learn/credentials/).`
    - حدد **إظهار في التدفق السياقي فقط**. يضمن هذا الخيار أن يتم إرجاع الإجابة فقط في سياق سؤال متابعة من سؤال الشهادة الأصلي.
1. حدد **إضافة مطالبة**.

## تدريب واختبار قاعدة المعارف

الآن، وبعد أن أصبحت لديك قاعدة معارف؛ فإنه يمكنك اختبارها في مدخل Language Studio.

1. احفظ التغييرات على قاعدة المعارف (KB) عن طريق تحديد الزر **حفظ** ضمن **علامة التبويب أزواج الأسئلة والإجابات** على اليسار.
1. بعد حفظ التغييرات، حدد الزر **اختبار** لفتح جزء الاختبار.
1. في جزء الاختبار، في الأعلى، قم بإلغاء تحديد **تضمين استجابة الإجابة القصيرة** (إذا لم يكن محددا بالفعل). ثم في الأسفل أدخل الرسالة `Hello`. وينبغي إرجاع استجابة مناسبة.
1. في جزء الاختبار، أدخل في الجزء السفلي رسالة تقول `What is Microsoft Learn?`. يجب إرجاع رد مناسب من الأسئلة الشائعة.
1. أدخل الرسالة `Thanks!` يجب إرجاع استجابة المحادثات التلقائية المناسبة.
1. إدخال الرسالة `Tell me about Microsoft credentials`. يجب أن يتم إرجاع الإجابة التي قمت بإنشائها مع رابط المتابعة السريع.
1. حدد الارتباط **تعرّف على المزيد حول متابعة بيانات الاعتماد**. يجب إرجاع إجابة المتابعة مع ارتباط إلى صفحة الشهادة.
1. عند الانتهاء من اختبار قاعدة المعرفة، قم بإغلاق جزء الاختبار.

## نشر قاعدة المعرفة

توفر قاعدة المعرفة خدمة خلفية يمكن لتطبيقات العميل استخدامها للإجابة على الأسئلة. أنت الآن جاهز لنشر قاعدة المعارف (KB) والوصول إلى واجهة REST الخاصة به من عميل.

1. في مشروع **LearnFAQ** في Language Studio، حدد **صفحة نشر قاعدة المعرفة (KB)**.
1. في أعلى الصفحة، حدد **نشر**. ثم حدد **نشر** لتأكيد رغبتك في نشر قاعدة المعارف (KB).
1. عند اكتمال النشر، حدد **الحصول على عنوان URL للتنبؤ** لعرض نقطة نهاية REST لقاعدة المعرفة الخاصة بك ولاحظ أن نموذج الطلب يتضمن معلمات لـ:
    - **projectName**: اسم مشروعك (الذي ينبغي أن يكون *LearnFAQ*)
    - **deploymentName**: اسم النشر الخاص بك (والذي يجب أن يكون *إنتاجاً*)
1. أغلق مربع حوار عنوان URL للتنبؤ.

## الاستعداد لتطوير تطبيق في Visual Studio Code

ستقوم بتطوير تطبيق الإجابة على أسئلتك باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.

> **تلميح**: إذا استنسخت بالفعل مستودع **mslearn-ai-language**، فافتحه في Visual Studio code. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة التطوير الخاصة بك.

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوح الألوان (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-language` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في Visual Studio Code.

    > **ملاحظة**: إذا عرضت لك Visual Studio Code رسالة منبثقة لمطالبتك بالثقة في التعليمات البرمجية التي تفتحها، فانقر فوق **نعم، أثق في خيار الكُتاب** في النافذة المنبثقة.

4. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

## تكوين تطبيقك

تم توفير تطبيقات لكل من C# وPython، بالإضافة إلى ملف نصي نموذجي ستستخدمه لاختبار التلخيص يتميز كلا التطبيقين بالوظيفة نفسها. أولاً، ستكمل بعض الأجزاء الرئيسية من التطبيق لتمكينه من استخدام مورد لغة الذكاء الاصطناعي في Azure الخاص بك.

1. في Visual Studio Code، في جزء **Explorer**، استعرض للوصول إلى المجلد **Labfiles/02-qna** ووسع نطاق المجلد **CSharp** أو **Python** استناداً إلى تفضيلات اللغة ومجلد **الساعة الناطقة** الذي يحتوي عليها. يحتوي كل مجلد على الملفات الخاصة باللغة الخاصة بالتطبيق الذي ستقوم بدمج وظيفة الإجابة على أسئلة لغة الذكاء الاصطناعي في Azure فيه.
2. انقر بزر الماوس الأيمن فوق مجلد **qna-app** الذي يحتوي على ملفات التعليمات البرمجية الخاصة بك وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة SDK للإجابة على أسئلة لغة الذكاء الاصطناعي في Azure عن طريق تشغيل الأمر المناسب لتفضيلات اللغة الخاصة بك:

    **C#:**

    ```
    dotnet add package Azure.AI.Language.QuestionAnswering
    ```

    **لغة Python**:

    ```
    pip install azure-ai-language-questionanswering
    ```

3. في جزء **Explorer**، في مجلد **qna-app**، افتح ملف التكوين للغتك المفضلة

    - **C#**: appsettings.json
    - **Python**: .env
    
4. قم بتحديث قيم التكوين لتضمين **نقطة النهاية** و**مفتاح** من مورد Azure Language الذي أنشأته (متوفر في صفحة **المفاتيح ونقطة النهاية** لمورد Azure AI Language في مدخل Microsoft Azure). يجب أن يكون اسم المشروع واسم النشر قاعدة المعارف (KB) المنشورة أيضا في هذا الملف.
5. احفظ ملف التكوين.

## إضافة تعليمية برمجية إلى التطبيق

أنت الآن جاهز لإضافة التعليمة البرمجية اللازمة لاستيراد مكتبات SDK المطلوبة، وإنشاء اتصال مصادق عليه بمشروعك المنشور، وإرسال الأسئلة.

1. لاحظ أن مجلد **qna-app** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: qna-app.py

    افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Text Analytics SDK:

    **C#**: Programs.cs

    ```csharp
    // import namespaces
    using Azure;
    using Azure.AI.Language.QuestionAnswering;
    ```

    **Python**: qna-app.py

    ```python
    # import namespaces
    from azure.core.credentials import AzureKeyCredential
    from azure.ai.language.questionanswering import QuestionAnsweringClient
    ```

1. في الدالة **Main**، لاحظ أنه تم بالفعل توفير التعليمات البرمجية لتحميل نقطة نهاية خدمة لغة الذكاء الاصطناعي في Azure والمفتاح من ملف التكوين. ثم ابحث عن التعليق **إنشاء عميل باستخدام نقطة النهاية والمفتاح**، وأضف التعليمة البرمجية التالية لإنشاء عميل لواجهة برمجة تطبيقات تحليل النص:

    **C#**: Programs.cs

    ```C#
    // Create client using endpoint and key
    AzureKeyCredential credentials = new AzureKeyCredential(aiSvcKey);
    Uri endpoint = new Uri(aiSvcEndpoint);
    QuestionAnsweringClient aiClient = new QuestionAnsweringClient(endpoint, credentials);
    ```

    **Python**: qna-app.py

    ```Python
    # Create client using endpoint and key
    credential = AzureKeyCredential(ai_key)
    ai_client = QuestionAnsweringClient(endpoint=ai_endpoint, credential=credential)
    ```

1. في الدالة **Main** ، ابحث عن التعليق **إرسال سؤال وعرض الإجابة**، وأضف التعليمات البرمجية التالية لقراءة الأسئلة بشكل متكرر من سطر الأوامر، وإرسالها إلى الخدمة، وعرض تفاصيل الإجابات:

    **C#**: Programs.cs

    ```C#
    // Submit a question and display the answer
    string user_question = "";
    while (user_question.ToLower() != "quit")
        {
            Console.Write("Question: ");
            user_question = Console.ReadLine();
            QuestionAnsweringProject project = new QuestionAnsweringProject(projectName, deploymentName);
            Response<AnswersResult> response = aiClient.GetAnswers(user_question, project);
            foreach (KnowledgeBaseAnswer answer in response.Value.Answers)
            {
                Console.WriteLine(answer.Answer);
                Console.WriteLine($"Confidence: {answer.Confidence:P2}");
                Console.WriteLine($"Source: {answer.Source}");
                Console.WriteLine();
            }
        }
    ```

    **Python**: qna-app.py

    ```Python
    # Submit a question and display the answer
    user_question = ''
    while user_question.lower() != 'quit':
        user_question = input('\nQuestion:\n')
        response = ai_client.get_answers(question=user_question,
                                        project_name=ai_project_name,
                                        deployment_name=ai_deployment_name)
        for candidate in response.answers:
            print(candidate.answer)
            print("Confidence: {}".format(candidate.confidence))
            print("Source: {}".format(candidate.source))
    ```

1. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **qna-app**، وأدخل الأمر التالي لتشغيل البرنامج:

    - **C#:** `dotnet run`
    - **Python**: `python qna-app.py`

    > **تلميح**: يمكنك استخدام أيقونة **تكبير حجم اللوحة** (**^**) في شريط أدوات المحطة الطرفية لرؤية المزيد من نص وحدة التحكم.

1. عند المطالبة، أدخل سؤالا لإرساله إلى مشروع الإجابة على سؤالك؛ على سبيل المثال `What is a learning path?`.
1. راجع الإجابة التي يتم إرجاعها.
1. اطرح المزيد من الأسئلة. عند الانتهاء، أدخِل `quit`.

## تنظيف الموارد

إذا انتهيت من استكشاف خدمة لغة الذكاء الاصطناعي في Azure، فيمكنك حذف الموارد التي قمت بإنشائها في هذا التمرين. وإليك الطريقة:

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
2. استعرض للوصول إلى مورد لغة الذكاء الاصطناعي في Azure الذي أنشأته في هذا المختبر.
3. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## مزيد من المعلومات

للتعرّف على المزيد حول الإجابة على الأسئلة في لغة الذكاء الاصطناعي في Azure، راجع [وثائق](https://learn.microsoft.com/azure/ai-services/language-service/question-answering/overview) لغة الذكاء الاصطناعي في Azure.