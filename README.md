# 👔 واجهة برمجة تطبيقات متجر الشهاوي للملابس الرجالي (Men's Clothing Store API)

<p align="center">
  <img src="./imgs/Logo.png" alt="API Brand" width="400"/>
</p>

واجهة برمجة تطبيقات (API) قوية وعالية الأداء مبنية باستخدام Node.js و Express.js. توفر هذه الخدمة بيانات تفصيلية لأكثر من 245 منتج من الملابس الرجالي والمعدات الرياضية من مختلف الفئات، مع ميزات متقدمة للبحث والفلترة وتقسيم الصفحات. تم تصميم الـ API لتكون سريعة، فعالة، وسهلة الاستخدام للمطورين.

---

## ✨ الميزات

-   **تحميل ديناميكي للبيانات:** يقوم السيرفر بقراءة وتحميل جميع ملفات `JSON` الخاصة بالمنتجات تلقائيًا عند بدء التشغيل.
-   **تخزين مؤقت عالي الأداء (Caching):** يتم تخزين جميع البيانات في الذاكرة لضمان استجابة فائقة السرعة للطلبات.
-   **بحث وفلترة متقدمة:** يمكنك البحث عن المنتجات بالاسم، الوصف، الفئة، اللون، السعر، وسنة الموديل.
-   **تقسيم صفحات ذكي (Smart Pagination):** للتحكم في كمية البيانات المُرجعة والحفاظ على الأداء العالي.
-   **نقاط وصول شاملة (Comprehensive Endpoints):** للحصول على كل المنتجات، أو منتجات فئة معينة، أو حتى منتج واحد محدد.
-   **إحصائيات متقدمة:** إحصائيات مفصلة عن المنتجات، الأسعار، الألوان، والفئات.

---

## 🚀 التثبيت والتشغيل

1.  **المتطلبات الأساسية:**
    تأكد من أن لديك [Node.js](https://nodejs.org/) (الإصدار 14 أو أعلى) مثبت على جهازك.

2.  **نسخ المشروع:**
    ```bash
    git clone <project-repository-url>
    cd <project-folder-name>
    ```

3.  **تثبيت الاعتماديات (Dependencies):**
    ```bash
    npm install express cors helmet morgan dotenv
    ```

4.  **تشغيل السيرفر:**
    ```bash
    node server.js
    ```

5.  عند التشغيل الناجح، ستظهر الرسالة التالية في وحدة التحكم (Terminal):
    ```
    🚀 Server is running on http://localhost:3000
    📅 Date: Monday, February 23, 2026
    🕐 Time: 01:28 AM (Cairo Time)
    📦 Total categories loaded: 13
    ```

---

## 📚 دليل نقاط الوصول (API Endpoints Guide)

**الرابط الأساسي (Base URL):** `http://localhost:3000`

### 🏠 1. الصفحة الرئيسية
-   **Endpoint:** `GET /`
-   **الوصف:** صفحة الترحيب التي تعرض جميع نقاط الوصول المتاحة.
-   **الرابط:** `http://localhost:3000/`

---

### 📥 2. جلب كل المنتجات
-   **Endpoint:** `GET /api/products/all`
-   **الوصف:** يقوم بجلب قائمة بجميع المنتجات. يدعم تقسيم الصفحات بشكل افتراضي لتحسين الأداء.
-   **Parameters:**
    -   `page` (اختياري): رقم الصفحة. الافتراضي `1`.
    -   `limit` (اختياري): عدد النتائج في الصفحة. الافتراضي `20`.
    -   `pagination` (اختياري): لتعطيل التقسيم وجلب كل المنتجات، استخدم القيمة `false`.
-   **مثال (مع تقسيم الصفحات):** `http://localhost:3000/api/products/all?page=2&limit=10`
-   **مثال (بدون تقسيم الصفحات):** `http://localhost:3000/api/products/all?pagination=false`

---

### 🔍 3. البحث والفلترة المتقدمة
-   **Endpoint:** `GET /api/products/search`
-   **الوصف:** يقوم بالبحث في جميع المنتجات بناءً على معايير محددة.
-   **Parameters:**
    -   `q` (اختياري): للبحث عن كلمة في اسم أو وصف المنتج.
    -   `category` (اختياري): للفلترة حسب الفئة.
    -   `color` (اختياري): للفلترة حسب اللون.
    -   `minPrice` (اختياري): للفلترة حسب السعر الأدنى.
    -   `maxPrice` (اختياري): للفلترة حسب السعر الأقصى.
    -   `minYear` (اختياري): للفلترة حسب سنة الموديل الأدنى.
    -   `maxYear` (اختياري): للفلترة حسب سنة الموديل الأقصى.
    -   `page`, `limit` (اختياري): لتقسيم صفحات نتائج البحث.
-   **مثال:** `http://localhost:3000/api/products/search?q=cotton&minPrice=100&maxPrice=500&category=mens-tshirts`

---

### 🆔 4. جلب منتج محدد بالـ ID
-   **Endpoint:** `GET /api/products/:id`
-   **الوصف:** يقوم بجلب بيانات منتج واحد محدد عن طريق الـ ID الخاص به.
-   **مثال:** `http://localhost:3000/api/products/1`
-   **مثال لـ ID غير موجود:** `http://localhost:3000/api/products/9999`

---

### 🗂️ 5. جلب المنتجات حسب الفئة

##### **التيشيرتات (T-Shirts) - 25 منتج**
-   **النوع:** تيشيرتات صيفي وشتوي وسويت شيرت.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-tshirts`

##### **القمصان (Shirts) - 25 منتج**
-   **النوع:** قمصان رسمية وكاجوال.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-shirts`

##### **البناطيل (Pants) - 20 منتج**
-   **النوع:** بناطيل جينز، كاجوال، ورسمية.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-pants`

##### **البدل (Suits) - 15 منتج**
-   **النوع:** بدل رسمية كاملة.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-suits`

##### **الجواكت والمعاطف (Jackets & Coats) - 20 منتج**
-   **النوع:** جواكت شتوية ومعاطف.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-jackets-coats`

##### **الأحذية (Shoes) - 10 منتج**
-   **النوع:** أحذية رسمية وكاجوال.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-shoes`

##### **الأحذية الرياضية (Sneakers) - 10 منتج**
-   **النوع:** أحذية رياضية من ماركات عالمية.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-sneakers`

##### **الشباشب والصنادل (Slippers & Sandals) - 15 منتج**
-   **النوع:** شباشب وصنادل للاستخدام اليومي.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-slippers-sandals`

##### **الإكسسوارات (Accessories) - 25 منتج**
-   **النوع:** أحزمة، محافظ، ساعات، وإكسسوارات أخرى.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-accessories`

##### **الجلابيات (Galabeya) - 20 منتج**
-   **النوع:** جلابيات رجالي تقليدية وعصرية.
-   **الرابط:** `http://localhost:3000/api/products/category/mens-galabeya`

##### **تيشيرتات الأندية (Football Jerseys) - 20 منتج**
-   **النوع:** تيشيرتات أندية كرة قدم عالمية ومحلية.
-   **الرابط:** `http://localhost:3000/api/products/category/football-jerseys`

##### **المعدات الرياضية (Sports Equipment) - 20 منتج**
-   **النوع:** شورتات، أحذية كرة قدم، وشرابات رياضية.
-   **الرابط:** `http://localhost:3000/api/products/category/sports-equipment`

##### **إكسسوارات كرة القدم (Football Accessories) - 20 منتج**
-   **النوع:** كرات، أعلام أندية، وشنط رياضية.
-   **الرابط:** `http://localhost:3000/api/products/category/football-accessories`

---

### 📊 6. إحصائيات المنتجات
-   **Endpoint:** `GET /api/products/stats`
-   **الوصف:** يعرض إحصائيات مفصلة عن جميع المنتجات.
-   **الرابط:** `http://localhost:3000/api/products/stats`

---

### 🌟 7. المنتجات المميزة
-   **Endpoint:** `GET /api/products/featured`
-   **الوصف:** يعرض منتجات مميزة مقسمة إلى: أحدث الموديلات، المنتجات الفاخرة، الوصلات الجديدة.
-   **الرابط:** `http://localhost:3000/api/products/featured`

---

### 🎲 8. منتجات عشوائية
-   **Endpoint:** `GET /api/products/random`
-   **الوصف:** يعرض منتجات عشوائية من جميع الفئات.
-   **Parameters:**
    -   `count` (اختياري): عدد المنتجات العشوائية المطلوبة. الافتراضي `5`.
-   **مثال:** `http://localhost:3000/api/products/random?count=10`

---

### 🔗 9. منتجات مشابهة
-   **Endpoint:** `GET /api/products/similar/:id`
-   **الوصف:** يعرض منتجات مشابهة لمنتج معين (من نفس الفئة).
-   **مثال:** `http://localhost:3000/api/products/similar/1`

---

### 🎨 10. فلترة متقدمة
-   **Endpoint:** `GET /api/products/filter`
-   **الوصف:** فلترة متقدمة مع إمكانية تطبيق أكثر من فلتر في نفس الوقت.
-   **Parameters:**
    -   `category` (اختياري): الفئة (يمكن تحديد أكثر من فئة مفصولة بفواصل).
    -   `minPrice`, `maxPrice` (اختياري): نطاق السعر.
    -   `color` (اختياري): اللون (يمكن تحديد أكثر من لون مفصولة بفواصل).
    -   `model` (اختياري): سنة الموديل.
    -   `sortBy` (اختياري): طريقة الترتيب (price, model, title).
    -   `sortOrder` (اختياري): اتجاه الترتيب (asc, desc).
-   **مثال:** `http://localhost:3000/api/products/filter?category=mens-tshirts,mens-shirts&minPrice=100&maxPrice=500&sortBy=price&sortOrder=asc`

---

### 💰 11. فلترة حسب نطاق السعر
-   **Endpoint:** `GET /api/products/price-range/:range`
-   **الوصف:** فلترة المنتجات حسب نطاق سعر محدد.
-   **القيم المتاحة:** `budget`, `mid`, `premium`, `luxury`
-   **مثال:** `http://localhost:3000/api/products/price-range/mid`

---

### 🎨 12. فلترة حسب اللون
-   **Endpoint:** `GET /api/products/color/:color`
-   **الوصف:** فلترة المنتجات حسب اللون.
-   **مثال:** `http://localhost:3000/api/products/color/black`

---

### 📈 13. ترتيب المنتجات
-   **Endpoint:** `GET /api/products/sort`
-   **الوصف:** ترتيب المنتجات حسب معيار معين.
-   **Parameters:**
    -   `by` (اختياري): معيار الترتيب (price, model, title).
    -   `order` (اختياري): اتجاه الترتيب (asc, desc).
    -   `category` (اختياري): الفئة المحددة للترتيب.
-   **مثال:** `http://localhost:3000/api/products/sort?by=price&order=desc&category=mens-tshirts`

---

### 📋 14. قائمة الفئات
-   **Endpoint:** `GET /api/categories`
-   **الوصف:** يعرض قائمة بجميع الفئات المتاحة مع عدد المنتجات في كل فئة.
-   **الرابط:** `http://localhost:3000/api/categories`

---

## 📝 أمثلة للاستخدام

### **لعمل متجر ملابس رجالي:**
```javascript
// الصفحة الرئيسية
const featured = await fetch('http://localhost:3000/api/products/featured');

// صفحة الفئة
const tshirts = await fetch('http://localhost:3000/api/products/category/mens-tshirts');

// صفحة المنتج
const product = await fetch('http://localhost:3000/api/products/15');

// البحث
const search = await fetch('http://localhost:3000/api/products/search?q=cotton&page=1&limit=12');