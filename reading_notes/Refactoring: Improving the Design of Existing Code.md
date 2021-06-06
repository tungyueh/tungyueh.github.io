# Refactoring: Improving the Design of Existing Code
## Chapter 1. Refactoring, a First Example
* 舉例比起原則更人讓人了解該如何應用而不向原則把事情弄得太通用
### The Starting Point
* 複製貼上 code 的問題在於之後需要修改的時候
* 當需要加功能的時候發現不好加就要先改成好加的樣子再加功能
### The First Step in Refactoring
* 需要有測試避免犯錯
* 用一行指令快速跑完所有測試，refactoring 過程會常常重複這個動作
* 測試要能顯示正確或失敗才不用花時間看到底結果如何
* 因為 refactoring 依賴於測試所以花時間去建立一個好的測試是很重要的
### Decomposing and Redistributing the Statement Method
* 從過長的部分拆解成小部分以便後續流程
* 目標是把新增功能的 duplicate code 減少
* 每次改一點點發現錯誤可以很快找到錯誤
* 任何人都可以寫出電腦懂得 code 但是只有好的 programmer 才有辦法寫出讓人懂得 code
#### Extract Method
* 找出有複雜邏輯的地方使用 Extract Method 
* 錯誤的 extract 會造成 bug 所以需要注意拿些地方可能會出錯
* 檢視準備修改的片段在 method 的 local variable
    * 沒被修改的可以當成 parameter 傳進去
    * 會被修改的如果只有一個可以回傳回去
* Extract 出來的 method 可以改變裡面 variable 賦予更有意義的名字讓 code 更清晰
#### Move Method
* 發現 method 沒使用到該 class 的資料代表放錯 class，使用 Move Method 移到適合的 class
* 移到合適的 class 可以少掉 parameter，可以重新命名 method
* 原本的 class 的 method 的 body 換成從新 class 拿到資料
* 找出所有舊的 method 替換成從新 method
* 如果舊的 method 是 public 可以留著保持該 class interface 不變
#### Replace Temp with Query
* Temp variable 在 refactoring 之後不會變動就可以移除
* 每次要用到值就去問
* Temp 通常需要傳來傳去，容易讓人迷失在該數值如何變化，在 long method 造成的影響更大
* 雖然改成去問的方式會需要每次重新計算但因為變成更小的部分之後優化會更容易
### Replacing the Conditional Logic on Price Code with Polymorphism
* switch statement 不要用其他人的東西當做 key，用自己的東西
* 不同的種類對於回答問題有不同的方式就可以用 subclasses
* 可以用 polymorphism 替換掉 switch statement
### Final Thoughts
* Extract Method, Move Method, Replace Conditional with Polymorphism 都是讓責任分散到更適合的地方所以更容易維護
* Refactoring 的節奏就是測試跟改一點的不斷循環
## Chapter 2. Principles in Refactoring
### Defining Refactoring
* 以名詞來解釋為更改內部架構以獲得更好理解或更容易修改但不影響外在行為
* 以動詞來解釋為用一連串的改變在不影響外在行為下重新架構軟體
* Reforing 雖然是清理 code 的行為但以更有效率、產生更少 bug、可控制的情況下清理 code
* Refactoring 是為了讓程式更容易理解跟修改，與其相反的是 performance optimization 是為了速度而讓程式變複雜
* Refactoring 不改變外在行為，軟體照常提供相同功能
#### The Two Hats
* 加新功能不改變現有的 code，藉由增加測試後讓測試通過當作進度
* Refactor 不增加新功能，只有 restructure code，不增加任何測試
* 開發軟體需要時常在上面兩種活動切換
* 加新功能的時候發現如果改變架構比較好加就該換帽子，改變架構完再換帽子開始加新功能，加完新功能發現不好懂就就繼續換帽子，開發過程中要隨時注意是戴哪頂帽子
### Why Should You Refactor?
* Refactoring 只是個工具而不是萬靈藥，是為了某些目的所使用的工具
#### Refactoring Improves the Design of Software
* 程式不 refactor 只會隨著時間變差，當改變 code 就會讓 code 失去原有的結構也就違背當初設計的目的
* 設計不好的 code 用了更多 code 做相同的事情，因為在不同地方都用不同 code 相同的事情，越多的 code 越難改對、需要越多時間讀懂，所以要讓設計更好就是要去除 duplicate code，讓未來的修改更容易，確保程式只在一個地方做一件事情
#### Refactoring Makes Software Easier to Understand
* 寫 code 就只是告訴電腦該做什麼事，用這種方式代表只用 code 跟電腦溝通，但除此之外還會有人看懂 code 後去修改，我們在乎能快速的修改好而不在乎電腦多跑一點 cycle
* Refactoring 能夠運作的 code 但沒有好的架構可以讓 code 更容易理解，用這種方式代表用 code 表達意圖
* 通常需要修改自己的 code 就是自己，能夠把需要知道的東西放在 code 裡面就不需要記太多東西
* Refacotring 幫助理解不熟悉的 code，讓 code 能更符合自己的理解，然後使用測試檢查所理解的東西是否正確
* Refactoring code 幫助我們排除細節更容易理解更高階的設計
### Refactoring Helps You Find Bugs
* 對於 code 了解程度越高則越容易找到 bugs，藉由 refacotring 慢慢對 code 認識越深，驗證之前的假設，bug 就會浮現出來
* 有著良好寫 code 習慣的 programmer 才是好的 programmer
#### Refactoring Helps You Program Faster
* Refactoring 顯而易見的可以增加軟體品質，但好像會讓開發速度變慢?
* 好的設計是快速開發的條件，如果沒有好設計一開始雖然會很快但之後常常需要修 bugs 而不是開發新功能，花更多時間理解系統找出 duplicate code 做修改，做新功能需要寫更多 code 來不斷 patch
* Refactoring 讓系統的設計不會毀壞，保持好的系統設計才能保持開發速度
### When Should You Refactor?
* Refactoring 不應該獨立時間出來而是存在於開發過程中，當決定要 refactor 代表要做些別的事情
#### The Rule of Three
* 第一次就直接做，第二次做相似的事情雖然知道會產生 duplicat code 但就這樣，第三次又遇到就該 refactor
#### Refactor When You Add Function
* 最常 refactor 的時候是要加入新 function 的時候，如果需要了解 code 在做什麼就 refactor 成更好理解的狀態，下次遇到就更容易理解
* 當發現目前設計不好加入新功能就思考該如何設計才比較容易加入新功能，藉由 refactoring 修正設計讓之後擴充更容易，這也是最快速的方法
#### Refactor When You Need to Fix a Bug
* 修正 bug 的 refactoring 是為了讓 code 更好理解
* 當發現 bug 代表 code 不夠清晰以至於沒發現 bug
#### Refactor As You Do a Code Review
* Code review 讓知識得以傳遞到整個 team，讓有經驗的人傳授知識給比較沒有經驗的人，讓人檢視寫的 code 對於 team 是否 clean，讓大家幫忙提供更好的想法
* Review 別人的 code 時給意見需要知道是否可以簡單做出來，可以自己試著先 refactor 讓 code 處在於給建議很容易理解的狀態，建議不再需要想像才能知道而是直接看見，再來可能又有第二層的想法跳出來。
* Refactoring 幫助 code review 有更實際的成果，而不只是建議而已
* 找一個 reviewer 跟作者一起 coding 由 reviewer 提供意見一起決定是否好 refactor
* 大一點的 design 應該要找多個人提供意見，使用 UML diagram 然後用 CRC cards 跑過不同情況
#### Why Refactoring Works
* 只做好今天的事情而不考慮未來則無法做未來的事情
* 發現之前錯誤的決定就該改變決定
* 為何寫程式這們難?
    * 越難讀懂得程式越難修改
    * 有 duplicated login 的程式很難修改
    * 程式加新功能需要動到之前的 code 會很難修改
    * 程式有複雜邏輯會很難修改
* 程式簡單易懂，所有邏輯都集中在一個地方，不允許修改現有 code 去影響行為，讓複雜邏輯簡單表達是我們所想要的
* Refactoring 是讓程式增加價值的過程，雖然沒有改變行為但是確保的品質可以維持開發速度
### What Do I Tell My Manager?
* 可以由品質或 review 的方式說服使用 refactoring
* 或者不用說因為怎麼做事是 programmer 的方式，refactoring 可以增加開發軟體或修正 bug 速度也剛好符合 manager 目標
### Problems with Refactoring
* 當新學到的工具可以大幅增加效率就很難知道什麼時候不該使用，因為尚未遇到不適合使用的情境所以無法得知
* 使用 refactoring 關注進度來判斷 refactoring 有沒有問題，然後找出解法或者知道該問題不適合使用 refactoring
#### Databases
* 很多商業邏輯都會跟 DB 綁再一起，所以很難 refactoring，另外一點是改變 schema 需要做 migration
* Nonobject databases 可以在 object model 跟 database model 加一層隔離，當改變其中一個 model 就不需要動到另外一個，雖然增加複雜度但是也增加彈性
* Object databases 改變 class 的 data structure 需要特別注意，可以移動行為但是移動 field 要注意
#### Changing Interfaces
* Object 好處在於在 interface 之內的實作都可以改變而不影響行為但是改變 interface 則什麼都可能發生
* Rename method 是一種簡單的改變 interface 的例子
* 改變 interface name 只要找出所有用到的地方一起改名字就可以但是有些無法找到跟改變的 code 就只能用更複雜的方式，這類 interface 稱為 published interface
* Refactoring published interface 需要讓新舊 interface 並存，讓舊 interface 的實作改由呼叫新 interface
* 盡量不要 published interface，團隊合作可以用 code base 來避免 publish interface
#### Design Changes That Are Difficult to Refactor
* 設計本身很難靠 refactor 來解決
* 先思考換設計是否很簡單，如果很簡單即是尚未滿足潛在的需求還是可以做 refactor，如果很困難則專注於設計
#### When Shouldn't You Refactor?
* Mess code 重寫可能比 refactor 好但目前沒有好的判斷方式
* Code 本身就有錯誤則就可以直接重寫，Refactor 前提是 code 是正確無誤的
* 先用 refactor 把系統分成許多部份，之後看要重寫還是 refactor 這些部分
* Deadline 之前不要 refactor 因為得到的效益只會在之後才顯現，適當的累積技術債也是維持功能正常的方式，需要好好管理債務避免被壓垮
* 時間常常不夠用是個需要 refactoring 的訊號
### Refactoring and Design
* Refactoring 可以補充設計的不足，先設計好再寫 code 可以減少 rework 的時間，設計可能存在很多缺漏
* Refactoring 可以是 upfront design 的替代品，先寫出來在 refactor 成形，這種方式也能夠寫出設計的很好的 code，但不是最有效率的方式
* 先設計好合理的版本後再去 refactor，可以減少設計一次到位的壓力
* Refactor 提供不斷嘗試解法的方法，每當想出一個解法會對於問題更加了解
* 為了能夠應付未來的變動會設計的很有彈性，但也變得難維護，也不一定用的上
* Refactoring 改變對於 change 評估，一樣可以假想可能的變動跟彈性的設計，但要思考是否可以從簡單的設計 refactor 成複雜且有彈性的設計，如果很容易就先做簡單的就好了
* Refactoring 可以讓我們使用簡單設計但不犧牲彈性，讓設計過程更簡單更沒有壓力，當需要改變時再 refactor 成彈性的設計就好
### Refactoring and Performance
* Refactoring 可能會造成速度變慢但是 refactoring 之後才比較好調整效能問題
* 在 hard real-time system 把使用時間用預算制分配給不同部分
* 每個 programmer 都要努力把速度提高，但通常運作不起來因為為了速度會讓系統複雜度提高之後開發就會變慢，可以增加速度的地方到處散佈所以改善某些地方只會改善整體一點點
* 通常最花時間的 code 只會集中在一小部分，在其他部分改善都是浪費時間而且讓系統更難懂
* 先不管速度只讓系統 well-factored 等到需要優化的時候再來調整
* 使用 profiler 找出花最多時間的部分，修改後重新用 profiler 量測，如果沒有改善就 revert，直到有改善為止
* Well-factored 系統讓我們更快速加入調整的 function，可以更精準找出花時間的地方因為 profiler 會幫助找到小的區塊
* 雖然一開始花比較多時間 refactoring 但之後比較好優化最終還是更快完成優化
### Where Did Refactoring Come From?
* 好的 programmer 會時常去清理 code 因為 clean code 比起 messy code 更容易修改
## Chapter 3. Bad Smells in Code
* 需要知道開始跟結束 refactoring 的時機跟知道如何 refactoring　一樣重要
* 沒有很明確的規則主要靠一些不好的 code structure 來判斷
### Duplicated Code
* 找一個一致的方法來處理重複出現的 code structure
* 同一個 class 有兩個 method 是同樣的 expression 可以使用 Extract Method 讓兩個 method 從同一個地方呼叫
* 同一個 expression 存在不同的 subclass 可以先使用 Extract Method 後再使用 Pull Up Field
    * Expression 有相似的地方先使用 Extract Method 把同樣跟不同的地方方開在使用 Form Template Method
    * 做同樣事情但使用的 algorithm 不同可以使用 Substitute Algorithm
* Duplicate 發生在不同 class 使用 Extract Class 抽出來後兩個 class 使用這個 class
### Long Method
* 舊的語言呼叫 subroutine 會有 overhead 但現代 OO 語言沒有這個問題，剩下是讀 code 的人需要跳來跳去但 IDE 可以幫忙消除這個問題，但重點是只要名字取的夠好就不需要去看內容
* 積極的分解 method 當想要註解的時候用寫一個新 method 取代，把需要註解的 code 放在 method 而名字用意圖而不是實際行為，目的是消除語意與行為的落差
* Method 使用很多參數跟暫存變數，在 extract method 過程中就不需要這麼多參數與暫存變數，利用 Replace Temp with Query 消除暫存變數，利用 Introducce Parameter Object 跟 Preserve whole object 消除多參數
* 還是有很多參數跟暫存變數的話可以使用 Replace Method with Method Object
* 藉由註解找出可以 extract 的地方因為註解代表想消除 code 跟目的的落差
* Conditional 跟 loop 可以用 Decompose Conditional
### Large Class
* Class 做太多事情會表現在 instance variable 過多，也會導致 duplicate code 的發生
* 使用 Extract Class 把相關聯的 instance variable 綁在一起，如果有相同的 prefix 或 suffix 可以使用 Extract Subclass
* 決定 client 如何使用 class 可以使用 Extract Interface
* GUI Class 需要保持 duplicate data 在不同地方的時候可以使用 Duplicate Observed Data 
### Long Parameter List
* 之前傾向需要的東西都用傳進去，這樣做是因為如果不傳進去就只能靠 global data 而 global data 更不好，但現在有了 object 所以 method 可以自己去拿需要的東西
* 長參數很容易隨著需要更多的東西而改變而且也難以理解，但只要改成 object 就可以不用這麼常改變
* Replace Method with Method 就可以從 object 得到需要的東西，Preserve Whole Object 讓呼叫的人可以從 object 拿到需要的資料，Introduce Parameter Object 把沒有邏輯的相關資料放在一起形成 object
* 如果不想增加 dependency 則不該做 refactoring，要思考 dependency structure
### Divergent Change
* 我們希望讓軟體容易修改，快速找到需要修改的地方然後修改
* class 修改太過頻繁需要使用 Extract Class 把跟修改原因有關的東西拉出來
### Shotgun Surgery
* 需要改動很多個不同的 class 這樣容易找不到需要修改的地方
* Move Method 跟 Move Field 把改變的地方集中到 class ，使用 Inline Classes 把相關行為聚在一起
### Feature Envy
* 當 method 需要從其他 class 取得值代表 method 應該使用 Move Method 移到那個 class，或者只有一部分的 method 就可以用 Extract Method 再來用 Move Method
* 當從多個 class 取得資料則把移到使用最多 data 的 class，可以先用 Extract Method 把 method 變小比較好移
* 有些設計會打破規則像是 Strategy 或 Visitor，可以依據把東西放在一起後再改的原則，
### Data Clumps
* data 通常都會成群使用像是 class 的某些 field，parameter list 常常都一樣，可以先用 Extract Class 把 data 放在一起，再把 method signatue 用 Introduce Parameter Object 或 Preserve Whole Object 減少 parameter 個數
* 思考如果將其中一個 data 移出 clump 則剩下的 data 是否還有意義
* 減少 field list 跟 parameter list 可以移除 bad smells，利用 feature envy 找出可以移到新 class 的 data
### Primitive Obsession
* Record types 讓我們能把資料組成有意義的 group，Primitive types 是 building blocks
* Object 可以讓 primitive 跟 larger class 的界線連結模糊
* 新手使用 object 會抗拒小的 object，但這些小的 object 可以集中管理相關的資料，
    * 使用 Replace Data Value with Object 把有自己行為跟相關聯的 data 放到另外一個 class 增加可讀性跟容易維護
    * 使用 Replace Type Code with Class 把沒有行為的相關聯 data 集中在另一個 class 讓 type hint 能幫忙早點檢查到錯誤
    * 使用 Replace Type Code with Subclasses 或 Replace Type Code with State/Strategy 當 type code 有用在 conditional 上
* 當 array 存了不同種類的東西要使用 Replace Array with Object 減少有人放錯種類到 array 導致失敗，減少找出問題的時間
### Switch Statements
* Object-oriented code 特色是很少 switch statement，switch statement 問題是散落在各處，需要修改時要找出所有的地方，而 object-oriented 的 polymorphism 可以幫助解決這個問題
* 當看到 switch statement 就應該考慮 polymorphism
    * Switch statement 沒有用 type code 時候則用 Extract Method 把 switch statement 拆開，用 Move Method 移到需要的 class
    * Switch statement 有用 type code 的時候使用 Replace Type Code with Subclasses or Replace Type Code with State/Strategy
    * 最後使用 Replace Conditional with Polymorphism
* 如果 switch statement 不常改動可以用 Replace Parameter with Explicit Methods
* 如果條件判斷需要 null 則用 Introduce Null Object
### Parallel Inheritance Hierarchies
* 當新增 subclass 的時候都需要在另外一個繼承關係也新增 subclass，可以藉由 class 的 prefix name 跟其他繼承的一樣找到
* 先讓其中一個繼承關係的 instance 參考另一個，再用 Move Method 跟 Move Field 就可以讓 subclass 消失
### Lazy Class
* 新增的 Class 都需要花時間去維護，所以如果 class 的能力不值得以一個 class 存在則應該被消除
* 有可能是因為 refactoring 過度或者不再預期內的更改
* Subclasses 做得事情不到 class 的程度則用 Collapse Hierarchy 移除
* 使用 Inline Class 把不需要的 class 的東西移出來
### Speculative Generality
* 為了之後可能的需求設計 hook 或 special cases 但可能之後都不會用到只是白白增加複雜度
* 使用 Collapse Hierarchy 把 abstract class 移除，使用 Inline Class 把 delegation 移除，使用 Remove Parameter 把沒用到的 parameter 移除，使用 Rename Method 把名字從通用改成更實際
* 症狀是 method 只在測試被使用，把這些 method 刪除跟相關測試移除
### Temporary Field
* 有時候 object 的 instance variale 在特定情形才有，這樣很不容易理解因為我們預期 object 應該要使用到所有變數
* 使用 Extract Class 把獨立的變數跟相關的 method 放到新的 class，可以用 Introduce Null Object 把 conditional code 處理好
* 通常是因為不想把變數傳來傳去所以放在 field 但這個 field 只在某段計算過程有意義，其他時間只是徒增困惑，這時候可以用 Extract Class 來把這些變數跟 method 包裝起來，只在需要的時候使用，這種稱為 method object 
### Message Chains
* Client 會問 object 來找到另外一個 object 如此反覆，代表 client 跟找尋的架構綑綁再一起了，只要當中斷掉就會影響 client
* Hide Delegate 讓 class 新增一個 method 直接呼叫另外的 class，可以對每個 chain 的 class 的這樣做但很有可能變成 Middle Man
* 觀察 object 被用來做什麼，使用 Extract Method 把用到的 code 用 Move Method 移到該 method
### Middle Man
* Encapsulation 把細節隱藏，通常透過 delegation 來做到
* 有時候太過頭會發現 class 有一半以上的 method 都是 delegating 其他 class，這時候要使用 Remove Middle Man 讓人直接與 object 溝通，如果 class method 做不多事情就用 Inline Method，如果有額外的行為使用 Replace Delegation with Inheritance 把 middle man 變成 subclass
### Inappropriate Intimacy
* Classes 有時候太過親近導致需要花很多時間釐清 private 的部分
* Move Method 跟 Move Field 可以減低 classes 之前的關係
* 看是否可以使用 Change Bidirectional Association to Unidirectional
* Classes 都想要某些東西把這些東西用 Extract Class 集中
* 使用 Hide Delegate 讓 class 當中間人
* Replace Delegation with Inheritance 當 classes 有很多簡單的 method 都在 delegate 其他 class 
### Alternative Classes with Different Interfaces
* Rename Method 把不同的 class 但做同樣事情的 method 換成一樣的名字
* 不斷使用 Move Method 把行為移到 classes 直到都相同
* Extract Superclass 把相同的部分變成 superclass 原本的變 subclass
### Incomplete Library Class
* Reuse 通常是 object 的目的但不應該過度相信也不否認，因為我們還是很依賴於 library
* Library 的作者通常不知道使用者需要什麼但使用者也無法改 library
* Introduce Foreign Method 在我們只需要一些 method 可以使用
* Introduce Local Extension. 在想要更多行為可以使用
### Data Class
* Classes 只有 field 跟 getting 跟 setting method 很容易被拿來做太多關於內部細節的動作
    * 有 public field 應該要用 Encapsulate Field 變成 private 再用 access method 讀取避免其他人直接修改 field
    * 有 collection field 使用 Encapsulate Collection 讓 getter method 回傳的是 read-only 然後不能用 setter method對 collection field 直接改變，改用 add 跟 remove
    * Field 不可改變則使用 Remove Setting Method
* 觀察其他 class 怎麼使用 data class 把相關行為用 Move Method 搬進 data class，無法直接移動用 Extract Method 新增一個在移動，最後開始 Hide Method 把 getter 跟 setter 隱藏起來
* Data class 一開始沒有行為沒關係但隨著行為變多應該要慢慢給予責任
### Refused Bequest
* Subclasses 不想繼承所有 parent 的東西
* 使用 Push Down Method 跟 Push Down Field 把只有該 subclass 用的東西從 parent 移進來，讓 parent 只剩下 common 的東西
* 本來都會用繼承後用一部分的行為而已所以看到這種不一定需要 refactoring，只有在造成困惑跟問題才需要修改
* 如果 subclass 不支援 superclass 的 interface 就需要使用 Replace Inheritance with Delegation 來修正
### Comments
* Comment 讓我們離 bad code 更接近，refactoring 完就會發現 comment 是多餘的
* 如果需要 comment code block 在做什麼則使用 Extract Method 給這段 code 一個 method，如果還是需要 comment 則使用 Rename Method
* 需要解釋規則則使用 Introduce Assertion
* Comment 適合用在不知道該怎麼做的時候，或者說明為什麼要這樣做
## Chapter 4. Building Tests
* Refactor 之前要確保有健全的測試
* 好的測試可以幫助寫 code 就算不是在 refactoring 也是一樣，雖然有點不直覺但接下來會解釋
### The Value of Self-testing Code
* 大部分真正寫程式的時間只佔開發的一小部分，主要都需要先搞清楚要做什麼然後設計，大部分的時間都在找 bug 在哪邊，找到 bug 就可以很快修好
* Class 應該都要有測試來測試自己
* 測試要能直接顯示結果正確與否減少確認的時間
* 測試要能輕鬆的跑就可以頻繁的跑，當開發過程出現 bug 就可以知道是因為剛剛寫的 code 所導致的，因為記憶猶新的關係所以很容易找到 bug，所以測試變成一個很好的 bug detector
* 說服其他人寫測試很困難因為需要多寫 code，除非可以明顯改善開發效率
* 開發功能要先寫好測試，測試可以幫助釐清目的、專注於 interface、知道目開發是否完成
### The JUnit Testing Framework
* Assert 是自動檢測結果的方法
* 時常跑測試
* 測試速度要快不然會不想測試
* 讓測試錯誤訊息淺顯易懂
* 先故意讓測試失敗藉此知道有測試到想要的部分
#### Unit and Functional Tests
* Unit test 只是幫助維持生產力，只測試自己的 class 的 interface
* Functional tests 確保軟體的行為正確，提供品質保證不管生產力，應該要由別的 team 撰寫
* Functional test 把整個系統當黑盒子，只使用公開出來的方式測試，只觀察 ouput data 的變化
* 當找的 bug 應該要有 unit test 讓 bug 顯現出來再去修正確保該 bug 不會再出現
### Adding More Tests
* 測試是為了找出問題所以要對風險較高的部分增加多一點的測試，簡單的部分不容易有問題所以不用有測試
* 要求寫完整的測試會讓人不想寫測試，寫測試只是為了確保擔心的部分會不會出錯，所以只要寫能有效率幫助的測試就好
* 測試要注重 boundary condition 因為這是最容易出錯的地方
* 特殊的情況也要特別測試
* Exceptions 也需要被測試
* 測試需要持續更新，測試幫助釐清 error condition 跟 boundary condition
* 找出風險在哪邊，看看複雜的部分然後思考可能出現的問題，雖然測試無法找出所有 bug 但 refactor 後理解會增加可以找到更深層的 bug
* Object 的 inheritance 跟 polymorphism 的組合多樣性造成測試的難度，先測試獨立的找出大部分的問題
* 測試 code 可以複製，之後再來找到 common 的部分 refactor，可以快速產生測試就好
* 使用測試建立 bug detector 然後頻繁的跑可以為開發帶來很大的幫助
## Chapter 5. Toward a Catalog of Refactorings
### Format of the Refactorings
* Refactoring 會有五個部分
    * 從 refactoring 方式的名字開始，這樣才有能夠建立起 refactoring 的詞彙
    * 介紹造成需要 refactoring 的情況跟如何 refactoring
    * Refactoring 的動機，介紹該 refactoring 跟不要的情況
    * 如何一步一步做 refactoring
    * Example 介紹 refactoring 如何作用
* Summary 包含對於問題的介紹跟提供大概如何 refactoring
* Mechanics 介紹如何 refactoring，提供簡潔的步驟，有需要再去看 example 的解釋
* 盡可能使用越小幅度的修改，但實際使用可以稍微大一點的幅度遇到問題才縮小幅度
### Finding References
* 使用電腦搜尋出所有要 refactoring 的 method 的 references
* 不要無腦搜尋取代，要思考是否正確的取代掉
* Strong typed language 可以故意把 feature 移除讓 compile 找出 dangling reference，但這個方法有壞處
* Compiler 可能會找的很慢，可以先用文字搜尋再用 compiler 重複確認
* Compiler 找不到 reflection API
### How Mature Are These Refactorings?
* Refactoring 的基本概念是一次修改一點然後不斷測試
* 知道自己正在 refactoring 並根據情況採用合適的技巧
* Refactoring 的方法只適用於 single-process，其他系統例如 concurrent 跟 distributed programming 有不同的方法
* Desing Patterns 是 refactoring 的目標，透過 refactoring 從其他地方有條理的變成期望的 pattern
## Chapter 6. Composing Methods
* 大部分 refactoring 是重組 method 讓 code 放在適當的地方，大部分的問題出在 method 太長所以隱藏太多資訊在複雜的邏輯之下
    * Extract Method 把一部分的 code 獨立成自己的 method
    * Inline Method 把 method 換成 method body，當 Extract Method 太過頭使 method 失去身為 method 的責任的時候可以使用
* Extract Method 最大問題是 local variable 跟 temps
    * Replace Temp with Query 可以移除掉大部分的 temps
    * 如果 temp 用在很多地方則可以使用 Split Temporary Variable
* 有時候 temporary variables 太過糾纏則可以使用 Replace Method with Method Object 來處理，藉由多一個 class 的代價讓我們可以處理複雜的 method
* Parameter 如果有 assign 則使用 Remove Assignments to Parameter
* 當 method 足夠簡單就可以使用更好的 algorithm 去改善，使用 Substitute Algorithm
### Extract Method
* 把 fragment 變成 method 然後用名字表達意圖
#### Motivation
* 當 method 太長或有 comment 解釋意圖就會用 Extract Method
* 命名良好的短 method 可以讓其他人更容易使用，形成 high level 的 method 看起來就像一連串的註解，overriding 也很容易
* Method name 要能夠縮短於 method body 的距離讓人更清楚該 method 的意圖
#### Mechanics
* 建立一個新 method 使用意圖來命名而不用實際做的事情
* 從 source method 複製 extracted code 到 target method
* 掃過一遍 extracted code 在 source method 的 local scope 有使用到的變數，這些要變成 target method 的 local variable 跟 parameter
* 查看是否有任何 temporary variable 在要 extract 的 code 中，把它宣告在 target method
* 查看 extracted code 是否有改變 local scope 的變數，如果有則查詢 extracted code 在 assign 回變數，如果有很多變數先使用 Split Temporary Variable 後再試一遍，再來使用 Replace Temp with Query 刪除 temporary variables
* 把 local-scope variable 當成 parameter 傳進 target method
* 把在 source method 的 extracted code 用 target method 取代
* 測試
### Inline Method
* Method body 已經足夠清楚表達 method name 就可以直接把 method body 放進 caller 然後移除該 method
#### Motivation
* 使用 method 比較不直接當 method body 已經足夠表達用意就可以移除，不然只是很煩人而已
* Inline Method 使用在發現有一堆 method 被分散，先將所有 method inline 後再去 extract，通常在 Replace Method with Method Object 之前很適合使用
* 當有人用太多 indirection 而 method 都只是 delegation 其他 method 讓人容易迷失，這時候就會用 inline method 把有用的留下沒用的刪除
#### Mechanics
* 檢查 method 不是 polymorphic 因為無法 inline subclasses overrided method
* 找出所有呼叫的地方
* 把呼叫的地方換成 method body
* 測試
* 移除 method
### Inline Temp
* 如果 temp 只有被簡單的 expression assigned 一次則用 expression 取代 temp
#### Motivation
* Inline Temp 通常是 Replace Temp with Query 的一部分，如果 temp 只有被 method call assigned 值可以先不用管，但如果需要 extract method 則要先 inline
#### Mechanics
* 宣告 temp 是 final 確保只被 assigned 一次
* 找出所有 temp 使用 right-hand side assignment 取代
* 測試
* 移除 temp 宣告跟 temp 的 assignment
* 測試
### Replace Temp with Query
* 如果使用 temp 存 expression 的結果，把 expression 變成 method，把所有 temp 都換成 expression，之後新的 method 就可以被其他 method 用了
#### Motivation
* Temps 的問題是暫時的跟 local，因為只有該 method 裡面才看的到所以容易造成 long method，換成 query method 就可以讓其他 method 使用把 code 變得整齊
* Replace Temp with Query 是 Extract Method 之前重要的一步，因為 local variable 會很難 extract 所以盡可能把 variable 換成 queries
* 如果 temp 只有被 assigned 一次而且產生 expression 結果沒有 side effect 就很簡單，其他比較複雜的需要先做 Split Temporary Variable 或 Separate Query from Modifier 讓 refactoring 變簡單一點，如果是透過 loop 收集結果需要把複製一些邏輯進去 query method
#### Mechanics
* 找出只被 assigned 一次的 temps，如果有被多次 assigned 先使用 Split Temporary Variable
* 宣告 temp 為 final
* Compile
* 把 assignment 的 right-hand side 變成 method
    * 先把 method 宣告成 private
    * 確認 method 沒有 side effects，如果有需要使用 Separate Query from Modifier
* Compile and test
* 使用 Replace Temp with Query
* Temp 通常用來儲存 loop 的結果，loop 可以 extract 成 method
* 效能問題等到實際發生再說，如果把 code factored 好也容易精準的優化
### Introduce Explaining Variable
* 把複雜的 expression 結果放進一個 temps 然後名字解釋目的
#### Motivation
* 太複雜的 expression 會難以解讀，temps 有幫助於管理這些 expression
* Introduce Explaining Variable 藉由良好命名的 temps 解釋 conditional logic 的目的
* 如果可以用 Extract Method 就用，因為 temp 只在單一 method 有用，method 可以讓整個 object 或其他 object 都使用
#### Mechanics
* 宣告 final temporary variable 然後把 expression 一部分結果存下來
* 用 temp 把 expression 的部分邏輯取代掉，如果有多個一次換一個
* 編譯跟測試
* 繼續 expression 的其他部分
### Split Temporary Variable
* Temporary variable 被 assign 不只一次，但不是 loop variable 或 collecting temporary variable
#### Motivation
* Temporary variable 用來做很多事，有些天生就是會被 assign 很多次例如 loop variable 或用來收集資訊
* 大多數 temporaries 是用來存下結果讓很多 code 可以使用，應該只能被 assign 一次，因為被 assign 多次就違反 SRP，使用 temp 代表不同事情很讓人混淆
#### Mechanics
* 把 temp 的名字換掉
* 把新名字的 temp 宣告成 final
* 把第二個 assignment 之前所有 reference 到的 temp 換成新名字
* 宣告第二個 assignment 的 temp
* 編譯跟測試
* 重複執行
### Remove Assignments to Parameters
* 使用 temporary variable 取代 assigns 給 parameter
#### Motivation
* 對傳進的 object 使用本來的 method 是可以的但不要換成另外的 object
* 對於 pass by value 或 pass by reference 會容易混淆
* 讓 paramter 保持不變比較清楚
#### Mechanics
* 為 parameter 建立 temporary variable
* 把 parameter 的 reference 都換成 temporary variable
* 把 assignment 從 paramter 換到 temporary variable
* 編譯跟測試
### Replace Method with Method Object
* Long method 有用到許多 local variable 所以無法用 Extract Method
* 把 method 變成 object 讓 local variable 都變成 object 的 field，之後可以慢慢分離 method 
#### Motivation
* 小的 method 讓我們能夠把事情表達的更清楚
* Method 有用到很多 local variable 讓分解變難可以先使用 Replace Temp with Query，如果不行最後才使用 Replace Method with Method Object
* 使用 Replace Method with Method Object 把 local variable 都變成 object 的 field 之後就容易使用 Extract Method
#### Mechanics
* 建立新的 class 名字取的跟 method 一樣
* 新的 class 建立 final field 給在 source object 的 field，建立 field 給 temporary variable 跟 method 的 parameter
* 新的 class 的 constructor 使用 source object 跟每個 parameter
* 新的 class 建立 compute method
* 複製原本的 method body 到 compute method，使用 source object field 
* 編譯
* 把舊的 method 換成 new object 然後呼叫 compute
### Substitute Algorithm
* 換一個更簡潔的演算法
#### Motivation
* 當有不同種方式可以達成目的就應該使用最簡單的一種，當 refactoring 把複雜東西變成簡單的片段都會有極限，到這個時候只能整個將 algorithm 取代換成更簡單的
* 想要用不同 algorithm 做點不同的事情要先從簡單的開始取代
* 先把 method 分解成簡單的再換掉 algorithm，因為要換掉複雜的 algorithm 很不容易
#### Mechanics
* 準備另外的 algorithm 並編譯成功
* 用新的 algorithm 跑過所有測試
* 若結果不同則比較與舊的 algorithm 有何不同