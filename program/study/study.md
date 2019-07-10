#讀書會分享
    https://github.com/104corp/104jb-c-CTeamKnowHow/wiki


### 1. Yii  1.1

   * 程式架構
      
        [Model-View-Controller](https://www.yiiframework.com/doc/guide/1.1/en/basics.mvc)
   ```     
    Application Life Cycle
        When handling a user request, an application will undergo the following life cycle:
        
        1.  Pre-initialize the application with CApplication::preinit();
        
        2.  Set up the error handling;
        
        3.  Register core application components;
        
        4.  Load application configuration;
        
        5.  Initialize the application with CApplication::init()
             *   Register application behaviors;
             *   Load static application components;
        6.  Raise an onBeginRequest event;
        
        7.  Process the user request:
             *   Collect information about the request;
             *   Create a controller;
             *   Run the controller;
        8.  Raise an onEndRequest event;
    ```
### 2. Slim 3 

   * 程式架構
   
        [Slim](http://www.slimframework.com/docs/v3/concepts/life-cycle.html)
   
        [Middleware](http://www.slimframework.com/docs/v3/concepts/middleware.html)
    
   * 套件介紹 
    ```
    "require":{
        "php": "^7.0",
        "codeception/codeception": "^2.5",
        "slim/twig-view": "^2.2",
        "slim/slim": "^3.9.0",
        "monolog/monolog": "^1.0",
        "hassankhan/config": "^2.0",
        "symfony/yaml": "^3.2",
        "swiftmailer/swiftmailer": "^6.0",
        "illuminate/database": "<5.7",
        "php-di/slim-bridge": "^2.0",
        "104corp/jblog": "^0.10",
        "symfony/cache": "^3.4",
        "symfony/dotenv": "^3.4"
    },
        "require-dev": {
        "squizlabs/php_codesniffer": "^2.8",
        "internations/http-mock": "^0.10",
        "phpunit/phpunit": "~4.0",
        "zircote/swagger-php": "^3.0"
    }
    ```
### 3. Laravel

   * 程式架構
   
        [Laravel](https://laravel.com/docs/5.8/lifecycle)


### 4. Free Talk
    工具、工作...等分享

### 5. AWS

   * [案例分享](https://aws.amazon.com/tw/getting-started/use-cases/?awsf.getting-started-content=use-case%23websites-apps)
   


### 參考學習文件

##### 程式設計概念
   * [PHP PSR規範](https://psr.phphub.org/)
   * [PHP 5.6.x 移植到 PHP 7.0.x](https://www.php.net/manual/zh/migration70.php)
   * [clean code 加上 物件導向 SOLID 原則](https://learnku.com/laravel/t/7774/the-conciseness-of-the-php-code-php-clean-code)
   * [專案架構設計](https://juejin.im/entry/58c602da128fe100603d7145)
   * [架構設計準則](http://kejyun.github.io/Laravel-5-Learning-Notes-Books/design-pattern/design-pattern-model-coding-structure-principle.html)
   * [在 Laravel 4 使用資源庫 (Repositories) 及服務 (Services) 去降低程式的耦合性](https://kejyuntw.gitbooks.io/laravel-4-learning-notes/laravel-design-pattern/model/decoupling-your-code-in-laravel-using-repositiories-and-services.html)

##### MVC 介紹
   * [mvc](https://zh.wikipedia.org/wiki/MVC)
   * [淺談MVC共通架構](https://dotblogs.com.tw/greengem/2018/02/27/174454)
   看到這句「也可以在Model類別中定義函數來操作Model，例如新增、修改、刪除、查詢，這樣，controller 呼叫時會更方便。」就好
   * [認識 MVC](https://openhome.cc/Gossip/Spring/MVC.html)
   * [MVC 與 Rails](https://openhome.cc/Gossip/Rails/MVC.html)
   看到第二張圖
   * [UCenter的MVC架構](http://www.aspphp.online/bianchen/wangye/php/phprm/201701/135751.html)
   看圖
   * [MVC相關圖1](https://www.google.com/imgres?imgurl=https%3A%2F%2Fi.stack.imgur.com%2FGvGPc.png&imgrefurl=https%3A%2F%2Fstackoverflow.com%2Fquestions%2F9608505%2Fzend-framework-current-route-in-bootstrap&docid=Ece04xls5MBZiM&tbnid=HRqswpN2qU-K4M%3A&vet=10ahUKEwj8hIfP05bjAhWPGqYKHeYeDX4QMwhBKAEwAQ..i&w=227&h=536&client=firefox-b-d&bih=722&biw=1536&q=zend%20lifecycle&ved=0ahUKEwj8hIfP05bjAhWPGqYKHeYeDX4QMwhBKAEwAQ&iact=mrc&uact=8)
   看圖
   * [MVC相關圖2](https://www.google.com/imgres?imgurl=https%3A%2F%2Fcdn-ak.f.st-hatena.com%2Fimages%2Ffotolife%2Fa%2Fallabout-techblog%2F20161107%2F20161107221435.png&imgrefurl=https%3A%2F%2Fallabout-tech.hatenablog.com%2Fentry%2F2016%2F11%2F29%2F100000&docid=O0bisci_qnS6PM&tbnid=FCoq29V2ynIg9M%3A&vet=10ahUKEwjrjZf01ZbjAhXJxosBHXAPBPgQMwhxKCYwJg..i&w=804&h=380&client=firefox-b-d&bih=722&biw=1536&q=service%20repository%20laravel&ved=0ahUKEwjrjZf01ZbjAhXJxosBHXAPBPgQMwhxKCYwJg&iact=mrc&uact=8)
   看圖
   * [如何組織優良的MVC架構](https://steemit.com/php/@linko-crypto/how-to-organize-your-project-with-php-and-laravel-to-get-the-best-structure-in-mvc-pattern)
   
   