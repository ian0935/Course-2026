# Secure Coding in C/C++

# 目錄

- [[#1. 課程總覽比較表|1. 課程總覽比較表]]
- [[#2. 課程定位|2. 課程定位]]
- [[#3. 上課重點|3. 上課重點]]
- [[#4. 課程主要綱要|4. 課程主要綱要]]
- [[#5. Important Keywords|5. Important Keywords]]
- [[#6. 技術能力地圖|6. 技術能力地圖]]
- [[#7. 可做的專題|7. 可做的專題]]
- [[#8. 對 AI Engineer 的價值|8. 對 AI Engineer 的價值]]
- [[#9. 對 Cybersecurity 的價值|9. 對 Cybersecurity 的價值]]
- [[#10. 對 Embedded Systems 的價值|10. 對 Embedded Systems 的價值]]
- [[#11. 對研究與論文的價值|11. 對研究與論文的價值]]
- [[#12. 學習順序建議|12. 學習順序建議]]
- [[#13. 履歷與學習歷程價值|13. 履歷與學習歷程價值]]
- [[#14. 一句話總結|14. 一句話總結]]
- [[#15. 最終評價|15. 最終評價]]

# 1. 課程總覽比較表

| 項目 | 內容 |
|------|------|
| 課程名稱 | Secure Coding in C/C++ |
| 領域 | Secure Software Development / Application Security |
| 難度 | ★★☆☆☆ |
| 時數 | 約 2 小時 |
| 課程評分 | 4.7 / 5 |
| 學員數 | 6,000+ |
| 核心能力 | Secure Coding、Memory Safety、Defensive Programming |
| 適合方向 | Cybersecurity、Embedded Systems、Firmware Security |

# 2. 課程定位

## 2.1 課程特色

本課程專注於 C/C++ 安全開發，而非一般語法教學。

課程從攻擊者角度出發，解析常見漏洞如何產生，再帶領學習者利用安全開發方法進行修補。

特色包括：

- Buffer Overflow 攻擊原理
- Heap 與 Stack 記憶體漏洞
- Format String Vulnerability
- Integer Overflow
- Race Condition
- Defensive Programming
- Secure Memory Management
- Automotive Security Case Study
- Smart Pointer 實務應用

## 2.2 適合對象

- C/C++ 開發者
- 韌體工程師
- Embedded Engineer
- Cybersecurity Engineer
- Reverse Engineering 學習者
- CTF 選手
- OSCP 準備者

# 3. 上課重點

- Memory Management
- Buffer Overflow
- Heap Overflow
- Integer Overflow
- Format String Attack
- Race Condition
- Error Handling
- Smart Pointer
- Principle of Least Privilege
- Defense in Depth
- Fail-safe Defaults

# 4. 課程主要綱要

## C/C++ 安全風險

系統底層的 C/C++ 開發時，因為它賦予了開發者**直接操控記憶體（Hardware-level Access）**的至高權力，任何一個小疏忽，都會直接演變成系統崩潰（Crash）或被駭客利用的**安全漏洞（Expl漏洞）**。

作為曾參與過網路安全攻防與逆向工程的開發者，我們用最精準、直擊漏洞本質的白話，來拆解四大 C/C++ 的致命安全風險：

## 1. Pointer Pitfalls（指標深淵）

**【漏洞本質：指錯地方、或是抓著消失的幽靈不放】**

指標是 C/C++ 最強大的武器，也是最容易自我毀滅的彈藥。常見的指標坑洞有：

- **Dangling Pointer / Use-After-Free (UAF，釋放後使用)：** 當你用 `free()` 或 `delete` 把一塊記憶體還給系統後，指標變成了「懸空指標」。如果你沒有立刻將它設為 `NULL`，後面又帶著它去讀寫數據，這就叫 **UAF**。
    
    - _駭客視角：_ 這是當今最值錢的漏洞之一。駭客可以動態分配一塊精心設計的惡意數據去填補那個被釋放的空洞，當你的程式再次呼叫該指標時，就會執行駭客的程式碼。
        
- **Buffer Overflow (緩衝區溢位)：** 指標在記憶體裡移動時，失去了邊界檢查（Boundary Check）。當你在陣列中寫入超過它容量的資料，資料就會滿出來，蓋掉鄰近的記憶體。
    
    - _駭客視角：_ 在 Call Stack（函式呼叫棧）中，陣列的上方往往存著「函式返回地址（Return Address）」。駭客故意讓資料溢位，把返回地址改成惡意指令的起點（如 Shellcode），當函式結束時，程式就會自動跳去執行駭客的指令。
        

## 2. Dangerous Functions（危險函式）

**【漏洞本質：不問長度、盲目信任輸入的盲盒函式】**

C 語言的標準函式庫（Standard Library）中，遺留了大量早年設計、在現代看來形同自殺的危險函式。它們的共通點就是：**「不檢查目標緩衝區的長度」**。

|危險函式|致命原因|安全替代方案|
|---|---|---|
|`gets()`|絕對的漏洞之王。使用者輸入多少它就收多少，**完全無法阻止緩衝區溢位**。現代編譯器已強制禁用。|`fgets()` (可指定最大讀取長度)|
|`strcpy()` / `strcat()`|複製或拼接字串時，不理會目標陣列夠不夠大，一看到 `\0`（字串結束符）才停止。|`strncpy()` / `strncat()`，或 C11 的 `strcpy_s()`|
|`sprintf()`|將格式化字串寫入緩衝區，若串接後的字串過長就會溢位。|`snprintf()` (限制寫入字元數)|

- **Format String Vulnerability (格式化字串漏洞)：** 如果直接寫 `printf(user_input);` 而不是 `printf("%s", user_input);`。使用者如果輸入 `%x %x %x %n`，就可以直接**窺探甚至竄改內部記憶體的值**。
    

## 3. Risky Type Conversions（危險的型態轉換）

**【漏洞本質：把大象塞進小盒子，或是把負數當成正數】**

C/C++ 的型態轉換非常自由，但隱含著嚴重的邏輯漏洞（Logic Flaws）：

- **Integer Overflow / Underflow (整數溢位)：** 當一個 `short`（最大 32767）加了 1，在電腦底層會直接變成 `-32768`（正變負）。
    
- **Signed / Unsigned Conversion (有號與無號轉換)：** 如果將一個負數（如 `-1`）強轉成無號整數（`unsigned int`），在記憶體二進位不變的情況下，這個值會瞬間變成 **4294967295（極大正數）**。
    
    - _災難場景：_
        
        C++
        
        ```
        void allocate_memory(int size) {
            if (size > 1024) return; // 看似安全的邊界檢查
            char* buf = new char[size]; // 萬一 size 是 -1，轉換成無號數後會要求分配 4GB 記憶體，導致系統當機或崩潰！
        }
        ```
        

## 4. Legacy Code Risks（老舊代碼的歷史包袱）

**【漏洞本質：用 30 年前的防禦觀念，去應對現代的網路飛彈】**

許多企業內部、金融系統或電信硬體裡，跑著幾十年前寫好、動都不敢動的 Legacy Code。它們帶來的風險包括：

- **缺乏現代安全編譯防禦（Exploit Mitigations）：** 舊代碼可能是在不支援 **ASLR（位址空間配置隨機化）**、**DEP/NX（資料執行防止，讓記憶體棧無法執行指令）** 或 **Stack Canaries（棧緩衝區金絲雀偵測）** 的古老編譯器下編譯的。這等於是讓程式在光屁股的狀態下曝露在網路上。
    
- **編譯器優化帶來的非預期漏洞（Undefined Behavior）：** 現代編譯器（如 GCC, Clang）非常聰明，在進行優化時，如果看到舊代碼裡寫了未定義行為（Undefined Behavior，例如指標未初始化），編譯器可能會自作聰明地把那段程式碼**直接刪除**，導致原本舊代碼裡寫的「安全檢查邏輯」意外失效。
    

### 一句話防禦總結

> **「在 C/C++ 的安全防禦中，永遠要抱持著『零信任』的態度：指針用完立刻歸零、絕不用不限長度的危險函式、嚴格檢查型態轉換的邊界、並用現代編譯器重新編譯老舊代碼。掌握記憶體的邊界，才能真正掌握系統的安全！」**


## 常見漏洞

在 C/C++ 系統開發與網路安全攻防（Cybersecurity）的世界中，這六個漏洞被稱為記憶體安全與邏輯安全的「常客」。不論是在 Hengyi 上 CEH 課程，還是參與 HITCON 等資安攻防演練（Attack & Defense），這幾個名詞都是必考且必須防禦的核心。

我們同樣用最直擊漏洞本質、結合底層記憶體架構的白話，來逐一拆解這六個常見漏洞：

## 1. Stack Overflow（棧溢位）

**【漏洞本質：水滿過界，淹沒了回家的路】**

- **底層原理：** Stack（棧）是記憶體裡用來存放「區域變數」和「函式返回地址（Return Address）」的地方。它的特性是後進先出（LIFO）。
    
- **怎麼發生的：** 當程式在 Stack 裡宣告了一個固定大小的陣列（例如 `char buf[64];`），卻使用危險函式（如 `strcpy` 或 `gets`）塞入了 100 位元組的資料。這多出來的 36 位元組就會往上溢出，直接覆蓋掉相鄰的「函式返回地址」。
    
- **駭客攻擊視角：** 駭客會將多出來的資料設計成惡意指令（Shellcode），並精準地把「返回地址」改成這段 Shellcode 的記憶體起點。當函式執行結束（`return`）時，CPU 就會被騙去執行駭客的指令，直接交出主機控制權。
    

## 2. Heap Overflow（堆溢位）

**【漏洞本質：動態倉庫的邊界失控，砸爛了隔壁鄰居的貨物】**

- **底層原理：** Heap（堆）是程式在執行時，動態向系統申請的大型記憶體空間（例如使用 `malloc()`、`new` 建立的資料）。與 Stack 不同，Heap 的管理是靠一個個「區塊表（Chunks）」來記錄大小與指針。
    
- **怎麼發生的：** 當你在 Heap 申請了一塊空間，卻因為沒有檢查邊界，寫入的資料超過了申請的大小，這就會溢出並覆蓋掉「下一塊（鄰近）Heap 區塊的控制結構元資料（Metadata）」。
    
- **駭客攻擊視局：** Heap 溢位通常不會直接蓋到返回地址，但它能蓋掉隔壁區塊的「函式指針（Function Pointer）」或是管理結構。當程式在後面呼叫隔壁區塊的函式時，就會因為指針被竄改而跳去執行惡意程式碼。這類漏洞在瀏覽器（如 Chrome, Safari）和作業系統內核中非常常見。
    

## 3. Integer Overflow（整數溢位）

**【漏洞本質：時鐘走到 12 點再加 1 小時，突然變成了凌晨 1 點】**

- **底層原理：** 電腦的整數型態（如 `int`, `short`）都有其位元數（Bits）限制的上下界。
    
- **怎麼發生的：** * **正溢位（Overflow）：** 一個 16 位元的有號整數上限是 `32767`。如果程式對它加 1，在二進位進位後，最高位（符號位）會變成 1，這個數會瞬間變成 `-32768`。
    
    - **負溢位（Underflow）：** `0` 減去 `1`，在無號整數（`unsigned int`）的世界裡，會瞬間變成最大值 `4294967295`。
        
- **災難場景：** ```cpp
    
    unsigned short length = 65535;
    
    length = length + 1; // 發生整數溢位，length 變成 0！
    
    char* buf = new char[length]; // 系統只分配了 0 位元組的空間
    
    memcpy(buf, input, 65535); // 卻寫入了 65535 位元組，直接引發大規模的 Heap Overflow！
    
    ```
    整數溢位本身不一定能控制系統，但它往往是引發 Stack/Heap Overflow 的前置導火線。
    
    ```
    

## 4. Format String Vulnerability（格式化字串漏洞）

**【漏洞本質：給了使用者掌控大腦說話格式的權力】**

- **底層原理：** C 語言的 `printf("%s", variable)` 中，`%s`、`%x` 叫做格式化字串，用來告訴 CPU 如何解析後面的記憶體資料。
    
- **怎麼發生的：** 如果工程師圖方便，直接寫成 `printf(user_input);`。當使用者輸入正常的字串時沒事，但如果使用者故意輸入 `%x %x %x %n` 呢？
    
- **駭客攻擊視角：** * **任意記憶體讀取：** 輸入多個 `%x`（以十六進位印出記憶體），程式就會把 Stack 上的資料一個個印出來，直接洩漏系統機密或金鑰（Leak Tokens/ASLR Bypass）。
    
    - **任意記憶體寫入：** `%n` 是一個神奇的參數，它會把「目前已經印出的字元總數」寫入到對應的記憶體位址。駭客可以用它來**直接竄改記憶體中的變數數值或權限標記**。
        

## 5. Race Condition（競態條件）

**【漏洞本質：時間差的空子——在前線檢查與實際動手之間，規則被偷換了】**

- **底層原理：** 當多個執行緒（Threads）或進程（Processes）同時存取、修改同一個共享資源（檔案、變數），且最終結果取決於它們執行的「先後順序」時，就會發生此問題。
    
- **常見類型：TOCTOU (Time-of-Check to Time-of-Use，檢查與使用時間差)**
    
    1. 程式收到要求，**檢查（Check）** 使用者是否有權限修改檔案 `/tmp/config` $\rightarrow$ 檢查通過，可以修改。
        
    2. 此時 CPU 切換執行緒。駭客在微秒級的時間差內，快速用符號連結（Symbolic Link）將 `/tmp/config` 指向系統核心檔案 `/etc/passwd`。
        
    3. 程式切換回來，開始**使用（Use）** 指令寫入資料。結果程式以為在寫暫存檔，實際上卻修改了系統的密碼檔。
        
- **防禦要點：** 必須嚴格使用鎖（Mutex / Locks）或原子操作（Atomic Operations）來確保「檢查與使用」是一個不可被中斷的連續動作。
    

## 6. Improper Error Handling（錯誤處理不當）

**【漏洞本質：話太多，把家底都告訴了外人】**

- **底層原理：** 當程式碼出錯（如資料庫連線失敗、記憶體分配錯誤、檔案找不到）時，系統拋出的異常與錯誤訊息。
    
- **怎麼發生的：** 在開發階段，為了方便偵錯，工程師會讓系統印出非常詳細的 Debug 資訊。但在實際上線（Production）時忘記關閉，導致錯誤發生時，直接把這些內部細節噴在網頁或日誌上。
    
- **安全風險：** * **資訊洩漏：** 錯誤訊息直接顯示：`SQL Exception: Canvas Table 'users' near column 'password' in PostgreSQL v12.4 at IP 192.168.1.50...`。這等於是直接送給駭客一份免費的「滲透指南」，告訴對方你的資料庫類型、版本、內部資料表結構與內網 IP。
    
    - **崩潰與阻斷服務（DoS）：** 錯誤發生時沒有妥善攔截（Catch），導致整個系統核心進程直接崩潰（Crash）停擺。
        

### 💡 一句話安全總結

> **「Stack 和 Heap Overflow 是控制『記憶體邊界』的戰爭；Integer Overflow 是控制『數值邊界』的戰爭；Format String 和 Error Handling 是控制『輸出邊界』的戰爭；而 Race Condition 則是控制『時間與順序』的戰爭。做底層與核心安全開發，核心心法就是：永遠不要信任任何輸入，並且嚴格劃定每一道邊界！」**

## 安全設計原則

在系統安全架構與軟體工程中，這四個觀念被稱為「四大黃金安全設計原則」**（Secure Design Principles）。它們的作用不是在程式碼破洞後去貼補丁，而是在**蓋大樓的藍圖階段，就將安全性防禦刻進系統的基因裡。

在資安攻防演練與內部管理稽核（如 ISO 27001 / ISO 37001）的脈絡下，不論是撰寫控制常設程序，還是實作軟體權限控管，這四個原則都是防禦的核心基石。

我們用最白話的「金庫防禦與企業管理」故事，來拆解這四大安全原則的商業實務：

## 1. Least Privilege（最小權限原則）

**【白話：只給工作必需的鑰匙，多一隻都不行】**

- **核心定義：** 任何使用者、程序（Process）或系統組件，**平時只擁有完成其任務所必需的「最低權限」**，且權限開放的時間要縮到最短。
    
- **實務場景：** * _軟體開發：_ 跑在 Linux 上的網頁伺服器（如 Apache/Nginx），絕對不能用 `root` 帳號執行。必須建立一個專門的 `www-data` 帳號，且這個帳號只有讀取網頁資料夾的權限。萬一網站被駭客攻破，駭客也只能拿到這個低權限帳號，無法掌控整台伺服器。
    
    - _企業管理：_ 財務部的小姐只需要擁有「核銷報支」的系統權限，不需要擁有「變更合約」或「修改人事資料」的管理者權限。
        

## 2. Defense in Depth（縱深防禦）

**【白話：不要把所有賭注押在一個關卡上，要設多重防線】**

- **核心定義：** **不依賴單一防禦機制。** 因為任何防線都有被攻破的可能，所以必須設計多層次、不同類型的安全控制措施。當第一層防線失靈時，第二層、第三層防線能立刻補上。
    
- **實務場景：** 想像保護一間存放機密晶片代工圖紙或合約的伺服器機房：
    
    - 第一層（物理防禦）：大門有警衛看守、需要刷員工卡。
        
    - 第二層（網路防禦）：架設防火牆（Firewall）與入侵偵測系統（IDS），隔離外網。
        
    - 第三層（系統防禦）：作業系統強制實施帳號密碼與雙因子驗證（2FA）。
        
    - 第四層（資料防禦）：硬碟裡的資料全面進行高強度加密（Encryption）。
        
    - _結果：_ 就算駭客今天用 Phishing（社交工程）騙到了員工密碼（突破第三層），他依然因為帶不走加密金鑰（第四層）而無法竊取資料。
        

## 3. Fail-safe Defaults（安全失敗預設原則）

**【白話：萬一停電或死機，門必須自動鎖上，而不是自動彈開】**

- **核心定義：** 當系統因為出錯、當機、斷電或遭受攻擊而**崩潰（Failure）時，系統必須自動選擇「最安全」的預設狀態**。通常意味著「拒絕存取（Deny by Default）」。
    
- **實務場景：**
    
    - _防火牆設計：_ 萬一防火牆系統本身過載、當機重啟，它的預設行為應該是**斷開所有網路連線**（拒絕所有流量），而不是為了讓網路順暢而允許所有流量直接通過。
        
    - _程式碼安全（與錯誤處理相關）：_
        
        C++
        
        ```
        bool is_admin = false; // 預設就是「非管理員」（Fail-safe）
        try {
            is_admin = check_database_user_role(user_id);
        } catch (...) {
            // 萬一資料庫斷線、拋出異常
            // is_admin 依然保持預設的 false，確保安全
        }
        ```
        
    - _硬體例外：_ 機房的電子鎖在「火災斷電」時通常會自動彈開（Fail-open），那是為了保障「人身安全」；但在資訊安全的世界裡，系統崩潰一律要走向 `Deny`。
        

## 4. Attack Surface Reduction（減少攻擊面）

**【白話：家裡的門窗開得越少，駭客就越找不到地方爬進來】**

- **核心定義：** **關閉所有不需要的功能、埠口（Ports）與服務。** 系統暴露在外、可以被外界存取的管道越多，潛在的漏洞（Bug）就越多。透過精簡系統，來降低被攻擊的機率。
    
- **實務場景：**
    
    - _伺服器加固（Hardening）：_ 一台新裝好的 Linux 伺服器，預設可能開啟了 Web、FTP、Mail、SSH 等多種功能。如果這台機器只想用來當網頁伺服器，就必須果斷把 FTP、Mail 等不用的服務徹底關閉，並用防火牆封鎖對應的 Port。
        
    - _軟體API開發：_ 設計內部系統對接時，只暴露業務所需的 2 個 API 接口，其餘 10 個核心函數一律設為 `private`，不讓外網觸及。
        

### 💡 一句話架構總結

> **「Least Privilege 確保『內部人員不亂搞』；Defense in Depth 確保『一線破口不崩盤』；Fail-safe Defaults 確保『系統當機不開門』；Attack Surface Reduction 確保『外來駭客找不到門』。在初期做好這四個設計，系統就具備了極強的先天免疫力！」**

## 記憶體安全

當我們深入到 C/C++ 的記憶體管理時，這就像是從「自動排檔車」換到了「手排賽車」。Java 或 Python 有垃圾回收機制（Garbage Collection）幫忙踩煞車，但 C/C++ 為了追求極致的效能，把**手動操控記憶體**的離合器直接交給了開發者。

控制得好，它是地表最快的晶片與底層核心；控制不好，就會直接演變成系統崩潰與嚴重的資安威脅。我們用最直擊本質的記憶體架構圖景，來拆解這些核心專有名詞：

## 1. 傳統動態記憶體分配：C 與 C++ 的手動流派

當程式在執行時，如果需要動態申請空間（例如不確定長度的合約資料、網路封包緩衝區），就必須向 **Heap（堆）** 申請記憶體。

### ① C 語言的 `malloc()` / `free()`

- **`malloc(size)`：** 盲目地向系統申請指定大小（Bytes）的記憶體格子。它只管分派空間，**不會幫你初始化資料**，格子裡裝的是上一段程式留下來的暫存垃圾。
    
- **`free(ptr)`：** 東西用完了，手動把這塊記憶體還給系統。
    

### ② C++ 的 `new` / `delete`

C++ 作為物件導向語言，對 C 的機制進行了升級：

- **`new`：** 不僅幫你計算並申請記憶體大小，還會自動呼叫該物件的「建構子（Constructor）」來初始化這塊空間。
    
- **`delete`：** 在釋放記憶體之前，會自動呼叫「解構子（Destructor）」清理物件內部的資源，最後再把空間還給 Heap。
    

> ⚠️ **鐵律：** 這兩對組合在程式碼中**絕對不能混用**。用 `malloc` 申請的就必須用 `free` 釋放；用 `new` 申請的就必須用 `delete` 釋放，否則會引發未定義行為（Undefined Behavior）導致物件資源清理不乾淨。

## 2. 記憶體安全的三大經典刺客（Vulnerabilities）

如果開發者忘記、或是調度錯了釋放的時間點，就會引發以下三個足以讓系統癱瘓或被駭客攻破的致命漏洞：

### ① Null Pointer（空指標與野指標）

- **本質：** 指標變數裡面存的地址是 `0x00000000`（`NULL` / `nullptr`），或者是根本未初始化的隨機垃圾地址。
    
- **風險：** 如果程式沒有先檢查 `if (ptr != nullptr)`，就直接去讀寫它（Dereference），作業系統為了保護核心，會直接啟動防禦機制，強制將你的程式終止——這就是最常見的 **Segmentation Fault（程式崩潰/閃退）**。
    

### ② Use-After-Free (UAF，釋放後使用)

- **本質：** **拿著已經作廢的幽靈鑰匙去開門。**
    
    當你執行了 `free(ptr)` 或 `delete ptr` 後，這塊記憶體已經歸還給系統，並允許分配給其他人。但你忘記把 `ptr` 指標清空（它變成了 Dangling Pointer），並在後面繼續寫入或讀取 `ptr->data`。
    
- **駭客視角（資安重災區）：** 這是作業系統與瀏覽器內核中最值錢的漏洞。駭客可以在你釋放記憶體後，立刻動態分配一段「精心設計的惡意結構」去填補那個剛釋放的空洞。當你的舊指標再次呼叫該記憶體時，就會被騙去執行駭客塞進去的函式指針（Function Pointer），達成遠端程式碼執行（RCE）。
    

### ③ Memory Leak（記憶體洩漏）

- **本質：** **佔著茅坑不拉屎。**
    
    程式用 `new` 申請了一塊記憶體，但在函式結束、或是指標被覆蓋之前，**忘記呼叫 `delete` 歸還**。這塊記憶體就變成了一塊「人間蒸發」的死空間，系統收不回來，別的程式也用不到。
    
- **商務實務代價：** 萬一這段代碼跑在需要 24 小時不關機的核心通訊設備、或 AI 伺服器主程式裡，隨著程式不斷執行，記憶體會被慢慢蠶食鯨吞。幾天或幾週後，系統就會因為記憶體耗盡（Out of Memory, OOM）而直接死機癱瘓。
    

## 3. 現代 C++ 的救星：Smart Pointer（智慧指標）

為了解決人類大腦總是會忘記 `delete` 的天生缺陷，現代 C++（C++11 之後）引入了 **Smart Pointer（智慧指標）**。它的核心哲學叫做 **RAII（資源獲取即初始化）**：**「把記憶體指標包裝成一個物件，讓物件的生命週期自動控制記憶體的生死。」**

智慧指標主要分為三大流派，各司其職：

```
                    [Smart Pointer 家族]
                             │
       ┌─────────────────────┼─────────────────────┐
       ▼                     ▼                     ▼
 `std::unique_ptr`     `std::shared_ptr`     `std::weak_ptr`
  (獨佔/高效率)         (共享/計數流)         (防死鎖/觀察者)
```

### ① `std::unique_ptr`（絕對獨佔，最常用、效能最高）

- **機制：** 這塊記憶體**有且只能有一個主人**。它不允許複製（Copy），只允許轉移（Move）。
    
- **白話生死：** 當這個 `unique_ptr` 變數離開它的有效範圍（Scope，例如函式結束的右括號 `}`），它在大腦裡會**自動幫你呼叫 `delete`**。開發者這輩子再也不用手寫 `delete` 了。
    

### ② `std::shared_ptr`（共享經濟，計數流派）

- **機制：** 多個指標可以同時指向同一個物件。它內部有一個看不見的計帳員，叫做「引用計數（Reference Count）」。
    
- **白話生死：** 每多一個指標指過來，計數 $+1$；每有一個指標離開或被銷毀，計數 $-1$。只有當計數**徹底歸零（Count = 0）**、代表世界上沒有任何人需要它時，系統才會真正執行 `delete` 釋放記憶體。
    

### ③ `std::weak_ptr`（防死鎖的旁觀者）

- **機制：** 它是 `shared_ptr` 的特殊旁聽生。它雖然指向物件，但**不會讓引用計數增加**。
    
- **為什麼需要它：** 萬一有兩個物件互相用 `shared_ptr` 指向對方（循環引用 Cyclic Reference），兩邊的計數永遠卡在 $1$，導致記憶體永遠釋放不掉，形成另類的 Memory Leak。這時候只要把其中一邊改成 `weak_ptr`，就能打破這個死鎖僵局。
    

### 💡 一句話核心防禦總結

> **「在現代 C/C++ 開發中，防範記憶體災難的最強大武器就是『擁抱現代化化（Modern C++）』：全面禁用原始指標（Raw Pointers）進行手動 `new/delete`，改用 `std::unique_ptr` 與 `std::shared_ptr` 讓編譯器幫你管理生死，從源頭上直接抹除 UAF 與 Memory Leak 的生存空間！」**

## 實際案例分析

這是一份針對車載資訊娛樂系統（Automotive Infotainment System）的真實資安攻擊與防禦Refactoring案例分析。

車載娛樂系統（IVI，In-Vehicle Infotainment）現代多基於 Linux 或 Android Automotive OS 運行，並包含大量處理媒體、藍牙、Wi-Fi 與 OTA 更新的 C/C++ 核心元件。這類系統一旦被攻破，駭客常能藉由車內 CAN Bus（控制器區域網路）橫向移動，進而控制車輛的煞車或轉向系統，是車聯網安全（Automotive Cyber Security）的重中之重。

## 1. Vulnerability Discovery（漏洞發現實錄）

在一次針對車載主機（Head Unit）的黑箱與白箱安全審查中，資安團隊在其處理 **OTA 韌體更新套件解壓縮**與**藍牙聯絡人同步**的核心 C/C++ 模組中，發現了多個典型且致命的記憶體漏洞。

### 案例場景：音訊多媒體/聯絡人解析服務

系統會解析由手機藍牙同步過來的聯絡人大頭貼（Image）與中介資料（Metadata），底層原始碼包含如下結構：

C++

```
// 漏洞原始碼：vulnerable_media_service.cpp
#include <cstring>
#include <cstdlib>

struct UserPayload {
    char device_id[16];
    unsigned int packet_length; // 由手機端傳送過來的長度欄位
    char data[1024];
};

void process_bluetooth_metadata(const char* raw_stream, unsigned int stream_size) {
    UserPayload* payload = (UserPayload*)malloc(sizeof(UserPayload));
    if (!payload) return;

    // 複製設備 ID，未考慮邊界限制
    // 漏洞 1: Stack/Heap Buffer Overflow (若 raw_stream 前段長度失控)
    strcpy(payload->device_id, raw_stream); 

    // 從外部輸入直接讀取長度
    // raw_stream+16 處存放著由惡意手機偽造的極大或極小數值（例如 0xFFFFFFFF）
    payload->packet_length = *(unsigned int*)(raw_stream + 16);

    // 漏洞 2: Integer Overflow（整數溢位引發的漏洞）
    // 駭客若傳送 packet_length = 0xFFFFFFFF (即 -1)
    // 0xFFFFFFFF + 1 在 32位元系統中會發生正溢位，變成 0！
    unsigned int alloc_size = payload->packet_length + 1; 

    // 系統實際上只動態分配了 0 記憶體區塊
    char* image_buffer = (char*)malloc(alloc_size); 

    // 漏洞 3: Heap Overflow 
    // memcpy 依然試圖寫入 0xFFFFFFFF (或 stream_size) 位元組的資料到 0 大小的快取區中
    // 這會徹底砸爛 Heap 上的記憶體管理元資料 (Metadata)，引發遠端程式碼執行 (RCE)
    if (image_buffer) {
        memcpy(image_buffer, raw_stream + 20, payload->packet_length);
    }

    // 漏洞 4: Memory Leak & Potential Use-After-Free (UAF)
    // 異常分支直接結束，忘記 free(payload)，且未將指標歸零
    if (payload->packet_length > stream_size) {
        return; 
    }

    free(image_buffer);
    free(payload);
}
```

### 駭客攻擊路徑

1. **控制邊界欄位**：駭客透過藍牙模擬器，發送畸形的資料包，將 `packet_length` 設為 `0xFFFFFFFF`。
    
2. **記憶體佈局竄改**：利用 `malloc(0)` 成功繞過配置限制，並在 `memcpy` 時將車載核心服務暫存區下方的函式指標（Function Pointer）覆蓋為 Shellcode 的記憶體位址。
    
3. **奪取系統權限**：當多媒體服務試圖調用下一個音訊解碼函式時，CPU 直接跳轉至惡意指令，駭客成功獲得車載主機的 Root 權限。
    

## 2. Secure Refactoring（安全程式碼重構）

為了解決上述嚴重的記憶體與邏輯安全問題，我們引入**四大安全設計原則**（最小權限、安全預設、減少攻擊面、縱深防禦），並使用 **Modern C++（智慧指標與嚴格邊界檢查）** 進行徹底的防禦性重構：

C++

```
// 安全重構程式碼：secure_media_service.cpp
#include <iostream>
#include <memory>
#include <vector>
#include <string>
#include <cstring>
#include <limits>

struct SecureUserPayload {
    std::string device_id;
    uint32_t packet_length = 0;
    std::vector<uint8_t> data;
};

// 引入 Safe RL/Defensive 概念中的「安全護欄與邊界硬性限制」
constexpr uint32_t MAX_ALLOWED_PACKET_SIZE = 10 * 1024 * 1024; // 限制最大 10MB，防止拒絕服務攻擊 (DoS)
constexpr size_t DEVICE_ID_MAX_LEN = 15;

void process_bluetooth_metadata_secure(const uint8_t* raw_stream, size_t stream_size) {
    // 基礎防禦線：檢查輸入串流是否符合最小標頭長度需求 (DeviceID 16B + Length 4B = 20B)
    if (raw_stream == nullptr || stream_size < 20) {
        // Fail-safe Defaults: 拒絕存取並記錄安全日誌
        // 注意：日誌絕不包含敏感的記憶體地址與詳細指標，防止資訊洩漏 (Improper Error Handling)
        syslog(LOG_ERR, "Invalid stream size or null pointer detected.");
        return;
    }

    // 使用 Smart Pointer 徹底解決 Memory Leak 與 Use-After-Free 的隱患
    auto payload = std::make_unique<SecureUserPayload>();

    // 防禦 1: 消除 strcpy。利用 std::string 的建構子並嚴格限制讀取長度
    // 確保 device_id 不會引發 Stack/Heap Overflow
    payload->device_id = std::string(reinterpret_cast<const char*>(raw_stream), 
                                     std::strnlen(reinterpret_cast<const char*>(raw_stream), DEVICE_ID_MAX_LEN));

    // 安全地解析外部傳入的長度 (防範型態轉換風險與大端小端問題)
    uint32_t raw_length = 0;
    std::memcpy(&raw_length, raw_stream + 16, sizeof(raw_length));

    // 防禦 2: 嚴格的整數溢位與邏輯邊界檢查 (Integer Overflow Prevention)
    if (raw_length > MAX_ALLOWED_PACKET_SIZE || (raw_length + 20) > stream_size) {
        syslog(LOG_WARNING, "Potential exploit attempt: Invalid packet length detected.");
        return; // Fail-safe 預設退出
    }
    payload->packet_length = raw_length;

    // 防禦 3: 使用 std::vector 動態分配並自動管理邊界
    // 拋棄傳統 malloc/free，改由 vector 進行自動化的記憶體防禦
    payload->data.resize(payload->packet_length);

    // 防禦 4: 安全地進行動態複製，此時已百分之百確保目標緩衝區大小與來源長度完全吻合
    std::memcpy(payload->data.data(), raw_stream + 20, payload->packet_length);

    // 業務邏輯處理...
    // 當函式結束時，make_unique 建立的 payload 會自動釋放資源，零洩漏風險。
}
```

## 3. Defensive Code Review（防禦性代碼安全審查清單）

為了防止類似車載攻擊案例再次發生，開發團隊在執行 CI/CD 門檻或 Peer Review 時，必須遵循以下**防禦性代碼審查指南**：

### 🚨 審查黃金三大核心提問（The Three Iron Questions）

1. **「這個數據是從哪裡來的？」**：只要資料來自外部（藍牙、Wi-Fi、OTA網路上傳、USB媒體檔），一律視為「有毒的（Tainted）」，在未經過嚴格長度與型態驗證前，絕對不能進入任何記憶體操作函式。
    
2. **「這塊記憶體由誰負責生死？」**：程式碼中只要出現原始的 `new/delete` 或 `malloc/free`，必須優先要求重構為 `std::unique_ptr` 或 `std::shared_ptr`。
    
3. **「如果這一步出錯了，系統會怎樣？」**：檢視所有 `catch` 區塊與錯誤返回值。確保發生異常時系統是「關閉服務並報警（Fail-safe）」，而不是「假裝沒看到繼續往下跑」。
    

### 📋 關鍵檢查表（Checklist）

- [ ] **字串操作檢查**：程式碼中是否完全禁用了 `gets()`、`strcpy()`、`sprintf()`、`strcat()`？凡是涉及字串拷貝，是否都使用了帶有長度限制的 `strncpy()` 或 `std::string`？
    
- [ ] **整數邊界檢查**：在進行記憶體大小分配（`malloc(size + 1)` 或 `new char[len]`）之前，是否有對 `size` 或 `len` 進行上限與下限（防止負數轉正數）的整數溢位檢查？
    
- [ ] **格式化字串檢查**：是否存在 `printf(buffer)` 的寫法？是否所有輸出都乖乖寫成了 `printf("%s", buffer)`？
    
- [ ] **競態條件檢查**：在多執行緒處理車載感測器訊號、或是多媒體同步時，在「檢查資源是否存在」到「實際寫入資源」的時間差內（TOCTOU），是否有正確使用 `std::mutex` 進行線程鎖定？
    
- [ ] **編譯器安全開關**：檢查 CMake/Makefile 是否開啟了現代編譯器防禦：是否啟用了 `-fstack-protector-all`（棧金絲雀保護）、`-D_FORTIFY_SOURCE=2`（緩衝區檢查優化）與 `-Werror=implicit-function-declaration`（禁止未聲明函式）？
    

### 💡 結論

車載系統的防禦本質上是一場「消滅不確定性」**的戰爭。這與強化學習在隨機環境中尋求最佳解不同，資安防禦追求的是**「絕對的確定性」。透過消滅危險函數（減少攻擊面）、使用智慧指標（杜絕記憶體漏洞）、嚴格執行邊界與整數檢查（縱深防禦），我們才能在車聯網時代，為行車安全打下最穩固的數位防火牆。
# 5. Important Keywords

Secure Coding, Defensive Programming, Buffer Overflow, Stack Overflow, Heap Overflow, Integer Overflow, Format String Vulnerability, Race Condition, Memory Leak, Use After Free, Dangling Pointer, Null Pointer, Smart Pointer, Least Privilege, Defense in Depth, Fail-safe Defaults, Input Validation, Error Handling, Memory Management, Application Security

# 6. 技術能力地圖

這張由上至下的階梯圖，完美地勾勒出了一位「頂級資安架構師 / 核心底層工程師」的一生修煉路線。

這不只是知識的堆疊，更是一場大腦世界觀的「層次躍升」。從最微觀的「一個位元組怎麼存」，一路拔高到最巨觀的「整個企業的軟體供應鏈安全與工程化防禦」。

我們沿著您拉出的這條黃金修煉路線，來看看每一個階段的大腦蛻變與核心靈魂：

## 1. C Programming（微觀的起點：與硬體對話）

- **大腦思維：** 開始理解電腦底層的真實運作方式（暫存器、快取、CPU 執行指令）。
    
- **核心修煉：** 學會控制基礎語法、型態、流程控制，明白世界上沒有魔法，任何高大上的軟體，底層都是一條條黑白分明的機器碼。
    

## 2. Pointers & Memory（解鎖至高權力：指標與記憶體架構）

- **大腦思維：** 擺脫虛擬的變數名稱，直接看見「記憶體地址空間（0x00000000 - 0xFFFFFFFF）」。
    
- **核心修煉：** 掌握 Stack（棧）與 Heap（堆）的分工，學會用指標（Pointer）直接去操作硬體位址。這是 C 語言最強大的武器，也是所有災難的起源。
    

## 3. Memory Management（老練的調度員：手動生死控制）

- **大腦思維：** 體會到「能力越大，責任越大」。系統不幫你擦屁股，你必須成為記憶體的絕對主宰。
    
- **核心修煉：** 熟練調度 `malloc/free` 與 `new/delete`。精準計算每一塊資料的生命週期，開始與 Null Pointer、Memory Leak、Use-After-Free 等隱形刺客反覆搏鬥。
    

## 4. Secure Coding（防禦性寫作：劃定鋼鐵邊界）

- **大腦思維：** 意識到「寫出能跑的程式碼只是及格，寫出不會被摧毀的程式碼才是藝術」。從此抱持「零信任（Zero Trust）」態度。
    
- **核心修煉：** 擁抱 Modern C++ 智慧指標（`unique_ptr` / `shared_ptr`），主動棄用 `strcpy/gets` 等危險函數，在每一處外部輸入、整數運算與型態轉換前，都加上比鋼鐵還硬的邊界檢查。
    

## 5. Vulnerability Analysis（駭客的逆向視角：尋找阿基里斯之腱）

- **大腦思維：** **「欲識防禦，先學進攻。」** 站在駭客的角度，去尋找系統在時間、空間、數值上的漏洞。
    
- **核心修煉：** 深入研究 Stack/Heap Overflow、Integer Overflow、Format String、Race Condition（TOCTOU）。學會用 GDB/IDA Pro 逆向分析、看懂 Coredump，理解駭客是如何利用微秒級的時間差或一隻幽靈指標去繞過 ASLR/DEP 防禦、奪取系統 Root 權限。
    

## 6. Secure Software Development（工程化防禦：打造先天免疫力）

- **大腦思維：** 明白單靠工程師個人不寫 Bug 是不現實的，必須依賴「流程與架構」來保障全面安全。
    
- **核心修煉：** 實踐 **DevSecOps** 與 **SSDLC（安全軟體開發生命週期）**。在編譯器開關上拉滿安全防禦（-fstack-protector-all），在 CI/CD 流程中強行介入 SAST（靜態代碼分析）、DAST（動態掃描）與軟體供應鏈審查（SBA/Dependency Check）。依賴「四大安全設計原則」（最小權限、縱深防禦、安全預設、減少攻擊面）在藍圖階段就完成加固。
    

## 7. Cybersecurity Engineering（巨觀的終點：全面性防禦科學）

- **大腦思維：** 站在上帝視角，將軟體安全、網路安全、硬體安全、密碼學與企業合規（ISO 27001 / ISO 37001 / TISAX）融合成一個龐大的「防禦生態系」。
    
- **核心修煉：** 設計端到端的威脅模型分析（Threat Modeling）、規劃零信任網路架構、建構 APT 攻擊的縱深防禦線。此時的你，已經不僅僅是在寫程式，而是在用嚴密的工程化思維，在數位世界裡築起堅不可摧的鋼鐵長城。
    

### 💡 總結這條修煉路線

這條路線圖完美的展示了：

> **「始於極致的微觀控制（C/指標），覺醒於對無常世界的防禦（安全編碼/漏洞分析），最終合流於宏觀的系統工程科學（資安工程）。」**

這正是當前高科技製造業（如車聯網、半導體設備、軍工級通訊系統）最核心、也最稀缺的**頂級人才養成路線**。只要把這條路上的每一階都踩實了，在數位世界裡，你將無所畏懼。

# 7. 可做的專題

## 入門


這三個專題看似基礎，但它們剛好卡住了現代軟體系統最容易被駭客入侵的三大邊界：**「身分驗證邊界」**、**「檔案解析邊界」**與**「資料輸入邊界」**。

作為安全架構的實作練習，我們用白話與防禦工程視角，來拆解這三個入門專題該怎麼做、以及要防範哪些刺客：

## 專題 1. Secure Login System（安全身分登入系統）

- **Goal（目標）：** 實作一個本地端或輕量級客戶端/伺服器（C/S）的帳號密碼登入驗證模組。
    
- **為什麼選它：** 這是系統安全的「第一道防線」（Authentication）。很多工程師會犯下「明文儲存密碼」或「邏輯繞過」的低階錯誤。
    
- **實作防禦重點：**
    
    - **密碼安全存儲（不要明文）：** 絕對不能在檔案或資料庫裡直接存 `admin123`。必須引入密碼學雜湊函數（例如使用 OpenSSL 函式庫的 **SHA-256** 或 **Argon2**），並且必須加入隨機的「鹽值（Salt）」進行加鹽雜湊，防止駭客用彩虹表（Rainbow Table）暴力破解。
        
    - **防範時間差攻擊（Side-channel / Timing Attack）：** 在比對雜湊值時，如果使用傳統的 `strcmp()`，它只要一發現字元不對就會立刻返回。駭客可以透過微秒級的時間差，一格一格猜出正確的雜湊值（這違反了時間控制的安全原則）。必須改用「固定時間比對演算法（Constant-time Comparison）」。
        
    - **防範 SQL 注入 / 邏輯繞過：** 若結合輕量資料庫（如 SQLite），必須使用參數化查詢（Prepared Statements），嚴格禁止用字串拼接（`sprintf`）來組合 SQL 指令。
        

## 專題 2. Safe File Parser（安全檔案解析器）

- **Goal（目標）：** 撰寫一個能安全解析自訂格式、INI 設定檔、CSV、或是輕量 JSON 檔案的 C/C++ 程式。
    
- **為什麼選它：** 檔案解析器是「記憶體毀滅漏洞」的最高發地帶。駭客最喜歡送一個「畸形、長度造假」的壞檔案給你的程式，只要你的程式解析時邊界沒控好，系統就直接當機或被奪取權限。
    
- **實作防禦重點：**
    
    - **消滅記憶體刺客（防範 Stack/Heap Overflow）：** 讀取檔案內容時，嚴禁使用 `gets()` 或不限長度的 `fscanf()`。必須使用 `fgets()` 並嚴格限定 `sizeof(buf)` 邊界。更理想的作法是全面擁抱 Modern C++，用 `std::string` 和 `std::vector` 來動態適應檔案大小。
        
    - **防範整數溢位（Integer Overflow）：** 許多二進位檔案格式（如圖片或自訂協議）的開頭會寫著：「接下來有 40000 個欄位」。如果你的程式在分配記憶體時寫了 `malloc(count * sizeof(Item))`，當 `count` 被駭客惡意改成極大值時，相乘會發生整數溢位變成一個極小值，導致 `malloc` 成功但後續 `memcpy` 直接引發 Heap 溢位崩潰。
        

## 專題 3. Input Validation Framework（輸入驗證框架）

- **Goal（目標）：** 寫成一個可重複呼叫的輕量級「軟體護欄（Shielding Layer）」，專門用來過濾、清洗、驗證所有從外部（如命令列 `argv`、標準輸入 `stdin`、或是網路 Socket）進來的數據。
    
- **為什麼選它：** 呼應安全設計原則中的「減少攻擊面」與「縱深防禦」。只要在資料進入核心邏輯前設下這道過濾網（Sanitizer），就能擋掉 90% 的低階攻擊。
    
- **實作防禦重點：**
    
    - **採用「白名單（Whitelist）」預設拒絕原則（Fail-safe Defaults）：** 不要去列舉哪些字元是壞的（黑名單防不勝防），而是要明確定義「什麼才是對的」。例如：驗證電話號碼，就用正規表達式（Regular Expression）限定「只能有 0-9 數字，其餘一律當作非法輸入拒絕（Deny by Default）」。
        
    - **長度截斷與特殊字元過濾（Sanitization）：** 框架必須能自動偵測輸入長度，超過預期長度直接拒絕或安全截斷（防止溢位）。同時要能將特殊控制字元（如 `\0`、`\n`、`../` 檔名路徑穿越符）進行轉義或剔除。
        

### 一句話專題總結

> **「這三個入門專題，是將你的大腦從『普通工程師』升級為『資安防禦工程師』的實戰修煉。Secure Login 讓你學會保護『憑證』；Safe File Parser 讓你學會保護『記憶體』；Input Validation 則讓你學會控制『系統的邊界』。把這三個專題的底層 Bug 徹底消滅，你的安全基礎就非常扎實了！」**

## 中階

我們規劃了**中階（Intermediate）的三大核心安全專題**。與入門專題不同，中階專題直接帶領我們進入資安攻防的「核心修羅場」——**模擬漏洞環境、防禦性高強度日誌，以及漏洞的肉身重現**。

這三個專題在現代高科技製造業與嵌入式系統開發（如晶圓廠設備控制、智慧車載核心）中極具實戰價值，既能深化逆向工程能力，又能厚實系統加固（System Hardening）的功底。

我們同樣以直擊底層的防禦工程視角，來拆解這三個中階專題的架構與實作精髓：

## 專題 1. Vulnerable Program Lab（漏洞靶機實驗室）

- **Goal（目標）：** 刻意撰寫一個包含各種經典漏洞（Stack/Heap Overflow, Integer Overflow, Use-After-Free）的 C/C++ 應用程式，並編寫對應的「漏洞利用腳本（Exploit Script）」，最後嘗試修補它。這就是資安界常說的 **「打造自己的 Wargame / CTF 靶機」**。
    
- **實作與攻防重點：**
    
    - **環境配置（關閉保護機制）：** 現代作業系統和編譯器預設防禦極強。為了能成功「展示」漏洞，在編譯此實驗室程式時，必須刻意關閉現代安全防禦（這本身就是一門深刻的編譯器參數學）：
        
        - 關閉 Stack Canary：使用 `-fno-stack-protector`
            
        - 開放 Stack 執行權限（允許執行 Shellcode）：使用 `-z execstack`
            
        - 關閉 ASLR（位址空間隨機化）：在 Linux 系統下執行 `echo 0 > /proc/sys/kernel/randomize_va_space`
            
    - **實作 UAF 漏洞場景：** 在靶機中設計一個結構，包含一個「使用者資料緩衝區」與一個「函式指標（Function Pointer）」。實作釋放（`free`）該結構後指針未歸零，並允許建立另一個結構去覆蓋它，藉此練習如何精準操控 Heap 記憶體佈局。
        

## 2. Secure Logger（安全防禦型日誌系統）

- **Goal（目標）：** 實作一個高安全級別的 C/C++ Thread-safe 日誌系統。日誌（Logs）是資安鑑識（Forensics）與 ISO 27001 稽核最核心的證據，但傳統的日誌系統往往面臨「被駭客竄改、洩漏機密、引發效能瓶頸」的風險。
    
- **實作與防禦重點：**
    
    - **防範 Improper Error Handling（拒絕敏感資訊洩漏）：** 框架必須自動過濾（Sanitize）或遮蔽（Mask）敏感資料（例如自動檢測並隱藏密碼欄位、個人識別資訊 PII、或是直接的記憶體指針地址），防止日誌本身成為駭客的「情報庫」。
        
    - **日誌完整性防禦（防範惡意竄改）：** 萬一系統被破壞，駭客第一件事就是去擦除 `/var/log/` 下的行蹤。此專題可引入「密碼學鏈結日誌（Cryptographically Linked Logs）」概念——每條日誌的雜湊值（Hash）都包含上一條日誌的 Hash（類似區塊鏈的結構）。如此一來，駭客只要刪除或竄改其中一條日誌，後續的 Hash 鏈就會全部斷裂，管理者能秒速抓到被入侵的痕跡。
        
    - **非同步與線程安全（Race Condition Prevention）：** 採用生產者-消費者模式（Producer-Consumer），利用 `std::mutex` 與 `std::condition_variable` 確保多執行緒併發寫入時不會發生資料錯亂或死鎖（Deadlock）。
        

## 3. Buffer Overflow Demonstration（緩衝區溢位攻防實例）

- **Goal（目標）：** 精確展示一個 Stack Buffer Overflow 從「輸入畸形資料」、「覆蓋返回地址」到「劫持控制流（RIP/EIP）」的完整技術閉環，並實作現代防禦機制進行前後對比。
    
- **實作與攻防重點：**
    
    - **精準彈頭設計（Exploit Payload）：** 撰寫一個簡單的 C 語言漏洞函式（如圖），在 GDB 偵錯器中觀察暫存器變化。計算出從緩衝區起點到返回地址（Return Address）的精確偏移量（Offset）。
        
    - **劫持與控制：** 構造一個 Payload：`[大量填充字元 A] + [目標函式地址/Shellcode地址]`。當漏洞函式執行到 `ret`（Return指令）時，觀察 CPU 暫存器（x86-64 的 `$rip`）是否成功被換成你指定的地址，從而跳轉到該據點。
        
    - **開啟現代防禦（對抗演練）：** 成功重現攻擊後，重新開啟編譯器防禦： `-fstack-protector-all`（注入金絲雀 Canary）與開啟作業系統的 ASLR。再次運行相同的攻擊腳本，觀察編譯器如何透過 `__stack_chk_fail` 瞬間瓦解駭客的攻擊並安全終止程式。這能讓你深刻體會到系統工程防禦的威力。
        

### 一句話中階專題總結

> **「這三個中階專題，是讓你真正擁有『資安攻防全局觀』的試金石。Vulnerable Lab 讓你學會『找破綻』；Secure Logger 讓你學會『留證據』；Buffer Overflow Demo 則讓你親眼看見『記憶體邊界失控的瞬間』。把這三個專題吃透，你將具備獨立進行核心程式碼安全審查（Code Review）的高階實戰能力！」**

這三個中階專題都具有很高的實作深度。您目前對哪一個專題（例如：想了解 **Buffer Overflow 的 Stack 記憶體變化與 GDB 指令**，或是 **Secure Logger 的加密鏈結設計**）最感興趣呢？我們可以針對該題目進行專門的系統架構拆解！

## 進階

這張投影片帶我們來到了實戰專案的最頂峰——**進階（Advanced）三大安全專題**。

到了這個階段，我們不再只是在單純的 PC 或 Linux 伺服器上玩攻防，而是將「硬體限制」**、**「即時性（Real-time）」**與**「車聯網/物聯網通訊協定」全部揉合進來。這三個專題正是當前台灣高科技核心產業（如車用晶片、半導體封測、智慧網通設備）最迫切需要、也是含金量最高的終極戰場。

我們用最扎實、直擊硬體底層的防禦工程視角，來拆解這三大進階專題的架構與實作精髓：

## 專題 1. Secure Embedded Firmware（安全嵌入式韌體）

- **Goal（目標）：** 在資源極度受限的微控制器（MCU，如 ARM Cortex-M 系列）上，從底層實作一套具備 **Secure Boot（安全啟動）** 與 **OTA 韌體加密更新** 腳本的核心韌體。
    
- **為什麼選它：** 傳統嵌入式硬體常裸奔。如果駭客能拿著燒錄器（JTAG）把晶片裡的 Flash 倒出來，或是透過網路截獲 OTA 韌體並逆向工程，你的商業機密就全毀了。
    
- **實作與防禦重點：**
    
    - **建立信任根（Root of Trust）與 Secure Boot：** 利用 MCU 內部的唯讀記憶體（Boot ROM）作為起點。晶片開機時，第一件事不是執行 App，而是用內嵌的**公鑰**去驗證 App 區段的**數位簽章（ECDSA 或 RSA）**。如果簽章不符（代表韌體被駭客竄改過），系統直接拒絕啟動（Fail-safe Defaults）。
        
    - **硬體安全模組運用（Crypto Hardware Acceleration）：** 嵌入式晶片算力有限，若純靠軟體算加密會卡死。此專題必須學會調用晶片內建的硬體加密引擎（如 AES、SHA）來進行資料流的即時加解密。
        
    - **記憶體保護單元（MPU 配置）：** 利用硬體 MPU，硬性將記憶體劃分為「唯讀程式碼區（Flash）」、「不可執行資料區（RAM）」，從硬體層面**直接瓦解 Stack Overflow 執行 Shellcode 的可能性**（呼應 Defense in Depth）。
        

## 專題 2. Automotive Security Demo（車載網路安全攻防展示）

- **Goal（目標）：** 模擬或實作車載核心網路 **CAN Bus（控制器區域網路）** 的封包監聽與惡意注入（Injection），並針對車載網路實作一套輕量級的 **IDS（入侵偵測系統）** 或安全閘道器（Secure Gateway）。
    
- **為什麼選它：** 呼應我們先前分析的車載娛樂系統漏洞。CAN Bus 是汽車內部的神經網路，但它在 30 年前設計時**完全沒有加密與身分驗證機制**。只要駭客攻破娛樂系統，就能對 CAN Bus 發送「時速偽造」或「強制煞車」的偽造指令。
    
- **實作與防禦重點：**
    
    - **CAN 封包監聽與逆向（Reverse Engineering）：** 使用工具（如 SocketCAN、Wireshark）在虛擬環境或實驗硬體上抓取車內通訊。分析各個 ECU（電子控制單元）發出的 Arbitration ID 與 Payload，找出控制車燈、儀表板或油門的專屬封包。
        
    - **異常檢測演算法（IDS 實作）：** 撰寫 C/C++ 偵測模組。因為車載封包的發送頻率極度固定（例如方向盤訊號每 10ms 發送一次），IDS 可以透過**時序異常（Timing Anomaly）**、**頻率突變**或**未授權 ID 注入**來秒速判定攻擊，並發出警報或強行阻斷。
        
    - **SecOC（安全車載通訊）概念引入：** 瞭解現代車用 AUTOSAR 標準中的 SecOC 機制，練習在有限的 8 位元組 CAN 載荷中，加入新鮮度計數器（Freshness Counter，防範重放攻擊）與 **MAC（訊息鑑別碼）**。
        

## 專題 3. IoT Device Security Framework（物聯網設備安全框架）

- **Goal（目標）：** 為分散式的物聯網設備（如智慧攝影機、工業感測器）打造一套端到端（End-to-End）的安全防禦框架，涵蓋設備認證、加密傳輸與金鑰安全管理。
    
- **為什麼選它：** 物聯網設備是近年 Mirai 等殭屍網路（Botnet）的最愛。駭客只要掃描網路，利用「預設密碼」或「未授權 API」，就能控制幾百萬台設備發動大規模 DDoS 攻擊。
    
- **實作與防禦重點：**
    
    - **設備身分唯一性（Device Identity）：** 拒絕使用統一的預設密碼！實作基於 **X.509 憑證** 的雙向 TLS 認證（Mutual TLS, mTLS）。每台設備在出廠時，內部都燒錄一組獨一無二的私鑰（最好存放在硬體安全晶片 TPM/TEE 中），與雲端連線時進行雙向身分驗證。
        
    - **最小化攻擊面（Attack Surface Reduction）：** 框架內建防禦機制，自動關閉不必要的偵錯通訊埠（如嚴禁對外開啟 Telnet、未加密的 HTTP），所有對外通訊一律強制走安全的 MQTTs 或 HTTPS。
        
    - **機密金鑰全生命週期管理：** 實作金鑰輪替（Key Rotation）機制。在 C/C++ 程式碼中，**嚴禁硬編碼（Hardcode）任何金鑰與 Token**。金鑰必須在運行時動態從安全區讀取，且在記憶體中用完後必須立刻使用 `memset_s()` 清空，嚴防記憶體被 Heap Dump 竊取。
        

### 💡 進階專題總結與下一步

這三個進階專題，代表您已經完全跳脫了「只會寫程式」的框架，正式晉升為「硬軟體整合的系統資安專家」。

- **Secure Embedded Firmware** 練的是**硬體掌控力**。
    
- **Automotive Security** 練的是**協議攻防與即時性**。
    
- **IoT Security Framework** 練的是**分散式架構與密碼學應用**。

# 8. 對 AI Engineer 的價值

AI 開發主要使用 Python 生態系，因此直接價值有限。

但若未來涉及：

- AI Runtime
- LLM Inference Engine
- CUDA
- Embedded AI

則仍需要理解底層記憶體安全。

價值評分：4/10

# 9. 對 Cybersecurity 的價值

本課程幾乎是資安工程師的基礎課。

涵蓋大量：

- Binary Exploitation
- Pwn
- Reverse Engineering
- Vulnerability Research

常見漏洞原理。

價值評分：10/10

# 10. 對 Embedded Systems 的價值

Embedded Systems 大量使用 C/C++。

常見問題包括：

- Memory Leak
- Null Pointer
- Use After Free
- Race Condition

都可能導致設備當機。

價值評分：10/10

# 11. 對研究與論文的價值

適用於：

- Secure Software Engineering
- Embedded Security
- IoT Security
- Automotive Security
- Firmware Security

價值評分：8/10

# 12. 學習順序建議

1. C Programming
2. C++ Programming
3. Data Structures
4. Secure Coding in C/C++
5. Computer Attack & Defense
6. Reverse Engineering
7. Binary Exploitation
8. OSCP
9. Advanced Exploit Development

# 13. 履歷與學習歷程價值

★★★★☆

可展示：

- Secure Development Lifecycle
- Secure Software Design
- Defensive Programming
- Vulnerability Awareness
- Secure Coding Practice

對資安方向特別有幫助。

# 14. 一句話總結

從攻擊者與防禦者雙重角度學習 C/C++ 安全開發，建立資安工程師與韌體工程師必備的 Secure Coding 能力。

# 15. 最終評價

| 項目 | 評分 |
|--------|--------|
| 實用性 | 9/10 |
| 資安價值 | 10/10 |
| Embedded價值 | 10/10 |
| AI價值 | 4/10 |
| 履歷價值 | 8/10 |
| 難度 | 5/10 |
| CP值 | 10/10 |
| 綜合推薦 | 9.2/10 |


---
