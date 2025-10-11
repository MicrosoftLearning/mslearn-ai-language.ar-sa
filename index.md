---
title: تمارين لغة الذكاء الاصطناعي في Azure
permalink: index.html
layout: home
---

# تمارين لغة الذكاء الاصطناعي في Azure

التمارين التالية مُصممة لتزويدك بتجربة تعليمية عملية تستكشف فيها المهام الشائعة التي يقوم بها المُطورون عند بناء حلول اللغة الطبيعية على Azure. 

> **ملاحظة**: لإكمال التمارين، ستحتاج إلى اشتراك Azure. إذا لم يكن لديك حسابًا مسبقًا، فيمكنك التسجيل للحصول على [حساب Azure](https://azure.microsoft.com/free). هناك خيار تجريبي مجاني للمستخدمين الجدد يتضمن رصيدًا لأول 30 يومًا.

## التدريبات

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %} {% for activity in labs  %}
<hr>

### [{{activity.lab.title}}]({{ site.github.url }}{{ activity.url }})

{{activity.lab.description}}

{% endfor %}

<hr>

> **ملاحظة**: على الرغم من أنه يمكنك إكمال هذه التدريبات بمفردها، إلا أنها مصممة لاستكمال الوحدات الموجودة على [Microsoft Learn](https://learn.microsoft.com/training/paths/develop-language-solutions-azure-ai/)؛ حيث ستجد تعمقًا في بعض المفاهيم الأساسية التي تستند إليها هذه التدريبات. 
