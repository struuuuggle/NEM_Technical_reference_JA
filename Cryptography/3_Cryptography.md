# 暗号法

> I understood the importance in principle of public key cryptography but it’s
> all moved much faster than I expected. I did not expect it to be a mainstay
> of advanced communications technology
>
> 公開鍵暗号方式の重要性についてはおおむね理解してはいましたが、ここまで早く普及したことは私の想定外でした。
> 発達したコミュニケーションテクノロジーの根幹になることを想定したものではなかったのです。
>
> Whitfield Diffie (Diffie-Hellman鍵共有の考案者)

ブロックチェーンテクノロジーはいくつかの暗号学的なコンセプトの利用を前提としています。
NEMは、他の多くの暗号通貨と同様、楕円曲線暗号に依拠した暗号法を利用しています。
以下の曲線を採用したことは、セキュリティとスピードを保証するうえで重要です。

NEMは、素数$$2^{255}-19$$の有限体上で定義される**歪曲エドワーズ曲線**(*Twisted Edwards curve*)

$$
-x^2 + y^2 = 1 - \frac{121665}{121666} x^2y^2
$$

を使用したデジタル署名アルゴリズムであるEd25519を使用することを選択しました。
これはD.J.Berstein et alによって開発された、世界でも有数の安全で高速な署名アルゴリズム[2](/References.md#2)です。

曲線上の巡回群$$G$$に対応するベースポイントを$$B$$とします。この群は $$q=2^{252}-27742317777372353535851937790883648493$$個の元を持ちます。
群上の任意の元$$A$$は256ビットの整数にエンコードすることができます。
これは256ビットの文字列として解釈することができ、デコードして再び$$A$$に戻すことができます。詳細は[2](/References.md#2)を見てください。

NEMでは、上記の論文中で言及されているハッシュ関数$$H$$として512ビットSHA3ハッシュ関数を用います。
