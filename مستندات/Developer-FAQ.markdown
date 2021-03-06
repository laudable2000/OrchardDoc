## What are the dependencies?
Orchard uses a number of external libraries. They can all be found under \lib directory in your enlistment, as well as are enumerated in [Orchard dependencies and libraries](Orchard-dependencies-and-libraries).

وابستگي ها چيست ؟
اورچارد از تعدادي کتابخانه خارجي استفاده مي کند . که مي توان تمامي آنها را در فولدر /lib در شاخه مربوطه پيدا کرد همچنين مي توان از لينک رو به رو آنها را پيدا کرد : [Orchard dependencies and libraries](Orchard-dependencies-and-libraries).

## What framework versions does Orchard support?
Up to version 1.7 Orchard supports .NET 4.0. As of version 1.8, Orchard is going to run on .NET 4.5 and IIS 7 (or newer).

اورچارد چه ورژن از framework را پشتيباني مي کند ؟

اورچارد از ورژن 1.7 با بالا قابليت پشتيباني از .NET 4.0 و از ورژن 1.8 اورچارد قادر به پشتيباني از .NET 4.5 و IIS 7(يا جديدتر( است .

## What are the master and 1.x branches? Which one should I be using?
شاخه های ورژن 1.x  و تنه ی اصلی چیست ؟ کدامیک را بهتر است استفاده کنم ؟
Those are the 2 branches corresponding to trunk (master) and development (1.x). 

All the active feature work is being done by the core team in the 1.x branch.
Whenever a new release is ready, changes get merged from 1.x to master.
Master is a stable branch and is normally always in a "green" state.
This should be the branch you would ideally work with.
1.x is the most recent branch in terms of activity but it can at times be unstable due to ongoing work.
Everything in 1.x in terms of the public surface is also more volatile: APIs can be changed at will and daily,
making a potential external contributor working on the branch more difficult.
For these reasons, it is advised to use master for your development purposes, and 1.x only if you're interested
in checking out how brand new features are being developed.
در اینجا 2 بخش که مربوط به  تنه ی اصلی و توسعه  (1.x) وجود دارد . تمامی خصوصیات پویای کار توسط تیم اصلی در بخش 1.x  انجام شده است . هروقت که یک ورژن جدید منتشر شده آماده باشد تغییرات با تنه ی اصلی ادغام داده می شود.
تنه ی اصلی یک بخش پایدار است و در حالت عادی همیشه در وضعیت سبز است . این در حالت عادی بهترین بخش برای شما برای کار کردن است . 1.x  آخرین ورژن از نظر کارهای انجام شده است ولی در حال حاضر ممکن است به دلیل کارهای در حال پیشرفت ناپایدار باشد. همچنین همه چیز در 1.x   در سطح عمومی راحت تر است . API ها میتوانند به درلحظه ی تمایل و روزانه تغییر کنند ، ایجاد بستر مشارکت بلقوه ی خارجی جهت کار بر روی نسخه ی نماینده بسیار سخت تر می باشد.  در حالت کلی پیشنهاد می شود که از نسخه ی اصلی استفاده شود و اگر خیلی مشتاق بودید که ببینید ورژن های 1.x چگونه توسعه پیدا می شوند.

## What types of extensions can I write?
 چه افزونه هایی می توانم بنویسم ؟
Orchard Modules and Themes are supported extensions today. Note that the module and themes API is a work-in-progress, and although it's possible to build these extensions today, you should expect changes that may break extensions built on the current codebase. Regular MVC 2 Areas are also supported as modules. 
ماژول های اورچارد و پوسته هایش امروزه افزونه های پشتیبانی شده هستند . در نظر داشته باشید که API  ماژول ها و پوسته ها یک کار در حال انجام شدن است و اگرچه ساختن این افزونه ها امکان پذیر است ، شما بهتر است  که تغییرات احتمالی در ساختار را در نظر داشته باشید . هرگونه فضایی در MVC 2 به عنوان ماژول نیز پشتیبانی می شوند .

## Where are Modules physically located?
ماژول ها کجا هستند ؟
The projects in the "Modules" folder are physically located under the "src\Orchard.Web\Modules" folder. This allows modules to contain ASP.NET views (aspx, ascx) and static content without having to copy files between projects to be able to run the project.
پروژه هایی که در فولدر ماژول قرار دارند در آدرس "src\Orchard.Web\Modules" قرار دارند . این به شما اجازه می دهد تا View(aspx, ascx)  و محتوای static  بدون داشتن کپی فایل ها بین پروژه ها تا قادر به راه انداختن پروژه باشیم . 

The Core modules are physically located under the "\src\Orchard.Web\Core" folder. 
ماژول های اصلی در آدرس  "\src\Orchard.Web\Core" قرار دارند .

## What is a Module.txt file?
فایل Module.txt چیست ؟
This is the module manifest. It has to be present at the root of the module's directory for Orchard to recognize it as a module and load it. It is a YAML-format file. Example module.txt with all possible supported fields:
این فایل حاوی مشخصات ماژول ما است . این فایل باید در روت فولدر ماژول قرار بگرد تا اوچارد ان را به عنوان ماژول تشخیص بدهد و آن را لود کند . دارای فرمت YAML  است .
به عنوان مثال یک module.txt  با تمام فیلد های پشتیبانی شده :
    
    name: AnotherWiki
    author: Coder Notaprogrammer
    website: http://anotherwiki.codeplex.com
    version: 1.2.3
    orchardversion: 1
    antiforgery: enabled
    features:
      AnotherWiki: 
        Description: My super wiki module for Orchard.
        Dependencies: Versioning, Search
        Category: Content types
      AnotherWiki Editor:
        Description: A rich editor for wiki contents.
        Dependencies: TinyMCE, AnotherWiki
        Category: Input methods
      AnotherWiki DistributionList:
        Description: Sends e-mail alerts when wiki contents gets published.
        Dependencies: AnotherWiki, Email Subscriptions
        Category: Email
      AnotherWiki Captcha:
        Description: Kills spam. Or makes it zombie-like.
        Dependencies: AnotherWiki, reCaptcha
        Category: Spam


## What is the AdminMenu.cs file?
AdminMenu.cs  فایل چیست ؟
This file has an implementation of the Orchard interface called INavigationProvider. It lets modules hook themselves into the admin menu in the backend. This is typically where you declare what links should your module inject into the Admin menu and what controller actions these links invoke.
این فایل پیاده سازی ای از اینترفیس اورچارد به نام INavigationProvider است. این اجازه می دهد که ماژولها خودشان را در پنل ادمین جا کنند . این معمولا جایی است که شما باید بیان کنید که کدام لینک از ماژول شما باید در منوی ادمین باشد و چه عملگر کنترلری این لینکها نیازدارند .


## What is the Permissions.cs file?
 فایل Permissions.cs چیست ؟
This file has an implementation of the Orchard interface called IPermissionProvider. It lets modules declare a set of permissions as well as attach those permissions to default Orchard roles. Once you add a new permission type to your module here, you will be able to use the Orchard authorization APIs to check that permission against the current user. You will also be able to manage which custom roles the permission belongs to in the Roles administration page.
این فایل دارای یک پیاده سازی از Orchard Interface به نام IPermissionProvider هست . این به ماژولهای شما اجازه می دهد که یک سری از دسترسی ها به دسترسی های اولیه ی ارچارد اضافه کرد . هنگامی که شما یک نوع دسترسی به ماژولتان اضافه می کنید ، شما قادر هستید که از Orchard authorization APIs استفاده کنید تا دسترسی یوزر هایتان را چک کنید . شما همچنین قادر هستید که در پنل مدیریت نقش به مدیریت کنید که کدام دسترسی به چه کسی تعلق دارد .


## How do I do authorization inside my module against current user/roles?
چگونه دسترسی به یوزر/نقش در ماژولم بدهم ؟
Orchard comes with a default services implementation of the IOrchardServices interface. Simply include IOrchardService in your constructor and you will get the default implementation injected. Like

اورچارد با یک سرویس اولیه که پیاده سازی ای از IOrchardServices interface است آمده است .
به راحتی IOrchardService را به constructor اضافه کنید و شما یک پیاده سازی اولیه اعمال کرده اید . به طور مثال :

    
    public AdminController(IMyService myService, IOrchardServices orchardServices) {
                _myService = myService;
                Services = orchardServices;
    }


At this point, services gives you Authorizer for authorization, Notifier for writing out notifications, ContentManager for access to the Orchard content manager and TransactionManager. At this point, to check if the current user has a certain permission, you would simply do:

در این مرحله سرویس ها به شما سرویس برای دادن درسترسی ،  اطلاع دهنده برای نوشتن اطلاعات ، مدیر محتوا برای دسترسی به محتوای مدیر اورچارد و مدیر تراکنش می دهد . در این مرحله برای چک کردن اینکه یوزر دسترسی های مورد نظر را دارد ، باید این کار را انجام دهید : 

    
    Services.Authorizer.Authorize(Permissions.SomeModulePermission, T("Some operation failed"));


## What are Core Modules?
ماژول های هسته ی اورچارد  چه هستند ؟
Core Modules are Orchard Modules you can find under \src\Orchard.Web\Core. They also constitute the Orchard.Core project in the solution. These are modules that are always enabled and come with the default Orchard installation. See "Why are Core modules modules?" and "Why are Core Modules Core Modules?" for more detailed information.

ماژول های هسته همان Orchard Modules هستند و شما می توانید آنها را در فولدر \src\Orchard.Web\Core پیدا کنید . اینها به علاوه شامل Orchard.Core Project نیز می شوند . اینها ماژول های هستند که همیشه فعال هستند و با اینستال اولیه ی اورچارد ریخته می شوند . برای اطلاعات بیشتر به سوال بعدی توجه کنید.

## Why are Core modules modules?
## چرا ماژولهای اصلی ماژول حساب می شوند ؟

The difference is similar to OS concepts of monolithic vs micro-kernel: it was pretty obvious during high level design of Orchard that an extensibility point such as modules was needed. Everything else would constitute the core framework. Take the Common module for example, which introduces the BodyPart, a core concept common to many types of content types, such as blog posts or pages. Now we could've implemented this as part of the Orchard framework dll, and have modules depend on it. But then it wouldn't get the benefit of being a module, such as being able to hook up handlers, drivers, views, routes etc. This also relates to MVC and areas, where everything that belongs to an area is under the same directory. It was pretty clear that the right choice was to get some core concepts out of the framework dll into a separate dll, and have them be modules. This is very similar to non-monolithic operating systems where parts of the core functionality is implemented as modules outside the kernel, talking to it via the same exact interfaces as the more higher level modules.
تفاوت مشابه است به مفاهیم OS  یکپارچه در مقابل micro-kernel : این بسیار مشهود است که در فرایند طراحی ارچارد یک نقطه ی قابل گسترش مانند ماژول نیاز مند هستیم . هرچیز دیگری جزو فریم ورک اصلی حساب می شوند. یک ماژول معمول را به عنوان مثال در نظر بگیرید ، که یک BodyPart ، یک مفاهیم معمولی به بسیاری از انواع داده ها به عنوان مثال پست ها یا صفحه های یک بلاگ. حال ما توانسته ایم این قسمت از فریم ورک ارچارد dll را پیاده سازی کنیم ، و ماژولهایی وابسته به آن داشته باشیم. ولی این نمی تواند مزیت های یک ماژول را داشته باشد ، به عنوان مثال قابلیت  کار با handlers , drivers, views, routes etc. این مربوط می شود به MVC و فضاها، هرجا که متعلق به یک فضا (area) باشد در بک فولد جای می گیرد . این خیلی مشهود است که

## Why are Core Modules Core Modules?
Now that we want core concepts to be implemented as modules, why not put them into the modules directory along with the rest of the more obvious Orchard modules, such as the comments module. Well, this time it's about dependencies. In Orchard, modules that are in the modules directory can be disabled, uninstalled or otherwise updated in a breaking way. We prefer modules that are self-contained and don't require other non-core modules as dependencies, as much as possible. That's part of the entire dynamism behind the content type architecture. Pages and Blog posts, which belong to Pages and Blog modules, don't reference Comments or Tags modules, but it's possible to attach comments or tags to pages and blogposts. This decoupled behavior is ensured by the underlying content type architecture and not by direct reference from one or the other modules. Core modules are part of the Orchard framework and it's ok for modules to depend on them. They will be distributed by us and for all practical purposes are integral parts of the Orchard framework. Modules can depend on them and directly access their public surface.

## How do I write and run tests?
## چگونه تست بنویسم و اجرا کنم ؟
Orchard comes with a solution folder called Tests. This hosts 2 types of tests:
ارچارد با یک فولدر راه حل به نام Tests آمده است . و 2 گونه از تست ها را پشتیبانی می کند :

* **Unit Tests**: These are NUnit test fixtures. To write a fixture for a module, simply create a new directory under Orchard.Tests.Modules and populate it with your tests. 
* **Unit Tests**: این ها لوازم NUnit تست هستند.  برای نوشتن یک تست برای یک ماژول ، به سادگی یک فولدر در زیر Orchard.Test.Modules میسازیم و تست خود را در آنجا می نویسیم
* **Integration Tests**: These are also NUnit tests, generated using SpecFlow ([http://www.specflow.org](http://www.specflow.org)) .feature files. Your integration tests would go under Orchard.Specs and there are a multitude of examples there you can look at if you are new to the BDD approach.  
* **Integration Tests**: این نیز جزو NUnit test, generated با استفاده از  ([http://www.specflow.org](http://www.specflow.org)) محصوب می شود .فایل های جانبی . تست های مختلط و ادغام شده در زیر Orchard.Specs می روند و در آنجا مثال هایی بسیاری وجود دارد که می توانید ببینید ، اگر به BDD approach جدید هستید.

Running the unit tests is a matter of right clicking the solution or appropriate project and choose Run Unit Tests.

> Note: this applies to writing tests for the modules that come with the standard source code distribution of Orchard. To write code for your own third-party modules, please work in your own separated directory. We will provide guidance on setting up a third-party module development environment.

## How do I contribute my changes to Orchard?
## چگونه به اورچارد کمک کنم ؟
Orchard is a community project and has a number of external contributors. To ensure the patch is accepted to Orchard, there are a few points to highlight:
اورجارد یک پروژه انجمن محور است و دارای تعدادی کمک دهنده خارجی است . برای اینکه مطمئن باشید patch شما مورد قبول اورچارد است باید تعدادی از قوائد را در نظر داشته باشید :

* **Code Conventions**: Orchard code conventions and style guidelines are explained in [Code conventions](Code-conventions). The source tree also contains a ReSharper ([http://www.jetbrains.com/resharper](http://www.jetbrains.com/resharper)) file at \src\Orchard.4.5.resharper that's going to considerably simplify you working with the Orchard conventions.
* **Code Conventions**:

* **Patch submission process:** Is detailed in [Contributing patches](Contributing-patches). Although .patch files are still supported as explained there, it is preferred to use forks and use the CodePlex UI to submit a pull request. For smaller changes patch files are also OK, however there is no CodePlex UI to manage them so you would have to attach them to bugs and hope they don't get lost. Also, always use the default branch for patches.

## How to build a WCF service that exposes Orchard functionality?

To host a WCF Service in Orchard, with all of its goodies coming from IoC you have to:

Create a SVC file for your service with the new Orchard Host Factory:

    
    <%@ ServiceHost Language="C#" Debug="true" 
    Service="Orchard.Service.Services.IService, Orchard.Service"
    Factory="Orchard.Wcf.OrchardServiceHostFactory, Orchard.Framework" %>


Register the service normally as an IDependency.

    
    using System.ServiceModel;
    
    namespace Orchard.Service.Services {
      [ServiceContract]
      public interface IService : IDependency {
        [OperationContract]
        string GetUserEmail(string username);
      }
    }


Provide implementation (i.e.: Service : IService).

## What's in App_Data?

The App_Data folder is used to store various kinds of data. Contents of App_data are never served. The contents are organized this way:

* File:**cache.dat** is a cache XML document describing what features are enabled for each tenant in the site. This being only a cache, modifying it may have unpredictable results.
* File:**hrestart.txt** is a file that is touched by the system to indicate a need to restart the application.
* Folder:**Dependencies** is used by dynamic compilation to store compiled dlls and has an XML file, dependencies.xml that tracks how each module was compiled (dynamically or not).
* Folder:**Exports** contains export XML files generated by the import/export feature.
* Folder:**Localization** contains localization po files.
* Folder:**Logs** contains log files.
* Folder:**RecipeQueue** is used during setup to queue the recipes to execute.
* Folder:**Sites** contains one folder per tenant. The default tenant is in the Default folder, which is all there is if no tenant was created. Each folder contains the following:
    * **mappings.bin** is a binary serialized cache of nHibernate mappings.
    * **Orchard.sdf** is the SQL CE database file for the tenant.
    * **reports.dat** is a legacy log file.
    * **Settings.txt** describes the low-level settings for the tenant (database provider, connection string, etc.)
* Folder:**Warmup** contains cached versions of pages generated by the warmup module, and a warmup.txt file that contains the timestamp for the last warmup file generation.

## Understanding bug status and triage

When you submit a bug, the team (or anybody subscribing to notifications) receives an e-mail. We do regular triage meetings with a small committee, sometimes as often as daily and usually at least once a week.

When we do triage, we make a query that returns all bugs in "Proposed" state, ordered by number of votes. This means that we are always looking at the most voted bugs first. If you care about a bug, you should vote for it, and it won't fall on deaf ears.

A bug that is still in "Proposed" state has not been triaged yet. When we look at a bug, several things can happen. We may close it if it doesn't reproduce, if it's by design or if it was fixed since submitted. We may ask for more information (and leave it in "Proposed" state). Or finally, we may move it to the "Active" bucket.

A bug that is in "Active" state has been triaged and should have been assigned a release. The release usually is one of the planned releases. Planned releases are usually the ones we are currently working on, plus a "Future Versions" release that we use for bugs and features that we want to handle but don't think we can do in the current cycle. The "Assigned to" field is only set when the bug is scheduled to be fixed in the current iteration or cycle. If it's in "Future Versions" it is usually unassigned.

Impact is usually set during triage but a "Low" value does not necessarily mean much: this is the default value so it might just mean that it hasn't been touched. It's OK to investigate with the team on the impact of a bug you care about.

## Developer Troubleshooting
##  عیب یابی توسعه دهنده

* **Record Names**: Your implementations of the ContentPartRecords shouldn't have properties that are known keywords to NHibernate. Examples include Identity, Version.
* 
* **Record Names**: پیاده سازی ContentPartRecords شما بهتر است که از کلمات رزرو شده Nhibernate نباشد ، به عنوان مثال Identity , Version.
* 
