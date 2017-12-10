# Multiple Linear regressing- backward Elimination
多個自變量X求一個應變量y

        Simple Linear Regression:       y=b0+b1*x1
        Multiple Linear Regression:(向量)    y=b0+b1*x1+b2*x2+...+bn*xn

範例: y=b0+b1*x1+b2*x2+ b3*x3+ b4*D1(將State改為一個虛擬變量)

 ![image](https://github.com/egroeglee/pictures/blob/master/MultipleLinearRegression/1.png)
 
        注意: (Dummy Variables Trap)虛擬變量陷阱(state:為名目尺度，所以要做分類數據處理)

訓練集處理完畢如下圖: 所以避免虛擬變量陷阱，需要刪除其中一列。 x = x[:, 1:]

  ![image](https://github.com/egroeglee/pictures/blob/master/MultipleLinearRegression/2.png)
  
預測結果與實際結果的比對

  ![image](https://github.com/egroeglee/pictures/blob/master/MultipleLinearRegression/3.png)
  
        下一步利用backward Elimination來找出最適合的自變量 (P value最低)
        
        y=b0+b1*x1+b2*x2+...+bn*xn
        b0是一個常數，但是這個函數不包含b0,我們要加入一個列axis=1 若加入行axis=0 (矩陣np.ones 40*1)，數值為1
        x_train = np.append(arr = np.ones((40,1)),values = x_train, axis =1)

  ![image](https://github.com/egroeglee/pictures/blob/master/MultipleLinearRegression/4.png)
  
        開始利用backward Elimination的方式一步一步篩選要剔除的自變量
        P Value最高的值(P>|t|)必須就在下一次的篩選中剔除(假設顯著性門檻值0.05)，下圖為X2 

  ![image](https://github.com/egroeglee/pictures/blob/master/MultipleLinearRegression/5.png)
  
        重複上述動作 直到找出最佳的P值(很小)

  ![image](https://github.com/egroeglee/pictures/blob/master/MultipleLinearRegression/6.png)
  
# 最終可證: RD的研發經費多寡會影響最後的收益。
