# SecureInject Androidアプリ 利用マニュアル

本マニュアルでは、専用Androidアプリ「SecureInject」のインストール方法、初期設定、およびテキスト送信手順を解説します。

---

## 1. 動作環境・事前準備

* **対応OS** ：Android 7.0 (API Level 24) 以上
* **通信規格** ：Bluetooth Low Energy (BLE)
* **必要物品** ：
  * Androidスマートフォン
  * SecureInject 本体（USB-C超小型キーボード）
  * 付属のMACアドレス記載シール（本体またはパッケージに同梱）

---

## 2. アプリ（APK）のインストール手順

本アプリは個人製作のためGoogle Playストア外で配布される野良アプリ（APKファイル）です。以下の手順でインストールを行ってください。

### Step 1: APKファイルのダウンロード
本リポジトリ（または指定のダウンロードリンク）から `app-release.apk` をダウンロードします。

### Step 2: インストール許可と実行
1. ダウンロードした `app-release.apk` をタップして開きます。
2. 「セキュリティ上の理由から、この提供元の不明なアプリをインストールすることはできません」という警告が出た場合は、**「設定」**をタップします。
3. **「この提供元のアプリを許可」**（または「不明なアプリのインストールを許可」）をオンにします。
4. 元の画面に戻り、**「インストール」**を実行します。

---

## 3. 初回セットアップ・初期設定

アプリを起動したら、まずはBluetooth権限の許可と、購入されたハードウェア本体とのダイレクト接続設定を行います。

### Step 1: 権限の許可
1. アプリ初回起動時に**「位置情報」**および**「近接デバイス（Bluetooth）」**へのアクセス許可ダイアログが表示されます。
2. 必ず**「許可」**（アプリの使用中のみ許可）を選択してください。
   *(※BLEデバイスの検索・接続に必要な権限です)*

### Step 2: MACアドレス設定
1. 画面右上の**「設定（歯車アイコン）」**をタップします。
2. **「MACアドレス」**の入力欄に、製品に付属しているシールに記載された**MACアドレス（12桁の英数字：例 `AA:BB:CC:11:22:33`）**を入力します。
   *(※スマホのキーボードが邪魔で保存できない場合は、スマホの戻るボタンをタップしてキーボードを消してください。初期化、キャンセルも同様です。)*
3. **「保存」**をタップして設定を適用します。

> 💡 **初期化機能について** > 設定画面内の「初期化（デフォルトに戻す）」ボタンを押すと、いつでも工場出荷時のデフォルト設定（プレフィックス・サフィックス設定等）に戻すことができます。

---

## 4. 基本的な使い方（テキスト注入手順）

PC側にハードウェア本体を接続し、スマホからテキストを転送する手順です。

### Step 1: ハードウェアの接続
1. 付属のUSBケーブルで、SecureInject本体（超小型キーボード）を対象のPC（Windows）に接続します。
2. PC側で標準キーボードとして認識されます。
3. PC側でPowerShell（ショートカット：`Win + X` → `I`　もしくは　`Win + R` → `powershell` → Enter）を開き、カーソルを点滅させておきます。またIMEは半角英数字入力（日本語変換オフ）にしておきます。

### Step 2: テキストの貼り付けと送信
1. スマホ側で、転送したいテキスト（AIが生成したプログラムコードや文章）をクリップボードにコピーします。
2. SecureInjectアプリの**「貼付」**ボタンで、メイン画面にある入力エリアにテキストを貼り付けます。Android OS機能の貼り付けで行なっても問題ありません。
3. 未接続の場合は**「Bluetooth接続」**ボタンを押下し、接続されたら**「Inject（送信）」**ボタンをタップします。「payload送信中」が出れば成功です。そのままお待ちください。

### Step 3: 転送完了の確認
1. BLE通信が開始され、SecureInject本体経由でPCへ自動的にキーボード打鍵が行われます。
2. 送信が完了するまでPCやスマホの操作を控え、お待ちください。
   *(※画面の自動回転が入ると送信キャンセルされます。自動回転オフで使用してください。また、PowerShellからフォーカスを外さないでください。)*

---

## 5. トラブルシューティング

<table style="width:100%; border-collapse: collapse;">
  <thead>
    <tr style="background-color: #f2f2f2;">
      <th style="border: 1px solid #ddd; padding: 8px; text-align: left; width: 25%;">症状</th>
      <th style="border: 1px solid #ddd; padding: 8px; text-align: left; width: 35%;">原因</th>
      <th style="border: 1px solid #ddd; padding: 8px; text-align: left; width: 40%;">対処法</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #ddd; padding: 8px; font-weight: bold;">アプリが本体に接続できない</td>
      <td style="border: 1px solid #ddd; padding: 8px;">MACアドレスの誤入力、またはBluetooth無効</td>
      <td style="border: 1px solid #ddd; padding: 8px;">設定画面でMACアドレスがシール表記と一致しているか確認してください。スマホのBluetooth機能がONになっているかも確認してください。</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 8px; font-weight: bold;">権限エラーが表示される</td>
      <td style="border: 1px solid #ddd; padding: 8px;">Bluetooth / 位置情報権限の未許可</td>
      <td style="border: 1px solid #ddd; padding: 8px;">スマホの「設定」&gt;「アプリ」&gt;「SecureInject」&gt;「権限」から、位置情報と近接デバイスの許可を有効にしてください。</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 8px; font-weight: bold;">PC側で記号や日本語が崩れる</td>
      <td style="border: 1px solid #ddd; padding: 8px;">PC側のキーボード配列設定<br>転送中断等による文字のバッファ残存</td>
      <td style="border: 1px solid #ddd; padding: 8px;">PC側のキーボードレイアウトが「日本語109キーボード」になっているか確認してください。<br><br>送信失敗などで継続して文字欠損するようになった場合は、スマホとPCを再起動したのち、再度送信してください。</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 8px; font-weight: bold;">送信途中でタイピングが止まる</td>
      <td style="border: 1px solid #ddd; padding: 8px;">接続の切断またはUSB抜け</td>
      <td style="border: 1px solid #ddd; padding: 8px;">USBケーブルの接続を確認し、再度「送信」ボタンを押してください。</td>
    </tr>
  </tbody>
</table>
