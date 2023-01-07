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

示範環境為 Pop!\_OS 18.04 搭配 gedit。

## 特色

* 可不照聲介韻順序輸入，如「ㄋㄠㄧˇ」會自動修正為「ㄋㄧㄠˇ」，改進自 [RIME設定檔-注音（google注音+台灣注音習慣）](http://deltazone.pixnet.net/blog/post/264319309-%E9%BC%A0%E9%AC%9A%E7%AE%A1%E6%B3%A8%E9%9F%B3%E6%96%B9%E6%A1%88---%E7%AC%A6%E5%90%88%E4%B8%80%E8%88%AC%E6%B3%A8%E9%9F%B3%E4%BD%BF%E7%94%A8%E8%80%85%E7%BF%92%E6%85%A3%E8%A8%AD)
* 對新手而言較為直覺的快速鍵綁定，例如用 Backspace 退格時，已完成組字的字會整字刪除，而非逐音節刪除
* 正確設定繁簡轉換 (行為可在方案選單中切換)
* 模擬新注音的行為，可以直接用「注音+空格」輸入注音本身、「聲調」鍵直接輸入聲調
* 將原始 RIME 設計的左右 Shift 對調，使較常用的「左 Shift」的功能變為臨時西文模式
* 儘可能在設定檔中加上註解，使得客製化更加便利

## 手動部署方法

以 Ubuntu 搭配 ibus 為例：

1. 將此專案拷貝到 `~/.config/ibus/rime` 下，並將需要的檔案符號連結至該目錄。

   ```bash
   git clone https://github.com/andy0130tw/iridium-bpmf
   ln -s iridium-bpmf/iridium_bpmf.schema.yaml .
   ln -s iridium-bpmf/iridium_bpmf_ext.dict.yaml .
   ln -s iridium-bpmf/iridium_bpmf_phrase.txt .
   ln -s iridium-bpmf/terra_pinyin.dict.yaml .
   ```

   (或是讀者若會使用 `xargs` 也可自行簡化此流程)

2. 依照 `default.custom.yaml.ref` 新建或修改設定檔補丁 `default.custom.yaml`。

   * `schema_list`：將本方案加入已啟用的方案列表
   * `key_binder/bindings`：修改有關移動選單游標的按鍵映射 \
     注意這個檔案預設使用者是使用橫向選字列表，然而這並非預設行為。如果要使用直向的配置，在此步驟將 `send` 參數的 `Page_{Up,Down}` 和其下兩行的對應參數交換。
   * `switcher`: 新增本方案會用到的開關

3. 在 Rime 選單上選擇「部署」。

4. 好耶<br>
   ![好耶](https://user-images.githubusercontent.com/5269414/115489814-714fa480-a28f-11eb-8f9b-2af83d5551c4.png)

# 已測試環境

作者已在以下環境中測試，皆可以正常使用本方案，無明顯功能差異。

* Ubuntu 18.04 LTS + GNOME + IBus
* Ubuntu 20.04 LTS + GNOME + IBus
* Ubuntu 18.04 LTS + Budgie + IBus
* Debian 10 + fcitx

有在小狼毫 (Windows) 或鼠鬚管 (Mac) 配置過此方案的朋友，歡迎在 [Issue tracker](https://github.com/andy0130tw/iridium-bpmf/issues) 分享。

> 2022/7/10: 作者入手了一臺 Macbook Air，目前使用鼠鬚管搭配此輸入方案，待測試妥善後會更新此文件。

## 常見問題

### 在 IBus 使用橫向選字列表

因為 ibus-rime 的設計細節，在 GNOME 底下 IBus 的選字列表不會遵照 `ibus-config` 內的方向設定，一律為直向，如圖所示：

![直向選字視窗](https://user-images.githubusercontent.com/5269414/115489988-c2f82f00-a28f-11eb-8aab-a24e756899db.png)

若要在 IBus 上使用橫向配置，必須明確於 `~/.config/ibus/rime/build/ibus_rime.yaml` 檔案指定，如果不存在的話手動建立並加入以下內容，

```yaml
style:
  horizontal: true
```

然後重新部署即可。似乎在某個特定版本的 `ibus-rime` 會自動建立這個檔案，則只要將 `horizontal` 屬性從 `false` 改成 `true` 就好。

> * [作者某天在整理 rime 設定檔的時候無意間查到的解法連結](https://forums.fedoraforum.org/showthread.php?320042-How-to-set-ibus-rime-to-horizontal-in-fedora-29&p=1819670#post1819670)。
> * [或是直接看程式碼](https://github.com/rime/ibus-rime/blob/1.5.0/rime_settings.c)。

# 實驗

一些與 RIME 有關的嘗試或實驗，為維護方便及維持此專案穩定性，會發佈在[另一個 repo](https://github.com/andy0130tw/aarrr-rime)，習慣本方案後可以搭配使用。
