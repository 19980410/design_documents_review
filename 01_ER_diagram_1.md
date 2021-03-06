# ER図1（問題点のみ）
## 全体
- 全てのテーブルに登録日と更新日がない
- > 登録日と更新日が全てのテーブルに存在しないので追加しましょう。

- 商品の入荷が管理できない
- > 商品の入荷情報はどのように管理しますか？

## 管理人テーブル
- 管理人とユーザーが１対多になっていること
- > 管理人とユーザーのリレーションは必要でしょうか？必要であれば理由を教えてください。

- 管理人と商品が１対多になっていること
- > 管理人と商品のリレーションは必要でしょうか？必要であれば理由を教えてください。

## エンドユーザーテーブルについて
- 住所や郵便番号が１つしか登録できない仕様になっている
- > 住所や郵便ばんごうがユーザー１人に対して1つしか持てません。複数の住所を登録したい場合はどうしますか？

- 退会用のステータスが存在しないこと
- > ユーザーを削除した後のレコードはどうなりますか？論理削除が考慮されておりません。

## 商品テーブルについて
- レーベル名が直で商品テーブルにあること
- ジャンル名が直で商品テーブルにあること
- アーティスト名が商品テーブルにあること
- > レーベル名、アーティスト名、ジャンル名全て、商品テーブルに含まれていますが、名前（アーティスト、レーベル、ジャンル）の変更があった場合全てのレコードを編集する必要がありますが、問題ありませんか？

- アーティスト名がカート内にあること
- > アーティスト名カラムをカートテーブルに持たせる必要はありますか？

- 曲順が分からないこと
- > 曲順が分からないです。曲が複数ある場合はどう対処しますか？

- ディスクが複数枚ある場合この設計だと対応できないこと
- > ディスクが複数存在する場合は、どう対処しますか？


## カートテーブルについて
- カートに入れている枚数が分からないこと
- > カートに入れている商品の枚数が分かりません。何枚買うかわかるようにしましょう。

- ユーザーと結びついていないため誰のカートか判別ができないこと
- > ユーザーとのリレーションがないため、誰のカートなのか判別できません。どのユーザーのカートかわかるようにしましょう。

- アーティスト名、ジャケット写真、シングルアルバム名がカートテーブルに入っていること
- > アーティスト名、ジャケット写真、シングルアルバム名がカートに必要でしょうか？商品テーブルに含まれている情報ですので、保存する理由を教えてください。

- カートテーブル内に合計金額カラムは必要ないこと
- > カートテーブルに合計金額を保存する必要はありますか？　購入前の金額は保存せずとも算出できます。

- PKがこのテーブルのIDではなく、注文IDとなっていること
- > PKがカートテーブルのIDではなく、注文IDとなっています。変更しましょう。

## 決済と購入履歴テーブルについて 
- 現在の設計だと購入した商品が分からない
- > 現在の設計だと購入した商品が分かりません。購入した商品が分かるように商品の情報を保存しましょう。

- 現在の設計だと購入した商品が分からない
- 送料がないこと
- > 送料を保存するカラムが存在しません。追加しましょう。

- 合計金額を保存するカラムが存在しないこと
- > 購入後は合計金額を保存するためのカラムを作成しましょう。

- 購入日カラムが必要ないこと
- > 購入日カラムは登録日時を使用できるので必要ありません。

- 決済テーブルというテーブル名がおかしいこと
- > テーブル名は管理者似合わせるために受注テーブル等に変更しましょう。

- 宛先名、郵便番号カラムがないこと
- > 送付先住所カラムがありますが、郵便番号や宛名はどのように管理しますか？１つにまとめてしまうと不便です。



**研修担当レビュー**
<font color="Red">再提出の際はこのレビューを残しておいてください。</font>
## 全体
- 入荷情報はどのように管理しますか？

## エンドユーザー
- エンドユーザーが退会した場合、該当のレコードはどうなりますか？

## 商品
- > アーティスト名がカート内にあること

とありますが、商品テーブルにアーティスト名カラムがあることは問題ありませんか？
- > カートテーブルとのカーディナリティが0以上ではないこと

とありますが、カーディナリティの意味について調べてみてください
- 複数のディスクを持つ設計になっていません。
- 商品のデータが削除されば場合該当のレコードはどうなりますか？
- 在庫数カラムがありますが大丈夫でしょうか？
- ステータスカラムはどのようなステータスが入るかわかりづらいです。

## カート
- `カート`というテーブルの命名はふさわしいでしょうか？
- 合計金額カラムは必要でしょうか？
- PKはあっていますか？

## 決済
- テーブル名はあっていますか？
- 購入日カラムは必要でしょうか？
- 合計金額カラムがありません
- カートテーブルとのリレーションは問題ありませんか？
- > 送付先住所カラムが１つしかないこと

とありますが、送付先住所は一つで十分かと思います
- 宛先名、郵便番号カラムは必要ありませんか？
 
