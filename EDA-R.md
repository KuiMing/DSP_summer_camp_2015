---
title       : EDA with R
subtitle    : 智庫驅動
author      : Ben Chen
job         : 
framework   : io2012-dsp
highlighter : highlight.js
hitheme     : zenburn
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
--- &vcenter .largecontent





## EDA的複習

- 了解如何看數據
    - 類別型數據
    - 數值型數據
    - 單一數據
    - 兩欄數據

--- &vcenter .largecontent

## 今天的目標

### 學習R 語言

- 透過實際的範例學習R 語言
    - 讀取資料
    - 選取資料
    - 敘述統計量
    - 視覺化

--- .segue .dark

## 工欲善其事，必先利其器

--- &vcenter .largecontent

## Rstudio 界面

- 程式碼編輯區
- 命令列區
- 其他資訊區
- 檔案系統區

--- &vcenter .largecontent

## 熟悉R 和Rstudio的界面

- 了解輸入
- 了解輸出
- 中斷程式

--- &vcenter .largecontent

## 熟悉R 和Rstudio的界面 - 請你跟我這樣做

### 命令列區

- 注意最左下腳的符號是`>`
- 輸入`"hello world"`後按下Enter，檢查螢幕輸出（記得加上引號）
- 輸入`1 + 1`後按下Enter，檢查螢幕輸出，注意有無引號
- 輸入`1 + `後按下Enter，檢查螢幕輸出，注意最左下角的開頭變成`+`
- 按下Ctrl + C或ESC，檢查哪一個按鈕會讓左下角回復成`>`開頭

--- &vcenter .largecontent

## 熟悉R 和Rstudio的界面 - 請你跟我這樣做

### 命令列區

- 在新的一行命令列區輸入`he`之後按下Enter
- 在新的一行命令列區輸入`he`之後按下tab

--- &vcenter .largecontent

## 熟悉R 和Rstudio的界面 - 請你跟我這樣做

### 程式碼編輯區

- 建立新的R Script檔案
- 在第一行輸入`he`隻後按下Ctrl + Enter後，觀察命令列區
- 利用滑鼠點選`he`後的位置，確認游標閃爍的位置在`he`之後，按下tab

--- .segue .dark

## R 的擴充功能

--- 

## [CRAN Task Views](http://cran.r-project.org/web/views/)

<img src='assets/img/CRAN-Task-Views.png' style='max-width: 100%;max-height: 100%'></img>

--- &vcenter .largecontent

## 套件的安裝

### UI

- 請見Demo

### 命令列


```r
install.views("topic-name") # 需要套件ctv
install.packages("pkg-name", repos = "來源")
```

--- &vcenter .largecontent

## 小挑戰

### 套件安裝

- 利用UI安裝`magrittr`
- 透過USB 安裝課程所需套件
    - `data.table`,`dplyr`, `ggplot2`

```r
# windows
utils:::menuInstallLocal()
# mac 
{
  pkgpath <- file.choose()
  pkgdir <- paste(head(strsplit(pkgpath, "/")[[1]], -1), collapse="/")
  invisible(lapply(dir(pkgdir, "*.tgz", full.names = TRUE), 
    install.packages, repos=NULL))
}
```

--- .dark .segue

## 讓我們來說R 語

--- &twocol .largecontent

## 敘述句(expression)

*** =left


```r
"1;2;3;"
```

```
## [1] "1;2;3;"
```

```r
1;2;3;
```

```
## [1] 1
```

```
## [1] 2
```

```
## [1] 3
```

*** =right

- 敘述句以`;`或`斷行`(輸入Enter)作結尾
- R 會把單引號`'`或雙引號`"`所包覆的敘述當成字串
- 沒有完成的敘述句，命令列的開頭會變成`+`
- 可以用Ctrl + C 中斷敘述句

--- .largecontent

## 註解

- `#`之後的程式碼會被當成註解
    - R 會完全忽略註解
    - 註解的功用是增加程式碼的可讀性


```r
1;2;#3
```

```
## [1] 1
```

```
## [1] 2
```

--- &twocol .largecontent

## 敘述句與數值運算

*** =left


```r
1 + 1
```

```
## [1] 2
```

```r
1 + 2 - 1
```

```
## [1] 2
```

```r
(1 + 1) * 2
```

```
## [1] 4
```

```r
2.5e3
```

```
## [1] 2500
```

*** =right

- 敘述句可以運算出一個R 物件
- 運算的順序符合先乘除後加減，括號最優先
- 中間有`e`的數值代表要再乘以10的冪次方

--- &twocol .largecontent

## 變數與賦值 `<-`或`=`

*** =left


```r
One
```

```
## Error in eval(expr, envir, enclos): 找不到物件 'One'
```

```r
One <- 1
One
```

```
## [1] 1
```

```r
Two = "2"
Two
```

```
## [1] "2"
```

*** =right

### 賦值

<center>
<img src='assets/img/assign-missing.png' style='max-width: 50%;max-height: 50%'></img>
</center>

$$\Downarrow$$

<center>
<img src='assets/img/assign-linking.png' style='max-width: 50%;max-height: 50%'></img>
</center>

--- &twocol .largecontent

## 向量

*** =left


```r
1:3
```

```
## [1] 1 2 3
```

```r
c(1, 2, 3) + 1
```

```
## [1] 2 3 4
```

```r
1:3 * 2
```

```
## [1] 2 4 6
```

*** =right

- 利用`c`和建立向量
- 利用`:`建立序列
- 運算是向量式的

<center><img src='assets/img/vectorize-plus-before.png' style='max-width: 50%;max-height: 50%'></img></center>
$$\Downarrow$$
<center><img src='assets/img/vectorize-plus-after.png' style='max-width: 50%;max-height: 50%'></img></center>

--- &vcenter .largecontent

## 呼叫函數

### 請在Rstudio的命令列區進行以下操作

- 輸入`c`，按下tab
    - 自動完成：列出所有`c`開頭的函數
    - 列出函數的說明文件
- 清空命令列，輸入`?c`後按下Enter
- 清空命令列，輸入`c`後按下Enter

--- &vcenter .largecontent

## 函數與參數

- 函數的參數可以改變函數的行為
- R 的函數是依照以下方式來解釋參數：
    - 名稱的partial matching
    - 順序
    - `...`
    - `...`之後的參數
- 專家區
    - R 的參數都是使用Pass By Value
    - 參數的複製是採用Copy on Write

--- .largecontent

## 小挑戰

### 請利用`+`、`-`、`*`或`/`來回答：


```r
# ubike在捷運市政府站(3號出口)站點於2015-03-01的每小時降雨量
rainfall1 <- c(0.157,0.432,0.702,0.947,1.129,1.224,1.241,
  1.218,1.201,1.207,1.225,1.233,1.227,1.218,1.22,1.233,
  1.244,1.246,1.242,1.242,1.249,1.257,1.258,1.252) 
# ubike在大鵬華城站點 於2015-03-01的每小時降雨量
rainfall2 <- c(0.041,0.315,0.586,0.83,1.013,1.108,1.124,
  1.102,1.085,1.091,1.108,1.116,1.11,1.102,1.104,1.116,
  1.127,1.129,1.126,1.125,1.132,1.14,1.141,1.136)
```

- `rainfall1`每小時的降雨量和`rainfall2`的差距

*** =pnotes


```r
rainfall1 - rainfall2
```

```
##  [1] 0.116 0.117 0.116 0.117 0.116 0.116
##  [7] 0.117 0.116 0.116 0.116 0.117 0.117
## [13] 0.117 0.116 0.116 0.117 0.117 0.117
## [19] 0.116 0.117 0.117 0.117 0.117 0.116
```

--- .segue .dark

## R 的資料結構

--- &vcenter .largecontent

## 資料的類型

- 數值型變數
- 類別型變數

--- .largecontent

## R 的數值型態：專用於數值型變數

- 數值型態
    - 整數(integer) `1L`
    - 實數(numeric) `1.5`


```r
99L;99.5
```

```
## [1] 99
```

```
## [1] 99.5
```

--- .largecontent

## R 的特殊數值型態

- 時間


```r
Sys.time()
```

```
## [1] "2015-07-02 07:41:16 CST"
```

```r
ISOdatetime(year = 1970, month = 1, day = 1, 
            hour = 0, min = 0, sec = 0)
```

```
## [1] "1970-01-01 CST"
```

--- .largecontent

## R 的類別型態

- 字串(character) `"1"`
- 類別(factor) `factor(1)`


```r
c("011", "012");factor(c("信義區","大安區","信義區"))
```

```
## [1] "011" "012"
```

```
## [1] 信義區 大安區 信義區
## Levels: 信義區 大安區
```

--- .largecontent

## 查詢變數的類別


```r
x <- 1:3
class(x)
```

```
## [1] "integer"
```

```r
x <- factor(c("1", "2", "3"))
class(x)
```

```
## [1] "factor"
```

--- .largecontent

## 資料型態的轉換 - 將數值轉換為類別

### 直接轉換


```r
x <- c(1, 2, 3, 2, 3, 2, 1)
as.character(x) # 字串
```

```
## [1] "1" "2" "3" "2" "3" "2" "1"
```

```r
factor(x) # 類別
```

```
## [1] 1 2 3 2 3 2 1
## Levels: 1 2 3
```

--- .largecontent

## 資料型態的轉換 - 將數值轉換為類別

### 分級


```r
x <- c(75, 81, 82, 76, 91, 92)
cut(x, breaks = c(70, 80, 90, 100))
```

```
## [1] (70,80]  (80,90]  (80,90]  (70,80] 
## [5] (90,100] (90,100]
## Levels: (70,80] (80,90] (90,100]
```

--- .largecontent

## 資料型態的轉換 - 將字串轉換為數值

### 直接轉換


```r
x <- c("1", "2", "3", "2", "a")
as.numeric(x)
```

```
## Warning: 強制變更過程中產生了 NA
```

```
## [1]  1  2  3  2 NA
```

- `NA`代表Not available，代表著**missing value**

--- .largecontent

## 資料型態的轉換 - 資料清理

### 民國80年至82年的國民生產毛額

<pre><code style="text-align: center;">
百萬元
5,023,763
5,614,679
6,205,338
</code></pre>


```r
gdp <- c("5,023,763", "5,614,679", "6,205,338")
as.numeric(gsub(",", "", gdp))
```

```
## [1] 5023763 5614679 6205338
```

--- &vcenter .largecontent

## R 是向量式

- 所有的資料都是向量
- 上述介紹的整數、實數、字串和類別型都是相同型態的向量
- `list`是R 物件的向量
- `data.frame`是長度相同的R 物件的向量

--- &vcenter .largecontent

## `data.frame`是最常使用的物件

- `data.frame`的概念在各種資料處理的領域非常常見
    - 例：資料庫
- （實務經驗）R 使用者會希望能透過前處理把資料轉換為`data.frame`的型式
- R 提供將資料匯入成`data.frame`的功能
- R 提供自`data.frame`開始的各種進階處理功能
    - 資料的整理
    - 圖形的繪製
    - 模型的配適與預測

--- &vcenter .largecontent

## 小挑戰

- 請問根據以下的輸出，這份ubike的各欄類別為何？

<!-- html table generated in R 3.2.1 by xtable 1.7-4 package -->
<!-- Wed Jun 24 03:13:51 2015 -->
<table border=1>
  <tr> <td> date </td> <td> factor </td> <td> tot </td> <td> integer </td> <td> min.bemp </td> <td> integer </td> </tr>
  <tr> <td> hour </td> <td> integer </td> <td> avg.sbi </td> <td> numeric </td> <td> std.bemp </td> <td> numeric </td> </tr>
  <tr> <td> sno </td> <td> integer </td> <td> max.sbi </td> <td> integer </td> <td> temp </td> <td> numeric </td> </tr>
  <tr> <td> sarea </td> <td> factor </td> <td> min.sbi </td> <td> integer </td> <td> humidity </td> <td> numeric </td> </tr>
  <tr> <td> sna </td> <td> factor </td> <td> std.sbi </td> <td> numeric </td> <td> pressure </td> <td> numeric </td> </tr>
  <tr> <td> lat </td> <td> numeric </td> <td> avg.bemp </td> <td> numeric </td> <td> max.anemo </td> <td> numeric </td> </tr>
  <tr> <td> lng </td> <td> numeric </td> <td> max.bemp </td> <td> integer </td> <td> rainfall </td> <td> numeric </td> </tr>
   </table>

--- .segue .dark

## 資料的讀取

--- .largecontent

## 讀取表格檔案 - 1. 先檢視資料


```r
# path <- "data/ubikeweatherbig5.csv"
# path <- "data/ubikeweatherutf8.csv"
path <- file.choose()
readLines(path, n = 5)
```

--- .largecontent

## 讀取表格檔案 - 2. 讀取資料

- 先讀取一部分，再讀取全部


```r
# sep是數據間的分隔符號，csv檔通常是用逗號；
# header用來控制資料的第1行是否為欄位名稱
# nrows決定讀取多少列
ubike <- read.table(path, sep = ",", header = TRUE, nrows = 100)
head(ubike)
# colClasses用來控制每一欄的class
ubike <- read.table(path, sep = ",", header = TRUE, 
  colClasses = c("factor", "integer", "integer", "factor", "factor", 
    "numeric", "numeric", "integer", "numeric", "integer", "integer", 
    "numeric", "numeric", "integer", "integer", "numeric", "numeric", 
    "numeric", "numeric", "numeric", "numeric"))
ubike <- fread(path) #神速的作法
```

--- .largecontent

## 常見的讀取錯誤

### 路徑錯誤


```r
path <- "wrong_path"
power <- read.table(file = path, header = TRUE, sep = ",")
```

```
## Warning in file(file, "rt"): 無法開啟檔案
## 'wrong_path' ：沒有此一檔案或目錄
```

```
## Error in file(file, "rt"): 無法開啟連結
```

- 絕對路徑
    - 確認檔案是否存在
- 相對路徑
    - 利用`getwd`了解R 當下的路徑位置

--- .largecontent

## 常見的讀取錯誤

### 格式錯誤


```r
path <- "data/ubike-hour-201412-big5.csv"
power <- read.table(file = path, header = TRUE, sep = "1")
```

```
## Error in read.table(file = path, header = TRUE, sep = "1"): more columns than column names
```

- 利用其他編輯器確認分隔符號
- 確認每列的資料的欄位是正確的
    - 必要時，請用其他文件編輯器校正欲讀取的檔案

--- .largecontent

## 常見的讀取錯誤

### 編碼錯誤


```r
path <- "data/ubike-hour-201412-big5.csv"
power <- read.table(file = path, header = TRUE, sep = ",", nrows = 10)
```

```
錯誤在type.convert(data[[i]], as.is = as.is[i], dec = dec, numerals = numerals,  : 
  無效的多位元組字串於 '<ab>H<b8>q<b0><cf>'
```

- 查詢檔案的編碼
    - 常見的中文編碼有`UTF-8`和`BIG-5`
    - 讀取時套上`file`函數指定編碼
    - 組合`readLines`、`iconv`和`write`來製造符合系統編碼的檔案

*** =pnotes

- 專家區

```r
path <- "data/ubike-hour-201412-big5.csv"
raw <- read.table(file(path, encoding = "BIG-5"), 
                  header = TRUE, sep = ",", 
                  nrows = 10)
raw <- read.csv(path, fileEncoding ='BIG-5')
raw <- readLines(path, n = 10, encoding = "BIG-5")
raw2 <- iconv(raw, from = "BIG-5", to = "UTF-8")
write(raw2, "data/ubikeweatherutf8.csv")
```

--- .largecontent

## ubike是一種`data.frame`


```r
class(ubike)
```

```
## [1] "data.frame"
```

--- &vcenter .largecontent

## 校正欄位名稱


```r
colnames(ubike) <- 
  c("日期", "時間", "場站代號", "場站區域", "場站名稱", 
  "緯度", "經度", "總停車格", "平均車輛數", "最大車輛數", 
  "最小車輛數", "車輛數標準差", "平均空位數", "最大空位數", 
  "最小空位數", "空位數標準差", "平均氣溫", "溼度", 
  "氣壓", "最大風速", "降雨量")
```

--- &vcenter .largecontent

## 合併多個檔案的資料


```r
# 輸入對的路徑讀檔
ub1=fread('data/ubike-hour-201412-utf8.csv')
ub2=fread('data/ubike-hour-201501-utf8.csv')
ub3=fread('data/ubike-hour-201502-utf8.csv')
ub4=fread('data/ubike-hour-201503-utf8.csv')
ub5=fread('data/ubike-hour-201504-utf8.csv')
# 'ubike-hour-201504-big5.csv' 有個欄位名稱跟其他的檔案不同
ubike=rbind(ub1,ub2,ub3,ub4)
colnames(ubike) =  c("日期", "時間", "場站代號", "場站區域", "場站名稱", 
    "緯度", "經度", "總停車格", "平均車輛數", "最大車輛數", 
    "最小車輛數", "車輛數標準差", "平均空位數", "最大空位數", 
    "最小空位數", "空位數標準差", "平均氣溫", "溼度", 
    "氣壓", "最大風速", "降雨量")
```

--- &vcenter .largecontent

## 合併多個檔案的資料


```r
colnames(ub5) <- 
  c("日期", "時間", "場站代號", "場站區域", "場站名稱", 
    "緯度", "經度", "總停車格", "平均車輛數", "最大車輛數", 
    "最小車輛數", "車輛數標準差", "平均空位數", "最大空位數", 
    "最小空位數", "空位數標準差", "平均氣溫", "溼度", 
    "氣壓", "最大風速", "降雨量")
ubike=rbind(ubike,ub5)
```

*** =pnotes

- 進階版

```r
setwd('data') # 設定目前路徑
filenames=dir() # 讀取目前路徑的目錄
# 以關鍵字抓出我們要的檔案
filenames=filenames[grepl('ubike-hour',filenames) &
                      grepl('big5',filenames)]
# 讀取多個檔案，並且合併在一起
ubike=do.call(rbind,lapply(filenames,function(x){
  y=fread(x)
  setnames(y,1:21,
    c("日期","時間","場站代號","場站區域","場站名稱", 
      "緯度","經度","總停車格","平均車輛數","最大車輛數", 
      "最小車輛數","車輛數標準差","平均空位數","最大空位數", 
      "最小空位數","空位數標準差","平均氣溫","溼度", 
      "氣壓","最大風速","降雨量"))
  }))
```

--- &vcenter .largecontent

## 未來的學習清單

### 各式資料庫的連接

- SQL Database: `RMySQL`, `RPostgreSQL`, `ROracle`, `RJDBC`, `RODBC`
- No SQL Database: `rmongodb`, `rredis`
- 讀取XML和網頁資料
    - `XML`套件和XPath
- 讀取json資料
    - `RJSONIO`套件

--- &vcenter .largecontent

## 更擅長整理資料的工具：python

<img src='assets/img/E1_super-01.png' style='max-width: 100%;max-height: 100%'></img>

<https://dsp.im/events/e1-basic-data-engineering-course/>

--- .segue .dark

## 資料的選取

--- .largecontent

## 布林運算

- `>` `<` `>=` `<=` `==` `!=`


```r
1 > 2;1 <= 2
```

```
## [1] FALSE
```

```
## [1] TRUE
```

```r
"A" == "A";"A" != "A"
```

```
## [1] TRUE
```

```
## [1] FALSE
```

--- .largecontent

## 向量的選取

### 坐標


```r
x <- 1:5; x[2:3]
```

```
## [1] 2 3
```

### 布林


```r
x <- 1:5; x > 3; x[x > 3]
```

```
## [1] FALSE FALSE FALSE  TRUE  TRUE
```

```
## [1] 4 5
```

--- &vcenter .largecontent

## 多重條件

- 且：`&`
    - `布林運算結果1 & 布林運算結果1`
- 或：`|`
    - `布林運算結果1 | 布林運算結果1`

--- .largecontent

## 小挑戰


```r
# 社會服務業自民國87至民國91年的年度用電量（度）
power1 <- c(6097059332, 6425887925, 6982579022, 7323992602.53436, 7954239517) 
# 製造業自民國87至民國91年的年度用電量（度）
power2 <- c(59090445718, 61981666330, 67378329131, 66127460204.6482, 69696372914.6949) 
```

- 運用index從`power1`中選取第88年和第90年的年度用電量。結果應該為：
    
    ```
    ## [1] 6425887925 7323992603
    ```
- 運用布林運算自`power2`中選出，製造業超過社會服務業9.5倍的用電年度的用電量。結果應該為：
    
    ```
    ## [1] 59090445718 61981666330 67378329131
    ```

--- .largecontent

## 表格的選取 - 座標


```r
ubike[2, 3]
```

```
## [1] 3
```


```
## [1] 1 2 3
```


--- .largecontent

## 表格的選取 - 欄


```r
head(ubike[["日期"]]) 
```

```
## [1] "2014-12-08" "2014-12-08"
## [3] "2014-12-08" "2014-12-08"
## [5] "2014-12-08" "2014-12-08"
```

```r
# head(ubike$日期)
head(ubike[,1])
```

```
## [1] 1
```

--- &twocol .largecontent

## 範例

*** =left

1. 自`ubike`選取`場站代號`
2. 將結果1.輸入至函數`unique`
3. 利用布林運算，把1.的結果和`1`比較
4. 將結果3.輸入至函數`which`
5. 利用3.和4.的結果選取ubike的列


*** =right


```r
ans1 <- ubike[["場站代號"]]
ans2 <- unique(ans1)
ans3 <- ans1 == 1
ans4 <- which(ans3)
ans5 <- ubike[ans3,]
ans5 <- ubike[ans4,]
```

--- &vcenter .largecontent

## 小挑戰

- 請查詢場站代號1099所在的行政區
- 請查詢場站代號1099的氣溫
    1. 自`ubike`選取`場站代號`
    2. 利用布林運算，把1.的結果和`1099`比較
    3. 自`ubike`選取2.的列之後，用1.的方法選取`平均氣溫`
        3.1 可利用座標的概同時選取出結果

*** =pnotes


```r
x1 <- ubike[["場站代號"]]
x2 <- x1 == 1099
x3 <- ubike[x2,]
x3 <- x3[["平均氣溫"]]
```

--- .largecontent

## 指令的壓縮

- 請大家學習「被壓縮的程式碼」該如何解讀
    - 掌握運算符號的運算順序


```r
ubike[ubike[["場站代號"]] == 1 & ubike[["日期"]] == "2015-03-01",]

x1 <- ubike[["場站代號"]] == 1
x2 <- ubike[["日期"]] == "2015-03-01"
x3 <- x1 & x2
x4 <- ubike[x3,]
```

--- .largecontent

## 2014 年最有影響的套件之一：magrittr

- 壓縮的程式碼不好讀
- 展開的程式碼會產生很多暫存變數
- 套件`magrittr`部份解決了這個問題


```r
ans1 <- ubike[["場站代號"]]
ans1.1 <- unique(ans1)

unique(ubike[["場站代號"]])

library(magrittr)
ubike[["場站代號"]] %>%
  unique
```

--- &vcenter .largecontent

## 2014 年最有影響的套件之一：dplyr

- 讓R 使用者可以用更有彈性的方式來處理資料
- 針對`data.frame`做設計（名稱中的`d`）
- 設計理念
    - 導入資料整理最重要的動作（非常類似SQL）
    - 快
    - 支援異質資料源（`data.frame`或資料庫中的表格）

--- .largecontent

## 學習dplyr的官方方式：`vignette`


```r
vignette(all = TRUE, package = "dplyr")
vignette("introduction", package = "dplyr")
```

- 更詳細的dplyr介紹可以閱讀dplyr的小論文
- R 的開發者會針對一個主題撰寫小論文做介紹

--- &twocol .largecontent

## dplyr簡介

*** =left

- `filter` 對列做篩選
- `select` 對欄做篩選
- `mutate` 更改欄或新增欄
- `arrange` 排列
- **`group_by` + `summarise` 分類

*** =right

<center><img src='assets/img/R_ETL_Fn1.png' style='max-width: 100%;max-height: 100%'></img></center>
出處：[資料科學愛好者年會資料分析上手課程：ETL1](https://www.youtube.com/watch?v=JD1eDxxrur0)

--- .segue .dark

## 資料的探索

--- &vcenter .largecontent

## 探索一個變數

### 量化數據

- 敘述統計量：`mean`、`sd`、`median`

### 質化數據

- 分佈表格：`table`
- 眾數：`table` + `sort`

--- &vcenter .largecontent

## 利用說明文件了解函數內容

### 範例：學習`mean`的用法

- 閱讀說明文件 `?mean`
- 嘗試範例 `example(mean)`
- 自動完成
    - 在命令列輸入`mena(`後按下`tab`

--- &vcenter .largecontent

## 探索一個量化變數

### 挑戰：學習`sd`的用法

- 透過`?sd`嘗試自學標準差的用法
- 選取`場站代號`為1和`日期`為"2015-03-01"的資料
- 計算`捷運市政府站(3號出口)`在`"2015-03-01"`的`降雨量`的標準差

*** =pnotes


```r
x1 <- ubike[["場站代號"]] == 1
x2 <- ubike[["日期"]] == "2015-03-01"
ubike[x1 & x2, "降雨量"]
sd(ubike[x1 & x2, "降雨量"])
```

```
## Warning in var(if (is.vector(x)) x else
## as.double(x), na.rm = na.rm): 強制變更過程中產生了
## NA
```

```r
library(dplyr)
sd(select(
  filter(ubike, 場站代號 == 1, 日期 == "2015-03-01"),
  降雨量)[["降雨量"]])

filter(ubike, 場站代號 == 1, 日期 == "2015-03-01") %>%
  select(降雨量) %>%
  extract2("降雨量") %>%
  sd
```

--- &twocol .largecontent

## 各行政區的站點數：學習`group_by`

*** =left

<img src='assets/img/R_ETL_Fn2.png' style='max-width: 100%;max-height: 100%'></img>

- `length`
- `mean`、`sd`、`median`
- `length(unique)`
- `paste(unique, collapse = ",")`

*** =right

### 每日的平均雨量


```r
group_by(ubike, 日期) %>%
  summarise(平均降雨量 = mean(降雨量))
```

### 各場站區域的站點數


```r
group_by(ubike, 場站區域) %>%
  summarise(站點數 = 
    length(unique(場站代號))) %>%
  arrange(站點數)
```

### 各場站區域的站點數


```r
group_by(ubike, 場站區域) %>%
  summarise(站點代號清單 = 
    paste(unique(場站代號), 
          collapse = ","))
```

--- &vcenter .largecontent 

## 探索一個質化變數

1. 利用`table`列出所有的`場站名稱`出現的次數

*** =pnotes


```r
head(sort(table(ubike[["場站名稱"]])))

table(ubike[["場站名稱"]]) %>%
  sort %>%
  head
```

--- .largecontent

## 探索變數間的關係

- `ftable`：質化 v.s. 質化
- bar chart：質化 v.s. 量化
- scatter plot： 量化 v.s. 量化

--- .largecontent

## 探索質化變數與質化變數的關係


```r
?ftable
example(ftable)
```

```
ftable> ## Start with a contingency table.
ftable> ftable(Titanic, row.vars = 1:3)
                   Survived  No Yes
Class Sex    Age                   
1st   Male   Child            0   5
             Adult          118  57
      Female Child            0   1
             Adult            4 140
```

--- &vcenter .largecontent

## 小挑戰：

1. 選取場站區域為`信義區`且日期為`"2015-03-01"`的列
2. 選取欄`平均車輛數`與`總停車格`
3. 利用布林運算式計算"`平均車輛數`"是否超過`總停車格`的一半
    - 命名為`空位較多`
4. 選取欄`時間`
5. 比較`時間`和`空位較多`的交互關係

---

## 小挑戰（參考答案）


```r
# 尋找信義區2015-03-01的資料
x1 <- filter(ubike, 場站區域 == "信義區", 日期 == "2015-03-01") 
# 尋找平均車輛數 < 總停車格半數的情況
x2 <- mutate(x1, 空位較多 = 平均車輛數 < 總停車格 / 2)
# 列表
ftable(x2[["時間"]], x2[["空位較多"]])
# 利用 %>%
tbl <- filter(ubike, 場站區域 == "信義區", 日期 == "2015-03-01")  %>%
  mutate(空位較多 = 平均車輛數 < 總停車格 / 2)
ftable(tbl[["時間"]], tbl[["空位較多"]])
```

--- .dark .segue

## ggplot2 簡介

--- &vcenter .largecontent

## ggplot2簡介

- 2014年，最具影響力的R套件之一
- R環境下的繪圖套件
- 取自 “The Grammar of Graphics” (Leland Wilkinson, 2005)
- 設計理念
  - 採用圖層系統
  - 用抽象的概念來控制圖形，避免細節繁瑣
  - 圖形美觀

--- &vcenter .largecontent

## ggplot2基本架構

- 資料 (data) 和映射 (mapping)
- 幾何對象 (<font color='red'>geom</font>etric)
- 座標尺度 (<font color='red'>scale</font>)
- 統計轉換 (<font color='red'>stat</font>istics)
- 座標系統 (<font color='red'>coord</font>inante)
- 圖層 (layer)
- 刻面 (<font color='red'>facet</font>)
- 主題 (<font color='red'>theme</font>)

--- &vcenter .largecontent

## ggplot2核心

- 注意事項
  - 使用 data.frame 儲存資料 (不可以丟 matrix 物件)
  - 使用 long format (利用reshape2將資料轉換成 1 row = 1 observation)
- 基本語法
  - ggplot 描述 data 從哪來
  - aes 描述圖上的元素跟 data 之類的對應關係
  - geom_xxx 描述要畫圖的類型及相關調整的參數
  - 常用的類型諸如：geom_bar, geom_points, geom_line, geom_polygon

--- .largecontent

## 質化 v.s. 量化：繪圖之前的整理資料

### 文山區各站點在"2015-02"的平均降雨量


```r
# grepl("要搜尋的字串", x, fixed = TRUE)
x1.1 <- grepl("2015-02", ubike[["日期"]], fixed = TRUE)
x1.2 <- ubike[["場站區域"]] == "文山區"
x2 <- group_by(ubike[x1.1,], 場站名稱) #以場站名稱作為群聚的依據
x3 <- summarise(x2, 平均降雨量 = mean(降雨量)) #算出各場站的平均降雨量

x3 <- filter(ubike, grepl("2015-02", 日期, fixed = TRUE), 
             場站區域 == "文山區") %>%
  group_by(場站名稱) %>% summarise(平均降雨量=mean(降雨量))
```

--- .largecontent

## 質化 v.s. 量化：barchart


```r
thm <- theme(text=element_text(size=20)) # 控制字體
# + theme_gray(base_family = "STHeiti") for Mac OS
las2 <- theme(axis.text.x = element_text(angle = 90, hjust = 1)) #控制字的方向
ggplot(x3) +
  geom_bar(aes(x = 場站名稱, y = 平均降雨量), stat = "identity") + 
  #stat = "identity"：直接以數值作為bar的高度
  thm + las2
```

--- .largecontent

## 質化 v.s. 量化：barchart

<img src="assets/fig/ubike.site.rainfall21-1.png" title="plot of chunk ubike.site.rainfall21" alt="plot of chunk ubike.site.rainfall21" style="display: block; margin: auto;" />

--- .largecontent

## 質化 v.s. 量化：boxplot 


```r
x3 <- filter(ubike, grepl("2015-02", 日期, fixed = TRUE), 
             場站區域 == "文山區")
ggplot(x3) +
  geom_boxplot(aes(x = 場站名稱, y = 最大風速)) +
  thm + las2
```

--- .largecontent

## 質化 v.s. 量化：boxplot 

<img src="assets/fig/ubike.site.rainfall31-1.png" title="plot of chunk ubike.site.rainfall31" alt="plot of chunk ubike.site.rainfall31" style="display: block; margin: auto;" />

--- &vcenter .largecontent

## 量化 v.s. 量化：繪圖之前的整理資料

### 文山區各站點在"2015-02"的平均溼度 vs. 平均雨量


```r
x3 <- filter(ubike, grepl("2015-02", 日期, fixed = TRUE), 場站區域 == "文山區") %>%
  group_by(場站名稱) %>% 
  summarise(平均降雨量 = mean(降雨量), 平均溼度 = mean(溼度))
```

--- .largecontent

## 量化 v.s. 量化：Scatter Plot


```r
ggplot(x3) +
  geom_point(aes(x = 平均溼度, y = 平均降雨量),size=5) + #size控制點的大小
  thm
```

<img src="assets/fig/ubike.site.wet.rainfall2-1.png" title="plot of chunk ubike.site.wet.rainfall2" alt="plot of chunk ubike.site.wet.rainfall2" style="display: block; margin: auto;" />


--- .largecontent

## 量化 v.s. 量化：Grouped Scatter Plot


```r
ggplot(x3) +
  # 放在aes裡的colour和size可依資料調整顏色和大小
  geom_point(aes(x = 平均溼度, y = 平均降雨量, colour = 場站名稱,size=平均降雨量))+
  # 限制大小
  scale_size(range=c(5,10)) +  
  thm
```

--- .largecontent

## 量化 v.s. 量化：Grouped Scatter Plot

<img src="assets/fig/ubike.site.wet.rainfall3-1.png" title="plot of chunk ubike.site.wet.rainfall3" alt="plot of chunk ubike.site.wet.rainfall3" style="display: block; margin: auto;" />

--- .largecontent

## 時間 v.s. 量化：繪圖之前的整理資料

### 文山區各站點每日平均雨量


```r
x3 <- filter(ubike, grepl("2015-02", 日期, fixed = TRUE), 場站區域 == "中和區") %>%
  group_by(日期,場站名稱) %>% 
  summarise(每日平均降雨量 = mean(降雨量))
```

--- .largecontent

## 時間 v.s. 量化：Line Plot


```r
ggplot(x3) + thm+las2+
  geom_line(aes(x = 日期, y = 每日平均降雨量,group=場站名稱,colour=場站名稱))
```

<img src="assets/fig/ubike.site.wet.rainfall13-1.png" title="plot of chunk ubike.site.wet.rainfall13" alt="plot of chunk ubike.site.wet.rainfall13" style="display: block; margin: auto;" />

--- .largecontent

## 時間 v.s. 量化：Line Plot in Facets


```r
ggplot(x3) +thm+las2+facet_wrap(~場站名稱,nrow=2)+ # facet_wrap將各站的情況分開畫
  geom_line(aes(x = 日期, y = 每日平均降雨量,group=場站名稱,colour=場站名稱))
```

<img src="assets/fig/ubike.site.wet.rainfall14-1.png" title="plot of chunk ubike.site.wet.rainfall14" alt="plot of chunk ubike.site.wet.rainfall14" style="display: block; margin: auto;" />


--- &vcenter .largecontent

- [ggplot2 cheat sheet from RStudio Inc.](http://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf)
- [ggplot2 官方文件](http://docs.ggplot2.org/current/index.html)

--- &vcenter .largecontent

## 圖形的美化

### Maker精神：雕圖

- 學習更底層的繪圖指令，如`grid`套件
- 學習原生的繪圖指令

### 站在巨人的肩膀上

- 使用如`ggthemes`等套件

--- &twocol

## [ggthemes](https://github.com/jrnold/ggthemes)

*** =left

<br/>
<br/>
<center>
<img src='assets/img/687474703a2f2f692e696d6775722e636f6d2f764e64366543542e706e67.png' style='max-width: 100%;max-height: 100%'></img>
</center>

*** =right

<br/>
<br/>
<center>
<img src='assets/img/687474703a2f2f692e696d6775722e636f6d2f7350764165334a2e706e67.png' style='max-width: 100%;max-height: 100%'></img>
</center>

--- .dark .segue

## 圖表的輸出

--- &vcenter .largecontent

## 輸出圖片

- Rstudio UI
- `savePlot`
- `bmp`、`png`、`jpeg`或`tiff`

--- &vcenter .largecontent

## 輸出表格

- `write.csv`
- `xtable`套件

--- &vcenter .largecontent

## R markdown 火力展示

- 本週四早場起

--- &vcenter .largecontent

## shiny

- <http://shiny.rstudio.com/gallery/>

--- .dark .segue

## 總結

--- &vcenter .largecontent

## 本週目標

### 環境設定

- 建立可以使用R 的環境
- 了解R 的使用界面

### 學習R 語言

- 透過實際的範例學習R 語言
    - 讀取資料
    - 選取資料
    - 敘述統計量與視覺化
- 利用實例來傳授學習的心法

--- &vcenter .largecontent

## 掌握心法後，如何自行利用R 解決問題

- 了解自己的需求
- 詢問關鍵字與函數
    - 歡迎來信 <benjamin0901@gmail.com> 或其他教師
    - 多多交流
        - [Taiwan R User Group](http://www.meetup.com/Taiwan-R)，mailing list: <Taiwan-useR-Group-list@meetup.com>
        - ptt R_Language版
        - [R軟體使用者論壇](https://groups.google.com/forum/#!forum/taiwanruser)
    - `sos`套件，請見Demo


--- .dark .segue

## Team Project
