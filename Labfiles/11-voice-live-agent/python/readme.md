# المتطلبات

## تشغيل في Cloud Shell

* اشتراك Azure مع وصول إلى OpenAI
* في حال التشغيل في Azure Cloud Shell، اختَر Bash shell. يتم تضمين Azure CLI وAzure Developer CLI في Cloud Shell.

## شغّل محليًا

* يمكنك تشغيل تطبيق الويب محليًا بعد تشغيل البرنامج النصي للنشر:
    * [Azure Developer CLI (azd)](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/install-azd)
    * [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
    * اشتراك Azure مع وصول إلى OpenAI


## متغيرات البيئة

يتم إنشاء ملف `.env` بواسطة البرنامج النصي *azdeploy.sh*. تتم إضافة نقطة نهاية نموذج الذكاء الاصطناعي، ومفتاح API، واسم النموذج في أثناء نشر الموارد.

## نشر موارد Azure

يتولى `azdeploy.sh` المقدم إنشاء الموارد المطلوبة في Azure:

* تغيير المتغيرَين في الجزء العلوي من البرنامج النصي لمطابقة احتياجاتك، لا تغيّر أي شيء آخر.
* بيان النص:
    * نشر نموذج *gpt-4o* باستخدام AZD.
    * إنشاء خدمة Azure Container Registry
    * استخدام مهام ACR لإنشاء صورة Dockerfile ونشرها إلى ACR
    * إنشاء خطة خدمة التطبيق
    * إنشاء تطبيق الويب لخدمة التطبيق
    * تكوين تطبيق الويب لصورة الحاوية في ACR
    * تكوين متغيرات بيئة تطبيق الويب
    * سيوفر البرنامج النصي نقطة نهاية خدمة التطبيق

يوفر البرنامج النصي خيارين للنشر: 1. نشر كامل، و2. إعادة نشر الصورة فقط. الخيار 2 هو فقط لما بعد النشر عندما تريد تجربة التغييرات في التطبيق. 

> ملاحظة: يمكنك تشغيل البرنامج النصي في PowerShell أو Bash، باستخدام الأمر `bash azdeploy.sh`، ويتيح لك هذا الأمر أيضًا تشغيل البرنامج النصي في Bash دون الحاجة إلى جعله قابلًا للتنفيذ.

## التطوير المحلي

### توفير نموذج الذكاء الاصطناعي لـ Azure

يمكنك تشغيل المشروع محليًا وتوفير نموذج الذكاء الاصطناعي فقط باتباع الخطوات التالية:

1. **تهيئة البيئة** (اختَر اسمًا وصفيًا):

   ```bash
   azd env new gpt-realtime-lab --confirm
   # or: azd env new your-name-gpt-experiment --confirm
   ```
   
   **مهم**: يصبح هذا الاسم جزءًا من أسماء موارد Azure!  
   تعيّن علامة `--confirm` هذا الاسم كبيئة افتراضية دون مطالبة.

1. **تعيين مجموعة الموارد الخاصة بك**:

   ```bash
   azd env set AZURE_RESOURCE_GROUP "rg-your-name-gpt"
   ```

1. **تسجيل الدخول وتوفير موارد الذكاء الاصطناعي**:

   ```bash
   az login
   azd provision
   ```

    > **مهم**: عدم تشغيل `azd deploy` - لم يتم تكوين التطبيق في قوالب AZD.

إذا قمت بتوفير النموذج فقط باستخدام أسلوب `azd provision`، فيجب إنشاء ملف `.env` في جذر الدليل بالإدخالات التالية:

```
AZURE_VOICE_LIVE_ENDPOINT=""
AZURE_VOICE_LIVE_API_KEY=""
VOICE_LIVE_MODEL=""
VOICE_LIVE_VOICE="en-US-JennyNeural"
VOICE_LIVE_INSTRUCTIONS="You are a helpful AI assistant with a focus on world history. Respond naturally and conversationally. Keep your responses concise but engaging."
VOICE_LIVE_VERBOSE="" #Suppresses excessive logging to the terminal if running locally
```

ملاحظات:

1. نقطة النهاية هي نقطة النهاية للنموذج ويجب أن تتضمن `https://<proj-name>.cognitiveservices.azure.com` فقط.
1. مفتاح API هو مفتاح النموذج.
1. النموذج هو اسم النموذج المُستخدم في أثناء النشر.
1. يمكنك استرداد هذه القيم من مدخل مصنع الذكاء الاصطناعي.

### تشغيل المشروع محليًا

تم إنشاء المشروع وإدارته باستخدام **uv**، ولكنها ليست مطلوبة لتشغيله. 

إذا كانت **uv** مثبتة لديك، فيتعين:

* تشغيل `uv venv` لإنشاء البيئة
* تشغيل `uv sync` لإضافة حزم
* الاسم المستعار الذي تم إنشاؤه لتطبيق الويب: `uv run web` لبدء البرنامج النصي `flask_app.py`.
* تم إنشاء ملف ‎requirements.txt‎ باستخدام `uv pip compile pyproject.toml -o requirements.txt`

إذا لم تكن **uv** مثبتة لديك، فيتعين:

* إنشاء البيئة: `python -m venv .venv`
* تنشيط البيئة: `.\.venv\Scripts\Activate.ps1`
* تثبيت التبعيات: `pip install -r requirements.txt`
* تشغيل التطبيق (من جذر المشروع): `python .\src\real_time_voice\flask_app.py`
