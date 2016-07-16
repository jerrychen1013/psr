# PSR
PSR整理 
  
#PSR-1  基本Coding標準(Basic Coding Standard) 
##1. PSR-1 總覽    
1. Files 務必(MUST)使用`<?php`或`<?`標籤
2. Files 內的PHP code務必(MUST)使用無BOM的UTF-8
3. Files 最好(Should)只用以宣告某物（例如物件、方法、常數）或賦值（例如產生輸出、改變ini設定），但最好不要(Shouldnot)同時做這兩件事
4. Namespaces 和 classes 務必(MUST)按照PSR:[PSR-0, PSR-4]的autoloading規範
5. Class名稱務必(MUST)以大寫開始駝峰命名(StudlyCaps)法來命名
6. Class常數務必(MUST)以全大寫命名，若以2個以上字命名，則以底線(underscore)分開之
7. Method名稱(MUST)以小寫開始駝峰命名法(camelCase)

##2. Files  
###2.1 PHP標籤
  >Files 務必(MUST)使用`<?php`或`<?`標籤 
###2.2 字元編碼
###2.3 賦值(Side Effects)


