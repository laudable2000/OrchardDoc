
سفارشی سازی تم 
تم پیشفرض اورچارد تم Machine نامیده می شود.به گونه ای طراحی شده است که نقطه شروع برای سفارشی سازی و توسعه تم جدید است .
در این مقاله تم Machine معرفی و نشان می دهد که چگونه شما می توانید تم خود را بر اساس (Site.css) تم Machine ایجاد و سفارشی کنید.



معرفی تم Machine
تم Machine یک پایه (Base) قدرتمند و انعطاف پذیر را فراهم می آورد. تصویر زیر ساختار فایل تم Machine  را نشان می دهد. 



![](../Upload/screenshots/ThemeMachine_structure.PNG)
فایل های  که قلب تم Machine هستند طرح صفحه بندی (Layout.cshtml) و استایل صفحه (Site.css). می باشد


بررسی اجمالی صفحه آرایی
با شرایط متفاوت در صفحه آرایی مناطق مختلفی تعریف شده است.  این عبارات شرطی محتوای هر قسمت را مشخص می نماید. اگر محتوای برای آن منطقه اختصاص داده نشود در صفحه آن قسمت نمایش داده نمی شود..
تصاویر زیر مناطق تعریف شده در طرح بندی صفحه را نشان می دهد.


![All the zones in The Theme Machine](../Attachments/Anatomy-of-a-theme/TheThemeMachineZoneScreenshot.PNG)

 
به طور معمول با استفاده از پنل مدیریت می توان محتوا برای مناطق انتخاب شده قرار داد.

# Overview of the CSS Styles
بررسی اجمالی CSS Styles


The style sheet (Site.css) for the Theme Machine provides an extensive set of styles for fine-grained control of the look and feel of your website. The style sheet groups styles to make it easier for you to locate a style that you want to customize. The following table shows the groupings and describes the type of styles available to you.

صفحه استایل (Site.css) برای تم Machine مجموعه گسترده ای از  استایل ها را برای کنترل وب سایت از لحاظ دیداری . صفحه استایلها شرایط راحت تری را برای سفارشی کردن تم فراهم می نماید. جدول زیر توضیح می دهد انواع استایل های که برای شما وجود دارد.

Grouping  | Description
--------- | ------------------------------------------------------------------------------------------------------------
General   | Contains the default styles for the body, headings, lists, and text elements.
Forms     | Contains styles related to HTML forms, such as **form**, **legend**, **fieldset**, **label**, and **input**.
Structure | Contains page layout styles for each of the zones defined in the Theme Machine.
Main      | Contains styles defined for blog posts, comments, tagged search, and search results.
Secondary | Contains additional layout styles for secondary content in aside zones, tripel zones, and footer quad zones.
Widgets   | Contains styles for selected widgets such as the search widget, edit-mode widgets, and content mode.
Pager     | Contains styles related to a pager shape.
Misc      | Contains styles for miscellaneous formatting, such as small, large, quiet, and highlight.

# Creating a Child Theme
You can create your own theme by customizing the Theme Machine. However, you should not edit the Theme Machine files directly. Instead, you should create a child theme and copy any files that you intend to change into the child theme. You don't need to copy any files that you do not intend to change -- a child theme inherits from its parent theme, and overrides just the files from the parent theme that you have customized.  When your child theme is active as the current theme, Orchard first looks to that theme to resolve files, and if not found, it will look to the parent (BaseTheme) to find the files instead (and so on... even your parent theme can have it's own parent).

ایجاد یک تم کوچک
شما می توانید با سفارشی کردن تم Machine تم خود را بسازید. به هر حال نباید مستقیما هیچ کدام از فایلهای تم Machine را ادیت نمایید. برای ایجاد یک تم باید فایلها تم را کپی نمایید و تغییرات را بر روی آن فایلها اعمال نمایید. 
لازم نیست فایلهایی که نیاز به تغییر ندارند را کپی نمایید یک تم زیر مجموعه ارث بری می کند از تم  و فقط  که تغییر داده اید   overrides نمایید. وقتی که شما تم خود را فعال می نمایید. اورچارد فایلها را resolve  می کند و اگر فایلی پیدا نکرد به تم مادر نگاه می کند برای ارث بری به عنوان تم مادر. 


The process of creating a child theme is this:

1. Generate the child theme's code structure using the command-line CodeGen utility.
2. Copy the files you want to change from the Theme Machine to your child theme.
3. Edit the files in the new child theme.
4. Apply the new theme to your website.


## Generating the Theme Structure
To generate the code structure for your new theme, we are going to use the **Code Generation** feature, which can be obtained from the **Gallery** > **Modules** page in the admin panel.  Once you have installed and activated the code generation feature, you will be able to generate a new theme from the Orchard command-line.  Refer to the [Using the command-line interface](Using-the-command-line-interface) topic if you need to know more about using commands in Orchard.

Open the Orchard command-line utility and enter the following command:

    
    codegen theme MyTheme /BasedOn:TheThemeMachine


If you are using Visual Studio for editing (or if you plan for your Theme to eventually contain code files too), you may also want specify the CreateProject and IncludeInSolution options as follows:

    
    codegen theme MyTheme /BasedOn:TheThemeMachine /CreateProject:true /IncludeInSolution:true



This line tells Orchard to create the code structure for a new theme, sets the name of the theme to _MyTheme_, and directs Orchard to base the theme on _TheThemeMachine_. The CodeGen command generates the following folder structure:

![](../Upload/screenshots/NewTheme_structure.PNG)

The only files created are the Theme.txt and Views\Web.config files. The Theme.txt file (the theme manifest) is where the Admin Panel looks for information such as the name of the theme.  This is also where your BaseTheme is specified. Web.config is a configuration file that ASP.NET MVC requires for rendering any views placed in the Views folder. You seldom have to make changes in the Web.config file. 


## Copying Files from the Theme Machine
To keep this example simple, the only file you will customize will be the Site.css file. Copy the Site.css file from TheThemeMachine\Styles folder to the MyTheme\Styles folder.

Currently, you must also copy the TheThemeMachine\Views\Layout.cshtml file to the MyTheme\Views folder. (It's anticipated that this step will not be required in later releases.)


## Customizing Theme Files
After copying the files you want to customize into your new theme folder, you can make changes to those files. You can also create new files as needed. In this example, the only change you will make is the background color for the body of the page. 

In the Site.css file that you copied, find the **body** style in the **General** section. Then change the background color from **#fff** to **#fff8dc** as shown in the following example:

    body { 
      font-size: 81.3%;
      color: #434343;
      background: #fff8dc; 
      font-family: Tahoma, "Helvetica Neue", Arial, Helvetica, sans-serif;
    }
This will change the background color to cornsilk, which is a light yellow.

You can also provide a thumbnail image of your new theme in the theme's root folder. The image file must be named Theme.png. The image will be displayed in the Admin Panel to help users select a theme.

The following image was copied from TheThemeMachine and changed to show the light-yellow background color. 
![](../Upload/screenshots/NewTheme_thumbnail.PNG)

## Applying Your New Theme
In the Admin Panel, under **Site Design**, select **Themes**. The **Manage Themes** page is displayed, and the new theme is listed under **Available Themes**:


![](../Upload/screenshots/themes_available.png)Click **Set Current**. The **Manage Themes** page is redisplayed showing **MyTheme** as the current theme.

You can now go to your website to see the new theme in action. 
