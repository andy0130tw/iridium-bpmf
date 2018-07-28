# Iridium-Bopomofo

> 銥是化學元素，符號為Ir，原子序為77，屬於鉑系過渡金屬，為質地堅硬易碎的銀白色固體。銥是所有元素中密度第二高的元素（僅次於鋨），而其耐腐蝕性是所有金屬元素中最高，在2000℃高溫下仍然能抵抗腐蝕。 (from [Wikipedia](https://zh.wikipedia.org/wiki/銥))

(又是一個) 基於 RIME、參酌其它注音輸入法習慣、符合臺灣使用習慣為規準的注音輸入方案。

配方： ℞ `iridium-bpmf`

使用「東風破」 [`plum`](https://github.com/rime/plum) 安裝：`bash rime-install andy0130tw/iridium-bpmf` \
注意：目前本方案尚依賴 [地球拼音](https://github.com/rime/rime-terra-pinyin) ℞ `terra-pinyin` 的字典檔。

## 示範

<p align="center">
<img alt="demo gif" src="../assets/demo.gif">
</p>

## 特色

* 可不照聲介韻順序輸入，如「ㄋㄠㄧˇ」會自動修正為「ㄋㄧㄠˇ」，改進自 [RIME設定檔-注音（google注音+台灣注音習慣）](http://deltazone.pixnet.net/blog/post/264319309-%E9%BC%A0%E9%AC%9A%E7%AE%A1%E6%B3%A8%E9%9F%B3%E6%96%B9%E6%A1%88---%E7%AC%A6%E5%90%88%E4%B8%80%E8%88%AC%E6%B3%A8%E9%9F%B3%E4%BD%BF%E7%94%A8%E8%80%85%E7%BF%92%E6%85%A3%E8%A8%AD)
* 對新手而言較為直覺的快速鍵綁定，例如用 Backspace 退格時，已完成組字的字會整字刪除，而非逐音節刪除
* 正確設定繁簡轉換 (行為可在方案選單中切換)
* 模擬新注音的行為，可以直接用「注音+空格」輸入注音本身、「聲調」鍵直接輸入聲調
* 將原始 RIME 設計的左右 Shift 對調，使較常用的「左 Shift」的功能變為臨時西文模式
* 儘可能在設定檔中加上註解，使得客製化更加便利

# 實驗
一些與 RIME 有關的嘗試或實驗，為維護方便及維持此專案穩定性，會發佈在[另一個 repo](https://github.com/andy0130tw/aarrr-rime)，習慣本方案後可以搭配使用。
