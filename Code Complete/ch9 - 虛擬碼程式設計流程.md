# 虛擬碼程式設計流程
### 類別建立
```
\                ---------------------------
				|							|
				v							|
開始---->建立類別的整體設計------------>建立類別中的子程式
				^							^
				|							|
				└----->複審並測試整個類別 <----┘ 
							└--------------------->完成
```	

### 子程式建立
```
開始------->設計子程式<----------->檢查設計
			   ^				   |
			   |				   |
			   |                   v
		複審並測試程式碼 <---> 編寫子程式的程式碼  
				└--------------------------------->完成
```	
## 如何寫好pseudocode
* 用類似英文的句型描述行為
* 避免使用目標程式語言的語法，虛擬碼可以讓你在一個目標語言略高的層次進行設計。
* 不要管目標語言，以虛擬碼描述解決方法的原意
* 虛擬碼要在足夠低的層次上撰寫，以便由他來近乎自動地產生程式碼。如果不夠低，會有些問題細節被忽略。
* 必須要不斷精煉，直到看起來很容易能寫出程式碼為止
* 好的 pseudocode 是可以當作產品程式碼的註解的
## 透過PPP建立子程式
### 設計子程式
* 檢查先決條件，檢查該子程式是否以定義好要做的工作並且是否與整體設計匹配
	* 也要檢查進入及離開子程式時的需求是否達成(資料位於合法範圍、檔案已打開/關閉、緩衝區填滿/清空)
* 定義子程式要解決的問題
	* 且描述的足夠詳細
	* 包含:	
		* 這個子程式要隱藏的資訊
		* 子程式的輸入
		* 子程式的輸出
		* 滿足子程式的前置條件(檔案是否開啟等等)
		* 滿足子程式的後置條件
* 為子程式命名
* 決定如何測試你的子程式
	* 想想要怎麼去測試，有助於寫出可測試的程式碼
* 使用standard library
* 考慮錯誤處理
	* 預想可能出錯的環節
	* 出錯的處理策略
* 考慮效率問題
	* 不是說每個程式都要有很高的效率，是說你要為了未來能夠將程式碼提高效率而設計，像是要有良好的抽象及封裝，未來可以換成其他效率更高的演算法。
	* 通常要改善效率應該先著重在高層次的設計，除非你能證明子程式無法滿足效率標準，不然去改善只是浪費力氣。
* 研究演算法及資料類型
* 編寫虛擬碼
	* 做完上述步驟就可以開始寫虛擬碼了
	* 先用句子寫出程式碼的描述，寫描述可以闡明你對子程式的理解
	* 寫完後就可以用高層次去編寫虛擬碼
* 考慮資料
	* 如果資料的操作是該子程式的重點，則值得在考慮子程式的邏輯前先搞清楚資料，把資料定義好。
* 檢查虛擬碼
	* 想想你如何向別人解釋虛擬碼
	* 確認透過虛擬碼可以很容易地知道這隻子程式在做甚麼
* 在虛擬碼中試驗想法，並且留下最好的結果(迭代)
	* 反覆的修改虛擬碼描述的子程式，找到幾乎能直接從虛擬碼轉換成程式碼的版本，如果層次太高就分解他，持續精煉，直到你覺得不寫程式碼是在浪費時間為止。
### 編寫子程式的程式碼
* 寫宣告(子程式的描述)
* 將頭尾兩句描述轉成虛擬碼，再將虛擬碼轉換為註解
* 為每條註解寫程式
* 檢查程式是否需要分解
	* 如果程式太大，則重構成另外一個子程式，並且也使用ppp設計
	* 如果沒有要拆，可以再為那些比較大型的虛擬碼底下的程式碼寫虛擬碼，寫完再轉換為程式碼
* 檢查程式碼
	* 如果不知道為什麼需要這段程式碼的話就想辦法去理解，做實驗或是跟別人討論等等
	* 確實理解每行程式碼的功能，只因為看起來可行就使用，遲早會發生問題
	* 編譯子程式:
		* 書中提到，不要常常編譯你的子程式，等到適當的時間才編譯能夠避免東拼西湊->編譯->修改這種程式寫法
		* 編譯時消除所有錯誤及警告
	* 在除錯器中逐行執行程式碼
		* 確保每一行都被執行且結果如預期
* 測試程式碼
	* 可以使用用測試資料來呼叫子程式的一套測試控管子程式或是一些提供你的子程式呼叫的木樁
* 消除程式中的錯誤
	* 如果程式中漏洞百出，就重寫吧，重寫出一個找不出漏洞的程式會比修補來得好
* 收尾
	* 檢查子程式的介面
		* 檢查所以輸入輸出都被使用
	* 檢查品質
		* 一個子程式只做一件事
		* 子程式間低耦合
		* 具有防禦性程式設計
	* 檢查變數
		* 是否有合適的變數名稱、沒使用到的物件
		* 檢查邏輯，是否有off-by-one的問題、
	* 檢查布局
		* 有用正確的空白字釐清子程式、運算式及參數清單的邏輯結構
	* 檢查子程式的文件
		* 確保子程式與轉換為註解的虛擬碼仍然匹配
		* 檢查演算法的描述、並非顯而易見的依賴性、難以理解的程式碼行為的解釋
	* 刪除不需要的註解
## PPP的替代方案
* TDD
* 重構
* design by contract
	* 程式具有前置條件、後置條件
	* 用斷言來驗證上述兩者
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU1MDU2MDgxNCwtODUwMDcwNjE4LDEzMT
cxODQ3NjIsLTE3NjY0Mjc4NjgsLTY3MzYxNTc3NywtMTk4NjQy
MDg4Myw2Mjg5MzYyNzEsLTE2MjI3NTQ4NjYsODgxNzIyNjQwLC
0xMTE5OTA4MTksNjAzMDQ3NDU1XX0=
-->