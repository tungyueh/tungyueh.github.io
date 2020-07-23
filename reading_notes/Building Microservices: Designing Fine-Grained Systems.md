# Building Microservices: Designing Fine-Grained Systems
## CHAPTER 1 Microservices
* Domain-driven design 幫助我們了解如何用 code 來表達現實世界的東西
* Continuous delivery 讓我們更有效率的推出產品
* On-demand virtualization 讓我們可以依照需求改變環境的規模
* Microservices 的出現是來自於融合現代軟體需求所產生
* 大多數公司發現使用 microservices architecture 可以更快速推出產品更使用新技術，更容易應付不同的需求

### What Are Microservices?
* Microservices 是一群小的、自主的 servicess 一起工作
#### Small, and Focused on Doing One Thing Well
* 當不斷加入新功能會使 codebase 變大以至於相似功能散落於各地讓修復 bugs 跟新增功能變得困難，所以在 monolithic system 中，我們盡量讓 code 相似的部分放在一起
* Microservices 使用相同方式讓 services 獨立，注重 business boundary 讓在裡面的 code 很明顯是為此功能所寫
#### Autonomous
* Microservice 是獨立的實體，雖然會有多餘的 overhead 但可以讓我們在分散式系統中更容易理解
* Microservice 彼此都是使用網路來溝通，強迫分離與減少 coupling
* Microservice 要仔細考量那些需要公開那些需要隱藏讓 consumer 與本身的 coupling 減少
* Microservice expose API 與 consumer 合作

### Key Benefits
* 雖然以下好處在分散式系統也是擁有，但 microservices 從根本考量這些好處而設計出來帶來更高維度的好處
#### Technology Heterogeneity
* 如果系統是由多個 service 所合作而成則可以挑選最好的方法來實作個別 service
* 使用不同的技術可以更容易增加系統效能
* 採用新技術可以降低風險
#### Resilience
* 系統一部分壞掉的時候如果可以隔離問題讓其他部分可以正常運作就可以讓系統更加穩定
* Monolithic service 中只要一部分壞掉則全部就會失效，但在 microservices 可以使用 service boundary 當成防火牆避免系統全部失效
* Microservices 系統會有額外的問題需要處理，例如網路失效
#### Scaling
* 對於 monolithic service 需要將全部一起 scale，但 microservices 可以只 scale 需要的部分來節省成本
#### Ease of Deployment
* 些微改動對於 monolithic service 需要全部重新 build 後 release 造成 release 緩慢，進而讓不同版本差異更大、風險更高
* Microservices 獨立 deploy 有改動的 service，當問題發生更容易知道是哪邊出錯馬上 rollback，也可以更快速推出新功能
#### Organizational Alignment
* 小的團隊負責小的 codebase 會更有效率，microservice 讓我們將組織與 service 更加貼近讓團隊人數與需要處理的 codebase 相符
#### Composability
* Microservice 可以讓 service 的功能以不同的方式被使用來適應現代有需多不同的需求
#### Optimizing for Replaceability
* 當 service 都很小的時候可以很容易刪除會重寫

### What About Service-Oriented Architecture?
* Service-oriented architecture (SOA) 是一種設計使用多個 service 一起合作提供系統的功能，這些 service 彼此以網路溝通而不是 process 裡的 method call
* SOA 推廣 service 的重複利用跟容易維護與修改
* SOA 是很好的點子但不知道該如何達成

### Other Decompositional Techniques
#### Shared Libraries
* 提供 library 讓不同 team 可以使用
* 缺點是 library 需要用同一種語言、部屬時候需要跟著 library 一起
#### Modules
* 有些語言提供 modular decomposition 可以 deploy 在 running process

### No Silver Bullet
* Microservice 並不是萬靈丹，使用它同時需要處理分散式系統有的問題，需要更了解部屬、測試、監控等方式

### Summary
* 了解到 microservices 的好處與跟其他 decompositional techniques 的差別

## CHAPTER 2 The Evolutionary Architect
* Microservice 讓我們有很多不同的選擇但也因此需要作出不同的選擇
### Inaccurate Comparisons
* Architect 負責確保技術可以整合來使系統可以給客戶使用，可能是與一個或多個團隊合作，會影響到軟體品質
* 我們嘗試以其他行業的方式來解釋我們正在做的事情，但又無法完全交代清楚，常常處在模糊地帶
* 其他行業的 architect 有嚴格的規定跟紀律，但軟體行業的 architect 沒有對於合格的定義
* 為了讓其他人了解所以挪用了其他專業的名稱，但也造成誤解
* Architect 會讓沉迷在圖表文件之中而遺忘了思考不斷變動的軟體本質，導致設計出來的系統無法彈性的符合需求
* 如果我們將 engineer 或 architect 的概念直接從其他地方挪用則會讓所有人造成傷害，所以需要重新定義符合我們情境的用詞

### An Evolutionary Vision for the Architect
* 軟體需要更快速的推出而且成品需要可以隨時更動符合需求，所以應該要專注於設計好的 framework 讓軟體可以進化成長而非製造出完美不可變動的成品
* IT architect 應該要像城市規劃者專注於考量目前與未來的情況規劃好區域規劃而不是實際去建造建築物
* 軟體就像城市需要迎合使用者的需求而變化而不是設想好所有可能的情形，architect 需要考量開發者跟維護者是否容易根據需求作改動
* Architect 需要知道有沒有按照規劃進行，如果越少規定則需要越多的參與來知道計畫是否有被正確執行，所以需要訂好大致的計畫然後只參與特定的實作
* Architect 需要讓使用者與開發者同樣開心

### Zoning
* Architect 不需要注意 service 裡面在做什麼而需要注意 service 之間怎麼溝通跟如何監控這些溝通來知道系統的狀態
* 雖然 team 可以對自己負責的 service 採用不同技術，但會讓人員難以在不同 team 流動跟難以招募人，如果不同 team 都採用不同的技術則可能會對於如何 scale 這些技術缺乏經驗
* 不同 service 都用不同 expose 技術會讓 consuming services 非常頭痛需要支援多種 interchange，所以要好好注意 service 之間的溝通
* Architect 需要參與 team 的運作來了解開發者的需求才有辦法打造開發者適合的架構

### A Principled Approach
* 設計系統就是再做決定中做取捨，而 microservice architecture 讓我們可以做出很多不同的取捨
* 透過 principles 跟 practuces 可以幫助我們做出好的決定
#### Strategic Goals
* Architect 不太需要定好 strategic goal 通常只需要確認技術跟的上目標就好
* 如果需要訂公司的 technical vision 則需要多花點時間考慮非技術面的部分
#### Principles
* Principle 是一堆 rule 幫助達成目標，有時也會改變
* Principle 數量最好少於 10 個才容易被記住也不容易重複或矛盾
* Heroku's 12 Factors 是一堆設計 principles 幫助 application 可以在 Heroku platform 運作良好。有些 principle 像是無法改變的限制。
#### Practices
* Practices 是如何實踐 principle 的方式包含詳細的實作方式，不同技術都有不同方式，開發者可以直接依照方法來使用
#### Combining Principles and Practices
* 只要可以讓系統進行好的演化則 principle 與 practice 的分別就不重要
* 在大組織中需要把 principle 與 practice 區分，因為不同的技術要有不同的 practice
#### A Real-World Example
* Practice 會規律的變動而 principle 通常保持固定

### The Required Standard
* 設計系統取捨時需要考量需要多少可變動性，考慮 service 之間哪些需要 constant 哪些不需要，在設計 microservice 時候不能失去 big picture，定義好每個 service 的 attributes
#### Monitoring
* 需要有整個系統的狀態，建議所有 service 都會發出狀態跟有統一的監控 metrics
* 不管是用 push 或 poll 的方式集中個 service 的狀態，重點是要統一就好
#### Interfaces
* 使用較少的 interface 來 integrate 是較好的作法
#### Architectural Safety
* 不要讓壞掉 service 毀掉整個系統，每個 service 都要做好 failure handling 避免系統太脆弱
* 根據規則做事才能快速又正確的處理錯誤

### Governance Through Code
* 花時間去確保大家都遵循 guildline 不是很容易做到
#### Exemplars
* 將標準或 best practice 寫成範例提供給開發者可以讓人探索 code 進而遵循
#### Tailored Service Template
* 如果讓開發者很容易依照提供的 guideline 開發就容易遵循 guideline
* 依照需求使用 library 可以減少需要的開發時間，藉由這些 library 讓 team 的開發速度變快而且不會讓 service 太糟
* 使用 library 就會造成選用語言的限制，要考量不用 library 可能造成的後果跟限定技術的好壞
* Service template 要謹慎使用，盡量為 optional，如果強制會讓開發負擔加重
* 過度的 shared code 後可能會造成 service 的 coupling 讓變動變緩慢

### Technical Debt
* 為了短期的利益而造成長期的成本稱為技術債，可能是為了快速推出 feature 所造成的
* 技術債不只是因為想要走捷徑而產生，也有可能是因為技術觀念改變導致系統不合也會
* Archietect 需要注意整個藍圖而了解其中的平衡，讓技術債可以被追蹤與償還

### Exception Handling
* 系統沒有依照所設計的運行就會產生例外，透過將這些例外記錄下來可以重新檢視是否與認知有所不同進而決定是否改變 principle 
* 有規模的公司會有許多限制來避免例外發生，而 microservice 給予 team 充分的自由來親自處理例外

### Governance and Leading from the Center
* Architect 的 technical goverance 是要確保實際的東西符合 technical vision
* Architect 要確保 principle 可以指導開發並且符合組織策略
* Governance 是團體活動需要大家一起不斷討論及改變
* Architect 職責在於讓 group 可以運作，而 group 整個要負責 governance
* 有時候 group 做出 architect 不同意的決定，但 architect 應該要依照 group 的決定因為 group 通常比個人睿智
* Group 是真正開發的人所以要放手讓他們自己決定， architect 要做的事情只是確保事情不會往最糟的方向去

### Building a Team
* 作為負責 technical vision 的人不只是要做出決定而是要幫助成員成長一起構築 vision
* 幫助周圍的人有很多不同的形式，在 microservice 中可以有自己的 service 所以比較容易成長
* 好的軟體通常由好的人所打造，要同時注重技術與人

### Summary
* Architect 要有 technical vision、了解所做的決定的影響、能夠與大家合作構築 vision、vision 能夠隨需求改變、找到標準與自治的平衡、管理團隊有依照 vision 實作
* Architect 能夠理解 feature 都是一連串的取捨之下才產生的，要能夠好好平衡這些取捨