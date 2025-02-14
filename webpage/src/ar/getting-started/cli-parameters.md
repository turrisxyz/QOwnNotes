# مُعامِلات واجهة سطر الأوامر

يمكنك استخدام هذه المُعامِلات في واجهة سطر الأوامر:

| المُعامِل                                                 | الوصف                                                                                         |
| --------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `<span dir="ltr">--help</span>`                     | يُظهر شاشة المساعدة                                                                           |
| `<span dir="ltr">--version</span>`                  | يعرض رقم نسخة التطبيق                                                                         |
| `<span dir="ltr">--portable</span>`                 | يشغل التطبيق في الوضع المحمول                                                                 |
| `<span dir="ltr">--clear-settings</span>`           | يمسح الإعدادات ويشغل التطبيق                                                                  |
| `<span dir="ltr">--dump-settings</span>`            | يطبع تفريغ الإعدادات ومعلومات أخرى عن التطبيق والبيئة، بصيغة ماركداون GitHub ويخرج من التطبيق |
| `<span dir="ltr">--session <اسم></span>`      | يشغل التطبيق في سياق مختلف للإعدادات والملفات الداخلية                                        |
| `<span dir="ltr">--allow-multiple-instances</span>` | يسمح بتشغيل عدة نسخ من تطبيق QOwnNotes حتى في حالة منع ذلك في الإعدادات                       |
| `<span dir="ltr">--action <اسم></span>`       | ينفذ إجراء قائمة بعد تشغيل التطبيق (انظر بالأسفل)                                             |

::: tip إذا كنت تواجه مشاكل مع QOwnNotes المثبت لديك، ربما تود أن تشغّل التطبيق بإعدادات جديدة بدون أن تفقد إعداداتك الحالية، باستخدام المُعامل <code dir="ltr">--session</code>.

```bash
QOwnNotes --session test
```
:::

قد تحتاج إلى تشغيل التطبيق من واجهة سطر الأوامر بطرق مختلفة على أنظمة التشغيل المختلفة:

| نظام التشغيل | الأمر                                                                               |
| ------------ | ----------------------------------------------------------------------------------- |
| لينكس        | `QOwnNotes` (أو `qownnotes` لو كان مثبتًا عبر snap)                                 |
| ماك أو إس    | `<span dir="ltr">/Applications/QOwnNotes.app/Contents/MacOS/QOwnNotes</span>` |
| ويندوز       | `QOwnNotes.exe`                                                                     |

## تنفيذ إجراءات قائمة بعد التشغيل

باستخدام المُعامِل <code dir="ltr">--action &lt;اسم&gt;</code>، يمكنك تنفيذ إجراءات قائمة بعد تشغيل التطبيق.

مثلا لإظهار حوار قائمة المهام بعد التشغيل، استخدم:

```bash
QOwnNotes --action actionShow_Todo_List
```

::: tip يمكنك الحصول على أسماء كائنات إجراءات القائمة من [mainwindow.ui](https://github.com/pbek/QOwnNotes/blob/develop/src/mainwindow.ui). فقط ابحث بالعنوان الإنجليزي للقائمة. لاحظ أن هذه النصوص قد تتغير بمرور الوقت. :::

لتنفيذ [إجراء برمجي](../scripting/methods-and-objects.md#registering-a-custom-action)، استخدم <code dir="ltr">customAction_</code> متبوعًا باسم الإجراء المخصص. اسم الإجراء المخصص هو المُعامل الأول في نداء `script.registerCustomAction` في البُريمج.

مثلا لتنفيذ الإجراء المخصص `myAction`، شغّل QOwnNotes هكذا:

```bash
QOwnNotes --action customAction_myAction
```

::: tip
إذا كنت تستخدم وضع النسخة الوحيدة وقمت بتشغيل QOwnNotes مرة ثانية باستخدام مُعامِل الإجراء، فإن إجراء القائمة سيُنفَّذ في النسخة الأولى.
:::
