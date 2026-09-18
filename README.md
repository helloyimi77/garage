# garage

自分用の愛車リスト。車・バイク・電動キックボード・ロードバイク・愛馬を1つのJSONで管理し、GitHub Pagesで表示する。ビルド不要。

## 公開手順

1. このフォルダの中身を `helloyimi77/garage` にpush
2. Settings → Pages → Source を `Deploy from a branch` / `main` / `/ (root)` にする
3. 数分後 `https://helloyimi77.github.io/garage/` で表示される

## 更新方法

`vehicles.json` をGitHub上で直接編集してコミットするだけ。1台 = 1オブジェクト。

```json
{
  "id": "unique-id",            // URLの #id に使う。英数字とハイフン
  "category": "car",            // car | bike | escooter | roadbike | horse
  "status": "active",           // active | sold
  "name": "ロードスター",
  "maker": "マツダ",
  "model": "ND5RC",
  "grade": "S Special Package",
  "year": 2019,
  "color": "ソウルレッド",
  "purchase": { "date": "2019-06-01", "type": "used", "price": 2500000 },
  "sold":     { "date": null, "price": null },
  "specs":    { "排気量": "1,496cc", "駆動方式": "FR" },   // 自由な key-value
  "customs":  [ { "part": "", "maker": "", "type": "", "date": "", "price": 0, "note": "" } ],
  "equipment":[ { "name": "", "maker": "", "price": 0 } ],
  "photos":   { "main": "images/xxx/main.jpg", "gallery": [] },
  "memo": ""
}
```

- `customs` は「今付いているもの」だけ（履歴は持たない）。過去車両は手放した時点の最終構成
- 総投入額 = `purchase.price` + `customs` の合計 + `equipment` の合計 を自動計算
- 写真は `images/<id>/` に置く。publicリポなのでナンバー等は写り込みに注意

## ローカルで確認

`file://` で直接開くと `fetch` が動かないので、簡易サーバーで配信する。

```
python3 -m http.server 8000
# → http://localhost:8000
```
