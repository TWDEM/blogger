newsflash template 修改事宜
作一下記錄，免得自己也忘掉 XD

## 一、Template  blogger 主題改造

1. key word search "free blogger template", "free blogger theme", "responsive theme"

2. 挑選中意的模版，下載安裝測試看看

3. 安裝之前，記得先把原本使用的模版備份
![back_up](https://i.imgur.com/Rmt8Ewi.png)

![download](https://i.imgur.com/O0nOeLf.png)

4. 至於在網路上找到所喜歡的新主題（通常為壓縮檔，解壓之後，其中應有一個副檔名為 .xml　的模版主題檔）下載後，也是同樣利用在 blogger 後台主題區「備份/還原」這個地方，把新的 xml 檔案上傳「還原」（參考上圖二：彈出的視窗「choose file」來進行上傳動作）。成功上傳新主題後，可以看看網誌的模樣是否如心中所想的模樣改變了。通常這之後就進入了微調或是大修的工作階段。微調部份是直接透過 blogger 後台的「版面配置」區進行直覺化的網誌區塊修改、移動或刪除。如果這邊作了更變仍無法改變網誌呈現出來的模樣，就必須直接進行主題 xml 檔案的（大）修改。

![](https://i.imgur.com/d1Yk7Ok.png)

5. "編輯 html"進入 xml 檔案線上編輯器 

![back_up](https://i.imgur.com/Rmt8Ewi.png)

![](https://i.imgur.com/undefined.png) 

template　主題會有點雜亂，因為這支 xml 檔案雜夾了 CSS, javascript, html (有時候網路上一支主題模版，會同時另有免費與付費版。後者除了功能強化外，主要差別可能在原作者會把免費版中的重要 js 程式碼加密，讓人無法任意“偷取”“複製”或“刪除”)

因擔心加密的程式碼中雜有不安全或奇怪的東西，所以還是花了10美元買了付費版的主題（這個價位還蠻佛心的）。這回大約修改的地方是：

- 1). xml 文件中原本出現 http:// 檢查是否能代換成 https://
有些網誌上的文章連結是否需改修改（http 改成 https），例如發現設定 CF nameserver + https everywhere 之後，首頁原本會出現的文章前200字卻消失，只剩下空白旳「閱讀全文」，查看這段程式碼猜想可能是 data-url='data:post.url' 未https 的問題(幸運猜對了)  

其它部份大至沒問題，主要麻煩還是過去舊文內容本身帶有不安全的連結或圖片檔 http:// 造成無法通過瀏覽器的安全查驗。  

 2). 有一些放在xml 的圖片是否要換掉，例如無圖之圖片檔

![](http://3.bp.blogspot.com/-Yw8BIuvwoSQ/VsjkCIMoltI/AAAAAAAAC4c/s55PW6xEKn0/s1600-r/nth.png) 
![](https://i.imgur.com/gkfv4Mx.png)

　3). 檢查主題原始代碼中是否帶有不安全的不明連結
 [privacy badger](https://www.eff.org/privacybadger) 檢查（盡量把　template 當中不明不必要的網站連結與追蹤器拿掉，但可惡的 google , facebook 無所不在

![](https://i.imgur.com/WO7s5EP.png)

![](https://i.imgur.com/wbJYNWu.png)

以上大約是修改 xml 過程一些要注意的地方，其實並不困難，因為最難的地方別人（模版主題原設計者）已經代為做好了。

6. SEO 優化:可直接在後台「設定」=> 「搜尋偏好設定」輸入關鍵字或民主平台重要資訊，以提高 organic search 訪客

![SEO](https://i.imgur.com/LVMLpDX.png)

7. 行動服務（手機版）調整
因為現已採用響應式設計模版（Responsive design），其可支援各種尺寸的螢幕大小，故在 blogger 後台的「主題」行動服務部份，可直接選用
－「在行動裝置上顯示電腦版主題」此選項，而不必採用 blogger 另外提供的行動版主題。

![](https://i.imgur.com/cMdQp6i.png)

與原本的網站相比，不管任何螢幕尺寸大小，新主題皆可自動伸縮調整版型圖片，提供讀者最適閱讀環境
![](https://i.imgur.com/17hcGFr.png)
![](https://i.imgur.com/8uZpUpI.png)
![](https://i.imgur.com/KxlfnhK.png)

8. 測試站改造完成，返回原始站台更新這支 xml 主題
前面的部份記錄了如何以 [newsflash](http://www.templatesyard.com/2017/08/newsflash-responsive-blogger-template.html) 主題為基礎，在測試站台上進行修改調整的大致過程。改過的檔案已存放在[本資源庫](https://github.com/TWDEM/blogger)，請下載壓縮檔後解壓，並依照前述 3),4) 部份，將**theme-twdem-final.xml** 這支檔案上傳到原網誌主題區即可。

## 二、Cloudflare 設定（for free SSL）

因 google blogger 對使用自定網域名並未支援 https 安全連線，故需多做此道手續，一方面配合瀏覧器加強安全連線的政策，一方面保護訪客用戶安全。請直接參考本篇：[BLOGGER 自訂網址套用 CLOUDFLARE FLEXIBLE SSL 設定全流程](https://www.techcoke.com/2017/01/blogger-cloudflare-flexible-ssl-https-step.html)

因已在「步驟一」完成主題模版檔案 xml 內容中的相關文章網址調整，故原資料中的文章舊檔連結已改成 https ，但有部份老舊文章中的圖片或對外連結仍然透過 http:// 的不安全方式取得，這我也沒辦法囉╮(－_－)╭ 

![](https://i.imgur.com/Pq0WZ3e.png)

[註] 若因採用 cloudflare，則會把域名 DNS 從 godaddy 轉由 cloudflare　代管，故未來若有需要修改 dns record, 則要在 cloudflare 處做變動。　
