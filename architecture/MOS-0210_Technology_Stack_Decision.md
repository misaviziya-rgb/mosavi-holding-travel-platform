# MOS-0210 — تصمیم پشته فناوری (Technology Stack Decision)

**هلدینگ خدمات موسوی | Mosavi Services Holding**

| | |
|---|---|
| **شناسه سند** | MOS-0210 |
| **نسخه** | 0.1 (Draft — Skeleton) |
| **وضعیت** | پیش‌نویس — در انتظار تصمیم معمار ارشد راهکار (CSA) |
| **مرجع بالادستی** | MOS-0200 (Architecture Design Document) |
| **تهیه‌کننده** | Production Engineer |
| **تأییدکننده نهایی** | Chief Solution Architect |

## یادداشت حاکمیتی

انتخاب پشته فناوری یک **تصمیم معماری**، نه یک واقعیت مستندسازی‌شده، است. Production Engineer فاقد اختیار برای اتخاذ این تصمیم است. بخش‌های زیر گزینه‌های رایج صنعت را به‌عنوان **ورودی برای بحث** فهرست می‌کنند؛ هیچ‌کدام تا تأیید صریح CSA، مبنای پیاده‌سازی قرار نمی‌گیرند.

---

## 1. معیارهای تصمیم‌گیری

پیش از انتخاب فناوری، معیارهای زیر باید توسط CSA اولویت‌بندی شوند: `[TBD]`

- دسترسی به نیروی متخصص در بازار ایران
- هزینه‌ی مجوز/میزبانی با توجه به الزامات میزبانی داخلی
- بلوغ اکوسیستم برای معماری رویداد-محور و AI Services (مطابق MOS-0200)
- سازگاری با مسیر مهاجرت تدریجی مونولیت ماژولار → میکروسرویس (در صورت تأیید رویکرد پیشنهادی MOS-0200 بخش ۵)

## 2. فرانت‌اند (Web / Mobile)

| لایه | گزینه‌های رایج صنعت | تصمیم |
|---|---|---|
| Web App | React / Next.js / Vue / Angular | `[TBD]` |
| Mobile App | React Native / Flutter / Native (iOS+Android جدا) | `[TBD]` |
| B2B Agency Portal | مشترک با Web App یا مجزا | `[TBD]` |
| State Management | `[TBD]` | `[TBD]` |
| Design System | `[TBD]` | `[TBD]` |

## 3. بک‌اند

| لایه | گزینه‌های رایج صنعت | تصمیم |
|---|---|---|
| زبان/فریم‌ورک اصلی | Node.js (NestJS) / Java (Spring Boot) / Go / Python (FastAPI/Django) / .NET | `[TBD]` |
| API Gateway | Kong / AWS API Gateway / NGINX / خوداستقرار | `[TBD]` |
| Message Broker | Kafka / RabbitMQ / Cloud-native (SQS/SNS) | `[TBD]` — وابسته به MOS-0200 بخش ۹ |
| Cache | Redis / Memcached | `[TBD]` |

## 4. پایگاه‌داده

جزئیات کامل در MOS-0220 (Database Design) پوشش داده می‌شود؛ در این‌جا فقط انتخاب موتور:

| نوع داده | گزینه‌های رایج | تصمیم |
|---|---|---|
| داده تراکنشی (OLTP) | PostgreSQL / MySQL | `[TBD]` |
| داده تحلیلی (OLAP) | ClickHouse / BigQuery / Snowflake | `[TBD]` |
| جستجو | Elasticsearch / OpenSearch / Meilisearch | `[TBD]` |
| Document/NoSQL (در صورت نیاز) | MongoDB / DynamoDB | `[TBD]` |

## 5. زیرساخت و DevOps

| حوزه | گزینه‌های رایج | تصمیم |
|---|---|---|
| Cloud Provider | ابر داخلی ایران (مطابق الزام میزبانی) / Hybrid | `[TBD]` — وابسته به MOS-0200 بخش ۱۲ |
| Containerization | Docker + Kubernetes | `[TBD]` |
| CI/CD | GitHub Actions / GitLab CI / Jenkins | `[TBD]` — هم‌راستا با فاز ۲ یکپارچه‌سازی AI (CI/CD بدون فراخوانی مدل) |
| Infrastructure as Code | Terraform / Pulumi | `[TBD]` |
| Observability | مطابق MOS-0200 بخش ۱۵ | `[TBD]` |

## 6. سرویس‌های هوش مصنوعی

جزئیات کامل در MOS-0250 (AI Architecture). انتخاب فناوری پایه: `[TBD]`

## 7. فهرست تصمیمات باز

| # | موضوع | نیازمند تصمیم از |
|---|---|---|
| 1 | زبان/فریم‌ورک بک‌اند اصلی | CSA |
| 2 | فریم‌ورک فرانت‌اند وب و موبایل | CSA |
| 3 | موتور پایگاه‌داده اصلی | CSA |
| 4 | Cloud Provider نهایی با توجه به الزام میزبانی داخل ایران | CSA + PO |
| 5 | Message Broker | CSA |
| 6 | پشته CI/CD | CSA |

## تاریخچه نسخه‌ها

| نسخه | تاریخ | وضعیت | شرح |
|---|---|---|---|
| 0.1 | 1405/04/20 | Draft — Skeleton | ایجاد چارچوب اولیه؛ تمامی انتخاب‌های فناوری در انتظار تصمیم CSA |
