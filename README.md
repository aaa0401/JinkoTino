# JinkoTino
らしいです。

## モデルの構築
```python
# keras
model.Sequenctial()
model.add(Dense(3, activation='sigmoid'))

# torch
nn.Linear(入力次元, 出力次元)
nn.Sigmoid()
``` 
層を宣言していき、同じxに対して順番に関数を適用することで学習を再現。

## 層の種類
- 全結合：```Dense(ユニット数、活性化関数) nn.Linear(入力次元、出力次元)```

## 活性化関数
- シグモイド関数：わからん
- ReLU：すごいやつ
- ソフトマックス：クラス分類はこれ
- 恒等写像：使われてるのかな

## モデルの学習
```python
# keras
model.compile(optimizer=オプティマイザ, loss=誤差関数, matrics=評価指標) # 学習の設定
model.fit()

#torch
```
- verbose：1=プログレスバーの表示

## 誤差関数(クライテリオンcriterion)
- crossentropy
- binary_crossentropy
kerasではコンパイル時にloss=""で決定。torchは毎回criterion(x, y)で求めた後にGradientTapeで勾配を求める

## オプティマイザ
- SGD(確率的降下法)：カス

### その他の小手先
- Heの重み初期化
- Xavierの重み初期化
- バッチ正規化

# RNN
## BPTT
時系列モデルではその時間の出力層だけでなく未来の隠れ層からも誤差を受け取る

## 気をつけること
- 直交行列を用いた重み初期化(np.linalg.svd()で求められる)
- ReLUを用いると発散する。シグモイドかtanh


# 関係ないけど覚えておくべき技術
- seed固定：いい結果が出たときseedがわかんないと再現できないぞ☆
