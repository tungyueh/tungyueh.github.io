# Code Complete Note

## Part I: Laying the Foundation
### Chapter 2: Metaphor of Software Development

很多偉大的發現是由聯想到不同事物所獲得的啟發，一個好的譬喻可以精準描述所要表達的意思，藉由譬喻也可以使人對於事物有更快速的理解，因為藉由已知的來連結未知的是人類所擅長的，工程師可以將問題已譬喻來描述他藉此來統合遇到的不同問題，之後遇到新的問題可以快速套用之前思考過的譬喻找出解決方式，而不是為這個問題設計出演算法後遇到新問題又繼續不斷重複流程而無法累積經驗，一個好的譬喻必定是可以從很多方面來對應也可以完美說明，像是一開始有人將寫程式比喻為寫信，稍微考慮一下就開始撰寫，寫好之後就放入信封寄送出不再變動，但寫程式是多人合作的項目而不是自己一個人的單打獨鬥，寫程式也不是有一個明顯的結束必須不斷維護跟修改，又有人將寫程式比喻像種田，必須不斷維護跟規劃，但寫程式不像種田一樣只要把種子放下去定期灌溉就可以等待豐收，於是乎人類將寫程式比喻成牡蠣生產珍珠的過程，一層一層的疊上去蛋白質以形成珍珠，最後最常比喻寫程式就像蓋房子一樣，有一開始的規劃，蓋什麼樣的房子，用什麼建材之類的，總之一個好的譬喻可以藉由多面向來驗證，善用好的譬喻可以事半功倍。

### Chapter 3: Measure Twice, Cut Once: Upstream Prerequisites

軟體開發流程由檢視需求開始，檢視完需求後根據需求打造架構，架構建立好之後開始設計，設計架構好就可以開始寫程式了。越前面階段發現缺陷所改動的成本可以越少，因此在打造軟體之前的準備工作是很重要的，如果再打造軟體途中才發現有缺陷可能會需要拋棄某些成果讓之前的工作浪費掉。身為軟體工程師需要教育老闆跟客戶我們打造軟體的流程跟解釋為什麼要花這麼多時間來準備而不是寫程式跟除錯，不只可以讓軟體界生態變更好也可以使接下來的工作更輕易的完成。
     首先要做的是釐清這個軟體需要解決的問題，需要把問題完整的描述清楚而不是直接提出可能的解法，以使用者的角度來描述問題而不是用工程師的思維來解決，有些問題可能是有更簡單的解決方法而不需要使用軟體來解決，
     問題列出後開始思考需求是什麼，列好需求不只可以幫助使用者更加了解自己需要解決的問題也可以幫助工程是在寫程式的過程中參考，不然工程師很容易在一邊寫程式的時候自己想需求造成爭吵，客戶如果想到有某些需求想要加入過改變必須擁有一套流程，幫助客戶冷靜思考跟提供改變所需要的成本以供客戶考量需求的重要性。雖然需求重要但還是要考量到需求是否真正為客戶帶來價值，不然單純的列出需求後沒有評估商業價值會讓許多需求都是白費工夫。
     需求決定後就可以開始來設計架構了，一個好的架構會將系統分成好幾個獨立的模組，每個模組都已定義好的功能跟輸出輸入，一個好的架構是簡單有條理的不能連工程師的覺得不合邏輯，一個好的架構可以針對每個需求都有一個解決方法，設計架構時不一定要將每一個模組都設計好這要能涵蓋 80% 的需求就可以了，

### Chapter 4:  Key Construction Decisions

每種語言都有不同的特性，根據需求來決定開發用的語言，組合語言的強項在提升效能而高階語言提供較多功能讓程式設計師使用，遇到問題時候要先自己思考該如何解決然後再思考如何使用該語言來實作，不然先想語言有提供哪些工具然後用這些工具來找出答案會容易讓人被語言所綁住，程式設計師應該是要使用語言而不是被語言所箝制住思考能力。

## Part II: Creating High-Quality Code
### Chapter 5: Design in Construction

Design 是個很困難的問題，不知道何時才算完成也不知道是否有完整思考過整個設計，所以 design 是一種推敲的過程，不斷重複思考來得出最好的方法。Design 最重要的是控制程式的複雜度，因為人類的腦袋不可能一次思考很多問題，只能專注在某一小部分上面，因為把複雜度降低讓人類得以專注於想要解決的問題上面，為了知道是否為好的設計可以從幾中指標來觀察
1. 最小化複雜度讓問題變得簡單而不是用很特殊的方法來解決，盡量保持所有的東西簡單且易懂
2. 讓程式易於維護，可以想像有人會不斷問你為什麼要這樣寫程式，這樣自然會把程式寫的好懂易於維護
3. 程式中的不同部分都盡量不相關，這樣改動某一部分的東西時候就可以不用考慮太多事情
4. 易於擴張
5. 可以重複利用程式碼
6. 一個 class 可以被很多人用到
7. 一個 class 用很少其他 class。 

Design 的流程為先將整體看過一遍大概要怎麼規劃，分成 sub system 後，在分成class，class 裡面會有 routines，對於每個部份要定義好功能，提供那些方法給其他人用，將那些資訊隱藏起來，若有類似功能可以用繼承的方法重複利用程式碼，對於可能變動的部分把這些隱藏起來，不要將實作寫在每個 class 裡面，不然之後做改動需要將每個 class 修改。可以利用 Design Pattern 來與其他人溝通減少說明設計的細節，也可以利用 design pattern 來作些許修改用來解決問題。Design 是不斷重複以上流程的行為，中途雖然會碰到錯誤的想法但可以從中學到東西進而在下次的 design 做得更好。

### Chapter 6: Working Classes

使用 Abstract data type (ADT) 將相關資料跟行為包裝起來，不僅可以降低複雜度也可以重複利用程式碼，還有隱藏實作細節、修改不必動到整個程式、集中化管理、程式本身就是文件的優點。一個好的 ADT 應該是所有 interface 都是是有關係，而且 interface 不能預設一些行為或者呼叫順序會有引響，不然使用的人都還要需要學習這些預設條件又會是複雜度上升。如果是 class 擁有的東西應該要用 containment，另外如果 class "是" 某個 class 時就可以使用 inheritance ，不需要再設計時就把 class 的繼承關係劃分得很細，目前需要什麼設計就要弄得簡單明瞭就可以了，還要注意只有一個 class 繼承的情形或者是 override function 卻不做事的情形，這時需要重新檢視設計。

### Chapter 7: High-Quality Routine
    
使用 routine 最大的好處就是可以降低複雜度，做好一個 routine 後使用者可以不用知道裡面的細節就得到需要的結果，routine 更可以為程式自我註解，只要 routine 的名字取的好就可以很輕易的看出在做什麼事，而不是需要花時間看懂這一坨 code 在做什麼，另外 routine 可以減少 code 的重複性跟修改優化只需要在這個 routine 做就可以而不是去修改散落在各地的 code。就算 routine 很小也不要因為心裡障礙就不去做，雖然此時很小但未來充滿不確定性，routine 建議的參數以不超過7個為準，routine 大小以大約一頁至兩頁作為準則。routine 名字通常是一個動詞搭配一個名詞，盡可能的將 routine 所做的事情濃縮在名字上，讓人可以一看名字就可以推測出 routine 的功能跟回傳的東西。

### Chapter 8: Defensive Programming

對於外部裝置給予的值需要檢查過後才繼續讓流程跑下去，如果發現不合法的值就立即警告並停止流程讓問題早點得到解決，不過一旦發現不合法的輸入時可以根據情形做出不同的回應，像是回傳正常的值、回傳上次的結果之類的。Assert 通常用於開發的時候，透過 assert 可以釐清 interface 跟 document，發生問題也可以早點排除，通常 Assert 是用於絕對不可能發生的情形，exception 用於不常發生的情形，當程式無法自己處理這個錯誤的時候可以 raise exception 期待有人可以幫助他解決，exception 必須符合自己的階層跟寫好原因，雖然 exception 會使複雜度提高但好好善用的話還是可以處理不少問題。但每次都必須檢查輸入的正確性是滿惱人的，所以可以將可信任跟不可信任的資料做分區，當資料從不可信任區流進可信任區時候必須做檢查，資料已經進入可信任區就不必再做檢查，通常從不可信任區到可信任區用 exception 的方式來處理，而可信任區中的流動是用 assert 的方式來處理，因為 assert 是不可能發生的情形，照理來說可信任區的資料一定是正確的所以用 assert 來處理。

### Chapter 9: The Pseudo-code  Programming Process

使用 pseudo-code 的好處是可以容易的讓別人 review 設計，寫好 pseudo-code 就等於寫好了文件。pseudo-code 不能綁定特定的語言，應該要通用到可以轉換成任何語言才是正確的。

## Part III: Variables
### Chapter 10: General Issues in Using Variables
    
變數要在使用之前才進行宣告跟出初始化，避免變數的 span time 跟 life time 太長造成程式的可讀性跟正確率降低，變數的 scope 也是也越小越好，從最小的範圍開始遇到必須擴大的時候想清楚後才能擴大，太早綁定變數與實際的數值會造成彈性變小，盡量越晚綁定越好，變數最好只有一個用途，不要用奇怪數字 -1 之類的數值表示異常狀態。

### Chapter 11: The Power of Variable Names

變數的名字是決定變數好壞的重要因素，賦予變數有意義的名字跟與本質相同可以讓人容易理解，盡量避免技術面的名詞反之使用描述問題本質的名字，將 total index first last 等等字詞放在變數的後面讓同一個變數有統一性，幫 boolean 變數命名時使用只有正面或反面意義的名字，例如 done, found ，避免使用像是 status 這種搞不清楚真假值的意思的名字。

### Chapter 12: Fundamental Data Types

避免使用 magic number, string, 因為使用特定的數字或字串代表某些意義會造成讓讀程式碼的人無法了解背後代表的意思降低可讀性，再者當需要改變 magic number 時候需要尋找所有用到此 magic number 的地方一一修改讓維護變得困難。

因為現在國際化的關係需要支援多種語言的需求，在設計一開始就需要考慮支援多種語言的情形。

妥善運用 Boolean 可以讓程式的可讀性提高，例如當需要判斷很多情況的時候可以用 boolean 變數代表判斷的意思，讓判斷式顯得很清楚。

Enum 可以讓 class 的 member 以英文描述，使用 Enum 可以增加程式碼的可讀性，還可以用在 function 需要回傳多種狀態的時候。

Array 是可以隨機存取的資料結構，但也是因為隨機存取的特性常常不小心 index 錯誤造成 bug，所以建議使用 array 還是用 sequential 的方式來運用避免錯誤。

### Chapter 13: Unusual Data Types

structure 將互相關聯哦資料組成一個資料結構，不但可以提高可讀性也可以讓人輕易理解資料的互相關聯性，雖然可以使用 class 來包裝但有時候用 structure 更容易理解，像是如果想要把資料結構互換可以用一般變數互換的方法，而且如果不把資料關聯成結構如果要新增或刪除某些資料就要搜尋整個程式找出所有需要修改的地方。如果 function 的參數有很多而且彼此都有互相關聯就可以包裝成一個結構，把此結構當成參數但切記這樣回提高 coupling，所以需要確認這些資料是有必要關聯後才包裝成結構。

Pointer 是程式最容易造成錯誤的地方，需要花很多心力才能找出問題，所以在寫程式就要有好習慣來避免嚴重的問題，最常見的問題就是修改到不該修改的記憶體導致整個程式發生預期外的行為。我們對於 pointer 的操作要在同一個 function 或 class，不要在一個 function 配置記憶體然後在其他 function 釋放記憶體。宣告 pointer 時候馬上給予值才不會被人誤用。使用 pointer 先確認記憶體是沒有 corrupt 的情況，接著再檢查記憶體代表的值是否合理。使用 pointer 還可以多加上 tag 來確保資料的完整性，配置記憶體時加上 tag，刪除記憶體檢查 tag，避免重複刪除的情形。避免對 pointer 做太多複雜的操作，例如 currentNode->next->prev = insertNode，會讓人不容易理解。可以藉由畫圖來理解指標的運作方式避免使用錯誤。刪除 pointer 要先確保還有方法可以找到指向的記憶體避免 garbage 產生。刪除記憶題時要把指向他的 poitner 指向 null。刪除記憶體前確認不是 null 避免重複刪除。

Global data 是指在整個程式內皆可以被讀取或修改，所以問題常發生於使用 global data 沒有意識到已經改變了，還有把 global data 取 alias 導致使用的人沒有意識到是 global data 所以沒有特別小心修改，多個 thread 環境之下也會讓 global data 產生 race condition。為何要使用聽起來很危險的 global data，理由是這個 data scope 就是整個程式所以變成 global data 也是合理的，另外還有需要用到 named constant 的時候但程式語言不支援。為了使用 global data 同時避免上述危險的情形，最基本的方法就是使用 access routine 來存取 global data，使用 access routine 可以實作 abstract data type 跟 information hiding，就算都不想要使用這兩種方法也可以得到下列好處，單純作為中央控管的方式，確保資料的存取修改都是有經過保護的。

## Part IV: Statements
### Chapter 14: Organizing Straight-Line Code

當 statements 有順序性時必須將 code 寫的容易看的出來有順序性，在重要的 code 上面還可以加上檢查確保有依照正確的順序執行。若沒有順序性的 statement 要將相關聯的 statement 寫在一起讓人容易閱讀，不要讓人需要不斷跳著程式碼才能得知想要的資訊。

### Chapter 15: Using Conditionals

使用 if-then-else statement 需要將正常的 case 寫在 if 裡面，越常見的 case 要寫在越上面的 if clasue。if clause 不要寫 null。確認 else clause 有被考慮過，如果覺得不需要處理 else 也要寫註解代表有思考過了。if clause 裡面的測試條件太複雜時候需要換成容易理解的 boolean 變數。

### Chapter 16: Controlling Loops

如果 loop content 可以預計跑的次數跟足夠簡單就使用 for loop, 反之則使用 while loop。把 loop content 想成是個黑盒子，把判斷 loop 執行與否的條件放在最上面讓人可以一眼看出什麼時候會執行 loop content，並且把控制 loop 的變因降到最低就可以減少出錯的次數。

進入跟離開 loop 的地方只有一個才不會讓人還要去找出所有進入點跟離開點增加閱讀的困難度，把 loop 初始化的 code 放在 loop 前面，使用 while true 代表無限迴圈而不使用 for i=1 to 99999 這種其實有限次數的 loop，盡量使用 for loop 因為 for loop 把 loop control 的方式都寫在開頭讓人容易理解也容易修改，如果 for loop 的 initiation, termination, iteration 沒有明確關聯請使用 while loop。

避免使用 empty loop，在 loop 開頭或結尾修改控制 loop 的變數，每個 loop 只做一項功能即使可以使用同一個 loop 達成兩項功能也不該這麼做，雖然分成兩個 loop 會有效率問題但等到真正成為效率瓶頸時才合併並且註解。

讓 loop 終止條件很明顯，不要使用奇怪的的手法跳出 loop，不要使用 loop 的 final value 來做判斷 loop 是否被完整執行。及早讓 loop 離開而不是先設好一堆 boolean 等到整個 loop content 都執行完才讓 loop header 判斷是否要離開，如果 loop 裡面有很多 break 四散在 loop content 就是一個危險的徵兆，使用 continue 可以跳過剩下的 loop content 減少縮排，但如果 continue 在 loop 中間或結尾就要使用 if 代替。

用頭腦跑過 loop 才是減少錯誤的方式，不要一直 try and error 直到 loop 運作正常，因為這只是把問題隱藏起來也沒有對於問題做出真正的了解。

使用有意義的變數名稱讓 nested loop 更容易理解，也可以避免誤用其他層的 loop 變數。

loop content 盡量在一頁內，層數不要大於3，如果太多層可以把 loop 變成 routine，越多行的 loop 增加越多複雜度所以要盡量寫的很明顯。

使用 inside out 的方式來建構複雜的 loop，先寫最內層的 loop 並且想像成 function，寫好後縮排加上 loop control，然後不斷重複這件事情。

### Chapter 17: Unusual Control Structures
若程式語言支援可以在 function 任何地方 return 請在可以增加可讀性的情況才使用，不然會讓人需要到處找所有 return 的地方。

recursion 使用在問題可以被分成很多個小問題而且小問題都是很簡單可以被解決，只有一小部分的問題適合用 recursion，更多一點的問題可以用 recursion 簡單解決但難以理解，對於多數問題使用 recursion 會使問題本身複雜很多。使用 recursion 要確保可以停下來，使用 safety counter 避免陷入無限迴圈，只在一個 routine 使用 recursion 因為若發生 routine A -> routine B -> routine C -> routine A 是非常難以偵測的，人對於處理一個 routine 的 recursion 已經是極限了，使用 recursion 之前要先確認其他方式不會比 recursion 更好才使用。

### Chapter 18: Table-Driven Methods
當遇到複雜邏輯處理或繼承時候可以試試看 table-driven method 來降低複雜度，使用 table-drive method 需要思考要怎麼 lookup table, direct access, indexed access, stair-step access，另外決定什麼 data 要放在 table 裡面，像是如果有某區間都是一樣的結果，一種做法是就把區段所有的 key 都存在 table，優點是很直覺而且改區段可以只改 table 就好，缺點是浪費空間，另一種方法可以將 key 轉換過後去存取，這樣只要存一個 key 在 table 裡面而不用浪費空間，轉換 key 的方法獨立包在 routine 裡面讓人知道這是 key 有經過轉換才去 lookup table。

Indexed access table 是先用 data 去 lookup table 找 index 再去找到結果，好處是當 data 大部分的結果都是不重要就可以節省空間，另外 data encode 在 table 裡面比起 data encode 在程式裡面好維護。

Stair-step access table 適合使用在 key 為某個範圍對應到結果的時候，當遇到 irregular data 也可以使用，但需要注意邊界問題還有使用 binary search 來尋找結果增加效率，如果願意使用空間換取速度也可以換成 indexed access table。

### Chapter 19: General Control Issues
Boolean expression: implicit 比較 boolean value，寫成 if(done) 不要寫成 if(done is True)，boolean test 太過於複雜可以把部分判斷變成一個 boolean 變數，如果複雜的判斷有一個意義且被常常使用就可以搬進一個 routine 但如果只有使用一次也是可以搬進 routine 增加可讀性，另外還使用 decision table 好處是資料變動只需要改動 table。

Deep nesting 會使人難以理解所以我們需要 refactor code 讓邏輯清晰，retest part of condition 可以減少 nested，當發現在成功情形下還有許多不同的情況可以把這些情況拉出來與成功情形一起測試減少 nested，如果在 loop 裡面有 deep nested if 可以將其中的 nested code 寫成 routine，另外還可以使用 object-oriented 的方式為情形寫好 class 各種類的情形為 sub class，

## Part V: Code Improvements

### Chapter 20: The Software-Quality Landscape
使用者跟 programmer 對於 Software quality 看法有不同的觀點，以外部的觀點來看 correctness, usability, efficiency, reliability, integrity, adapability, accuracy, robustness 代表 software quality 的指標，內部觀點來看則是 maintainability, flexibility, portability, reusability, readability, testability, understandability，但是不可能同時達成這些指標需要考量 project 的目標來決定要用那些指標評估 software quality。

增加 software quality 需要先定義好要達成的目標，需要明確指出 software quality 為優先的目標讓工程師內心會去努力達成，為 software 寫 unit test 或者 basic function test 可以當成評估 quality 的一項指標，藉由 test passed 跟 failed 與 code coverage 來清楚知道 software quality 是增加還是降低，code review 或者 pair programming 也是可以提高 software quality 的一種方式。開發過程中同時考慮 software quality 會比沒有考慮好，要在開發過程中保持 software quality 可以建立處理未預期的 spec 變更的流程。
  
利用不同的方式找出 defect，在越早的開發階段發現問題可以花越少時間處理，造成的傷害也會越少。

### Chapter 21: Collaborative Construction
由於給個開發者都會有各自的盲點，藉由合作的方式來產出 code 會減少軟體的缺陷，所以雖然開發時間會比較慢但維護時間會減少很多。人類比起單純測試可以觀察到不清楚的錯誤訊息、不適合的註解、hard-coded variable、重複出現的 code pattern，另外由於開發者會知道自己的 code 會被 review 所以開發時就會產出比較高品質的 code。團隊中採用合作的方式可以讓成員對所有 code 都有一定的熟悉度減少團隊成員離開的衝擊，修正缺陷的速度也會變快因為團隊成員都可以來修正而不用等到特定的人來處理，另外有經驗的開發者可以傳承經驗讓整個團隊成員可以快速提升實力。

Pair programming 是指一個人實際寫程式而另外一個人思考程式正確性、搶先一步預想接下來會如何寫程式、評估 design 好壞跟如何測試。pair programming 強迫在需要寫出 quick and dirty code 時候還是要提高 code quality。

Formal Inspection 是一種特定的 review 方式，比起一般的 review 方式 formal inspection 有下列幾種特徵
1. reviewer 會有 checklist 來專注在過去曾發生的問題上 
2. inspection 專注於找出缺陷而不是修正方法 
3. reviewer 先準備好發現的問題後去 inspection meeting 
4. 有不同的角色 
5. moderator 不是作者 
6. moderator 有接受過 moderating inspection 的訓練 
7. inspection meeting 只有在所有參與者準備好才會舉行 
8. 每一次的 inspection 都會收集資料用來讓未來的 inspection 進步 
9. 管理者不會參與 inspection meeting
Inspection 有下列以下角色 
1. Moderator: 確保 review 有以足夠快但又能找出大部分的缺陷的的速度執行，需要能知道細節但不需要針對 design 或 code 有專精的研究，主要負責把 review,  inspection checklist, 舉辦 meeting, 報告 inspection result, 追蹤會議的 action item
2.  Author: 實際產出 design 或 code 的人在 inspection 中比較屬於次要的角色，需要確保 design 或 code 不需要過多的解釋就可以被 review
3. Reviewer: 任何對 design 或 code 又興趣的人，主要目的是找出缺陷
4. Scribe: 在 meeting 中記錄找到的錯誤跟 action item 不能是 author 也不能是 moderator
5. Management: 不應該參加 inspection review 因為如意讓技術的問題演變成政治的問題。管理者應該只檢視成果而不是過程。

通常 inspection 至少要三人最多六人是較合適的，因為至少要 moderator, author, reviewer 所以需要三人，研究發現更多的 reviewer 也不會找出更多的缺陷所以差不多最多六人。

Inspection 有著不同的階段 
1. Planning: author 將完成的 design 或 code 交給 moderator，moderator 準備 meeting 跟把 code 以及 checklist 交給 reviewer
2. Overview: 如果 review 對於 code 不熟悉可以請 author 講解必須的知識但不能講解 design 或 code
3. Preparation: reviewer 根據 checklist 檢查 code，或檢查 code 是否有符合需求
4. Inspection Meeting: reviewer 提出發現到的問題讓大家討論是否真的為一個問題，一但確認是個問題後不再繼續討論解法
5. Inspection Report: moderator 產生 report 包含所有的問題，根據問題的 checklist 確保所有問題都會被修正並可以幫助下次 inspection 專注於這些問題， 還可以記錄找到的問題跟花費的時間關係觀察效率如何決定 inspection 存廢與否
6. Rework: author 收到 moderator 的問題清單加以修正
7. Follow-Up: Moderator 查看問題清單是否都有被修正完成
8. Third-Hour Meeting: 因為 inspection meeting 不允許討論解法但有時候有人還是想要討論解法，可以舉行不正式的 meeting 來討論。

### Chapter 22: Developer Testing
測試可以增加軟體品質的一種主流的做法，測試會有開發者或者專門測試的人來進行，測試方法則有 Unit testing 針對 class, routine 進行測試，Component testing 也是針對 class, routine 進行測試但規模通常是多個開發者所開發的，Integration testing 測試組合起來的 class 是否成功運作慢慢的擴展到整個系統，Regression testing 重複測試之前已經測試成功過的 test case 找出確保開發過程中不會把已開發的功能弄壞，System testing 使E用最終的 configuration 搭配軟體跟硬體的環境，針對安全性、效能、使用資源、timing issue 各種之前在較低層級測試所無法發現的問題。測試通常分為 black-box 跟 white-box testing，black-box 只對測試內容一無所知而 white-box 則是相反。

測試在軟體開發項目中與其他項目最為不同也因此開發者都較難接受測試這個項目納入開發流程，主要原因有下面幾點
1. 測試目標是要找出錯誤但開發目標是要沒有錯誤
2. 就算測試了也無法證明已經沒有任何錯誤了
3. 測試本身無法增加軟體品質，如果以錯誤結果當成衡量軟體品質的指標時，如果找出越多錯誤不就反而代表軟體品質越低落，但根本在於不斷增加測試項目並不會改善軟體品質而是要從改善開發著手
4. 測試需要假設會從 code 找到錯誤但開發者通常都會覺得自己開發完的 code 不會有任何錯誤，但開發者應該要希望自己找到錯誤而不是由其他人找到。對於測試的結果可以在開發過程中衡量軟體的品質也可以找出常見的錯誤來提醒之後開發需要特別注意的地方。開發過程中需要對 unit 做好測試在組合起來，不然等到組合起來發現錯誤就很難 debug。

開發者的測試建議有下列幾點
1. 為每個需求都進行測試確保需求都有被實作，連 security, storage, installation procedure 也是可以規劃測試
2. 設計階段規劃好測試項目確保設計有被實作
3. 使用 basic testing 增加測試項目接這用 data-flow testing 補齊缺少的測試，只少要把每行 code 都測試過一遍。

要先寫好測試還是實作完再寫測試比較好? 提倡先寫測試的人以下幾點原因
1. 先寫好測試並不會增加工作量
2. 寫測試的時候可以發現預計實作方法的缺陷提早改正
3. 先寫測試強迫開發者思考需求或設計是否有缺陷也會產出品質更好的 code
4. 因為糟糕的需求難以些出測試，所以先寫測試就會提早發現。

開發者的測試有其極限，開發者通常只會測試正常的運作而不會測試各種會讓 code 壞掉的測試項目，開發者對於 code coverage 過度樂觀，開發者會跳過複雜的測試項目。

如果將所有可能的測試項目都測試過一遍就可以證明軟體的正確性但現實上所有的可能測試項目會有超級多種組合使測試幾乎永遠不可能跑完，但所有可能的測試項目中都會存在多餘的測試項目藉由削減這些測試可以減少需要測試的項目。規劃測試需要一步一步的進行，先使用 structured basic testing 測試程式中的每一個 statement，接著使用 data-flow testing 藉由觀察 data 的定義-使用方式找出 basic testing 缺少的 test case。Equivalence Partitioning 將可以產生同一種錯誤的 test case 只留下一個減少測試所需要的項目。Boundary Analysis 測試關於 condition 邊界的地方減少 off-by-one error。Bad data 可以用來測試不合理的情況看看程式有沒有正確處理。Good data 也需要被測試使用 minimum or maximum configuration 來測試程式。

改善測試的方法有下列幾點
1. project 初期就規劃好測試，把測試的重要性看的與與其他階段一樣，如此一來也會分配時間給測試
2. Regression testing 讓舊有功能不會受到新加入的功能影響
3. Automated testing 管理 regression testing 的結果，因為靠人工跑 regression testing 會容易忽略錯誤，透過自動化可以讓 test 跑的比較頻繁容易早點看出是哪邊新的 code 導致 test 壞掉。

保存重複測試的結果用來衡量 project 的進步與否。

### Chapter 23: Debugging
Debugging 是一種找出錯誤的根本原因並且修正的過程。而我們可以從找尋缺陷與修正的過程中學習到不同的東西
1. 缺陷可以增加對於程式的理解因為如果有完全理解的話就不會又缺陷
2. 當發現缺陷可以思考為什麼會製造出這種缺陷、要怎麼更快速的找到這個缺陷、是否有其他類似的缺陷問題、是否可以再發生問題之前修正好
3. 當閱讀程式碼以找尋缺陷時候可以同時思考是否容易讀、這段 code 是否可以更好、是否可以進行 refactor、讓下次撰寫程式碼的時候能進步
4. 分析一下自己找到缺陷的方式修正做法讓 debug 效率增加
5. 分析自己修正缺陷的方式是否有修正 root cause 而不是增加 special case 處理問題的表象

透過 debugging 過程可以知道怎麼提升 code quality 讓以後自己 debug 時間減少。Debugging 不是使用亂猜的方式，要徹底理解問題找出問題的根源並且修正。心理預設 bug 是自己寫的 code 所產生的可以幫助 debug 過程。

以科學化的方法找出缺陷
1. Stabilize error: 使 error 可以重複性的發生，如果無法重複發生就有可能是初始化問題、timing issue、dangling-pointer problem
2. Locate the source of the error
   - 收集可以製造出缺陷的資料
   - 分析資料提出假設
   - 找出方法確證假設是否正確
   - 確認假設的正確性
3. Fix the defect
4. Test the fix
5. Lookup similar errors

修正缺陷需要徹底了解問題的核心才做修正，不然可能會導致更多的缺陷產生，除了瞭解問題之外也要了解程式本身才有辦法做出正確的修改，不要急著馬上修正缺陷，先花點時間跑測試確認假設是正確的，急於修正缺陷而沒有仔細思考所有可能的情形反而會花更多的時間來修正缺陷，使用 special case 修正缺陷不僅沒有修正問題的根源還會使程式變得難以維護，使用猜測的方式來修正缺陷不僅沒有正確修正缺陷更不會學習到任何東西，修正缺陷後自己要檢查也需要看看是否有副作用出現，修正缺陷後要增加 unit test 以避免重複發生，修正錯誤後還要找找看有沒有類似的缺陷。

### Chapter 24: Refactoring

現代軟體常常需要變動以應付源源不絕與不斷變動的需求，因此軟體本身需要不斷演化以適應新的需求。演化過程中我們需要確保是以進步的方式做演化而不是退化，當需求變動必須讓軟體演化時可以把這當成一個機會讓軟體對於未來類似的改動可以更容易。

改進軟體內部品質讓 code 更容易讀懂跟改動但又不改變原有的行為稱為 refactoring，當 code 難以維護或者一開始就沒有寫好就需要 refactoring，下面有幾點可以看出需要做 refactoring 的特徵。
* Code is duplicated: 重複的 code 會使之後需要同時改動，也違反了 Don't Repeat Yourself 原則跟 複製與貼上就是設計錯誤
* A routine is too long: routine 長過一個螢幕可以顯示的範圍就是需要改動，可以藉由模組化來縮短 routine
* A loop is too long or too deeply nested: 過深的縮排可以換成 routine 來減少縮排
* Class has poor cohesion: class 中有太多不相關的東西就需要分離成更多 class
* A class interface dose not provider consistent level of abstraction: 不斷變動過程可能會讓 class interface 不一致
* A parameter list has too many parameters:  架構良好的程式通常有很小小但定義良好的 routine，所以 routine 有太多的 parameter 就是個警訊
* Changes within a class tend to be compartmentalized: 當發現改動一部分的 class 卻不需要改動另一部分的 class 表示這個 class 還可以被分割成不同的 class
* Changes require parallel modifications to multiple classes: 當發現常常需要改動同一批 class 的時候，或許可以嘗試 rearrange class 讓改動只需要動一個 class 就好
* Inheritance hierarchies have to modified in parallel: 改動 subclass 卻常常需要動到 parent class
* Case statement have to modified in parallel: 常常需要同時改動類似的 case statement 可以思考用 inheritance 是否更好
* Related data items that are used together are not organized into class: 常常需要改動相同 data items，可以考慮用 class 封裝起來操作
* A routine used more features of another class than of it own class: 當 routine 更常使用其他 class 的 feature 可以考慮把 routine 搬到那個 class
* A primitive data type is overloaded: 使用 primitive data type 代表現實世界的東西時候，可以用 class 來代表並獲得 type checking 的幫助
* A class doesn't do very much: 當 class 責任不夠大可以考慮合併到其他 class
* A chain of routines passes tramp data: 當發現 routine 只是把收到的資料轉送給另一個 routine 可以問問自己是否有符合 routine 的 abstraction，如果沒有想其他發法讓 routine interface 更 consistent
* A middleman object isn't do anything: 如果發現 class 只是轉送 parameter 給其他 class 的 routine，可以考慮刪除這個 middleman
* One class is overly intimate with another: 當發現 class 對於其他 class 知道的太多就違反 encapsulation 的原則，會讓 code 難以管理跟改動造成更大的漣漪
* A routine has a poor name: 如果發現 routine name 難以理解就要馬上修正，因為越晚修正越難處理
* Data member are public: public data member 通常都是不好的作法，模糊了 interface 跟 implementation 的界線。不僅違反 encapsulation 更讓以後改動的彈性降低
* A subclass use only a small percentage of its parents' routines: 當 subclass 只是想要用 parent class 的 routine 就會有這種情形發生，建議可以將 subclass relationship 從 is-a relationship 轉成 has-a relationship
* Comment are used to explain difficult code: 遇到 bad code 就重寫它不要再註解解釋
* Global variables are used: 可以重新想想是否有其他方式可以不用使用 global variable，隨著 refactoring 或許對 code 有更高熟悉度可以想出不用 global variable 的方法
* A routine uses setup code before a routine call or takedown code after a routine call: 當呼叫 routine 之前需要 setup 一堆 code 或呼叫之後需要 takedown 一堆 code 但 routine 卻不用給任何參數就是個徵兆，可以改寫成傳參數給 routine 取代 setup 一堆 code
* A program contains code that seems like it might be needed someday: 這些 code 在未來常常不會用到，其他人看到會以為是有經過測試過或者被試用過而造成誤導。

### Chapter 25: Code-Tuning Strategies

#### 25.1 Performance Overview
* code tuning 只是讓系統效率變好的其中一種方式，通常還有其他花更少時間或不用動到 code 的方式
* programmer 通常習慣透過 code 看世界，但 user 只會在乎程式的 feature 而不是 code quality，user 只在意 throughput 而不是 performance
* 只在一處增加速度可能會導致整體系統變慢
* 確定要增加效率時需要考慮下面幾點
    * Program Requirements: 通常 performance requirement 都會比真正的 requirement 嚴格許多，開始著手 performance 問題前先確定這是值得被解決的
    * Program Design: 有些程式設計的很難寫出高效率的程式，所以針對程式設計可以較容易寫出高效率的程式
        * 為每個 resource 設定 performance 目標讓整體程式的效率可以預測，如果每個 resource 都有達成目標則最後就會達成目標，但途中發現某的 resource 無法達成目標就可以盡早重新 design
        * 可以為了長遠的規劃先不達到效率的要求，但規劃好容易修改的設計後只要慢慢將效率差的部分換成效率好的最終還是可以達到設定的效率
    * Class and Routine Design: 這層級主要考慮選擇的 data types 跟 algorithms，這些會直接影響到記憶體與執行速度
    * Operating-System Interactions: 如果程式有使用 external files, dynamic memory, output device 通常就是跟 operating system 互動
    * Code Compilation: 好的 compiler 會將 clear, high level language code 轉成有效率的 machine code
    * Hardware: 有時候最便宜最好的方法就是升級硬體
    * Code Tuning: 修改原本正確的 code 讓它跑的更快，通常侷限在小範圍裡

#### 25.2 Introduction to Code Tuning
* 提升效能 code tuning 不是最有效率的方法，從 program architecture, class design, algorithm selection，可以讓效能有顯著的提升
* 提升效能 code tuning 不是最簡單的方式，直接買好一點的硬體或換優化能力比較好的 compiler 會更容易
* 提升效能 code tuning 不是負擔最小的方式，手動調整的 code 不但需要花很多時間更讓 code 變的難維護
* 80/20 法則也可套用在程式最佳化上面，通常 20% 的 routine 占用80% 程式運行時間，所以要先找出耗用時間最多的部分才來做優化
* 在 high-level language 寫越少 code 並不會讓 machine code 的 speed 增加或 size 減少
* 每次改變程式都需要 profile performance 才能知道是否有幫助，包含 compiler 跟 compiler 版本、library 跟 library 版本、處理器、記憶體大小之類的東西。
* 不要再一開始就把每個 routine 都最佳化，因為在程式完成之前很難知道 bottleneck 在哪邊，過早的最佳化只是在浪費時間，就算猜對 bottleneck 在哪邊也會對其他部分矯枉過正，如果太專注在最佳化會讓其他更重要的東西例如: 正確性、information hiding，易讀性變成次要目標

#### 25.3 Kinds of Fat and Molasses
* Common Sources of inefficiency
    * Input/Output Operation: 不使用不需要的 I/O，如果處理檔案可以在記憶體處理就不要從 disk 拿出來或者透過網路
    * Paging: operation 讓系統需要 swap page of memory 比起在一個 page memory 處理慢上許多
    * System calls: 使用 system call 需要耗費很多時間，因為要經歷 context switch
    * Interpreted languages: 需要在產生 machine code 之前處理滿一行程式碼
    * Errors: 錯誤會導致程式變慢

#### 25.4 Measurement
* 經驗無法幫助如何最佳化，因為經驗是累積在過去的機器、語言及 compiler
* performance measurements 需要精確，可以利用 profiling tool
* 確保只計算正在 tuning 那段 code 的時間，使用 CPU clock tick 來計算避免把系統 switch 到別的程式的時間計算下去

#### 25.5 Iteration
* 透過各種不同的優化方式累積起來可以達到很顯著的優化

#### 25.6 Summary of the Approach to Code Tuning
1. 開發容易理解與修改的軟體
2. 如果 performance 很糟糕
    a. 存好目前的 code
    b. 測量系統找出耗費最多時間的部分
    c. 考量是因為不適當的 design, data types, algorithm 導致的，如果是回到第一步
    d. Tune bottleneck
    e. 測試每次的 improvement
    f. 如果 improvement 無效，revert code 到 step (a) 存的狀態

### Chapter 26: Code-Tuning Techniques
* code-tuning 表面上看起來跟 refactoring 有點像但是 refactoring 是改善 internal structure 而 code-tuning 反而是破壞 internal structure

#### 26.1 Logic
* Stop Testing When You Know the Answer
    * short-circuit evaluation: compiler 會在知道答案後就馬上停止，了解語言支不支援，如果不支援需要自己注意此類情況
    * 判斷 array 是否含有負數不需要完整找過一遍，只要發現有負數就可以立刻跳出
* Order Tests by Frequency: 盡量把速度快或者常用到的測試擺在前面
* Compare Performance of Similar Logic Structures: 不同語言對於相似的邏輯結構會有不同的表現，像是 case 與 if-then-else
* Substitute Table Lookups for Complicated Expressions: 遇到需要很複雜的測試邏輯可以改用 lookup table 來增加效率，雖然定義 table 有點難懂但是只要加好註解後就不會這麼難懂了，另外如果定義改變用 table 的方式也比較好改
* Use Lazy Evaluation: 直到需要處理才去處理

#### 26.2 Loops
* Unswitching: 不再 loop 裡面做決定，把做決定的判斷移出 loop，但缺點是會讓 code 變不好讀與不好維護
* Jamming: 把多個有著相同 element set 的 loop 在融合在同一個 loop，但缺點是一旦 index 改變有可能需要重新分開，另外要注意順序跟之前不變
* Unrolling: 把一次處理多個 element 減少 loop 的次數但會讓 code 變得難懂於難維護
* Minimizing the Work Inside Loops: 把可以移到 loop 外面的計算移到外面，不僅速度更快也更容易讀懂
* Sentinel Values: 把 sentinel value 放到 search 尾的後面確保會停止
* Putting the Busiest Loop on the Inside: Nested loop 中最忙的 loop 放到裡面可以節省總 loop 次數
* Strength Reduction: 把 loop 中比較昂貴的操作像是乘法換成便宜的操作像是加法

#### 26.3 Data Transformations
* Use Integers Rather Than Floating-Point Numbers: 整數的加法跟乘法都比浮點數更快
* Use the Fewest Array Dimensions Possible: 使用一維的陣列會比起二維的陣列快
* Minimize Array References: 減少對於 array 的 element 讀取，如果 loop 中都存取同一個 element 可以在外面先存取好記錄下來給 loop 用
* Use Supplementary Indexes: 使用輔助的 index 可以加速存取 data type 的特徵
    * String-Length Index: 可以加入長度的資訊在不定長度的資料型態才不用每次用到都需要計算加速
    * Independent, Parallel Index Structure: 操作 index 比起直接操作 data type 更有效率，sorting 或 searching index 都會比起直接操作資料快
* Use Caching: 暫存常用到的值，加快存取速度

#### 26.4 Expressions
* Exploit Algebraic Identities: 藉由代數的 identity 可以把 operation 替換成便宜的
* Use Strength Reduction: 使用 cheap operation 代替 expensive operation
    * 使用加法取代乘法
    * 使用乘法取代指數運算
    * 使用 long 或 int 取代 long long
    * 使用 fix-point numbers 取代 float-point numbers
    * 使用 single-precision number 代替 double-precision number
    * 使用 shift operation 取代乘2或除2的操作
* Initialize at Compile Time: 把 routine 中不會改變的值抽出來變成常數
* Be Wary of System Routines: system routine 很昂貴但我們其實不需要這麼精準的答案就可以用自己寫的 routine 就好
* Use the Correct Type of Constants: 使用正確的型態避免花時間在型態轉換上面
* Precompute Results: 把之前算過的結果存起來，或者在一開始就全部算好
* Eliminate Common Subexpressions: 如果有重複的 sub expression 可以 assign 到變數壁面重複計算

#### 26.5 Routines
* routine decomposition 對於 code-tuning 是很強大的工具
    * 只要加速一個 routine 就可以同時加速使用到這個 routine 的人
    * 小的 well-define routine 很容易用 low-level language 重寫加速
* Rewrite Routines Inline: 古老時代的 machine 呼叫 routine 會需要許多 swap 導致程式變慢，但現代的 machine 不會有這種問題

#### 26.6 Recoding in a Low-Level Language
* 遇到 performance bottleneck 時候可以用 low-level language recode

## Part VI: System Considerations

### Chapter 27: How Program Size Affects Construction

#### 27.1 Communication and Size
* 當負責專案的 programmer 越多時，產生的溝通成本會越大也更容易發生溝通上的誤解
* 大型的專案需要建立 streamline 的溝通或者合理的限制溝通數量

#### 27.2 Range of Project Sizes
* 專案規模很難以界定，用團隊成員的數量是比較好的定義

#### 27.3 Effect of Project Size on Errors
* 大型專案有比較高比例的錯誤發生在設計與需求上
* 錯誤密度會隨著專案規模增加而上升

#### 27.4 Effect of Project Size on Productivity
* 小型專案上的生產力取決於 programmer 本身的能李
* 大型專案上的生產力則是受團隊大小與組織影響比較多

#### 27.5 Effect of Project Size on Development Activities
* 專案規模越大開發所佔的比例越低，因為其他部分會隨著專案規模變大所需要的時間會飛快的成長
* 當專案變成產品時候需要再不同環境下測試過、加上文件說明跟維護，一個軟體產品比起軟體程式需要多三倍的時間
* 軟體系統需要設計好介面整合不同的程式所以也比起單一程式需要多三倍的時間
* 如果以打造程式的時間來推估打造系統的時間會低估所需的時間
* 專案規模越大則規範會越多，不同的專案需要不同程度的規範
* 越正式的專案需要更多的 paper work，因為需要文件來 coordinate 大家的想法

### Chapter 28: Managing Construction
#### 28.1 Encouraging Good Coding
* 由於 code 是 construction 主要的產出，所以最關鍵的是如何鼓勵良好的 coding practice，通常需要找個大家認可的高手的人來訂下 technical standard 才能讓底下 programmer 願意遵守
* 訂定規則需要考慮組織的適用性，盡量訂下有彈性的 guideline 或者提供 best practice 讓人參考
* 達成 good code practice 的技巧
    * 同時讓兩個人以上負責 project 的一部分，可以確保至少有兩個人思考過 code 是可以正常運作且可讀懂
    * Review 所有的 code: 通常至少兩個人 review code 就確保三個人有讀過這段 code，當 code 需要給人 review 就會使寫 code 的人提升 code 品質，同時可以建立起團隊的 code 標準，另外可以預防有人離開但剩下的人沒有人可以後續維護的問題
    * Require code sign-offs: senior technical personnel 需要 sign code 表示 code 已經完成
    * 提供好的 code 給大家參考，清楚提供品質的目標
    * 強調 code 都是公共的資產，programmer 都會覺得自己寫的 code 就是自己的，但是 project code 應該是所有人都可以讀取並修改
    * 獎勵好的 code，對於非常好的 code 才給獎勵，但如果無法分辨就乾脆都不給，因為給錯反而比不給糟

#### 28.2 Configuration Management
* software project 非常不穩定，code 會變、設計會變、需求也會變
* configuration management 是用系統化的方式處理有關任何變動
    * 如果不管理變動則會容易寫出不需要或不相容的 code，或者最後整合才發現根本無法整合，大家無法朝向一個明確的目標前進只會中途不斷迷路
    * 如果過度管理變動可能會造成專案無法前進
* 如果每次需求或設計變動時都接受時，最後可能會發現專案像在跑步機上面自己感覺有再前進但是根本只在原地踏步
    * 任何變動都需要經過系統化的過程來釐清什麼是對專案有幫助
    * 把所有想法或建議都先寫下來成為之後的待作清單，才不會因為明明有一個好的改動但是因為專案落後而被捨棄
    * 對於任何變動都需要預測所需要的時間，包含 code review、重新測試，讓所有人清楚變動是錯綜複雜且需要時間的即使第一時間覺得只是個簡單的改動
    * 對於大的變動需要有警覺，通常大變動都是不可逆的，雖然重新回去檢視需求和架構很麻煩但比起從做一遍好多了
    * 建立一個 change-control board 管理變動，任何需求都會寫在上面，之後定期評估這些變動來跟決定優先順序
    * 別讓官僚文化排除 change control，可以用 email 當成 change board 讓所有人了解這個過程或者把 change 當成 defect 之後由 defect-tracking system 處理
* code version-control tool 可以幫助當改了 code 有 error 發生時可以對照舊的 code 找出原因
* 一個好的 version-control software 有以下條件
    * 同時處理同個檔案不會出現問題
    * 可以簡單的更新檔案到現在的版本
    * 可以回到任何版本的任何檔案
    * 可以得到任何版本的任何檔案的變動的部分
    * 不用擔心個人的備份問題，因為 version-control 提供另一層的保護
* Tool versions: 需要把 compiler, linker, code library 也包含進 version control 之中
* 建立標準化的環境讓大家不會因為環境的差異而遭遇不同的問題
* 建立備份計畫，週期性的備份 code 並且特定時間嘗試還原資料檢查是否備份成功，結束專案後把所有之後還原 product 需要的東西都打包起來放到安全的地方

#### 28.3 Estimating a Construction Schedule
* 建立預測的目標，找出為何需要預測、只要預測 construction 或者全部的開發過程、需要預測的多準，樂觀或悲觀的預測會對結果造成什麼影響
* 不要匆促的預測不然容易不精準，需要當成一個小 project 來預測時程
* 預測之前需要訂好需求，不然無法預測
* 檢視越細節的部份可以預測的更精準
* 使用不同的方法預測並且比較這些結果
* 定期重新預測，隨著專案進行時預測可以更加準確
* 根據公司專案的經驗跟專案大小用來預測未來專案的時程
* 預測是找出專案完成的時間的重要部分，一旦專案有了 delivery time 跟 specification 則重要的是如何控制預算並且準時交付專案
* 專案落後的處理方式
    * 保持樂觀的心態期待之後會趕上: 了解目前的落後是為了未來的加速，因為先花時間在釐清 spec 、訂好需求、做好測試上之後就可以更加快速
    * 擴張團隊: 雖然 Fred Brook's Law 說在專案晚期加入新成員因為會花掉其他成員 training 新成員的時間而新成員也需要 training 後才能有產出導致專案會更晚，但是只要將專案的工作分割好就算新成員不需要 training 也可以上手就可能使專案趕上
    * 減少 project scope: 少做一個 feature 等於少掉了 design, coding, debugging, testing, documentation，所以專案一開始把所有 feature 分類成必須有、有也不錯、有沒有都可以的類別，當專案落後就專注在必須有的 feature 就好，若必須有的 feature 一定要做出來也可以先做出比較沒那麼好得版本，例如暴力解、很慢、很花記憶體之類的缺點，之後再來改進

#### 28.4 Measurement
* 任何專案的屬性都可以被測量，有測量比起完全不測量的好
* 測量後的數據作為之後開發過程的參考
* 測量數據都是要可以被量化的，這樣才能用來比較優劣
* 先從大方向的測量開始做起，再來隨著專案的特性挑選需要測量的面向
* 測量需要原因，確認目標後提出問題再去測量

### Chapter 29: Integration
* Integration 把分開的軟體部分組合成一個系統
* 建立軟體部分的順序與 integration 的順序息息相關，只有建造好的部分才能整合

#### 29.1 Importance of the Integration Approach
* 如果建造及整合軟體的順序錯誤會難以撰寫 code、測試及 debug，途中也會不清楚進度、複雜度造成過度樂觀的情況
* 仔細整合會有下列的好處
    * 容易找出缺陷
    * 較少的缺陷
    * 較短時間產出第一版可用的產品
    * 較短的開發時程
    * 提高完成專案的機率
    * 更可靠的時程預估
    * 更精準的進度
    * 改善 code quality
    * 較少的文件

#### 29.2 Integration Frequency—Phased or Incremental?
* Phased Integration
    * Steps:
        1. 設計、寫 code、測試、除錯每個 class，稱為 unit development
        2. 把所有 class 組成一個系統
        3. 測試跟除錯整個系統
    * 缺點:
        * 當把所有 class 組合再一起時，問題發生時有太多可能出錯的部分，有可能是 class 本身壞掉、兩個 class interface 之間的問題或者兩個 class 交互作用的問題
        * 直到專案晚期才有辦法開始整合
    * 對於只有 2-3 個 class 的程式 phased integration 或許是比較好的方式，但其他通常是用 incremental integration 比較好
* Incremental Integration
    * Steps:
        1. 開發系統部分的功能當作基本的骨架，測試跟除錯
        2. 設計，寫 code、測試、除錯 class
        3. 整合新的 class 到骨架，測試及除錯，若還有剩餘的功能重複第二步驟
    * 假設需要整合多個 class 可以先用 incremental integration 的方式整合好這些 class 在來把整合好的部分整合進主系統
    * 優點:
        * 容易找出錯誤的原因: 由於一次只新增一個 class 則問題發生點就被限縮，另外一次整合一個 class 會產生比較少的問題不容易發生多個問題互相遮掩的問題
        * 系統在早期就可以作用: 當 code 開始整合且執行時，即使系統還不可用但可以讓人看到結果提高信心度
        * 更容易監測進度: 頻繁的整合可以輕易看出哪些功能有沒有被實作與否
        * 增進客戶關係: 客戶喜歡看到專案的進度跟頻繁整合代表進度有再前進
        * 系統的部分被更完整的測試過: 頻繁整合過程中，系統的部分在每次整合都會被測試到
        * 建立系統需要較少的開發時程: 仔細規劃整合可以讓工作平行處理

#### 29.3 Incremental Integration Strategies
* phased integration 不需要規劃整合的順序因為都是在相同時間一次整合
* incremental integration 需要謹慎的規劃，整合的順序會影響到開發的順序
* Top-Down Integration
    * 在繼承最上端的 class 需要先開發跟整合
    * class 的 interface 需要仔細的規範，問題常發生在 class 之間互動的問題
    * 優點
        * 系統的邏輯可以在早期就被測試好
        * 專案早期就可以有部分功能的系統可以運作
        * 底層細節的 detail design 完成前就可以開始 coding
    * 缺點
        * 把 tricky 的系統介面留到最後才做可能造成需要改動 high-level design
        * 很多個 low-level class 需要途中一起整合破壞掉原本 incremental integration 的用意
        * 現實中採用完全的 top-down 是不太可能的
        * 如果 class 中沒有 top 就無法使用
    * 可以局部採用 top-down integration
* Bottom-Up Integration
    * 從繼承最底部的 class 開始開發跟整合
    * 優點: 及早發現潛藏的 system interface 問題
    * 缺點
        * 把 high-level system interface 整合留到最後，如果 high-level design 發現有問題需要把 low-level 工作捨棄
        * 需要完成系統的設計才能開始整合，若沒有好好設計會導致 low-level code 反過來主導 high-level design 違反 information hiding 跟 object-oriented design 的原則
* Sandwich Integration
    * 同時使用 top-down 跟 bottom-up 的方式整合取捨者兩種的好壞
    * 現實中常用的方式
* Risk-Oriented Integration
    * 先整合困難的部分，通常 top 跟 bottom 都是困難的部分所以會先整合
    * 雖然跟 sandwich integration 順序很像但是動機不一樣
* Feature-Oriented Integration
    * 一次整合一個 feature
    * 整合 feature 或許會一次整合多個 class 但是只有 feature 整合之前有好好整合過就比較不會喪失 incremental 的好處
    * 不需要整合途中需要暫時讓整個系統作用的支架
    * 每次整合 feature 代表在功能性上面有進步，作為專案進度的證據，如果想要提早釋出較少功能的系統也可以辦到
    * 更容易使用 object-oriented design，因為 object 通常可以對應 feature
    * 實際上的難度與純 top-down 跟 bottom-up 一樣困難
* T-Shaped Integration
    * 挑選一個 slice 先做開發及整合確保 top-down 跟 bottom-up 都沒問題再繼續做其他的 slice

#### 29.4 Daily Build and Smoke Test
* 每天每個 file 都需要被 compiled, linked 跟 combine 到 executable program，接著進行 smoke test 確認最基本的功能可以成功運作
* 降低程式品質不佳的機率，透過 daily build 跟 smoke test 可以清楚知道目前的狀態
* 容易找出系統壞掉的原因，檢查哪一天壞掉跟 commit 那些 code 就容易知道壞掉的原因
* 頻繁的整合可能會造成沒有預見到的錯誤累積在專案最後才爆炸
* 把 daily build 當成專案的心跳，每天的 build 可以快速整合大家的成果跟及時修正錯誤
* 修正壞掉的 build 是最優先的事情
* smoke test 對於系統 end to end 的檢查，主要找出重要的問題
* daily build 缺少 smoke test 幾乎沒有價值，smoke test 維持品質及找出整合問題
* smoke test 需要跟系統與時俱進
* 將 daily build 與 smoke test 自動化
* 當專案需要把 daily build 跟更新 smoke test 最為重要的事情時需要有人專門負責 daily build 與 smoke test
* 整合有意義的時候才進行整合，不要整合沒有意義的 code 進系統
* 很少整合 code 到系統是個警訊，有可能一次整合太多 code 失去 daily build 的用意，頻繁的整合迫使開發者需要將工作分割
* 要求開發者自己先 smoke test 即將要整合的 code
* 建立已經被整合好的 code base，讓開發者可以知道目前整合好的 code 用來測試即將需要整合的 code
    * 整合的 code 會先進 code base 後如果 smoke test 成功後才會正式進入 code base
    * 小型的專案利用 version control system 來查看新進的 code
* 建立讓 build 壞掉的罰則，讓大家知道確保 daily build 健康是專案的第一要務，要求暫停手上的工作直到 daily build 修好
* 早上 release build，測試者早上就可以拿最新的 build 來測試，build 也肯可能會 delay 所以早上 release 還有點時間可以修復，發現問題時也比較容易找到工程師來解決
* 在時程壓力之下還是要維持 daily build 跟 smoke test，因為壓力之下更容易犯錯所以需要 daily build 跟 smoke test 來把關

### Chapter 30: Programming Tools
#### 30.1 Design Tools
* Design tool 通常是圖像化的工具，可以藉由圖像表達設計概念
* Design tool 幫我們管理區塊的排列及區塊間的連結關係，讓我們不必費心於此

#### 30.2 Source-Code Tools
* Editing
    * Integrated Development Environments (IDEs)
        * editor 有 compilation 跟 error detection 功能
        * 整合 source-code control, build, test, debugging tool
        * 檢視程式的架構
        * 挑到任何 class, routine, variable
        * 跳到任何使用到該 class, routine, variable 的地方
        * 自動 formatting
        * 提供程式語言的編輯建議
        * Brace matching
        * 提供常見的程式語言樣板
        * 自動縮排
    * Multiple-File String Searching and Replacing
        * 發現錯誤時使用這種工具找出所有其他檔案相似的錯誤
        * 能提供搜尋完全符合的字串、相似的字串及支援 regular expression
        * 如果想把 routine, constant, global variable 換個更好的名字就可以使用，如果很容易在多個檔案換名字則有更多機會讓我們願意換更好的名字增加可讀性
    * Diff Tools
        * Programmer 常常需要比較兩個檔案的差異，如果修正錯誤中嘗試改 code 後發現不可行則工具可以讓我們知道那些地方是我們修改過的
        * 與其他人合作是會想要看其他人做了那些改變就可以使用這種工具
        * 通常整合在 revision-control tool
    * Merge Tools
        * 有一種 revision tool 只讓一個人在同一個時間修改檔案，所以不會有 merge 問題
        * 另一種 revision tool 允許多人同時改檔案只在 check-in 時候做 merge change，所以需要 merge tool 的幫忙
        * 通常會自動 merge 簡單的部分，無法判斷的部分就會詢問 programmer 該如何改動
    * Source-Code Beautifiers
        * 將 source code 的風格一致化
        * 有一種工具在不改變 source code 的情況下產生更好看的格式
        * 另一種會改動 source code 來一致化，通常使用在 legacy code 上面
    * Interface Documentation Tools
        * 有些工具可以分析 source code 的 programmer-interface documentation
        * source code 通常使用 @tag 欄位來表示需要被分析
    * Templates
        * 常用到的東西想要一致化就可以使用樣板
        * routine 前面的註解可以使用樣板自動加入讓 programmer 願意遵守 coding 跟 documentation style
    * Cross-Reference Tools
        * 列出 variable 跟 routine 跟被用到的地方
        * 通常使用網頁的方式呈現
    * Class Hierarchy Generators
        * 產生 class 的繼承關係
        * 用來除錯
        * 更成用來分析程式架構及模組化程式
* Analyzing Code Quality
    * Picky Syntax and Semantics Checkers
        * 提供比起編譯器更加完整的檢查
        * 檢查語法上正確但是常見的錯誤
    * Metrics Reporters
        * 分析程式碼及產出報告
        * 分析 routine 的複雜度，讓 programmer 重新檢視複雜度高的 routine
        * 計算 code 的行數、宣告次數、註解多寡、空白的行數
        * 追蹤 defect，紀錄哪個 programmer 製造的、修正的、修正次數，就可以知道哪些 routine 最常被修改
* Refactoring Source Code
    * Refactorers
        * 容易在整個 code base 下改動 class 名稱
        * 選取想要變成 routine 的 code 就可以抽出成 routine 必且自動排好 parameter list
    * Restructurers
        * 把 spaghetti code 轉成 better-structured code
        * 如果原本邏輯就很糟轉換後來是很糟
        * 通常在簡單或常出現的例子上使用，接著手動調整困難的部分
    * Code Translators
        * 將 code 從一個語言轉到另一個語言
* Version Control
    * Source-code control
    * Dependency control
    * Project documentation versioning
    * Relating project artifacts: 需求、code、測試項目
* Data Dictionaries
    * 描述 project 中有意義的資料
    * 避免使用重複的 class name
    * 避免使用不同的 class name 代表相同東西
#### 30.3 Executable-Code Tools
* Code Creation
    * Compilers and Linkers: compiler 將 source code 轉換成 executable code, linker link 需要的 object files 到 program
    * Build Tools: 減少 build 現在版本的時間，build tool 檢查相依性確保一致性，只重新編譯有相依性的部分。
    * Code Libraries: 快速寫出高品質程式其中一個方法是找出 open source 可用的高品質 library
    * Code-Generation Wizards: 通常在 database application 使用，雖然自動產生的 code 不會比人類寫的 code 好但是指至少可以運作，對於需要實驗性質或 prototype 的 production code 可以快速的實作出來
    * Setup and Installation: 檢查是否有缺少需要的 library，版本之類的東西
    * Preprocessor: 容易切換 development code 與 production code 進行 debugging
* Code Tuning: 
    * Execution Profilers: 可以統計各個 statment 所跑過的次數與時間讓我們容易找出需要改進的地方進行調整
    * Assembler Listings and Disassemblers: 有時候想要看 high-level language 產生的 assembler code 去了解為什麼看起來應該要很快但是實際跑得很慢，有些 high-level language 不會產生 assembler listings 所以需要 disassembler 從 machine code 產生 assembler code

#### 30.4 Tool-Oriented Environments
* Unix 有名在於有需多小工具可以很好的共同作用，組合再一起可以形成更大的功能

#### 30.5 Building Your Own Programming Tools
* building tool 是程式中很基礎的一件事
* Project-Specific Tools
    * 產生特出的測試資料
    * 檢查資料的品質
    * 模擬硬體的環境
* Scripts
    * 自動化處理需要重複做的事情
    * 當發現自己不斷的重複某些事情就可以考慮寫個 script 自動化

## Part VII: Software Craftsmanship

### Chapter 31: Layout and Style
#### 31.1 Layout Fundamentals
* The Fundamental Theorem of Formatting
    * 一個好的排版要能表達出程式邏輯結構
    * 這種方式可以讓好邏輯的 code 看起來不錯，爛邏輯的 code 看起來很糟
    * 不需要讓所有 code 都看起來好看的排版方式
* Human and Computer Interpretations of a Program
    * 電腦使用 brace 或 begin, end 等等關鍵字來理解程式結構
    * 人類使用視覺來理解程式結構
    * 不正確的排版會造成人類與電腦的認知不同
* How Much Is Good Layout Worth?
    * 寫程式首先要讓機器讀的到，再來讓其他人讀得懂
    * 程式設計師仰賴程式結構來記憶，所以好的排版更容易記憶
    * 雖然好的排版有很多種但重要的是要保持一致性
* Layout as Religion
    * Programmer 自己對於排版的喜好會不易理解不同排版的 code
    * 排版好壞通常有很多爭議，programmer 應該保持開放的心態接受新的排版方式
* Objectives of Good Layout
    * 精確表達邏輯結構
    * 保持顯示邏輯結構的一致性
    * 增加可讀性
    * 不需要為了保持排版導致需要修改很多地方

#### 31.2 Layout Techniques
* White Space
    * 包含 spaces, tabs, line breaks, blank lines
    * 寫程式像寫書一樣需要把作者想像中的組織架構呈現出來，讓讀者可以知道邏輯是如何組織的
    * Grouping: 利用空白將相關的 statement group 再一起
    * Blank lines: 把不相關的 statement 分開
    * Indentation: 使用縮排表達邏輯架構
* Parentheses: 盡量使用括弧避免讓人需要思考程式的執行順序

#### 31.3 Layout Styles
* Pure Blocks: 都會有 begin 跟 end 來形成一個 block 所以 block 裡面的縮排也是很自然的，因此沒有可以爭議的地方
* Emulating Pure Blocks: 在沒有 pure block 的語言可以把 { 或 } 當成 pure block 的開始與結束
* Using begin-end Pairs (Braces) to Designate Block Boundaries: 把 begin-end 當成 block 的一部分而不是 control 的開始與結束
* Endline Layout: 把 block 縮排到中間或結尾，begin 之後接上 parameter list，但遇到 nested 的結構就會讓 code 很難讀懂，如果第一航 code 的長度變更則後面的 code 都需要做修改造成維護的困難

#### 31.4 Laying Out Control Structures
* Fine Points of Formatting Control-Structure Blocks
    * 避免 begin-end pairs 沒有縮排，會讓 begin, end 不屬於 control construct 也不屬於 statement
    ``` c
    for ( int i = 0; i < MAX_LINES; i++ )
    {
        ReadLine( i );
        ProcessLine( i );
    }
    ```
    * 避免重複縮排，statement 多縮排一次不僅比較複雜遇到 nest statement 就會變得很難讀懂
    ``` c
        for ( int i = 0; i < MAX_LINES; i++ )
        {
            ReadLine( i );
            ProcessLine( i );
        }
    ```
* Other Considerations
    * 在沒有 begin-end pairs 情況下使用 blank line 區分出無關的邏輯
    * 保持 single-statement block 的排版一致性
    * 對於複雜的 expression 把不同的 condition 放在不同的 line
    * 避免使用 goto，因為會難以證明程式正確性跟難以排版，若一定要用到可以將 label 名字使用全大寫跟擺在明顯的地方，上下都圍繞 blank line，不縮排向左靠齊都可以讓 labe 很明顯

#### 31.5 Laying Out Individual Statements
* 每行長度不超過 80 個字
    * 超過 80個字比較難讀
    * 80個字限制會減少 deep nesting 的情況
    * 現在螢幕比較大一點就可以偶爾超過限制
* 使用空白增加可讀性
    * Logic expression 中 identifier 左右加上空白
    * Array reference 中 index 左右加上空白
    * Routine argument 左右加上空白
* 排版 continuation lines
    * 讓不完整的 statement 明顯一點
        * 讓分開的 statement 很明顯看得出語法錯誤就會讓人知道這是不完整的 statement
        * 把 continuation character 放到 continuation line 的開頭
    * 把相關的 element 放在一起，例如 array reference, argument to the routine
    * routine-call continuation line 與一般縮排一樣
    * 讓 continuation line 的結尾容易被找到
    * control statement continuation line 與一般縮排一樣
    * 不要對齊 assignment statement 的右邊，會難維護
    * assignment statement continuation line 與一般縮排一樣
* 一行程式碼只用一個 statement
    * 把多個 statement 放在同一行只是會讓複雜的 code 看起來很簡單而容易讓人忽略
    * 把多個 statement 放在同一行並不會讓 compiler 知道要優化這行 code
    * 一行一個 statement 讓人可以只從上往下讀然後注意縮排，而不需要從左到右去找還有哪些 statemtn 藏在同一行 code
    * compiler 只會提供 error 的 line number，把多個 statement 放在同一行不容易找到錯誤
    * line-oriented debugger 容易 step through，多個 statement 在同一行就會一次執行全部 statement
    * 一行一個 statement 讓人容易修改、註解、刪除 statement 
    * C++ 避免使用多個 operator 在同一行，因為沒有定義 evaulated 的順序，所以任何結果都有可能產生，每行只做一個 operation 不但容易看出 bug 也讓其他人不用思考 side effect 的問題
* 宣告 data 的排版
    * 一行只宣告一個 data
    * 宣告 data 的地方要靠近使用的地方，不但減少 data 的 live time  之後 refactoring 成 routine 也比較方便
    * 有道理的排好 data 宣告的順序，通常相同 type 放在一起因為相同 type 通常會用在一起
    * C++ 將 asterisk 放在變數那邊，如果放在 type 那邊又有多個 statement 視覺上會以為所有變數都是 pointer 但其實只有第一個

#### 31.6 Laying Out Comments
* 將 comment 跟相關的 code 一起縮排
* 每個 comment 至少有一個 blank line 讓其他 programmer 想要 over view program 比較容易

#### 31.7 Laying Out Routines
* 使用 blank line 分隔出 routine 的區塊
* 使用 standard indention 在 routine argument
    ``` c
    public void InsertionSort(
        SortArray data,
        int firstElement,
        int lastElement
    )
    ```
    
#### 31.8 Laying Out Classes
* Laying Out Class Interfaces
    * Header comment 描述 class 的使用方法
    * Constructors 跟 destructors
    * Public routines
    * Protected routines
    * Private routines 跟 member data
* Laying Out Class Implementations
    * header comment 描述內容
    * Class data
    * Public routines
    * Protected routines
    * Private routines
    * 當有多個 class 在同個 file 裡面，使用多個 blank line 代表新的 class 的開頭，如果語言沒有限制最多幾個 file 則最好一個 file 一個 class
* Laying Out Files and Programs
    * 只放一個 class 到一個 file，file 應該包含目的相同的一堆 routine，而這些 routine 可以稱為 class，
    * file name 要與 class name 相關
    * 使用至少兩個 blank line 將相同 file 裡的 routine 分開

### Chapter 32: Self-Documenting Code
#### 32.1 External Documentation
* Unit development folders: 開發者在開發過程中備註的文件，包含為何採用該設計、相關需求、實作方式、設計備註
* Detailed-design document: low-level 設計的文件，說明選擇該設計方式的理由

#### 32.2 Programming Style as Documentation
* 相較於外部的文件，內部的文件是指列在 source code 之中的，是最為詳細的文件也是與 code 最高度相關的文件
* Code-level 文件主要來自於好的 programming style，包含程式架構、使用直接且容易瞭解的實作、好的 function 跟 variable name、排版清楚、最簡化 control-flow 與資料結構

#### 32.3 To Comment or Not to Comment
* 註解應該要表達無法從 code 表達出來的東西，不應該重複解釋 code 已經表達過的事情
* 註解要能讓人快速找到想要看的部分


#### 32.4 Keys to Effective Comments
* 註解種類
    * Repeat of the Code: 重複解釋 code 要做的事情，只是讓讀的人有更多東西要讀，並沒有提供任何額外的資訊
    * Explanation of the Code: 解釋程式複雜、詭異的部分，但如果程式複雜到需要註解或許可以考慮直接改良而不是加上註解
    * Marker in the Code: 用來提醒開發者尚未完成或代處理的部分，需要規定大家都使用相同關鍵字來當 marker 以便日後搜尋，release 之前務必檢查這些 marker
    * Summary of the Code: 使用一兩句話總結 code 作用，讓人可以容易找到需要修改的地方
    * Description of the Code’s Intent: 表明這段 code 的意圖，通常使用在描述問題而不是解法
    * Information That Cannot Possibly Be Expressed by the Code Itself: 無法在 code 中表達的資訊，例如: 版權宣告、保密通知、版號等等
* 有效率的註解
    * 通常需要花很多時間寫註解有兩種
        * 註解風格需要花時間很多時間，請使用其他省時間的風格，如果註解不容易更改，維護註解變困難後會導致註解過時並容易誤導
        * 難以使用註解表達程式作用，可能代表並不了解這段程式的作用，所以寫註解的時間其實是了解程式作用的時間，而這段時間是必要的不管有沒有要寫註解
    * 使用容易修改的註解方式: 太過 fancy 的註解都難以修改
    * 使用 Pseudocode Programming Process 減少註解時間: 先寫好 code 的註解再來寫 code
    * 把註解加入開發過程: 如果把註解放在最後會讓人覺得是多一項負擔，最後在寫註解還需要回想當初開發這段 code 的目的，如果覺得已經很難寫 code 了還要寫註解就應該先停下來把註解寫好釐清思緒再來寫 code，同時註解也寫好了
    * 效能並不是不註解的理由: 古老時代註解可能會導致效能變差但現代已經不會有所差別

#### 32.5 Commenting Techniques
* Commenting Individual Lines: 通常好的 code 不太需要為單行作註解，可能是複雜到需要註解或標示含有的錯誤
    * 不要使用意義不明的註解
    * Avoid endline comments on single lines: 通常都是重複 code 的目的，空間比較少只能寫短的註解，不易修改因為需要縮排好
    * Avoid endline comments for multiple lines of code: 需要讀完程式碼跟註解才能知道這是這段程式碼的註解而不是單行註解
    * 可以使用 endline comment 的例外:
        * 資料宣告可以使用 endline comment: 通常資料宣告比較短所以後面有足夠空間寫註解
        * 避免使用 endline comment 來註解維護事項: 註解應該是要說明為何 code 可以正確運作而不是為何無法運作，使用 version-control 軟體來做比較適合
        * 使用 endline comment 標示出 block 的尾端
* Commenting Paragraphs of Code: 使用一到兩句話說明這段 code 的目的，而不是實作方法，如果實作方法有誤則說明目的的註解不需要更改，所以說明目的註解更容易維護
    * 註解要能表達程式的目的，不需重複程式邏輯，盡量提供程式沒有提供的資訊，藉由思考如果要把這段程式變成 function 則會如何命名就可以比較容易下好的註解
        * Poor: 檢查所有輸入字串直到找出 "$" 或者全部找過
        * Good: 找出輸入字串有沒有 "$", 找出 command-word terminator ($)
    * 專注於 code 本身的註解，為變數取目的明瞭的名字，例如 done 比較不清楚但 foundTheTerminator 比較清楚，或者直接包裝成 function
    * 段落註解應該要說明這段 code 要做什麼而不是怎麼做，這樣才會專注在問題本身而不是程式上，如果程式有足夠說明時可以把註解變成段落標題讓人容易找到
    * 使用註解來讓讀的人可以快速掌握程式作用跟要去哪邊看更詳細的情況
    * 讓每個註解都有意義，如果太多註解會模糊程式本身
    * 註解特殊的部分，像是使用不直覺的方式來實作是因為效能考量
    * 避免使用縮寫在註解中
    * 區分主要與次要的註解
    * 註解錯誤或不再規格的 feature
    * 註解為何不使用好的 coding style
    * 不註解 tricky code 而是改寫
* Commenting Data Declarations
    * 註解數值的單位，最好把單位放進變數名稱裡面
    * 註解數值的範圍
    * 註解數值背後的意義，如果語言不支援 enum 型態的話
    * 註解輸入資料的限制，也可以用 assertion 限制
    * 註解 flag 的每個 bit 的意義
    * 註解中的變數名稱要與被註解的變數名稱一樣確保改動時可以被搜尋到
    * 註解 global data 表示為何需要 global，使用時也要表明是個 global 變數
* Commenting Control Structures
    * 在每個 if, case, loop or block 前加上註解，這類通常都需要解釋而且在前面也容易讓人看到
    * 註解在 control structure 的結尾，對於很長或很深的 loop 這類註解可以幫助讓人理解邏輯結構
    * loop 後的註解當成一種警告，代表 loop 已經過長需要重新改寫比較好
* Commenting Routines
    * 讓註解與 code 保持相近確保改動時註解也會一起被改動
    * 使用一到兩句話描述 routine，如果無法做到代表 routine 太過複雜需要重新設計
    * 註解在參數宣告的地方
    * 使用 code documentation utilities 像是 Javadoc，可以容易維持 code 與註解的一致性
    * 區分輸入與輸出的資料
    * 註解預期的資料
    * 註解程式的限制，說明在未預期的情況下會產生何種輸出
    * 說明 routine 會對 global 造成什麼變化
    * 註解使用的演算法來源
    * 使用註解標記出特定位置，以便後續搜尋可以快速找到想要的地方
* Commenting Classes, Files, and Programs
    * General Guidelines for Class Documentation
        * 從設計的角度說明 class，提供無法從 code 看出的資訊才是有用的，描述設計方法跟為何採用跟棄用某些設計方法的原因
        * 描述限制、假設、錯誤處理的責任、演算法的出處，對於 global 的影響等等
        * 註解 class 的 interface，如果 programmer 無法單純從 interface 就了解該如何使用 class 則封裝不完全
        * 不要註解 class 內部的實作細節，不然會破壞封裝的原則
    * General Guidelines for File Documentation
        * 描述檔案的作用及內容，說明為何 routine 都在這個檔案，為何不同 class 要放在同一個檔案，為何要分散放到不同的檔案
        * 把維護人資訊放到檔案中讓人知道誰對這個檔案負責，在大型專案中需要讓特定 programmer 負責特定區塊的程式
        * 包含 version-control tag
        * 包含版權宣告
        * 檔案名稱需要與內容的 class 相近
* 把 code 想成一本書來做註解有助於 programmer 了解 code 的組織性

### Chapter 33: Personal Character
* 只有自己決定要成為好的 programmer 才會慢慢變成好的 programmer
* Programmer 不需要很聰明因為要徹底了解程式需要有無限的記憶來吸收所有的細節並且同時處理
* 越能體會自己無法單靠小小的腦袋去理解程式越能成為好的 programmer
* 好的 programming practice 都是在降低對大腦的負擔
* 體會到自己的極限後便會不斷的探索來補償自己的不足
* 隨時保持好奇心才會跟上時代
    * 如果不了解 feature 如何作用可以使用小程式來測試理解，能快速的遇到錯誤並從中學習
    * 從好專案中學習，通常著名的專案都會包含各種 problem solving 的技巧
    * 把程式碼當成小說來讀
    * 多讀其他書可以拓展視野
    * 嘗試成為更好的 programmer，跟著好的 programmer 的成長歷程
* 誠實的面對自己
    * 如果不是專家就不要假裝成專家
    * 坦誠面對自己的錯誤
    * 了解 compiler 的警告而不是裝作沒看到或隱藏起來
    * 徹底了解程式而不是編譯完後看看能不能跑
    * 提供真實的狀態報告
    * 提供真實的預估時程，如果被要求調整也要堅守底線
* 大型專案最注重的是紀律，大家需要照標準做事才能讓最後的成品有一致性
* 面對不想做的工作有三種方法
    * 不斷的推遲工作
    * 用最少時間做完
    * 寫一個工具去做讓自己永遠不需要去做
* 建立好習慣是很重要的因為之後做事情都是依照之前的習慣，如果要改掉不好的習慣就要用一個好的習慣去取代

### Chapter 34: Themes in Software Craftsmanship

### Chapter 35: Where to Find More Information
