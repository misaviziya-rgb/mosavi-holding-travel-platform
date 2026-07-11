# MOS-0220 — طراحی پایگاه‌داده (Database Design)

**هلدینگ خدمات موسوی | Mosavi Services Holding**

| | |
|---|---|
| **شناسه سند** | MOS-0220 |
| **نسخه** | 0.1 (Draft — Skeleton) |
| **وضعیت** | پیش‌نویس — در انتظار تصمیم معمار ارشد راهکار (CSA) |
| **مرجع بالادستی** | MOS-0200، MOS-0210 (Technology Stack) |
| **تهیه‌کننده** | Production Engineer |
| **تأییدکننده نهایی** | Chief Solution Architect |

## یادداشت حاکمیتی

طراحی پایگاه‌داده (استراتژی تفکیک، مدل منطقی داده، انتخاب موتور) تصمیم معماری است. این سند چارچوب و سؤالات لازم را فراهم می‌کند؛ مدل داده تفصیلی هر Bounded Context باید پس از نهایی‌شدن MOS-0100 (BRD) و تأیید CSA تکمیل شود.

---

## 1. استراتژی کلی داده

| سؤال | گزینه‌های رایج | تصمیم |
|---|---|---|
| تفکیک داده بین سرویس‌ها | Database-per-service / Shared Database / Hybrid | `[TBD]` — وابسته به MOS-0200 بخش ۵ |
| مدل سازگاری | Strong Consistency در برابر Eventual Consistency به‌ازای هر Context | `[TBD]` |
| استراتژی چند-مستأجری داده | مطابق MOS-0200 بخش ۶ | `[TBD]` |

## 2. مدل داده منطقی (پیش‌نویس بر اساس Bounded Contextهای پیشنهادی MOS-0200)

> ⚠ فهرست موجودیت‌های زیر **پیشنهادی و غیرقطعی** است و باید در برابر محتوای نهایی MOS-0100 اعتبارسنجی شود.

| Bounded Context | موجودیت‌های اصلی پیشنهادی | وضعیت |
|---|---|---|
| Identity & Access | User، Role، Permission، Session | 🟡 پیشنهادی |
| Catalog & Search | Product/Service Listing، Category، Price، Availability | 🟡 پیشنهادی |
| Booking | Booking، BookingItem، Itinerary، Status History | 🟡 پیشنهادی |
| Payment & Settlement | Transaction، Invoice، Commission، Refund | 🟡 پیشنهادی |
| Supplier Management | Supplier، Contract، Inventory Feed | 🟡 پیشنهادی |
| Partner/Agency Management | Agency، AgencyUser، CommissionRule | 🟡 پیشنهادی |

جزئیات کامل هر موجودیت (فیلدها، روابط، محدودیت‌ها) باید در تکرار بعدی، پس از تأیید CSA و دریافت محتوای MOS-0100، اضافه شود.

## 3. استراتژی مهاجرت و نسخه‌بندی Schema

`[TBD]` — ابزار (Flyway/Liquibase/سایر)، فرآیند بازبینی تغییرات Schema، سیاست Rollback.

## 4. نگهداری و بایگانی داده (Retention & Archival)

| نوع داده | سیاست پیشنهادی | تصمیم |
|---|---|---|
| داده تراکنشی فعال | `[TBD]` | `[TBD]` |
| لاگ‌های سیستمی | `[TBD]` | `[TBD]` |
| داده شخصی کاربران (مطابق الزامات حفاظت داده) | `[TBD]` | `[TBD]` — نیازمند تأیید CSA + الزامات قانونی |

## 5. پشتیبان‌گیری و بازیابی

جزئیات کامل در MOS-0200 بخش ۱۳ (Disaster Recovery). این‌جا فقط سیاست سطح پایگاه‌داده: `[TBD]`

## 6. کارایی و ایندکس‌گذاری

`[TBD]` — استراتژی ایندکس‌گذاری، Partitioning، Read Replica، وابسته به موتور انتخاب‌شده در MOS-0210.

## 7. فهرست تصمیمات باز

| # | موضوع | نیازمند تصمیم از |
|---|---|---|
| 1 | استراتژی Database-per-service در برابر Shared | CSA |
| 2 | مدل داده تفصیلی هر Bounded Context | CSA + محتوای نهایی MOS-0100 |
| 3 | ابزار مهاجرت Schema | CSA |
| 4 | سیاست نگهداری و حذف داده شخصی | CSA + الزامات قانونی |
| 5 | استراتژی Backup/Restore | CSA |

## تاریخچه نسخه‌ها

| نسخه | تاریخ | وضعیت | شرح |
|---|---|---|---|
| 0.1 | 1405/04/20 | Draft — Skeleton | ایجاد چارچوب اولیه؛ مدل داده پیشنهادی و غیرقطعی؛ در انتظار تصمیم CSA |
