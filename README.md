# FDA_HW3-1 Report

#### 1. How did you preprocess this dataset?
因為資料中的變數都是時序資料，所以我對Open Price、Close Price、High Price、Low Price這四個變數，當日與前一天的數據做一階差分作為變數，並且將當日的Open Price與Close Price的差做為新的變數(move)，最後以Close Price當日與隔天數據的一階差分的正負項作為反應變數(y)。

#### 2. Which classifier reaches the highest classification accuracy in this dataset? Why ? Can this result remain if the dataset is different?

|model|train acc|test acc|
|-|-|-|
|Logistic Regression|0.5460|0.5400|
|Neural Network|0.5597|0.5480|
|LinearSVC|0.5433|0.5480|
|Ensemble|0.5561|**0.5760**|

- 除了Logistic Regression和|Neural Network以外，我選擇的分類器為LinearSVC，test accuracy最佳的模型為NN和LinearSVC，準確度皆為0.5480，但實際上三個模型在預測能力上沒有太大的差異。
- 考慮到三個模型的train accuracy與test accuracy都沒有很大的差異，所以沒有overfitting的問題，並且三個模型的預測能力相當，有嘗試二階差分但沒有進步，我認為這些變數的預測能力大約就在0.54左右，所以要提升準確度可以需要額外的資訊，例如市場指標或是國際金融的資訊。
- 也因為變數沒有很複雜，所以很難看出三個模型在時序資料上的配適能力。所以如果資料集改變，我想並不是三個模型都有相當的預測能力。

#### 3. How did you improve your classifiers ?
我將三個模型的預測結果做weighted sum，並且得到0.576的test accuracy，明顯優於三個模型分別預測的結果。
