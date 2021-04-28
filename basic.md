# JinkoTino
らしいです。

## モデルの構築
```python
# keras
model.Sequenctial()
model.add(Dense(3, activation='sigmoid'))
...

# tf
class MLP(Model):
  def __init__():
    self.l1 = Dense(ユニット数, activation=活性化関数)
    
  def call():
    

# torch
class DNN(nn.module)
  def __init__():
    self.l1 = nn.Linear(入力次元, 出力次元)
    self.a1 = nn.Sigmoid()
    
  def forward():
    入力xにレイヤーの関数を掛けていく処理


``` 
層を宣言していき、同じxに対して順番に関数を適用することで学習を再現。

## 層の種類
- 全結合：```Dense(ユニット数、活性化関数) nn.Linear(入力次元、出力次元)```

## 活性化関数
- Sigmoid：わからん
- tanh：シグモイドに比べて勾配が消失しにくい
- ReLU：tanhに比べて高次元において勾配が消えにくい
- leakyReLU：負の場合でも傾き!=0としたためReLUの問題を解決したが、効果はまちまち
- ParametricReLU：勾配自体も学習内で変えていこうというもの
- ELU：
- softmax：クラス分類はこれ
- linear：実数値はこれ
勾配消失問題は層が深くなると発散したり0になったりすること。うまく活性化関数を選ばないとこうなる。  
ReLUは学習率が大きい場合、一度負となり(傾き0)不活性化したニューロンが再び活性化しにくいという難点がある。  


## モデルの学習
```python
# keras, tf
model.compile(optimizer=オプティマイザ, loss=誤差関数, matrics=評価指標) # 学習の設定
hist = model.fit(学習データ, 学習ラベル, epochs=エポック数, batch_size=バッチサイズ)

# torch
criterion = torch.nn.CrossEntropyLoss(reduction=減衰法)
optimus = torch.optim.SGD(model.parameters(), lr=0.1)

#以下学習の1ステップ
model.train()
preds = model(x)
loss = criterion(t, preds)
optimizer.zero_grad()
loss.backward()
optimiser.step()

```
- verbose：1=プログレスバーの表示


## 誤差関数(criterion)
- "crossentropy"
- "binary_crossentropy"
- BCELoss
- MeanSquadError:MSELoss
kerasではコンパイル時にloss=""で決定。torchは毎回criterion(x, y)で求めた後にGradientTapeで勾配を求める

## オプティマイザ
- SGD(確率的降下法)：カス
- ADAM

### 学習に関連する小手先
- Heの重み初期化
- Xavierの重み初期化
- バッチ正規化
- シャッフル
- 早期終了 ```EarlyStopping(monitor='val_loss'), patience=最大上昇, verbose=1)

# 関係ないけど覚えておくべき技術
- seed固定：いい結果が出たときseedがわかんないと再現できないぞ☆

# 有用な関数
- reshape：形を整える
- device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
