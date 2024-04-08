---
title: Noah的小記2 那些創立網站時遇到的問題與解方
date: 2024-03-02 00:03:09
categories: Noah的小記
tags:
---
在架設網站的時候，儘管事先在網路閱讀了許多教學，按部就班地完成了設定的步驟，但每個人的帳戶、電腦情況和軟體的版本有所不同，難免會出現一些預料之外的情況。因此，我決定用一篇文章，說明我在架設網站時所遇到的種種問題，以及排除的方法。

首先，是使用hexo指令時的報錯。

既然這個網站是用hexo架設的，當然是使用hexo指令來創建、編修、發布文件。但有次使用hexo的指令後，Git Bash跳出了以下報錯：
**Commands:help Get help on a command.init Create a new Hexo folder.version Display version information...**
從錯誤訊息看不太出問題出在哪裡，只知道此刻hexo的所有指令皆未能順利執行。

事實上，這是因為檔案路徑已經被移動過了。

<!-- more -->

在創建網站時，電腦端會同步產生一個叫做「github page」的資料夾，將所有相關資料存放在裡面。因此，當我們使用hexo指令時，指向的位置當然要是github page，也就是離檔案位置最近的地方。如果不慎更動到檔案路徑，無論你重複再多次指令，github page都無法收到。我們可以在Git Bash使用cd指令，重新指派檔案路徑，寫法如下：

cd ~/Documents/中間的檔案路徑/"github page"

當然，也可以從檔案總管直接找到github page，點進資料夾後在空白處按右鍵，選擇「顯示其他選項－Git Bash Here」，直接在檔案位置開啟Git Bash，檔案路徑就會直接預設到github page了。

再來，是[郵箱與名字的遺失](https://blog.csdn.net/qq_26540999/article/details/53445589)。

一次使用hexo指令發布文章時，Git Bash出現了以下報錯：
**git config --global user.email "you@example.com"**
**git config --global user.name "Your Name"...**
**to set your account's default identity.**
**Omit --global to set the identity only in this repository...**
**fatal: unable to auto-detect email address (got 'Administrator@MS-201610130300.(none)')**

這次的錯誤訊息就很明顯了，要我們重新設定身分。簡單來說，在使用github page發佈文章時，系統會先創建一個git資料夾，把檔案放入資料夾後再發佈。而電腦在創建git資料夾的過程中發現我們提供的身分訊息並不完整，此時只要手動在Git Bash中補充其所需訊息即可，寫法如下：

git config --global user.email "你的郵箱"
git config--global user.name "你的名字"

注意"你的郵箱"和"你的名字"的部分，要填入自己在創建帳號時所使用的信箱和名字，輸入後再次送出指令就會恢復正常了。

最後是一個困擾我很久的問題。當初在設定hexo的時候，參考了許多網路文章。其中一篇寫到若要設定網頁的圖片背景，可在github page/source/_data裡找到一個叫做styles.styl的檔案，在裡面打上以下內容：
body {
    background: url(圖片的檔案路徑);
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: top center;
}
先說結論，在styles.styl檔裡面設定網頁的圖片背景這點是對的，但打法錯了。若是照打上去，會出現ParseError，也就是格式上的錯誤。我自己試成功的設定方式如下：
background: 圖片的檔案路徑
background-size: cover
background-repeat: no-repeat
background-attachment: fixed
background-position: top center
內容大致上和教學一致，但外面不用加上body{}，圖片的檔案路徑也不用加url，句尾去掉;，最後把不必要的空白行和縮排去除即可。
