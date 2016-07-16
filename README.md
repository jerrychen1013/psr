# PSR
PSR整理   
目錄    
  
#PSR-1  基本Coding標準(Basic Coding Standard) 
##1. PSR-1 總覽    
1. Files 務必(MUST)使用`<?php`或`<?`標籤
2. Files 內的PHP code務必(MUST)使用無BOM的UTF-8
3. Files 最好(Should)只用以宣告Symbols（例如物件、方法、常數）或賦值（例如產生輸出、改變ini設定）      
   但最好不要(Should not)同時做這兩件事    
    ```PHP     
    /**同時做宣告和賦值的範例*/  
    <?php   
        // 賦值(Side effect): change ini settings 
        ini_set('error_reporting', E_ALL);

        // 賦值(Side effect): loads a file
        include "file.php";

        // 賦值(Side effect): generates output
        echo "<html>\n";

        // 宣告Symbols
        function foo()
        {
            // function body
        }
        
        
    /**只做宣告而不賦值的範例*/      
    <?php
    // 宣告Symbols
    function foo()
    {
        // function body
    }

    // conditional declaration is *not* a side effect
    if (! function_exists('bar'))       
    {
            function bar()
        {
            // function body
        }
    }
    ```     
4. Namespaces 和 classes 務必(MUST)按照PSR:[PSR-0, PSR-4]的autoloading規範    
    ```PHP     
    // PHP 5.3(含)之後的版本
    <?php
        namespace Vendor\Model;

        class Foo
        {
        }       
        
    // PHP 5.2.x(含)之前的版本:
    <?php
        
        class Vendor_Model_Foo
        {
        }
    ```
5. Class名稱務必(MUST)以大寫開始駝峰命名(StudlyCaps)法來命名            
    ```PHP     
    // 範例
    <?php
    class Foo
    {
    }       
    ```
6. Class常數務必(MUST)以全大寫命名，若以2個以上字命名，則以底線(underscore)分開之   
    ```PHP     
    // 範例
    <?php
    namespace Vendor\Model;

    class Foo
    {
        const VERSION = '1.0';
        const DATE_APPROVED = '2012-06-01';
    }       
    ```
7. Method名稱(MUST)以小寫開始駝峰命名法(camelCase)




