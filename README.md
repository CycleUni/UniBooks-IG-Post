# UniBooks IG Post

UniBooks Instagram 貼文的原稿與輸出，使用 [Marp](https://marp.app/) 把 Markdown 輸出成 IG 輪播圖片。

## 結構

```
UniBooks-IG-Post/
├── ig.css              共用主題（1080×1350，IG 4:5 直式）
├── package.json        Marp CLI 套件，所有貼文共用
├── node_modules/       （不進 git）
└── User Guide/         第一篇：平台介紹與使用方式（8 頁）
    ├── guide.md        Marp 原稿
    ├── logo-mark.svg、wordmark-light.svg  品牌 logo（取自網站 icons，字標為淺色版）
    └── out/            輸出的 PNG
```

每篇貼文一個資料夾，內含 `*.md`、素材與 `out/`。

## 使用

第一次先安裝套件：

```bash
npm install
```

在貼文資料夾內輸出 PNG（以 `User Guide` 為例）：

```bash
cd "User Guide"
CHROME_PATH="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" npx marp guide.md --theme ../ig.css --images png --allow-local-files -o out/slide.png
```

會產生 `out/slide.001.png`、`slide.002.png`……，依序上傳 IG 即可。

即時預覽：

```bash
npx marp -s . --theme ../ig.css
```

## 新增貼文

1. 在本資料夾下新增資料夾，例如 `Campus Market/`。
2. 複製 `User Guide/guide.md` 當範本，檔頭保留 `marp: true` 與 `theme: ig`。
3. 以 `---` 分頁，用 `<!-- _class: dark -->` 做深綠底頁（封面、結尾）。
4. 輸出時 `--theme` 指向 `../ig.css`。

## 品牌色

| 用途 | 色碼 |
| --- | --- |
| 主色（深綠） | `#1E5C46` |
| 強調（黃） | `#FAC775` |
| 標籤（暖橘） | `#C8763F` |
| 背景 | `#F2F7F4` |

## 注意

- 不要在 CSS 用 Google Fonts `@import`，會讓輸出卡住；使用系統字型（PingFang TC / Noto Sans TC）。
- Marp 用的 Chrome 若與正在開啟的 Chrome 衝突而卡住，關掉再重跑，或在指令前加 `perl -e 'alarm 100; exec @ARGV'` 做逾時保護。
- IG 貼文內文的網址不能點，要引導到主頁（Bio）連結 `unibooks.app`。
- 校慶攤位活動不放進貼文，另外用限時動態發布。
