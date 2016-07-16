# PSR
PSR整理   
名詞：  
>MUST: 務必     
>MUST Not: 務必不要     
>Should: 最好       
>Should Not: 最好不要       
>MAY: 也許         
        
#目錄       
[PSR-1  基本Coding標準(Basic Coding Standard)](PSR-1  基本Coding標準(Basic Coding Standard))        
[PSR-2  基本Coding標準(Basic Coding Standard)](PSR-2  基本Coding標準(Basic Coding Standard))        
  
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
    namespace Vendor\Model;

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
    
#PSR-2  基本Coding標準(Basic Coding Standard) 
##1. PSR-2 總覽    
###檔案面(file)     
1.  Code務必(MUST)使用**4個空白(spaces)當縮排，而非tab**     
    >N.b.: Using only spaces, and not mixing spaces with tabs, 
    >helps to avoid problems with diffs, patches, history, 
    >and annotations. The use of spaces also makes it easy to insert fine-grained sub-indentation for inter-line alignment.
        
2.  File只包含PHP Code時，`?>`務必(MUST)刪除    
    >理由是`?>`後若有多出空白，會被瀏覽器解析        
3.  所有PHP files務必(MUST)使用Unix LF做行尾     
4.  所有PHP files務必(MUST)以一行空白做結尾
5.  每行Code的長度務必不要(MUST Not)有寫死(hard limit)的長度限制;    
    1. 軟性限制務必(MUST)在120字元內;   
    2. **每行最好(Should)不多於80個字元;**
6.  非空白行的行尾務必不要(MUST Not)有結尾空白格     
7.  空白行也許(MAY)可增加來促進程式碼可讀性和呈現Code的相關區塊       
8.  每行Code不要有多於一個陳述(statement)         
9.  PHP的true, false, null務必(MUST)要小寫       
10. Nampspace宣告和use宣告區塊的後面務必(MUST)要有一行空白
    ```PHP
    <?php
    namespace Vendor\Package;

    use FooClass;
    use BarClass as Bar;
    use OtherVendor\OtherPackage\BazClass;

    // ... additional PHP code ...
    ```
11. extends & implements務必(MUST)和class name宣告在同一行      
    ```PHP
    <?php
    namespace Vendor\Package;

    use FooClass;
    use BarClass as Bar;
    use OtherVendor\OtherPackage\BazClass;

    class ClassName extends ParentClass implements \ArrayAccess, \Countable
    {
        // constants, properties, methods
    }
    ```     
    **如果有多重interface要implements**, 所有interface前都要有一個縮排, 第一個interface要換行。     
    ```PHP
    <?php
    namespace Vendor\Package;

    use FooClass;
    use BarClass as Bar;
    use OtherVendor\OtherPackage\BazClass;

    class ClassName extends ParentClass implements
        \ArrayAccess,
        \Countable,
        \Serializable
    {
        // constants, properties, methods
    }
    ```         
    
###Class, Method, Property面
1. 所有屬性(Properties)和方法(Methods)都要宣告可視性(Visibility, 含public, protected, private);        
    ```PHP
    <?php
    namespace Vendor\Package;

    class ClassName
    {
        public $foo = null;
    }
    ```
2. 務必不要(MUST Not)使用`var`來宣告property 可視性    
    
    ~~var $foo;~~
    
3. 每個statement務必不要(MUST Not)宣告多於一個property      
4. Property名稱最好不要(Should Not)用一個底線做前綴來表示protected or private可視性        
5. Method名稱最好不要(Should Not)用一個底線做前綴來表示protected or private可視性      
6. Method名稱後務必不要(MUST Not)有一個空格           
7. Class和Method的左大括弧`{`和右大括弧`}`務必(MUST)要獨自為一行     
8. Method的左括弧`(`後務必不要(MUST Not)有空格；右括弧`)`前務必不要(MUST Not)有空格   
9. Method參數list中，每個**逗號後面**務必(MUST)要有一個空格；每個**逗號前面**務必不要(MUST Not)有一個空格

    ####6~9點範例     
    ```PHP
    <?php
    namespace Vendor\Package;
    
    class ClassName
    {
        public function fooBarBaz($arg1, &$arg2, $arg3 = [])
        {
            // method body
        }
    }
    ```

10. Method參數list也許(MAY)可斷行，若要斷行，每個參數(含第一個)務必(MUST)都要斷行並有一個縮排。     
    每行務必不可(MUST Not)有多於一個參數        
    ```PHP
    <?php
    namespace Vendor\Package;

    class ClassName
    {
        public function aVeryLongMethodName(
            ClassTypeHint $arg1,
            &$arg2,
            array $arg3 = []
        ) {
            // method body
        }
    }
    ```
11. abstract和final務必(MUST)在**可視性**之前宣告   
12. static務必(MUST)在**可視性之後**宣告        
    **11~12點範例**     
    ```PHP
    <?php
    namespace Vendor\Package;

    abstract class ClassName
    {
        protected static $foo;

        abstract protected function zim();

        final public static function bar()
        {
            // method body
        }
    }
    ```     
###呼叫Method or Function
1. Method or Function和括弧`()`之間務必不可(MUST Not)有空格
2. 左括弧`(`後不可有空格；右括弧`)`前不可有空格
3. 參數list中，逗號前務必不可(MUST Not)有空格；逗號後務必(MUST)有空格       
    **範例**        
    ```PHP
    <?php
    bar();
    $foo->bar($arg1);
    Foo::bar($arg2, $arg3);
    ```
4. 參數list可以斷行，每個參數(含第一個)都要斷行並有一個縮排     
    ```PHP
    <?php
    $foo->bar(
        $longArgument,
        $longerArgument,
        $muchLongerArgument
    );
    ```     
###控制結構(Control Structures)，例如if-else, switch, while     
1.  控制結構關鍵字(if, switch...)之後務必(MUST)要有一個空白
2.  左括弧`(`**後**務必不要(MUST Not)有一個空白
3.  右括弧`)`**前**務必不要(MUST Not)有一個空白
4.  左大括弧`{`和右大括弧`}`之間務必(MUST)要有一個空白；        
    左大括弧`{`之前務必(MUST)有一個空白;        
    左大括弧`{`和控制結構關鍵字要同一行;
5.  `{}`內的Code務必(MUST)要有一個縮排
6.  右大括弧`}`務必(MUST)要獨自一行
7.  **if, elseif, else**範例
    ```PHP
    <?php
    if ($expr1) {
        // if body
    } elseif ($expr2) {
        // elseif body
    } else {
        // else body;
    }
    ```
8.  **switch, case**範例
    ```PHP
    <?php
    switch ($expr) {
        case 0:
            echo 'First case, with a break';
            break;
        case 1:
            echo 'Second case, which falls through';
            // no break
        case 2:
        case 3:
        case 4:
            echo 'Third case, return instead of break';
            return;
        default:
            echo 'Default case';
            break;
    }
    ```
9.  **while, do while**範例
    ```PHP      
    <?php
    while ($expr) {
        // structure body

    do {
        // structure body;
    } while ($expr);
    ```
10. **for**範例
    ```PHP
    <?php
    for ($i = 0; $i < 10; $i++) {
        // for body
    }
    ```
11. **foreach**範例
    ```PHP
    <?php
    foreach ($iterable as $key => $value) {
        // foreach body
    }
    ```
12. **try, catch**範例
    ```PHP
    <?php
    try {
        // try body
    } catch (FirstExceptionType $e) {
        // catch body
    } catch (OtherExceptionType $e) {
        // catch body
    }
    ```     
###封閉性(Closures)
1. function後務必(MUST)有一個空格；use的前後務必(MUST)有一個空格
2. 左大括弧`{`務必(MUST)和function關鍵字同行；右大括弧`}`務必(MUST)獨自一行
3. 左括弧`(`後務必不要(MUST Not)有一個空格；右括弧`)`前務必不要(MUST Not)有一個空格
4. 參數list或變數list中的逗號前務必不要(MUST Not)有一個空格，逗號後務必(MUST)要有一個空格
5. 參數的預設值務必(MUST)放在參數list的最後一個        
    ```PHP
    <?php
    $closureWithArgs = function ($arg1, $arg2) {
        // body
    };

    $closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
        // body
    };
    ```
6. 參數list和變數list可以斷行，但每個參數或變數都要斷行(含第一個)並要縮排一次。每行只能有一個參數
    ```PHP
    <?php
    $longArgs_noVars = function (
        $longArgument,
        $longerArgument,
        $muchLongerArgument
    ) {
        // body
    };
    
    $noArgs_longVars = function () use (
        $longVar1,
        $longerVar2,
        $muchLongerVar3
    ) {
       // body
    };

    $longArgs_longVars = function (
        $longArgument,
        $longerArgument,
        $muchLongerArgument
    ) use (
        $longVar1,
        $longerVar2,
        $muchLongerVar3
    ) {
       // body
    };

    $longArgs_shortVars = function (
        $longArgument,
        $longerArgument,
        $muchLongerArgument
    ) use ($var1) {
       // body
    };
    
    $shortArgs_longVars = function ($arg) use (
        $longVar1,
        $longerVar2,
        $muchLongerVar3
    ) {
       // body
    };
    ```     
    7. 封閉性也可直接作為Method or Function的一個參數
    ```PHP
    <?php
    $foo->bar(
        $arg1,
        function ($arg2) use ($var1) {
            // body
        },
        $arg3
    );
    ```     
    
#PSR-3  Logger Interface 
##1. PSR-3 總覽(待續) 

 




