#ModernWeb2016
08/24 Day 1

09:40 - 10:30 Typing
Douglas Crockford
PayPal
"JavaScript: 優良部分" 的作者

Intro
This talk looks at the history of typing (指的是打字, 而不是資料型別), from the invention of the typewriter, to electrification, to computers, to poking pieces of glass with our fingers. It also looks at the special typographic requirements of programming, and uses typing as a metaphor for how we evolve our technologies.

Rebus Principle
文字本來是表意的，但會拿它的音去標其他同音或類似音的字
例如：用 bee 和 leaf 去標 belief
用中文舉例則是：
”象“，本來是指大象，被借去表示 “樣子” 的意思
而後來很晚才又創造出 “像” 這個字來表示 "樣子"  

語言的形成 
字母由來 (參考資料：http://news.gamme.com.tw/363852 感謝hubuki提供）
Phoenicia --> Greece --> Rome

ABCDEFZHIKLMNOPQRSTVX
--> CG (表達不同音), IJ, UV (表達子母音), W (應該要稱作 double-V)
--> & (e + t) 最後沒有納入字母
--> 小寫字母的出現

Excerpt from The Declaration of Independence
Life, Liberty, and the Pursuit of Happiness (s 長得像 f)
Long s: ſ ; round s: s
 德文的 ß 其實是兩個 S 的組成

Technology 
- Marks on media
- Printing
- Typing
- Digital Media

打字機 
1867, Christopher Latham Sholes, 打字機之父, 將打字機商業化
上下排按鍵相差 1/4 格是因為要錯開機械式槓桿
QUERTY 排列式要降低按鍵打架的機率
最早的電腦雛形 人們很久以前就開始"Computing"
編碼 ASCII
字型的混淆 (Ø vs O, 數字 1 vs 字母 l (小 L))
CR, LF
DEL (RUB OUT): ASCII 127, punch card a row of holes

中間提到0 , 1必須用小指才按的到, 但人們不想改變0, 1在打字機上的位置? 有點忘記
0,1 因為小指力氣不足，因此沒有安排在機械打字機上，1  在後來被加上，但 0 就一直放在錯誤的位置至今
用英文的O和小寫l 來代表
因為容易把0與O搞混，所以用Ø來區分。https://en.m.wikipedia.org/wiki/Slashed_zero

Shift key, Control key  的由來 
Shift: 源於打字機按鈕，可以按住上移(Shift)打印頭，以切換大小寫 https://youtu.be/YtG6YAxL89I
Tab key (Ctrl + I (eye))
ESC
原本用意真的是跳脫字元(escape)，但現在只剩下結束程序的意義
我有玩BBS我知道XD

Crockford Keyboard
排的方方正正
依照字母順序排列

等寬字型 vs 非等寬字型

Programma
http://programma.us
寫程式用的typeface (垂直置中、空括弧中間有空隙)
:= += -> >< (x) [f] {w} f() <> \/ /\   ...etc.
cwxvywz

技術的演進多半不是憑空想像，而是透過改善先人成果，但也繼承了歷史包袱 (為了解決當時問題的解法，拿到今日看會是不好的設計)。所以要時時審視，時空背景一旦改變，過去的技術是否已經不合時宜，需要打掉重練
從 keyboard layout 改變的歷史看 legacy 的恐怖影響，也是這就是他簡化 JS 的原因吧，去掉 legacy 不妙的地方。
個人覺得用 keyboard layout 會比 keyboard typing 要來的好些些

10:30 - 11:20 Building and Deploying Scalable Microservices with Go & Kubernetes (Ian Matthew Lewis / Google)
Ian Matthew Lewis
Google
Intro
As systems grow, using configuration management to pin applications to a specific host and use the host as the application unit doesn’t scale. Applications need to be broken up into smaller services. One application per host becomes increasingly inefficient.
Containers have opened up many new possibilities in how we can deploy our applications. Containers enable us to run a service on any host at any time and we can deploy many containers onto a single host.
Managing the containers is easy with a system like Kubernetes. This talk will help attendees wrap their minds around complex topics like distributed configuration management, service discovery, application scheduling, and resource management at scale. I will cover many concepts in Kubernetes, such as Deployments, ReplicaSets, and ConfigMaps and illustrate how developers can use these tools to deploy their services.

Monolithic Apps
Requires large resources per instance
Hard to scale properly
Hard for teams to have ownership of code
Hard to set up SLOs around performance and availability
(SLO : Service Level Objective)

Microservices (SOA)
break up a big app into smaller apps
each app can be scaled independently
參考資料
http://blog.maxkit.com.tw/2015/07/microservices.html

Shared Machines
No isolation
No namespacing
Common libs
Highly coupled apps and OS

Virtual Machines
Some isolation
Inefficient
Still highly coupled to the guest OS
Hard to manage

Containers

- For the last 15 years, Google has been building the world's fastest, most powerful infrastructure
- Search / Gmail / Google Maps / Chrome / Android

Cloud Technology Innovations
- 2003 GFS
- 2004 MapReduce
- 2006 Big Table
- 2007 ...

Google has been running all our services in Containers for over 10 year, We start over 2 billion containers every week.

Containers Microservices
- packaging apps / libs together
- on top  of kernel

Reasons for using containers
Fast
- simple and fast compared to VMs. Can be started in just a few milliseconds.
Portable
- can be run in many environments
Efficiency
- low overhead. resources used by containers can be limited.

Container Management
- How to deploy to multiple nodes?
- How to deal with node failures?
- How to deal with container failures?
- How do you update your applications?
- How can your containers discover and communicate with each other?

Large-scale cluster management at Google with Borg
http://research.google.com/pubs/pub43438.html

Developer View

job hello_world = {
    runtime = { cell = 'ic' }
    binary = '.../hello_world_webserver'
    args = { port = '%port%' }
    requirements {
        ram = 100m
        disk = 100m
        cpu = 0.1
    }
    replicas = 5
}

Kubernetes

Greek for "Helmsman"; also the root of the word "Governor"
- container orchestrator
- runs containers
- supports multiple cloud and bare-metal environments
- inspired and informed by Google's experiences and internal system
- open source, written in Go
- manage applications, not machines

A 10 years old system
http://kubernetes.io/
Support By CNCF (Cloud Native Computing Foundation) (https://cncf.io/)
Borg: The Predecessor to Kubernetes
Scheduler works similarly to Tetris.

Deployments & ReplicaSets
Rolling Updates

Services
a group of pods that work together
- grouped by a selector
Defines access policy
- load balanced or headless
Gets a stable **virtual IP** and port
- sometimes called the service portal
- also a DNS name
VIP is managed by kube-proxy
- watches all services
- updates iptables when backends change

Hides complexity - ideal for non-native apps
 
Demo
Web --> Guestbook --> Redis
Web --> NGWord

Wrap Up
https://cloud.google.com/container-engine

11:50 -12:30
A - 報導者 -  一場開放原始碼的實驗 (簡信昌/ 報導者ＣＴＯ)
Intro
報導者，不只是臺灣第一個實驗非營利經營模式的媒體，更是一次臺灣媒體網站的開源革命。
從推廣開放原始碼，籌辦研討會。到去年第四季正式透過『報導者』的成立，進行一場開放原始碼的革命跟實驗，從整個網站架構的原始碼全部以 MIT 授權釋出，到原生內容以『創意共享（Creative Commons）』授權開放使用，從這場實驗，可以讓一般企業看到一些不同的思考方向。

講者資歷：P3Party、YAPC、OSDC、Yahoo
g0v
經濟動能廣告 -> 工程師火啦～ -> g0v 開始運作
去中心化
不只政治，還有文藝 -> Opendata、萌典......
問為什麼沒有人來做，你就是沒有人！
虛擬到實體活動
g0v => open data  意外之旅~

 報導者
由來
媒體業快倒了，要有新發展
中天不可信，自己來
About
非營利組織
產出慢、內容深入
視覺化、互動實驗
急診室 https://www.twreporter.org/a/newsgame-emergency
Open Source
Open Content
(報導者)Why Open Source
技術不是一切（非媒體的核心價值）
內容才是王道
如何相信媒體=>無解
台灣產業不尊重技術（忘了怎麼提到）例子: 上報（http://www.inside.com.tw/2016/07/14/tech-media）
Start
9/14 公布
12/16 上線
用 Wordpress？
技術
React + Redux
Eve Framework
Apache
MongoDB
Docker
CMS: https://atavist.com/
原本沒 API 是報導者自己挖出來的
有效能瓶頸
無法滿足需求
打算 Migrate to http://keystonejs.com/
為什麼要搞這麼複雜
如何應付有特殊新聞時的突發大型流量 -> Scalable
容易 reuse
KeystoneJS
使編輯工具更方便
內容編輯器改 Draft.js
Next
Revamp
APP
Search
Keystone.js i18n
Visualization Tool
AMP
Recommendation
附加功能
ElasticSearch
Redis
Static Page Generator
Logger
APP
Lesson Learn
Transitional Industry
Engineers don't want to join the industry
what will be good for News site
Building environment is more important than building source code.
Architect design is important.
工程師不太願意加入媒體業
仍是傳統觀念的人把持這個產業
如何打造一個Developer的環境

B - 快快樂樂學會 Angular 2 網站開發框架 ( Will 保哥 / 多奇數位創意技術總監 )
Intro
在 Web 的世界裡，推坑是唯一不變的真理，有好的技術，就是要拿出來一起分享。想當年，AngularJS 的出現，帶給大家的是一次又一次的驚喜，但這高潮迭起的學習曲線，著實讓人又愛又恨。大家也見識過 React 的絢麗登場，效能優異的 VDOM 技術霎時震攝了不少前端攻城獅，不過能力越強，責任也就越大，隨之而來的便是架構上的混亂與不知所措。現在，Angular 2 的到來，不但挾帶強大的架構優勢與全新的元件化技術降低學習門檻，優異的 TypeScript 與各式開發工具的火力支援更是如虎添翼，如果再算上國內外龐大的社群基礎，可預見的必在這活熱的前端世界掀起一場絢麗的戰火。本堂講座，將帶大家快快樂樂上手 Angular 2 網站開發框架。

套件改版 (海濤梗) :laughing: 
不要執著你之前學會的任何技術
跟Angular 1比較
速度更快
學習曲線更低
平台支援更強大
Angular 2 的開發語言
Typescript 2, es6, es5, dart
Angular 2 的開發工具
Visual Studio Code (建議)
Visual Studio 2015
WebStorm (商用)
...
元件的組成
範本 (Template)
類別
中繼資料 (Metadata)
程式碼結構
import { Component } from '@angular/core';

@Component({
    selector: '...',
    templateUrl: '...',
    styleUrls: [ 'app.component.css' ]
})

export class AppComponent {
    ...
}
使用 Angular CLI 建立專案
> ng new projectname
> cd projectname
> ng serve
使用 Angular CLI 建立元件
> ng g c componentname
Angular 2 開發框架介紹
http://blog.miniasp.com/post/2016/07/26/Introduction-to-Angular-2.aspx
使用 TypeScript 開發，寫起來很像 C#。

Webpack 會幫忙注入 Javascript
網頁會自動重整，不用手賤按 F5 或是 Ctrl+R (建議大螢幕或雙螢幕開發)

{{title}}
(click)="title='...'" event binding
[title]="title" property binding - support both DOM property and HTML attribute
應該是 DOM property & HTML attributes 嗎？
should be. :)
It is.

{{ }} 的 binding 方式內建 HTML Encode

{{ item.date | date: 'y-MM-dd' }}

組件化
建立directive：<app-article [item] = "item"></app-article>


http://www.slideshare.net/WillHuangTW/happy-leaning-angular-2-web-framework-modern-web-2016


C - 寫出所有人都能輕鬆讀懂的測試程式 (Cucumber.js)
https://github.com/cucumber/cucumber-js

BDD:
有效溝通
減少落差
支援多國語言 

Cucumber.js是
會說話的程式碼
用口語的方法寫測試
讓溝通更順暢
測!試即文件

Gherkin
Cucumber.js的描述語句
描述商業邏輯、程式行為

https://relishapp.com/

文件可以直接丟CI CD，也可以直接轉換成web網站

Feature(功能)：功能說明、使用情境
Scenario(場景、劇本)：操作的方式、特定的流程
Step(步驟)：流程步驟

Given(假設)：前情提要、初始化
When(當)
Then(那麼)

火力展示: node.js+Cucumber.js+chai 

測試不只是測試
產生測試報告
製作可以瀏覽的文件
Pickles(Win Only)
產出各種格式的報表
html
docx (???：老闆...... 你知道的
pdf
...
支援markdown
支援搜尋
有效產出
產生報表

產表工具
cucumber-html-report

測試涵蓋率
Istanbul

13:30 - 14:10

A - 電子商務 Audience Marketing, Growth Hacking 自動化設計及成效報告
Audience Marketing(受眾)
contact
behavior
loyalty (RFM model)

情境：80 歲老奶奶在萬年打卡
   可不可以賣他鋼彈？

從台灣受眾推測日本受眾
當消費者購買/點擊行為發生，貼標籤在消費者身上(產品類型/興趣/年齡/性別...)

Growth Hacking Model  AARRR
Acquisition
Facebook Id / Line mid / Google ID /... 識別不同平台的使用者 將資料綁定於UID
追蹤單一 user 在不同平台上的行為 
Activation
Searched Keywords
Active Interest
Product Catalog
Purchase history
Browser history
Retention
Referral
Revenue

參考資料
cookie exchange: 點擊廣告後可在各平台/device的facebook看見相關廣告
SEO 球來就打: https://www.awoo.org/poa
SEO 關鍵字建議工具: https://www.awoo.org/kelo 天下污垢無狗 (囧

B - React Native for Web
Why React Native for Web?
團隊編制：iOS * 1 ,  Android * 1 , FrontEnd *1
但是FED幫不上mobile的忙
藉由React 教學相長

過去 - 開發 App
iOS 工程師 --> iOS App
Android 工程師 --> Android App
Front-end 工程師 --> 幫不上忙
現在 - 開發 App
FrontEnd工程師
   ↓
React Native App
(iOS,Android)
↗                    ↖
iOS工程師         Android工程師

開發速度: 280% up
Bug 消化速度: 250% up
有這回事XD?
新挑戰- Omni-Channel App(全渠道)
不需要安裝，可快速體驗服務
介面一致       

VDOM --> WEB VIEW

React Native
VDOM --> iOS View
 ↘Android View

https://github.com/necolas/react-native-web
============================= Setup =========================
先有React native環境
install react native web
準備 webpack環境
YEOMAN => environment generator script
https://github.com/leeabc/generator-react-native-web
============================== 實戰 ==========================
找出附近的寶可夢，並顯示 IV 列表
Backend:
Express 4.x
Pokemon-GO-node-api
GPS資料
RN's navigator.geolocation

跨平台更進一步!
同時開發 iOS, Android, Web
搭配 Electron 就可跨足 5 平台 (+Mac, Windows)

疑慮
能否得到 React Native 的青睞
支援的完整度


C - 從圖資學出發，探索網頁與搜尋引擎的本質，一起好好寫好 HTML 吧！ 

HTML5 Semantic Elements
使 HTML Tag 有意義
Schema.org
SEO
meat:keyword已經被google放棄
不願面對的過往
Table Layout
被塞到爆的 metadata
被 Google 放棄惹
Google Bombing
一堆 div => div濫用病（同種:table濫用病）
Information Science + Library Science -> HTML + SEO/SE
knowledge -> information -> data -> information -> knowledge ....
靈的轉移！
Information => Inform（語言 / HTTP協定）、Form（聲波 / 純文件）、Format（中文 / HTML)、Formation（廢話 / 網頁內容)
網站 -> 書，搜尋引擎 -> 圖書館
如何有序地收錄並容易被找到？
書中的篇章
網站中的網頁
開始寫之前要先擬定大綱
各標籤之間有主從關係
語意標籤：article, section, header, footer, nav, aside, h1~h3, p
以內容架構為核心撰寫 HTML , 外觀交給CSS決定
你不該因為外觀，而修改（破壞）你的HTML
Metadata
Open Graph
Twitter Card
...More
搜尋引擎有演算法可以抓到真正的關鍵字
關鍵字定法
Title -> H1 Header
Level 2~3 Header
Description Metadata
工具
W3C Validatorl
https://validator.w3.org/
https://validator.w3.org/nu/
W3C HTML 建議書
https://www.w3.org/TR/html/
W3C HTML5 建議書
https://www.w3.org/TR/html5/


14:20 - 15:00

A - StreetVoice 自動化部署演進
CD & 部署: https://www.ansible.com/
CI: https://travis-ci.org/

部署環境:
development
staging
production
自動化部署的前提
足夠的自動化測試 (unit test with high coverage)
工作流程
git flow (可參考 https://ihower.tw/blog/archives/5140)
workflow
open issue -> feature branch -> commit -> PR (github) -> unit -> merge to develop (send notification to slack after CD done) -> stage -> master -> production
pull request 搭配 code review，通常發生在unit test之後
using Slack to notify everyone, everything
時間
終於要講到部署的演進了
終於啊!
FTP => Fabric => SaltStack => Ansible
為什麼換到最後的Ansible?  這件事情只有幾個人知道
FTP - 到現在其實還是很多人在使用
Fabric - 可以做很多事情，可以做到狀態更新
SaltStack - 
多使用python
使用hubot 控制 saltstack
Ansible  - 坑比較少
相較於saltstack設定比較簡單
寫程式=> 丟上版本控制 => 單元測試 => 自動部署 => 更新程式，狀態
Git                  Travis Cl        Ansible          AWS
什麼時候不能自動化
DB migration (with mariaDB)
在staging 新增欄位
在production 刪除欄位
NoSQL沒差
自動化之後的優勢
Focus on development ex: auto close issue


B - 馭風 － 搜狗分散式追蹤系統的設計與實現
分布式技術特點
 分布式服務
 分布數儲存
 分布式訊息
 分布式計算
服務關係複雜
數據規模大
服務調用鏈路長
無法快速定位性能瓶頸和異常

Google Dapper


為什麼要自建馭風系統
複雜的異構系統
服務體系內有眾多的架構系統java，c++，php等
海量數據儲存與計算
服務化體系
監控報警體系
馭風系統簡介
分佈式平台下的性能監控與監控平台
應用服務調用與追蹤
數據展示、統計分析、預測功能
提升解決問題的效率
日誌儲存、處理
目標
低消耗
對服務性能影響減少
線上服務是否監控可控
低侵入性
盡可能少侵入或不侵入業務系統
透明
減少開發人員負擔
時效性
盡可能快速
海量數據
支持海量數據存儲
支持海量數據中快速檢索數據
處理流程
數據採集
組件埋點
本地日誌
異步傳輸
數據處理
權限檢驗
數據過濾
數據適配
數據儲存
原始數據
統計數據
配置訊息
決策分析
統計分析
閾值報警
趨勢預測
系統設計理念
調用鍊
Trace 樹
多個 span 節點構成
TraceID 被透傳到上下游所有節點，將孤立的系統日誌串連在一起
埋點時間
客戶端發送
服物端接收
服物端響應
客戶接收
埋點類型
單向型
客戶端創建調用鍵生成日誌
雙向型
客戶端 + 服務端，傳輸上下文，生成日誌
數據採集
埋點
低侵入
中間件建埋點
標準格式
C++/JAVA 多語言版本
低消耗
本地日誌
異步收集
高可控
開關控制
採樣率
日誌收集agent
自研的agent
支持斷點繼傳
輸出到消息陣列
支持日誌文件竹心日戈滾動
異步傳輸
埋點
哪些數據
調用類型、對端 IP、服務名稱、耗時、層級關係、異常訊息、業務自定義數據
調用方式
同步
異步
埋點信息傳輸
本地共享，通過線程數據共享方式
傳輸通過Http Header或RPC參數透傳數據到下游
日誌採集
監控日誌 -> 檢測變化現成 -> 獲取日誌內容（列隊） -> checkpoint （處理後的日誌位置）狀態管理 -> Checkpoint 文件
數據處理
消息列隊 -> 讀取消息列隊 -> 日誌過濾（數據格式、權限校驗）-> 數據適配轉換->儲存 SQL （數據日誌、二級處理）-> SQL 引擎
數據儲存
特點
海量儲存，寫多讀少
低延遲查詢
複雜條件查詢
HBase
高可靠性、高性能、面向列、可伸縮的分布式存儲系統
SQL引擎-Phoenix
復染查詢條件http://www.laravel-dojo.com/opensource/wagon
支持SQL方式查詢
高速查詢、低延遲
如何設計
HBase 設計
Rowkey 設計，均勻分布無熱點
TraceID + SpanID 拼接（TraceID 是 UUID）
Phoenix 表設計
增加索引（時間、服務名、應用名）
每個 Span 一條紀錄
不同機器日誌合併
SR、SS和CS、CR字段由不同的機器日志填充
一個Span跨越不同的主機日志，通過Hbase存儲合併到一條紀錄
系統價值
系統性能可視化
服務關鍵路徑
調用鍵路拓撲關係
快速故障定位
趨勢預測與擴容的基礎
總結
客戶端
中間件埋點
異步數據傳輸
可控性
服務端
流式計算
海量儲存
高速查詢
決策分析
分析報表
趨勢預測
行業解決方案
淘寶：Egale Eye
Twitter：Zipkin
點評：CAT
新浪微博：Watchman
唯品會：Mercury
智能化
預測優化系統瓶頸&故障報警自動處理
提高資源利用率
彈性計算&動態擴縮容


C - Rethink React in Elm (鄭遠祥 (LY) / Appier前端工程師)
https://speakerdeck.com/yhsiang/rethink-react-in-elm （↑太帥了)

Programming History
Assembly ：難維護
C：記憶體管理不易
Java：很多奇怪的type
javascript：統一世界

Elm
coding style for UI design
http://elm-lang.org

Elm Data structure
List - 不能用 index 取得 element, 僅可同型態，可轉為 array
Array - 可用 index 取得 element
Set
Tuple - 一組的元素 (有點像 key value pair?)
Dict
Record - immutable 
Ref: https://dennisreimann.de/articles/elm-data-structures-list-array-set-dict.html

Be Direct
pure function --> Stateless function
easy to reason about --> easy to refactor
safe --> reliable
monad --> "callbacks"

Elm Architecture
view - 類似 React 中的 component
model
messages
update

15:30 - 16:10

A - Dance with i13n (與 instrumentation 共舞)
ru031l

What is i13n
instrumentation簡寫i (13個英文字母) n
i18n = internationalization, L10n = localization XD
from instrumentation 確保服務走在正確的路上
透過i13n收集的data來知道我們的長處在哪裡，有哪些可以改進服務的地方 (收集user's work flow, 行為)
有種在喊口號的感覺（搭給恭候母后？
Choose right framework (ex: YWA or Rapid) (R.I.P. YWA)
Stable
Clear and effective report
Life cycle
Framework 的選擇 - Open 比封閉好，有 document 才好用。
GA setup (Google Analize)
看投影片
In-line script 會影響 page render 的效能
好用，但如果Google API修改，會造成工程師維護不易(dependency太高)
Choose a suitable Framework
easy plug & remove
make data set semantic & readable
third..........
gaExt.js 
https://github.com/meistudioli/gaExt
封裝ga
我與GA的補強計畫 https://www.facebook.com/notes/paul-li/10153833718602211/
Google 分析 debugger 吐出資訊太多? 
https://chrome.google.com/webstore/detail/google-analytics-debugger/jnkmfdileelhofjcijamephohjechhna?hl=en
針對single module中可以被點擊的元素才會發送beacon 
為什麼不考慮GTM?
XDDDDDDDDDDDDD
辛苦了
超辛苦… 要不要等投影片就好？ XDD
Module Track
設定想獲取的user行為動作定義 取得beacon
從debugger獲取特定行為資訊
有點不確定 // 加回來了XD
Debugger 獲得行為資訊這件事，不知道是不是需要特別的設定？
註解被爆掉了 =.=a
剛看他範例code是有 針對click動作 輸出"user點擊購買btn" 之類的
Google Analytics Debugger 裝好就可以用了，不用特別設定就可以看到每一頁滿滿的屎。
26頁他有設定一個行為 應該是GA不夠specific?
A/B test
改變web 內容test user行為有沒變更
以實驗組跟對照組 來比較哪一個(web內容)較受歡迎
ex: 利用 gaExt.js 來測試哪個按鈕比較有效（比如說比較容易吸引人按 like）by Chris
Web Components 
瞭解 working flow 後 才能track
太多的trigger 會造成日後維護的困難
ref
自動化測試：protractor + cucumber
http://www.protractortest.org/ (Angular)
http://www.seleniumhq.org/

LauMu 啊不，是 Paul 的投影片 (感謝 Michael Huang 提供)
http://mei.homin.com.tw/Keynote_dance_with_i13n.html#!p=0


p B - 讓你的 PHP 開發流程再次潮起來
投影片http://www.slideshare.net/shengyou/modern-web-2016-php

探索歷程
- PHP v5.3
- CodeIgniter v2.2
- Laravel v4.0 ~ v5.2
  
Laravel 道場
- www.laravel-dojo.com

身為傳教士的反思
- 先改善效益最大的地方
- 一次改變一點不要太多
- 每一歩都不會太難
- 讓成員感受到好處
- 自然而然

優化方向
- 本地端可以獨立運作
- 新舊專案使用不同 php 版本
- 開發時的環境就是上線時的環境
- 降低新成員進入專案時的門檻

PHP 為何不潮? 
版本很難更新
難導入 Laravel ( PHP 版本要求高，新版的 5.3 要求 PHP 5.5.9 )

透過 Vagrant 導入 ( Vagrant + VirtualBox)
Homestead

懶人包
http://www.laravel-dojo.com/opensource/wagon

Git
GUI - Sourcetree, GitKraken
SVN
FTP

工具選用
PhpStorm
Visual Studio Code

除錯工具除錯工具
echo
var_dump
print_r
編輯器 + XDebug

Composer
packagist
composer init
composer require
composer update

套件生態系
awesome-php

autoload psr-4
namespace
classmap
files

composer repositories

satis
toranproxy

導入 Migration 工具

Phinx
Propel
LazyRecord



C - Servo 平行瀏覽器引擎
為何要作新的引擎？
效能
平行化
GPU (WebRender)
記憶體安全
嵌入式
Performance
早期瀏覽器都只考慮 single thread
CSS 運算
parallel layout
subtree 自己內部先排版之後再結合起來
省電
CPU 的耗電量非線性 ex. 80% >>> 50% (數字舉例而已)
GPU
某一種動畫盡量不要用效能很差？
WebRender
60fps
No WebGL, Canvas
不用了解 implemention
只需要會 Javascript 和 CSS
使用 GPU
模仿遊戲引擎的模式
原本：來一個請求就畫一個疊上去
修改後：先蒐集完， sort 過後，再畫出來
Security
Chrome 前 50 個 Security Bug
大多都和 Memory 有關
用 Rust ！
Rust  https://www.rust-lang.org/en-US/
編譯時會檢查 Memory Leak 等安全性問題
Feature
Ownership & move
Guaranteed memory safety
Threads without data races
Pattern matching
Type inference
C/C++ bindings
and more!
記憶體洩漏常常發生在 HTML5 的 video audio
Modularity
HTML + CSS + JS -> DOM -> Flow Tree -> Display List -> Layers -> Final Output
Cargo and crates.io
有兩百多個 crates 組成
Developer Happiness
Github Workflow
有 Bot 幫忙 assign reviewer
Bot 作 Auto-test ，成功過後才會 merge
Test the Web Forward
Cross-browser Web Platform Test (WPT)
Servo 經常測試 WPT 或甚至貢獻 WPT 測試
CSS Test
一個是要測試的檔案，一個是已知現有的檔案，兩者必須要一模一樣
JS Teste
呼叫 API 後檢查是否與預期相符（例如 select document.body 是否真的是 body）
Working Remotely
Sync -> ASync
Github Issues & Email
IRC
可以即時一點
可是因為時區所以大多數沒辦法很即時
Video Conference
非必要時不會開視訊會議
This Week In Servo
某某人做了什麼大事情
Workweeks
半年舉辦一次
喝酒吃飯聊天
Session
討論 Bug
Sharing & Lightning Talk
Party!
Why contributing
好好玩
有挑戰性
很新的專案，還有很多很基本但還沒做的東西
可以學一些東西
HTML & CSS Spec
Data Structure
Algorithm
Parallel programming
Computer graphics
DevOps
如何參與？
Download nightly https://download.servo.org/
到 Github 看 issue 修 bug

16:20 - 17:00
A - 恰如其分的 MySQL 設計技巧
最低限度產品只會產出爛產品
技術債
架構先決
沒有完美架構，只有最適合的架構
架構是演進的，不要過早優化(但先想下一步是好的)
License
GPL 的感染性
預先考慮好授權問題
Elastic business
合併
is_lock, is_deleted, is_... => status = 1, 2, ... （ 1 = deleted, 2 =  locked, ...）
標籤雲
在 M 時間內不要看到 N 廣告
M -> 年/月/週/時/分/秒
N -> 相同/同類
Workload
Proccessing
OLTP
回應時間要求高
交易完整性高
安全性高
OLAP
回應要求低
資料量多
交易完整性低
安全性低
Data warehouse
存資料不運算
應用
熱資料
冷儲存
Intensive
CPU/ Memory/ Storage/ Bandwidth ..
Capacity
ㄧ千萬人同時在線
電子商務，線上媒體
低延遲回應
廣告平台30ms
高頻交易0.5~3ms
醫療
不是每個東西都可以放雲端
程式語言選擇影響很大
效能增加
降低成本
Bond
Scale-up
Hardware
CPU
CPU Cache 對 InnoDB 影響很大
Hyper Threading 有助
啟用 Node Interleaving 可避免 NUMA
多核心處理
Memory
原則上越多越好
確保能把所需資料表儲存在記憶體中
Storage
PCLe NVMe SSD > SSD > HDD （BlockSize 對 SSD 影響極大）
Bandwidth 與 IOPS
循序性寫 +RAID HDD 不比 SSD 慢
OS Kernel
vm.swappiness = 1
Kernel 2.6.32 時有變更 
vm.dirty_background_ratio
IO scheduler
File System
Database
Design & Config
Connection pool
MySQL
線程模式
Appliciation
N+1 Queries / ORM
Bad SQL
Bad Schema Design
某些編碼下 VARCHAR(760) 比 VARCHAR(770) 快
某些編碼下 VARCHAR(190) 比 VARCHAR(200) 快
MySQL 5.7 之後幾乎沒差
Primary Index 循序式比亂序式快
Bad SQL
Big Transcation
Big Patch
Clustering
Deadlock and rollback
Disaster Recovery
Multi Regional Resiliency
大數據與微服務
大多不用 RDBMS ？
大數據
JVM 的天下
微服務(Micro Service)
部屬快
效能高
開發快
Java
Container Size 過大
alpine
授權問題
安裝前需要「人工同意」授權
整體不可分割，不可刪除任何檔案
小結
RDBMS 其實可以用
降低開發與維護人
系統異質性低
依然相容現行大數據架構
支持容器化、混合雲、私有雲(顧問性質)
大數據核心與對外服務層權責分離(兼具安全性)
其實大多時候我們不需要大數據解決方案

B - 從 Guanyu 談設計 Serverless 服務

Serverless Architectures (http://martinfowler.com/articles/serverless.html)
FaaS / BaaS /Container
Message-, UI-, or event-driven
Stateless
Cold-start latency
Cost & Scalability
Minimal but not no-operation

AWS Lambda
Managed FaaS (Function as a Service)
Ram (CPU), Timeout, Role,, VPC
Support many languages (Node, python, java, ...)
Integration with CloudWatch, Logs, IAM
Unlimited potential (運算能力無限 信用卡預算有限
功能：
Pull & push model
Concurency cap (soft limit)
No shared memory (shm)
Potentially shared /tmp
Burstable / Throttled CPU

Lambda Frameworks (in Node)
Apex
Claudia
 Serverless framework (formely JAWS)

ref:
淺析 serverless 架構與實作 http://abalone0204.github.io/2016/05/22/serverless-simple-crud/
關羽-docker https://github.com/clifflu/guanyu-docker
Live demo repo https://github.com/clifflu/serverless-modernweb-16 


C - Data Fetching 的過去與未來 － from REST to GraphQL + Relay

slide: https://chentsulin.github.io/modernweb2016-graphql-relay-intro

Server side 服務以 REST 最熱門，但有些難解的問題
Nested relations - 物件間有複雜關聯時
Not efficient with bad network - 多次來回取資料時
Versioning - 前後端版本不一致時
Growing amount of api endpoints
...(沒記到的看投影片)
easy to over-fetching or under-fetching
GraphQL - 針對 application 進行 query，不是對 DB 做 query
 這樣一來，front end 工程師也要瞭解後端物件的 schema 嗎？
是的。但其實用REST也要知道每個API，但用GQL可以少記很多
我以為要 query 的話，可能要更瞭解後端的物件關聯。
只要開發後端的人document寫夠好，gql的schema是很容易理解的。事實上GraphiQL會自動產生document，所以寫document也不算太難
帥喔！我的文件就是 skype 的對話紀綠！ :D
你的前端在你背後，他很火
XDrz 
應該說了解你可以取得的資料的 Schema 不是 DB Schema，不知道後端有什麼東西的話會無從 query
query:
{
    user(id: 12345){
        name
    }
}
response: {
    name: 'handsome boy'
}

Only fetch what we need
Type System 
Type 的定義也是透過 json
Type 也可以被查詢
List = 其他語言中的 array
GraphiQL - 測試 GraphQL schema 的工具
補充一下，其實除了Relay，前端用來接GQL的，還有Apollo，Lokka。依框架複雜度: Relay > Apollo > Lokka。Lokka就是 GQL 的 fetch，如果想在原有的架構下使用GQL，可以從他開始。Apollo跟redux有不錯的結合，Relay雖然最複雜，但最能發揮GQL的好處
避免 N+1 query，可以減少查詢次數
Relay 的 cache 有做以下工作
normalize
immutable
views subscribe record IDs

resources
看投影片
17:00~
Drink Time :sunglasses: 


08/25 Day 2

09:40 - 10:30 Tuning NGINX for High Performance
All link：https://shadrin.org/talks/

...how to handle more customers per single server.
Igor Sysoev, NGINX creator & our founder

 About NGINX, Inc
Founded in 2011, NGINX Plus first released in 2013
VC-backed by enterprise software industry leaders
Offices in San Francisco, London, and Moscow
750+ commercial customers
100+ employees

Architecture approach
Design for scaling
Segment microservices out
vs monolithic application approach 
take specific services out to containers, virtual machines, ...
separate from main application
e.g. changing instances of authentication services based on time of day
Use caching and microcaching
memcache, browser-level caching
reduce number of requests reaching backend
reverse proxy
Basic NGINX placement
Client <-- HTTP/2 --> NGINX <-- HTTP/1.X, FastCGI, UWSGI, etc --> Servers
Inside NGINX =>這張圖片blog 裡面有
Master Process
Child Processes
Cache Manager, Cache Leader, Workers...
https://www.nginx.com/blog/inside-nginx-how-we-designed-for-performance-scale/
OS tuning
net.core.somaxconn
net.core.netdev_max_backlog
net.ipv4.ip_local_port_range
sys.fs.file_max
number of file descriptors for particular userK
applies to sockets
/etc/security/limits.conf, nofile setting
See https://www.nginx.com/blog/tuning-nginx/
Overcoming ephemeral port exhaustion
Increase local port range => use this "net.ipv4.ip_local_port_range"
Split traffic across multiple IPs
Nginx since 1.11.2 uses IP_BIND_ADDRESS_NO_PORT socket option when available
https://www.nginx.com/blog/overcoming-ephemeral-port-exhaustion-nginx-plus/
Minimal NGINX configuration
不要放圖片吧有點肥
想說可以省點時間
events {}
http {
    server {
        listen 80;
        location / {
          proxy_pass http://backend;
        }
    }
    upstream backend {
      server backend1.example.com:8080;
      server backend2.example.com:8080;
    }
}
NGINX Core Features
Use correct number of worker_processes
auto
# of available CPU cores
Increase worker_connections
Increase worker_rlimit_nofile
Turn off accept_mutex: accept_mutex off;
Turn on Sendfile: sendfile on;
Use thread pools if I/O needs offloading: aio threads;
https://www.nginx.com/blog/thread-pools-boost -performance-9x/

HTTP Keep Alive
Keepalive connections allow to reuse the same TCP connection for multiple HTTP requests
For HTTP/1.1, no need to define anything, it's enabled by default on the frontend.
Keepalives provide major performance benefit when used
HTTP Keep Alive: Benchmark
HTTPS with NO keepalive
Plain HTTP
HTTP/s with SSL
Keepalive on the Frontend:
keepalive_requests 100;
keepalive_timeout 75s;
https://www.nginx.com/blog/http-keepalives-and-web-performance/
Keepalive on the Backend:
server {
    location / {
        proxy_pass http://backend;
        proxy_http_version 1.1;
        proxy_set_header Connection "";
    }    
    upstream backend {
      server backend1.example.com:8080;
      server backend2.example.com:8080;
      keepalive 32;
    }
}
HTTP Caching
Microcaching with NGINX (https://www.nginx.com/blog/benefits-of-microcaching-nginx/)
Cache placement strategies (https://www.nginx.com/blog/cache-placement-strategies-nginx-plus/)
HTTP/2 (https://simular.co/knowledge/site-build/68-about-http2-and-http11.html)
Introduced in 2015 as standard
Based on Google's SPDY
Include majar changes compared to HTTP/1
Binary with HPACK
Multiple Streams
Prioritization
Server Push
HTTP/2 benchmark
NGINX 1.10.0
Ubuntu 16.04
Openssl 1.0.2
Chrome
Measuring full page reload
4x faster than HTTP/1
HTTP/2 支援性 (http://caniuse.com/#feat=http2) 
Not supported
Opera Mini
Android Browser
chromium 51 之後就支援了
恩，應該是檢者簡報沒更新
Partial Support
IE11 - limited to Windows 10
Measuring your results
NGINX provides extensive logs with custom variables
NGINX has simple set of metrics with stub_status module
NGINX Plus provides more extensive metrics with Extended Status module
NGINX Amplify is a free monitoring SaaS solution.
Nginx Amplify: https://www.nginx.com/amplify/
Conclusions
Plan for scalability early
Tune low level operating stytem
Configure Keepalive
Configure caching
Enable HTTP/2
Measure your results
How to contribute
hg.nginx.org
github.com/nginx
wiki.nginx.org
nginx.org/mailman
Ref: https://shadrin.org/talks/

10:30 - 11:20 前端工程體系的變革
前端工程體系的演進

關於工程
技術leader職責＝工程體系構建＋團隊成長＋業務支撐
即使產品水面上(表面)看起來一樣，重要的是水面下的組成
(左圖) 程式能力支撐 (右圖) 工程師人力苦撐

手機淘寶
超大用戶量
手機淘寶日活躍用戶約 1.5 億 (媽啊這什麼概念！)
MAU 3.69 億
多部門業務插入
天貓、聚划算流量會導入淘寶
Hybrid App
2013 年導入
圖片型應用
圖片由用戶產生
量很大
圖片是買家主要決定購買與否的依據

工程體系的目標
研發效率  產出質量
安全性 穩定性 性能 平台性
大用戶量 圖片 Hybrid 多部門接入
 架構圖要不要後補？
之後再補吧這有點難畫

工程體系的型態
庫（框架） 
演進
中心化基礎庫 Base.js 
有什麼塞什麼，七七八八全進去
檔案超大性能差
難 debug
沒人敢修改
拆解與依賴 libs
獨立的 lib 移出
依賴關係整理清楚
比較好 review
對格式有要求，故好操作
分層、系統規劃
組件層、功能層、擴展層
限制不同 layer 的 lib 只能跟特定的 lib 產生依賴 (不容許跨層依賴?)
原則
必要性
所有人都能寫的，不要寫進庫，大家都不寫或不想寫的才寫進庫
案例：架構組應該幹這個苦活，把類似 env 的判斷寫成庫
複用性
每個業務都要用到的
案例：每個業務用到的 API 都需要 timestamp 等資訊，故直接寫成庫
原子性
每一個庫要是完全獨立的
有種公司內部建立開源社群的感覺
哪些應該要共用...應該要開不少會才能討論完 XD 最擔心是共用的越來越多...架構 Team 要深入了解所有的業務才行
一個相依性如果太複雜 會產生歷史共業與包袱的恐怖感
大型公司裡面，的確常常會有「共用組」這種小組的存在，工作內容大多只能用忍辱負重四個字來形容
(共用組路過...)
設計
https://github.com/amfe/lib-flexible
https://github.com/amfe/gesture-js
https://github.com/amfe/amfe-cubicbezier
等補圖
工具 （狹義: 命令行，廣義: 流程）
演進
調適、Web Server、DNS、init、Grunt -> gulp、Proxy、構件 ...........
無法整合一團亂
創建 -> 開發 -> 調試 -> 測試 -> 發布
一個工具只能有一種類型，超過者必須拆開
設計
工具 -> 工具鏈
新工具必須能放進現有工具鏈
平台
營運業務平台
產品搭建平台
補圖


11:50 - 12:30
A - 電商基礎架構之路
成立中國的亞馬遜
業務模式決定架構
網站/無線
沒有自己的物流體系
電商系統特徵
7x24 
功能堆積 (很多年了，很多工程師多年堆積下來，100多個系統)
系統龐雜
不易維護
峰值波動 (天天都有小促銷 每年有大促銷如光棍節、書香節 => 可能產生好幾倍的流量)(流量太大，要求高擴展性、即時監控，可以彈性的調整，可以應付忽然的流量變動。)
關聯性強
邊界模糊 (大家不見得清楚自己該做啥，舉例：很多工程師年輕經驗不足，他對東西的理解是自己的，非與他人的共識)
敏感度高
技術債務 (利潤低、競爭激烈 => 易欠下許多技術債)
異構
天天都在促銷
書香節
什麼是基礎架構
Infrastructure (基礎設施很重要大家都懂，但要你選去做業務系統還是基礎架構，大家多半都選業務系統。但講者認為他們在基礎架設這一塊是很看重的。)
(1)大數據平台 作業平台 緩存平台 消息平台 數據庫集群 業務監控 搜索引擎 自動化測試平台
(2)流量管控/權限管理/流程管理/持續集承/日志中心/...
(3)網路/安全/資源管理/配置中心/自動部署/系統監控/私有雲/公有雲
為什麼要建設基礎架構？
夯實基礎，事半功倍
IT技術的價值在於複用，完善的基礎架構將會為系統快速演進提供保障，高效響應業務需求
隔離業務代碼與框架、平台
提高系統可控性
系統越複雜，規模越大越難以管理，需要系統化的手段使之成為一套有機的的整體
降低技術債，提高管理效率
建設基礎架構通過技術手段減少債務風險，完善的基礎架構能夠降低溝通成本、節約時間、提高管理效率
基礎架構建設的時機
順勢而為，撥亂為治 (例如發生了某個重大問題，順勢建構一個系統解決問題。)
自底而上，由點及面
管理層不一定知道問題的痛點
抓住痛點，有備無患 
亡羊補牢，猶未晚矣 (舉例：之前欠的債，到了不能忍受的程度，還是要往羊補牢還債)
部署架構
Metro Mirror
Global Mirror
兩地三機房不等於兩地三中心
私有雲/公有雲需要更強運維
異地備援，實際上是否真能運作
(講者重點在於理想(想像/規劃)與實際能力是有差距的，所以你真的有演練過異常狀況嗎？你真的有能力解決異常發生時並維持高可用嗎？)
數據庫管理
MySQL, SQL Server, Greenplum, Oracle, mongoDB
上千台伺服器資料庫管理需要一個管理系統
緩存集群管理
Redis
看個書就決定用某技術（看 Redis 的書就覺得自己學會了 超糟）
系統監控
Nagios (本來想把所有監控都放在 Nagios，但最後還是拆開
ZABBIX
貫穿產品生命週期
項目管理
自動部署
監控告警
問題跟蹤
項目管理系統 (自己開發的)
PDLC開發流程管理工具
敏捷看板(大螢幕)
自動化運維部署平台 (自己開發的)
批量發佈
自動
備份
但不到 CD 的程度
應用監控 (自己開發的)
服務監控 (自己開發的)
SLA
監控應用統計 (自己開發的)
報單跟蹤 (自己開發的)
報警報單數據展示
組件-->框架-->平台
DubboX
應用框架DDFrame
Elastic-job https://github.com/dangdangdotcom/elastic-job 
Sharding-JDBC(開源輕量級分庫分表中間件)
總結
用自動替代人工 (減少錯誤、規範標準化)
用小系統驅動大團隊
用基礎平台支撐上層應用 (累積基礎建設)

B - 深入 CSS3 動畫應用及模組開發方式
動畫分類
Transition 
(屬性 時間 延遲 速度)
Animation 
名稱  時間 延遲 速度 次數 方向  填充模式
Transition: （將transition寫在class裡面，只用jQuery add/remove class）
寫在normal狀態
寫在結束狀態（較少見）
撰寫位置
起始狀態: 只有一種過渡動畫 (常見)
結束狀態: 可拆分兩種過渡動畫控制 (少見)
動畫堆疊
transition: set1, set2, set3;
Animation: 
複雜的動畫交給我就對了
缺點：沒有連續性(例如mouseout時 會瞬間回復原始狀態，不會有漸變)
關鍵影格
@keyframes 動畫名稱 {
    ...
}
time: s, ms　
delay: 正值，負值，秒，毫秒

延遲時間軸

速度
預設 ease (加速後減速)
設定於 animation 中 - 只控制第一段
設定於 @keyframes 中 - 分段控制 f
cubic-bezier(0,0,1,1) - 效果最佳
方向
預設 0% > 100%
reverse 反方向
alternate 往返 (切記次數要 > 2)
alternate-reverse 反向往返
優先處理動畫，可用動畫來設定定位

填充模式 (fill mode)
能不用就不用，避免影響 transition 設定

動畫堆疊
animation: set1, set2, set3;
CSS3 animation 效能調校
CSS3 效能比 JS 好
影響效能的原因: 重繪
影響效能的屬性
width & height
border & outline
background
padding & margin
show & hide (display)
下列屬性也會影響只是比較小
align & vertical-align
position & TRBL
shadow
如果只是需要框線可以考慮改用Shadow實作(因為Border跟Box-Model有關)
跟排版無關，只跟呈現相關
color
float & clear
其實
只要跟排版相關的屬性都會影響
跟Box model有關的東西都會'嚴重'影響
3D 催落去
will-change: transform(強迫gpu繪製 先畫  效能較好)
transform: translate3d
transform: rotate3d
transform-style: preserve-3d (上面三個可用這個代替)
但是上述都是假象
不同系統有不同狀況
不同硬體有不同狀況
translate3d  在WIN上有顯著改善
在MAC反而掉格
Translate3d搭配TRBL最糟糕
建議
動畫盡量避免長距離的移動
動畫時間不要太長

CSS 模組化
以功能建構 (e.g. Bootstrap)
註:你要改一個CLASS還是改一堆CLASS
以外觀建構
css可快取，只更改html的class可減少網頁從抓css的時間及客戶端快取導致畫面未更新的問題
同質性分析
擴充性分析
animation特性:優先運算完畢
animation-name 
animation-duration
animation-delay
animation-timing-function 速度控制
animation-iteration-count 次數控制
animation-direction 方向控制
animation-fill-mode
animation-play-state
可以寫成一行

使用具語意的命名
避免css屬性衝突
動畫盡量使用css3屬性製作
避免transform設定値衝突
建議使用效果疊加 (e.g. translate + margin)

CSS可樂站長
http://csscoke.com

負値馬上動，或不讓它動
倒帶 - transition 順序
加減速設定

C - 遠端團隊專案建立與管理

軟體開發者可以遠距工作的特性，激發出了遠端團隊管理的想法。
讓偏鄉(?) 開發者也能容易的參與開發團隊。

遠端偕同工作
一種遙不可及，但又不

遠端管理者
PDCA（Plan-Do-Check-Action）

將發散資訊 - 經過整合集結 - 收斂為產品最後的執行方式
開會工具
zoom, skype
線上編輯工具
google doc,office 360 ,Quip
應該是 office 365，可能講者錯置

工具只是形式，溝通才是重點

遠端開發困難點
開發過程如果有疑問 無法馬上問人(對於junior來說)
需要溝通程式寫作方式 協同開發
測試
遠端開發者≠獨自開發者
利用slack發問
技術、心理影響更大
情感的關係很少
有話就說出來比較好處理
鼓勵大家把問題說出來

遠端開發者必備特質
獨立解決問題的能力
豐富的專案經驗
擁抱改變的胸襟
了解溝通的方式

訓練流程
建立溝通管道
文字如何表達
定義基礎溝通時機
促進遠端者主動聯繫
每個人溝通方式不同，需建立相同語言機制，才能遠端仍能傳達想法
 溝通的成本好像更高

重新開始＝>重心開始

團隊注重有格局
架構 骨幹
（但也有模糊之處）

程式開發需溝通的項目
開發也有所謂的技術債 (該做而未做的技術調整，或是為了趕工而做的妥協)
好/壞的味道

有時候最敏捷的寫法
不一定是最好讀的作法

不是每個人都可以寫出神之程式碼

定義DoD 清楚表達每個TASK最小完成定義
很有感 有時候不小心寫了不必要的東西 做白工QQ
 有感+1，常常會有工作不知道完成多少的狀況，但 trello 上的 card 已經被移到 done 那邊去了 XDD
DoD 是什麼的縮寫？
Definion of  Done
遠端會議VS辦公室會議
（開會就飽了）

遠團隊更需要清楚的問題描述
信心的建立很重要！
如果信心(信任)瓦解，對工程師產出感到懷疑，會很難恢復
遠距會議的大綱、主旨更加重要 (總之就是清楚的溝通)

遠端會議
排定可預期的會議時間與會議目標

遠端會議
遠則網路穩定，安靜或者收音清楚之場所

為原遠端團隊，信心何其重要

 工具採用流程
 首先，管理者只能相信

建立遠端規則
新手須知規則
會議必須要即時參與
工作時間保持線上網路順暢
什麼樣的訊息，多久時間要回應 ex(吃飯，長時間離開，需要跟團隊知會)
排定定期會議
好快 XD
gg
等釋放簡報再補吧

IFTTThttps://ifttt.com/
Task management - JIRA

以週為單位，以功能完成為基準（並非程式碼數量）

感想感想
團對節奏違紀數管理之根本
溝通為底 技術為輔 掌握成員特質
身為管理者永遠要多看產品 多看TASK 多想三秒能夠省下一星期的悔恨
建力信心與溝通，成員願意將問題曝光揭露
工具只是輔助，遠端是一種手段，重點還是回到溝通成本



13:30 - 14:10
A - 移動開發的銀彈 -- React Native 探索與實踐
銀彈技術銀彈技術
可以提高生產力
降低開發成本
提高生產力 降低開發成本

移動開發技術的發展
2006 Symbian WML
2009 ios Android
2011 Hybrid PhoneGap
2012 插件化
2014 HTML5
2015 React Native 動態化

移動開發技術對比


使用 React Native 取得的成果
-節省成本
 - 1名前端 = 1 ios + 1 android 工程師
-平台復用
  - 無縫遷移奉
-性能體驗
  - 性能提升、原生體驗
-快速迭代
  - 即時響應
  - 隨時發布

解決安裝痛點
 牆內連上 npm 很慢，只能透過牆內的鏡像站，也可以自行架設私有鏡像站。


組件化思路
基礎組件
工具組件封裝 ( UIExplorer )
物組件封裝
原生組件封裝
開源社群（JSCOACH https://js.coach/）

平台復用原則
  - 學習一次，隨處可用
  - 不追求完全抹平差異
  - 他們自己使用的經驗，可達到 70%~85% 代碼復用率
覆用組件邏輯，區分組件樣式
分離複雜組件差異

調適踩坑
Chrome 裡 Network 無法查看到Fetch請求
因為 React 的Fetch請求是透過Polyfill來實現

解決方法：
修改 React代碼 ( 不推薦 )
使用第三方插件Fiddler做代理


調適深層次頁面,總是從啟動更新
Reload
live reload
hot reload

第三方庫，Debug OK真機環境下crash
依賴window atob，真機無瀏覽器環境
JS庫無環境依賴
封裝 Native 庫

熱更新方案
設計Bundle Server
提供版本查詢服務
設計客戶端交互
制定更新策略 ( 全量/ 增量 )
(雲服務) CodePush / AppHub


移動項目寄宿選行移動項目寄
移動項目寄宿選型宿選型
是我LAG還是hackpad當了
我剛剛一直502  Orz
B - 電商平台與解離架構 CMS 整合開發

CMS 走向前後分離

以內容驅動的時尚產業電子商務為例

Ex: citiesocial (找好東西) 好東西賣場 Unipapa

三個類別
Standalone, CMS Extension, Saas(shopify)

What is CMS
多用途，資料，DB端

0資料庫 1編輯人員介面 2網站介面構成 3前端設計表現與互動

0-1 Headless CMS

Decoupled CMS - 專注在編輯人員介面和資料庫上，提供 API 供前端實作 end user interface。

CMS常見應用：
MVC JS Frameworks, Mobile Apps, Staic page generator

常見 Decoupled CMS選擇：
Drupal 7 + Service, Drupal 8, WP + JSON, Contentful Cloud...

SWAGGER (不同api溝通)

Content Integration
Shopify <-> Drupal <-> Customer

Content Driven Commerce
導流 無縫接軌 社群內容

CMX(講師籌備中的研討會):
cmxconf.tw


電子商務
導流
無縫接軌
社群內容
 文章內容導入產品
 名人導流 (內部客群)
 電子報 (訂購電子報獲得折扣)
 節日活動促銷
 參加活動
 線上客服導購
 搜尋功能導購
 評論 (收集資料 Structure data)
評論不單是評論，其實是在蒐集使用者的喜好資料。

Ref: cmxconf.tw

C - 用 Arduino 與 three.js 實作互動式全息投影網頁
Input> Logic > Output 
output
Hologram
案例介紹:
https://vimeo.com/150736956
實作demo:
https://www.youtube.com/watch?v=qBYIIC4i6Vc
四個Renderer繪出同樣的內容，然後利用CSS 去轉向
用ＣＳＳ做梯形 => 會讓圖形變形 => 所以用切的 (css clip-path)
Input
硬體輸入 raspberry API / Arduino
RFID > Arduino > PC > Browser > Screen
https://www.youtube.com/watch?v=u40WqUjEgBs
RFID 頻率會造成感應的問題

14:20 - 15:00
A - 技術趨動用戶體驗優化在趕集的實踐
非設計類用戶體驗的痛點
  無響應
  慢
  崩潰
體驗問題會導致用戶丟失
  - 因 crash 丟失用戶數 / crash用戶總數 (大約會有1/3的用戶因此流失)
遭遇體驗問題後的用戶行為
Crash 62%
慢 47%
差評 26%
卸載 79% 
解決用戶體驗問題的第一階段
技術架構
性能數據 & Crash數據 --> Data Center --> 實時監控
全國性能概覽

B - 利用 Golang 架設 Line 機器人，作為網站的推廣大使
Slide: http://goo.gl/IYv1BU 
IM Bot
可以針對使用者的訊息，自動回應的程式
How to choose program language
Easy to write
Fast in Run and Compile
Powerful Concurrency
Powerful built-in toolchain
What is Go
Create by Google
Feature: 
Compiled
Statically Typed
Garbage Collection
主要為了 server side programming 所製作出的語言
C語言演化而來
Go Fast!
Compile Fast
Run Fast
Efficient for computer and fun for human
存檔自動排版
可疑語法的解析（ex: a != 1 || a != 2）
Tools
Go Vet
Go Lint
GoRoutine (Multiple Thread in Go)
簡單寫出 multi-thread 程式
Support HTTP/2 after Go 1.6
Built-in Test (內建測試，只要在function name 前面加上關鍵字 test )
Built-in Benchmark Test 
GoMobile 可放在iOS上面
https://play.golang.org/ => Go Playground
GO JSON Tutial
ㄧ恍神就漏掉了，請其他人補充
可以參考：http://goo.gl/hzs6AO
GoLang IDE
Vim
Visual studio Code (裝Go Extension可做debug)
Start to Build IM Bot
Introduce Heroku (Platform As a Service)
use an acconut-based pool
缺點是sleeps every 30mins
support one click deploy
http://huli.logdown.com/posts/726082-line-bot-api-tutorial(別人寫的教學文)
https://blog.ccjeng.com/2016/06/Line-BOT-API.html （別人寫的教學文趴兔）
create account
1. request line ace
2. deploy to heroku by one click
github.com/kkdai/LineBotTemplate
3. fill your hero app callback address to line bot
4. 
5. fill you line bot information

講師舉例可以做到 加LINE好友後，bot自動say hello
Build a smart bot
EX: 台北天氣如何？
語意分析
intent 
entity
LUIS (Microsoft 語意分析 service) https://www.luis.ai/ 
支援中文
Future
Bot to Bot(No more API)
How to build Right Brain (Art Sense) ?



C - Web 終將統治世界？用 JavaScript 打造的影像處理軟體！
起源
HTML5 Canvas
http://www.betterphoto.com/home.asp

作品集
piconion
cropper
photogrid

程式架構 (講者的感覺，實際的 code 不見得如此)
User Interface
Photo processing functions (比較獨立的功能，反而比較好做
Chrome App File API

Chrome app 可以直接存取檔案
廣告收益
台灣如果是1，日本大概2~3，美國4~5
做web很容易全球化，只要翻譯就好了
Chrome app 即將於 2018 Phase out
用 Google Drive API 取代，並加上可讓使用者下載的功能
自行開發，沒用框架，只用到 JQuery (主要是 selector 比較好寫)

Repeated line: Follow your heart (or feeling...)
比較賺錢的反而是看起來爛的東西 (e.g. 心理測驗)

15:30 - 16:10
A - Universal Angular 2 in FinTech


B - 如何透過語意網路與使用者行為優化使用者經驗
Slides: https://goo.gl/cZMf6C
We have slides too!
如何猜使用者的想法
根據網頁資訊提升SEO
使用者可能的八個思維去操作網頁的下一步
後：比較不需要因為瀏覽器都有
左/右：找到物件的關聯性，ex: 通常買了ＡＰ下一個會買線
內/外：想要ＡＰ使用什麼樣的ＣＰＵ，power等等
Different has different thinking of searching
字詞的觀點：
同樣的方法可能適合分類，但是不一定適合資料搜尋
tag與keyword  不一定能混用 （如"我的朋友"無法當tag，keyword有時不夠客觀）
標籤的可能性
下好下滿標籤可以好好地做出data-driven的 UI
常用語意網路關係
要考量時間性，例如說柯文哲4年內還是市長(is a)，4年後不一定是台北市長，這時可以用關係的距離來表示
從屬關係可能沒有那麼絕對 ex: iphone上面一層應該是手機？or  Apple ?
同樣的詞用不同的方式去定義，就不一定是相反或是相同的關係
ex: 國民黨＆民進黨可以是Opposite or 同屬政黨
語意網路怎麼用
下標籤的目的是要聚合結果
透過結構化資料讓分析工具可以更精確地知道這個網頁在幹麻
如何提供麵包屑給Google
自動化詞庫
不同狀況下可能會有不同的加權比重
賣女裝的店，賣女裝字詞沒有意義，洋裝比較有意義
洪荒之力字詞沒有歷史背景，只是根據一個電影來的詞，所以要有自動化詞庫
朱立倫去參加雙城論壇遇到沙梅林，所以以當天詞彙來說，兩者等價且有關連
Future
直接呈現使用者最願意看到的info而不是照著時間軸或是原本網站的架構

透過語意分析知道人民的想法
也可以透過上一場的Bot做進一步的應用

參考資料
JSON-LD http://json-ld.org/
Struture Data Plan https://schema.org/
結構化資料驗證工具 https://search.google.com/structured-data/testing-tool

C - 無痛網站自動化測試
http://goo.gl/mp0NbA
 太棒了！一開始就有投影片！ XD
:emoji_1f647: 
https://github.com/alincode/modern-web-2016-e2etest

SDET(Software Design Engineer in Test) - 設計測試流程、調校測試流程

Selenium 比較複雜，所以選用了框架 - WebDriverIO
 只要懂Jquery就能寫！(感動 

Chimp (另一個 tool) 可以做 hot reload，可以簡化測試流程。

編寫前端測試時，愈省愈好！
reuse your step
建構測試環境
建構 selenium hub
建構 selenium 結點
使用 cloud service 可以簡化流程
sauce lab
(參考投影片)
WebDriverIO 語法支援 jquery selector

16:20 - 17:00
A - 移動娛樂直播下監控與極限優化

社交直播
低端設備對性能的要求更高
弱網路也要有良好的體驗
互動性,時時性的要求更嚴

優化
明確的方案適用場景
對優化方案深入論證
方案可執行性
方案可論證性
避免過度優化
以絕大多數的ＵＸ為準
少數用戶將及體驗
減少無效優化投入

web業務對優化方案選擇的影響
前後端完全分離
重前端邏輯的MV
基於node的全線開發

實踐
透過監控發現業務問題
實現業務實時告警
完善監控日誌方便問題定位
統計日報反應業務整體質量

產品不能一味的放棄對低端機用戶的支持，對低端機用戶採取適當的降級

圖片資源優化
減少請求
壓縮大小
選擇適合的圖片格式

直撥優化 

####  GOP (Good Of Picture)

 i, p, b frame (9 frame only include one i frame)
 Each frame take 5 second, wait at least 3 frame ( **15 seconds**)
 Make sure user(viewer) first get i-frame

 錄播優化

- 動態調整 GOP


B - Modern HTML Email Development
Slides: https://speakerdeck.com/othree/modern-html-email-development (by @lindsayrain)
講師愛用帳號：othree
speakerdeck.com/othree
github.com/othree
今天內容： 
現況 
資源 
工具

現況：
Text Email (日本人愛用，且排版顯示清楚)
HTML Email
problems
Lots of mail clients (web, android, iOS...)
Dekstop
buggy CSS support
need table layout
Mobile
need responsive design 
Web
Good CSS but no <style> support
Need sandbox
No <style> in web client
No media query
<video> support 
No float
No JS
一堆環境問題
詭異的特性
沒文件
沒標準
沒除錯工具
為什麼不標準化？
Mail Client 沒完全遵照 Web 標準
資安議題
<script> <style> on mail.google.com ?
應用程式會太大
customized engine or webview
HTML Email 標準討論不熱烈 （w3c相關論壇冷淡）
Mobile-first Email
至少要三層 <div> （崩
media query and display:table for desktop
outlook.com 要用 hack
桌面版 Outlook 要用 <table> 加 conditional comment
https://medium.com/cm-engineering/coding-mobile-first-emails-1513ac4673e#.x1pxvbp3r
資源：
前人拓荒
沒標準
但有很多文件
Campaign Mail
當你要做活動要一次發個幾千幾萬封 mail 時，這種就叫做 Campaign Mail
工具：
Premailer
HTML Inline style
Litmus
Live preview
Email Market Share
https://emailclientmarketshare.com/
MJML
Mailjet Markup Language
A new markup language for HTML email
簡單來說就是把 HTML 打掉重新設計一個專門 for Email 的標記語言
Based on React
Open Source
很難客製化
Component 有限
與現有 HTML 可能不相容
有些 CSS 會被移除
ex gradient background


C - Hexo 開發歷程
選這堂課是不歸路，真後悔！！

為何？

