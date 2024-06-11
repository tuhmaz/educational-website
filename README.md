# educational-website
README لمشروع الموقع التعليمي
مقدمة
هذا المشروع يهدف إلى بناء موقع تعليمي يحتوي على صفوف دراسية، مواد دراسية، فصول دراسية، ومقالات مرفقة بملفات تعليمية مختلفة. الموقع يدعم إدارة الأخبار وإعدادات الموقع، ويوفر واجهات للمستخدمين بناءً على أدوارهم (مدير، مشرف، عضو).

المتطلبات
PHP >= 7.4
Composer
Node.js و NPM
MySQL أو أي قاعدة بيانات تدعمها Laravel
إعداد المشروع
استنساخ المستودع

bash
Copy code
git clone https://github.com/username/educational-website.git
cd educational-website
تثبيت الاعتمادات باستخدام Composer

bash
Copy code
composer install
تثبيت الاعتمادات باستخدام NPM

bash
Copy code
npm install
نسخ ملف البيئة وتعديله

bash
Copy code
cp .env.example .env
php artisan key:generate
تكوين إعدادات قاعدة البيانات في .env

تشغيل الهجرات لإنشاء الجداول في قاعدة البيانات

bash
Copy code
php artisan migrate
بناء ملفات CSS و JavaScript

bash
Copy code
npm run dev
هيكلة الملفات
lua
Copy code
project-root/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Dashboard/
│   │   │   │   ├── GradeController.php
│   │   │   │   ├── SubjectController.php
│   │   │   │   ├── TermController.php
│   │   │   │   ├── ArticleController.php
│   │   │   │   ├── FileController.php
│   │   │   │   ├── NewsController.php
│   │   │   │   ├── UserController.php
│   │   │   │   ├── SettingsController.php
│   │   │   ├── Frontend/
│   │   │   │   ├── HomeController.php
│   │   │   │   ├── GradeController.php
│   │   │   │   ├── SubjectController.php
│   │   │   │   ├── TermController.php
│   │   │   │   ├── ArticleController.php
│   │   │   │   ├── NewsController.php
│   │   ├── Middleware/
│   │   ├── Requests/
│   │   └── Kernel.php
│   ├── Models/
│   │   ├── Grade.php
│   │   ├── Subject.php
│   │   ├── Term.php
│   │   ├── Article.php
│   │   ├── File.php
│   │   ├── News.php
│   │   ├── User.php
│   │   ├── Setting.php
│   ├── Providers/
│   │   ├── RouteServiceProvider.php
│   ├── Policies/
│   └── ...
├── config/
├── database/
│   ├── migrations/
│   │   ├── create_settings_table.php
│   │   ├── create_terms_table.php
│   ├── seeders/
│   └── factories/
├── resources/
│   ├── views/
│   │   ├── dashboard/
│   │   │   ├── grades/
│   │   │   │   ├── index.blade.php
│   │   │   │   ├── create.blade.php
│   │   │   │   ├── edit.blade.php
│   │   │   ├── subjects/
│   │   │   │   ├── index.blade.php
│   │   │   │   ├── create.blade.php
│   │   │   │   ├── edit.blade.php
│   │   │   ├── terms/
│   │   │   │   ├── index.blade.php
│   │   │   │   ├── create.blade.php
│   │   │   │   ├── edit.blade.php
│   │   │   ├── articles/
│   │   │   │   ├── index.blade.php
│   │   │   │   ├── create.blade.php
│   │   │   │   ├── edit.blade.php
│   │   │   ├── files/
│   │   │   │   ├── index.blade.php
│   │   │   │   ├── create.blade.php
│   │   │   │   ├── edit.blade.php
│   │   │   ├── news/
│   │   │   │   ├── index.blade.php
│   │   │   │   ├── create.blade.php
│   │   │   │   ├── edit.blade.php
│   │   │   ├── users/
│   │   │   │   ├── index.blade.php
│   │   │   │   ├── create.blade.php
│   │   │   │   ├── edit.blade.php
│   │   │   ├── settings/
│   │   │   │   ├── index.blade.php
│   │   ├── frontend/
│   │   │   ├── home.blade.php
│   │   │   ├── grades/
│   │   │   │   ├── show.blade.php
│   │   │   ├── subjects/
│   │   │   │   ├── show.blade.php
│   │   │   ├── terms/
│   │   │   │   ├── show.blade.php
│   │   │   ├── articles/
│   │   │   │   ├── show.blade.php
│   │   │   ├── news/
│   │   │   │   ├── show.blade.php
│   ├── js/
│   └── css/
├── routes/
│   ├── dashboard.php
│   ├── frontend.php
│   ├── web.php
│   ├── api.php
├── storage/
├── tests/
│   ├── Feature/
│   ├── Unit/
├── public/
│   ├── css/
│   ├── js/
│   ├── images/
│   └── ...
├── .env
├── composer.json
└── ...

الراوتر
ملف routes/web.php
php
Copy code
<?php

use Illuminate\Support\Facades\Route;
use App\Http\Controllers\Frontend\HomeController;
use App\Http\Controllers\Frontend\GradeController;
use App\Http\Controllers\Frontend\SubjectController;
use App\Http\Controllers\Frontend\TermController;
use App\Http\Controllers\Frontend\ArticleController;
use App\Http\Controllers\Frontend\NewsController;

Route::get('/', [HomeController::class, 'index'])->name('home');
Route::get('/grades/{grade}', [GradeController::class, 'show'])->name('grades.show');
Route::get('/subjects/{subject}', [SubjectController::class, 'show'])->name('subjects.show');
Route::get('/terms/{term}', [TermController::class, 'show'])->name('terms.show');
Route::get('/articles/{article}', [ArticleController::class, 'show'])->name('articles.show');
Route::get('/news/{news}', [NewsController::class, 'show'])->name('news.show');
ملف routes/dashboard.php
php
Copy code
<?php

use Illuminate\Support\Facades\Route;
use App\Http\Controllers\Dashboard\GradeController;
use App\Http\Controllers\Dashboard\SubjectController;
use App\Http\Controllers\Dashboard\TermController;
use App\Http\Controllers\Dashboard\ArticleController;
use App\Http\Controllers\Dashboard\FileController;
use App\Http\Controllers\Dashboard\NewsController;
use App\Http\Controllers\Dashboard\UserController;
use App\Http\Controllers\Dashboard\SettingsController;

Route::middleware(['auth:sanctum', 'verified'])->prefix('dashboard')->name('dashboard.')->group(function () {
    Route::resource('grades', GradeController::class);
    Route::resource('subjects', SubjectController::class);
    Route::resource('terms', TermController::class);
    Route::resource('articles', ArticleController::class);
    Route::resource('files', FileController::class);
    Route::resource('news', NewsController::class);
    Route::resource('users', UserController::class);
    Route::get('settings', [SettingsController::class, 'index'])->name('settings.index');
    Route::post('settings', [SettingsController::class, 'update'])->name('settings.update');
});
ملاحظات إضافية
إدارة الإصدارات: تأكد من استخدام Git لإدارة التغييرات في المشروع.
التوثيق: قم بتوثيق جميع الخطوات والإعدادات في ملفات README أو وثائق منفصلة.
الاختبارات: استخدم PHPUnit وPest لكتابة اختبارات وحدات واختبارات تكامل.
الأداء: استخدم التخزين المؤقت (Caching) لتحسين أداء التطبيق.
تصميم متجاوب: تأكد من أن الواجهة الأمامية متجاوبة وتعمل بشكل جيد على جميع الأجهزة.
الحماية: استخدم أفضل ممارسات الحماية في Laravel لحماية التطبيق.
التعاون: استخدم أدوات إدارة المشاريع مثل Trello أو Jira لتتبع التقدم.
إذا كنت مستعدًا، يمكننا البدء في تنفيذ المشروع خطوة بخطوة. دعني أعرف من أين تريد أن نبدأ!
