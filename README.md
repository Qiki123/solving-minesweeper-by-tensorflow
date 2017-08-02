# TensorFlow solve minesweeper

## 簡介
使用 TensorFlow 訓練 model 解 minesweeper (踩地雷)

model 正確率達到 94%  E(in) = 97.69% E(out) = 94.34 

## 開發環境

Ubuntu 17 + Python 3.5 + TensorFlow 1.2

## 檔案簡介

| 檔案 | 簡介 |
| ------ | ------ |
| model-gamma.py| model 定義 & model 訓練 |
| gui.py | model 解採地雷 | 
| minesweeper.py | 視覺化 model 解採地雷 |
| dataset.py | 將 minesweeper.py 產生的遊戲內容轉換並包裝成訓練資料 |
| packages | 專案用到 python 的套件 (pip freeze  > packages) | 
| model/ac-96/ | 預先訓練完的 model  |
| data | 預先產生的 dataset |

## 使用方法
以 CPU 訓練 model 訓練時間約 1 小時 50 分鐘

訓練完成後 checkpoint & model 會儲存在 ./model/model-gamma/run-{date}-{time}

- 訓練 model 
~~~bash
$> python model-gamma.py
~~~

- 查看訓練結果
~~~bash
$> python gui.py -t ./model/model-gamma/run-{date}-{time}/model-gamma-{check-point}.meta -m model-gamma.py
~~~

- 使用預先訓練的 model
~~~bash
$> python gui.py -t ./model/ac-96/model-gamma-3500.meta -m model-gamma.py
~~~

- 使用 TensorBoard 查看結果
~~~bash
$> tensorboard --logdir ./model/model-gamma/run-{date}-{time}/
~~~
