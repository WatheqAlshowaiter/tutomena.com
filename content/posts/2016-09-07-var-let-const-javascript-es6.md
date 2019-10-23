---
title: 'الفرق بين let ،var و const في جافاسكريبت'
date: '2016-09-07'
slug: 'web-development/javascript/var-let-const-javascript-es6'
template: 'post'
categories:
  - جافاسكريبت
  - متميز
tags:
  - es2015
thumbnail: '../thumbnails/js.png'
---

# الجديد في ES2015

مع الإصدار الأخير للغة البرمجة **جافاسكريبت** والمعروف اختصارا ب **ES2015**، ظهرت كلمات مفتاحية جديدة عديدة في اللغة لتمنح **مبرمج الجافاسكريبت** فرصا وإمكانيات جديدة للقيام بتطبيقات قوية ومتطورة. وسنتكلم في هذا المقال عن **الكلمتين المفتاحيتين (Keywords)** التاليتين :

- **let**
- **const**

أولا هاتين الكلمتن تستعملان لإنشاء المتغيرات تماما مثلما هو الحال بالنسبة ل **var** ولكن بطبيعة الحال هناك فروقات جوهرية بين هذه الكلمات الثلاثة، سنحاول توضيحها وشرحها على النحو التالي :

## var

تستعمل هذه الكلمة لإنشاء متغيرات داخل الكائن العلوي window وهذه المتغيرات إما أن تكون عامة global يمكن الوصول إليها في جميع أنحاء التطبيق أو قد تكون في نطاق محدد وهو نطاق دالة معينة (function-scoped) بحيث لا يمكن الوصول إليها خارج هذه الدالة (private variables). هذه الكلمة المفتاحية موجودة منذ الإصدارات الأولى لجافاسكريبت ولكن الوقت جاء لإضافة بدائل عنها تكون أكثر مرونة وأمانا حتى تساير هذه اللغة الإيقاع السريع الذي يتقدم به مجال برمجيات الويب والجافاسكريبت بصفة عامة. ولهذا ظهر **let** في الإصدار الأخير من الجافاسكريبت.

```js
function varTest() {
  var x = 1;
  if (true) {
    var x = 2; // نفس المتغير
    console.log(x); // 2
  }
  console.log(x); // 2
}
```

## let

بعكس var فإن let تمكننا من إنشاء متغيرات تابعة لنطاقات أضيق قد تكون دوال أو فقط تعابير شرطية أو حلقات متكررة وغيرها ولهذا تسمى هذه المتغيرات بالإنجليزية block-scoped أي أنك لا تستطيع الوصول إليها خارج ال block الذي صُرِّح بها فيه.

```js
function letTest() {
  let x = 1;
  if (true) {
    let x = 2; // متغير آخر
    console.log(x); // 2
  }
  console.log(x); // 1
}
```

وعندما تحاول استعمال متغير قبل التصريح به فإنك ستحصل على خطأ جميل :) في برمجيتك من نوع **ReferenceError** على عكس ما اعتدنا علينا مع الكلمة المفتاحية **var** حيث كانت تعطى لكل متغير قيمة افتراضية وهي _undefined حتى قبل إنشاء هذا المتغير._

## const 

هذه الكلمة تعمل تماما بنفس خصائص **let** أي أنها block-scoped كذلك إلا أنها، كما يدل على ذلك اسمها، تستعمل فقط للتصريح بالثوابت **Constants** التي تأخذ قيمة **واحدة** فقط طيلة حياة البرنامج ولا يمكن تغييرها.

```js
function constTest() {
  let x = true;

  if (x) {
    const P = 3.14;
    console.log(P); // 3.14
  }

  console.log(P); // ReferenceError
}
```

من خصائص **const** أنه من الضروري إعطاء قيمة للثابتة فور التصريح بها وهذا الأمر طبيعي كون الثابتة يصرح بها عند الحاجة إليها فقط ولا يمكن تغييرها فيما بعد في ذات النطاق scope الذي أنشأت فيه.

```js
const P = 3.14;
P = 3.142; // Uncaught TypeError
```

## خاتمة

هذا ليس كل ما يمكن قوله حول هذه الكلمات المفتاحية وخصائصها، ولكننا وددنا فقط التعريف بها وبأهم أدوارها ومميزاتها وليس التعمق في تعقيداتها والمرور على كافة الحالات التي قد تصادفك معها كمبرمج.

المطورون القادمون من جافا و C++ وغيرها من اللغات المعروفة سيفهمون جيدا مفهوم **_block-scoped variables_** وفوائده، ومطورو الجافاسكريبت المتمرسون يثمنون هذه التغييرات التي ستدفع اللغة نحو الأمام. ورغم أن دعم المتصفحات والأجهزة لهذه التغيرات ليس كاملا بعد إلا أنه لن يطول انتظاره ولذلك يستحسن بكل مطور جافاسكريبت أن يبقى متيقضا وعلى علم بكل جديد حتى يندمج بشكل سلس ومرن مع كل التغييرات.