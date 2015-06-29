---
title       : Exploratory Data Analysis
subtitle    : 智庫驅動
author      : Ben Chen
job         : 
framework   : io2012-dsp
highlighter : highlight.js
hitheme     : zenburn
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
--- &twocol .largecontent





## 關於講師

*** =left

### Ben Chen

- 生物資訊
- 生技公司研發工程師
- Taiwan R User Group Officer
- DSP講師



*** =right

<img src='assets/img/ben.JPG' style='max-width: 75%;max-height: 75%'></img>

--- &vcenter .largecontent

<center><img src='assets/img/Data_visualization_process_v1.png' style='max-width: 75%;max-height: 75%'></img></center>

出處：<http://en.wikipedia.org/wiki/File:Data_visualization_process_v1.png>

--- &vcenter .largecontent

## 大綱

- EDA 的目的
- 如何掌握資料的脈絡
- 觀察數據的方法

--- .dark .segue

## EDA的目的

--- &vcenter .largecontent

## Tukey, John W. (1977). Exploratory Data Analysis. Pearson. ISBN 978-0201076165. 

- 檢查資料的正確性
- 尋找現象中可能的因果關係
- 確認進階分析中的假設是否合理
- 選擇正確的分析工具和技術
- 建議未來的數據收集方向

--- &twocol .largecontent

## 檢查資料的正確性

*** =left

- 錯誤的資料很常見
    - 輸入錯誤
    - 處理的程式錯誤
    - 對資料的值解釋錯誤
    
*** =right

<img src='assets/img/incorrect_temperature.png' style='max-width: 100%;max-height: 100%'></img>

--- &twocol .largecontent

## 尋找數據中潛在的因果關係

*** =left

- 因果關係不容易發現
- 需要對問題本質的理解，加上數據的佐證

*** =right

![plot of chunk ubike-hour-temp](assets/fig/ubike-hour-temp-1.png) 

--- &twocol .largecontent

## 確認進階分析中的假設是否合理

*** =left

- 可以用常態分佈來描述這個數據嗎？

*** =right

![plot of chunk ubike-hour-temp-density](assets/fig/ubike-hour-temp-density-1.png) 

--- &twocol .largecontent

## 選擇正確的分析工具和技術

*** =left

- 是線性關係，還是非線性關係呢？

*** =right

![plot of chunk cars1](assets/fig/cars1-1.png) 

--- &vcenter .largecontent

## 建議未來的數據收集方向和分析方向

![plot of chunk future](assets/fig/future-1.png) 

--- .dark .segue

## 如何掌握資料的脈絡

--- &vcenter .largecontent

## 如何掌握資料的脈絡

- 了解資料的物理意義
    - 收集的目的
    - 收集的方法
- 了解資料的欄位與對應的類型
- 檢查和整理資料

--- &vcenter .largecontent

## 了解資料的物理意義

<img src='assets/img/20150130_MarchMad_627x349.jpg' style='max-width: 100%;max-height: 100%'></img>

出處：<https://www.kaggle.com/c/march-machine-learning-mania-2015>

--- &vcenter .largecontent

## 了解資料的物理意義

<img src='assets/img/Automated-Data-Collection.jpg' style='max-width: 100%;max-height: 100%'></img>

出處：<http://www.memex.ca/solution/automated-data-collection/>

--- &vcenter .largecontent

## 了解資料的欄位與對應的類型

### Kaggle
<br/>
<img src='assets/img/kaggle-march-machine-learning-mania-2015.png' style='max-width: 95%;max-height: 95%'></img>

--- &vcenter .largecontent

## 了解資料的欄位與對應的類型

### Ubike

<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Mon Jun 22 08:11:05 2015 -->
<table border=1>
<tr> <th> date </th> <th> hour </th> <th> sarea </th> <th> sna </th> <th> lat </th> <th> lng </th>  </tr>
  <tr> <td> 2014-12-08 </td> <td align="right">  15 </td> <td> 信義區 </td> <td> 捷運市政府站(3號出口) </td> <td align="right"> 25.04 </td> <td align="right"> 121.57 </td> </tr>
  <tr> <td> 2014-12-08 </td> <td align="right">  15 </td> <td> 大安區 </td> <td> 捷運國父紀念館站(2號出口) </td> <td align="right"> 25.04 </td> <td align="right"> 121.56 </td> </tr>
  <tr> <td> 2014-12-08 </td> <td align="right">  15 </td> <td> 信義區 </td> <td> 台北市政府 </td> <td align="right"> 25.04 </td> <td align="right"> 121.57 </td> </tr>
  <tr> <td> 2014-12-08 </td> <td align="right">  15 </td> <td> 信義區 </td> <td> 市民廣場 </td> <td align="right"> 25.04 </td> <td align="right"> 121.56 </td> </tr>
  <tr> <td> 2014-12-08 </td> <td align="right">  15 </td> <td> 信義區 </td> <td> 興雅國中 </td> <td align="right"> 25.04 </td> <td align="right"> 121.57 </td> </tr>
  <tr> <td> 2014-12-08 </td> <td align="right">  15 </td> <td> 信義區 </td> <td> 世貿二館 </td> <td align="right"> 25.03 </td> <td align="right"> 121.57 </td> </tr>
   </table>

--- &vcenter .largecontent

## 了解資料的欄位與對應的類型

- 數值型變數
- 類別型變數
- 標籤型變數

--- &vcenter .largecontent

## 了解資料的欄位與對應的類型 - 數值型變數

- 一定是以數字表示
- 可以做加法和減法的運算
- 一定擁有相對的大小關係
- 範例
    - 氣溫
    - 時間
    - 價格
    - 數量

--- &vcenter .largecontent

## 了解資料的欄位與對應的類型 - 類別型變數

- 可能是以數字表示
- 不能做加法和減法的運算
- 不一定擁有相對的大小關係
- 範例
    - 日期、月份
    - 性別
    - 數值區間，如年齡區間


--- &twocol .largecontent

## 了解資料的欄位與對應的類型 - 標籤型變數

*** =left

- 通常是類別型或數值型變數的壓縮
- 已經被定義在某些資料庫系統之中
- 轉換為對應的類別型變數與數值型變數
- 範例
    - 文章分類標籤
    - 臉書標籤

*** =right

<img src='assets/img/facebookhashtag.png' style='max-width: 100%;max-height: 100%'></img>
出處: <http://www.techbang.com/posts/13673-import-facebook-official-hashtag-label-features-marked-with-a-keywords>

--- &twocol .largecontent

## 數值型變數可以轉換為類別型變數

- [Data Binning](http://en.wikipedia.org/wiki/Data_binning)

*** =left

![plot of chunk iris-num](assets/fig/iris-num-1.png) 

*** =right

![plot of chunk iris-cat](assets/fig/iris-cat-1.png) 

--- &vcenter .largecontent

## 檢查和整理資料

- 檢查資料是否正確
- 檢查資料內容和物理意義的一致性


--- .segue .dark

## 觀察數據的方法

--- &vcenter .largecontent

## 觀察單一欄位的資料

- 數值型變數
- 類別型變數

--- &vcenter .largecontent

## 類別型變數 - 各類別的值與分佈

<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Mon Jun 22 08:11:06 2015 -->
<table border=1>
  <tr> <td> 三重區 </td> <td align="right"> 16 </td> <td> 內湖區 </td> <td align="right"> 15 </td> <td> 大安區 </td> <td align="right"> 30 </td> <td> 板橋區 </td> <td align="right"> 4 </td> </tr>
  <tr> <td> 中和區 </td> <td align="right"> 4 </td> <td> 北投區 </td> <td align="right"> 12 </td> <td> 文山區 </td> <td align="right"> 12 </td> <td> 永和區 </td> <td align="right"> 10 </td> </tr>
  <tr> <td> 中山區 </td> <td align="right"> 20 </td> <td> 南港區 </td> <td align="right"> 13 </td> <td> 新店區 </td> <td align="right"> 15 </td> <td> 汐止區 </td> <td align="right"> 18 </td> </tr>
  <tr> <td> 中正區 </td> <td align="right"> 20 </td> <td> 士林區 </td> <td align="right"> 14 </td> <td> 新莊區 </td> <td align="right"> 13 </td> <td> 萬華區 </td> <td align="right"> 12 </td> </tr>
  <tr> <td> 信義區 </td> <td align="right"> 23 </td> <td> 大同區 </td> <td align="right"> 11 </td> <td> 松山區 </td> <td align="right"> 15 </td> <td> 蘆洲區 </td> <td align="right"> 7 </td> </tr>
   </table>

--- &vcenter .largecontent

## 類別型變數 - 各類別的值與分佈

<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Mon Jun 22 08:11:06 2015 -->
<table border=1>
  <tr> <td> 三重區 </td> <td align="right"> 16 </td> <td> 內湖區 </td> <td align="right"> 15 </td> <td> 大安區 </td> <td align="right"> 30 </td> <td> 板橋區 </td> <td align="right"> 4 </td> <td> 苓雅區 </td> <td align="right"> 1 </td> </tr>
  <tr> <td> 中和區 </td> <td align="right"> 4 </td> <td> 北投區 </td> <td align="right"> 12 </td> <td> 文山區 </td> <td align="right"> 12 </td> <td> 永和區 </td> <td align="right"> 10 </td> <td>  </td> <td align="right">  </td> </tr>
  <tr> <td> 中山區 </td> <td align="right"> 20 </td> <td> 南港區 </td> <td align="right"> 13 </td> <td> 新店區 </td> <td align="right"> 15 </td> <td> 汐止區 </td> <td align="right"> 18 </td> <td>  </td> <td align="right">  </td> </tr>
  <tr> <td> 中正區 </td> <td align="right"> 20 </td> <td> 士林區 </td> <td align="right"> 14 </td> <td> 新莊區 </td> <td align="right"> 13 </td> <td> 萬華區 </td> <td align="right"> 12 </td> <td>  </td> <td align="right">  </td> </tr>
  <tr> <td> 信義區 </td> <td align="right"> 23 </td> <td> 大同區 </td> <td align="right"> 11 </td> <td> 松山區 </td> <td align="right"> 15 </td> <td> 蘆洲區 </td> <td align="right"> 7 </td> <td>  </td> <td align="right">  </td> </tr>
   </table>

--- &vcenter .largecontent

## 類別型變數 - 各類別的值與分佈

![plot of chunk level-ubike-pie](assets/fig/level-ubike-pie-1.png) 

--- &vcenter .largecontent

## 單一欄位的資料 - 數值型變數

- 數值分佈
- 中心位置
- 分散程度

--- &twocol .largecontent

## 單一欄位的資料 - 數值分佈

- 單峰或雙峰
- 左偏或右偏

*** =left

![plot of chunk binomode](assets/fig/binomode-1.png) 

*** =right

![plot of chunk skewness](assets/fig/skewness-1.png) 

--- &twocol .largecontent

## 單一欄位的資料 - 中心位置

*** =left

- 平均數
- 中位數
- 眾數

*** =right

![plot of chunk center](assets/fig/center-1.png) 

--- &vcenter .largecontent

## [101年中華民國家庭收支統計](http://win.dgbas.gov.tw/fies/doc/result/101.pdf)

- 每戶可支配所得
    - 平均為92.4萬元
    - 中位數為80.8萬元

--- &vcenter .largecontent

## [美國新進律師薪水分佈](http://www.nalp.org/uploads/0812Research.pdf)

<img src='assets/img/lawyer_salary.png' style='width: 150%'></img>

--- &twocol .largecontent

## 信義區與大安區住宅價格比較

*** =left

<br/>
<br/>
<br/>
<br/>

<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Mon Jun 22 08:11:09 2015 -->
<table border=1>
<tr> <th>  </th> <th> 房價 </th> <th> 信義區 </th> <th> 大安區 </th>  </tr>
  <tr> <td align="right"> 1 </td> <td> 25% </td> <td align="right"> 12.50 </td> <td align="right"> 14.80 </td> </tr>
  <tr> <td align="right"> 2 </td> <td> 50% </td> <td align="right"> 18.00 </td> <td align="right"> 23.40 </td> </tr>
  <tr> <td align="right"> 3 </td> <td> 平均 </td> <td align="right"> 25.20 </td> <td align="right"> 31.50 </td> </tr>
  <tr> <td align="right"> 4 </td> <td> 75% </td> <td align="right"> 25.60 </td> <td align="right"> 37.40 </td> </tr>
   </table>

*** =right

<br/>
<br/>
<img src='assets/img/house_distribution.png' style='max-width: 100%;max-height: 100%'></img>

--- &twocol .largecontent

## 單一欄位的資料 - 分散程度

*** =left

- 標準差：$\sigma$
- 離差
- 四分位差
- 變異係數：$\sigma/\bar{x}$

*** =right

![plot of chunk center2](assets/fig/center2-1.png) 

--- &vcenter .largecontent

## 觀察兩個欄位的資料 - 相關性

- 有因果關係一定有相關性
- 相關性不一定代表有因果關係

--- &vcenter .largecontent

## 車速和煞車的關係

![plot of chunk cars2](assets/fig/cars2-1.png) 

--- &vcenter .largecontent

## [吸煙和肺癌的關係](http://www.tomotherapy.org.tw/15mc_1950.htm)

- 在1939年，德國的研究指出，和健康人比起來，肺癌患者中吸菸者較多。
- 1950年早期，在美國由Ernst Wynder 及 Evarts Graham所做，包含了600位肺癌患者及600位對照組的研究。
- Doll和Hill發出了超過34,000份問卷，針對英國男性醫生收集吸煙習慣的細節，且進一步隨問卷調查，並記錄死亡原因。在1954年第一篇研究報告發表在英國醫學雜誌，而後續的訪查報告於1956年發表。
- 1964年美國衛生局長所提出的報告，結論是「在男性吸煙與肺癌間具有因果關係；而且吸煙影響的幅度遠遠超過其他所有因素。」

--- &vcenter .largecontent

## [相關性還是因果關係？](http://www.bloomberg.com/bw/magazine/correlation-or-causation-12012011-gfx.html)

<img src='assets/img/cc1.png' style='width:150%;'/>

--- &vcenter .largecontent

## [相關性還是因果關係？](http://www.bloomberg.com/bw/magazine/correlation-or-causation-12012011-gfx.html)

<img src='assets/img/cc6.png' style='width:150%;'/>

--- &vcenter .largecontent

## 預測和相關性

- 只有單一數據時，基本的預測方式：
    - 類別型變數：猜出現最多次的類別（眾數）
    - 數值型變數：猜中心點
- 只用一月份的平均氣溫猜測二月份的氣溫，平均誤差的平方為：12.020453
- 考慮每小時氣溫的變化之後，平均誤差的平方變成：10.123030

--- &vcenter .largecontent

## 觀察兩個欄位的資料 - 類別 vs 類別

### 列聯表

<br/>

<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Tue Jun 23 06:12:42 2015 -->
<table border=1>
<tr> <th> Survived </th> <th> Count </th>  </tr>
  <tr> <td> No </td> <td align="right"> 1490 </td> </tr>
  <tr> <td> Yes </td> <td align="right"> 711 </td> </tr>
   </table>
<br/>
### 交叉比對
<br/>
<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Thu Jun 25 23:02:03 2015 -->
<table border=1>
<tr> <th> Survived </th> <th> Male </th> <th> Female </th>  </tr>
  <tr> <td> No </td> <td align="right"> 1364 </td> <td align="right"> 126 </td> </tr>
  <tr> <td> Yes </td> <td align="right"> 367 </td> <td align="right"> 344 </td> </tr>
   </table>

--- &vcenter .largecontent

## 觀察兩個欄位的資料 - 類別 vs 類別

### 科系與性別交叉比對
<br>
<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Thu Jun 25 23:02:04 2015 -->
<table border=1>
<tr> <th> Dep. </th> <th> 女 </th> <th> 男 </th>  </tr>
  <tr> <td> 理 </td> <td align="right"> 4 </td> <td align="right"> 6 </td> </tr>
  <tr> <td> 管 </td> <td align="right"> 6 </td> <td align="right"> 7 </td> </tr>
  <tr> <td> 資工 </td> <td align="right"> 1 </td> <td align="right"> 8 </td> </tr>
  <tr> <td> 資管 </td> <td align="right"> 3 </td> <td align="right"> 7 </td> </tr>
   </table>

--- &twocol .largecontent

## 觀察兩個欄位的資料 - 類別 vs 數值

<center>
![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png) 
</center>

--- &twocol .largecontent

## 觀察兩個欄位的資料 - 類別 vs 數值

<center>
![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png) 
</center>


--- &twocol .largecontent

## 觀察兩個欄位的資料 - 類別 vs 數值

<center>
![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-1.png) 
</center>

--- &twocol .largecontent

## 觀察兩個欄位的資料 - 類別 vs 數值

*** =left

<br/>
<br/>
<br/>
<br/>

<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Mon Jun 22 08:11:19 2015 -->
<table border=1>
<tr> <th>  </th> <th> 房價 </th> <th> 信義區 </th> <th> 大安區 </th>  </tr>
  <tr> <td align="right"> 1 </td> <td> 25% </td> <td align="right"> 12.50 </td> <td align="right"> 14.80 </td> </tr>
  <tr> <td align="right"> 2 </td> <td> 50% </td> <td align="right"> 18.00 </td> <td align="right"> 23.40 </td> </tr>
  <tr> <td align="right"> 3 </td> <td> 平均 </td> <td align="right"> 25.20 </td> <td align="right"> 31.50 </td> </tr>
  <tr> <td align="right"> 4 </td> <td> 75% </td> <td align="right"> 25.60 </td> <td align="right"> 37.40 </td> </tr>
   </table>

*** =right

<br/>
<br/>
<img src='assets/img/house_distribution.png' style='max-width: 100%;max-height: 100%'></img>

--- &vcenter .largecontent

## 觀察兩個欄位的資料 - 類別(?) vs 數值

### BoxPlot

![plot of chunk ubike-temp-hour](assets/fig/ubike-temp-hour-1.png) 

--- &twocol .largecontent

## 觀察兩個欄位的資料 - 數值 vs 數值

### 相關係數

*** =left

![plot of chunk cor1](assets/fig/cor1-1.png) 

相關係數：-0.069416

*** =right

![plot of chunk cor2](assets/fig/cor2-1.png) 

相關係數：0.9370255

--- &twocol .largecontent

## 觀察兩個欄位的資料 - 數值 vs 數值

### X-Y散佈圖

*** =left

![plot of chunk xy](assets/fig/xy-1.png) 

*** =right

<br/>
<img src='assets/img/cc1.png' style='max-width: 100%;max-height: 100%'></img>

--- &twocol .largecontent

## 總結

### 單一數據

*** =left

- 類別型數據
    - 類別分佈
        - 表格
        - barplot

*** =right

- 數值型數據
    - 數值分佈
        - density
        - Boxplot
    - 中心位置
    - 分散程度

--- &twocol .largecontent

## 總結

### 雙數據 - 檢視相關性 

*** =left

- 類別 vs 類別
    - 列聯表
- 類別 vs 數值
    - 條件分佈
    - 條件Boxplot

*** =right

- 數值 vs 數值
    - 相關係數
    - X-Y 散部圖
    - 時間變化圖



--- .dark .segue

## 觀察數據的工具：R

--- &vcenter

## R 來自世界上最專業的統計學家

<center><img src='assets/img/statician_10521919-655x280.jpg' style='max-width: 100%;max-height: 100%'></img></center>

圖片來源： <http://myfootpath.com/careers/engineering-careers/statistician-careers/>

---

## R 可以輸出高品質的視覺化

<img src='assets/img/flights_sml.jpg' style='max-width: 100%;max-height: 100%'></img>

取自<http://www.r-bloggers.com/mapping-the-worlds-biggest-airlines/>

--- &vcenter

## R 有驚人彈性和潛力

<center><img src='assets/img/fig_10_cran1.png' style='max-width: 75%;max-height: 75%'></img></center>

取自 <http://r4stats.com/2013/03/19/r-2012-growth-exceeds-sas-all-time-total/>

--- &vcenter

## R 很容易和其他工具整合

<center>
![plot of chunk r-integration](assets/fig/r-integration-1.png) 
</center>

--- &vcenter

## R 很容易擴充和客製化

<center><img src='assets/img/t134_3ca_lg.jpg' style='max-width: 100%;max-height: 100%'></img></center>
來源：<http://img.diynetwork.com/DIY/2003/09/18/t134_3ca_med.jpg>

--- &vcenter .largecontent

## 今天的目標

### 環境設定

- 建立可以使用R 的環境
- 了解R 的使用界面

--- &vcenter .largecontent

## 安裝 R 與 Rstudio

### 請參考現場示範


--- .dark .segue

## Team Project
