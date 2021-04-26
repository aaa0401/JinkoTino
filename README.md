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


## 誤差関数(クライテリオンcriterion)
- クロスエントロピー：いろんな種類があるね

## オプティマイザ
- SGD(確率的降下法)：カス
