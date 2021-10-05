登录天池，可使用淘宝 & 支付宝登录，https://account.aliyun.com/login/login.htm

下载比赛数据集，https://tianchi.aliyun.com/competition/entrance/231784/information

配置本地Notebook环境

使用Pandas完成数据集读取（其中zip文件需要解压后读取）


```python
import pandas as pd
Train_data = pd.read_csv('data/used_car_train_20200313.csv', sep=' ')
Test_data = pd.read_csv('data/used_car_testB_20200421.csv', sep=' ')

```


```python
Train_data.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SaleID</th>
      <th>name</th>
      <th>regDate</th>
      <th>model</th>
      <th>brand</th>
      <th>bodyType</th>
      <th>fuelType</th>
      <th>gearbox</th>
      <th>power</th>
      <th>kilometer</th>
      <th>...</th>
      <th>v_5</th>
      <th>v_6</th>
      <th>v_7</th>
      <th>v_8</th>
      <th>v_9</th>
      <th>v_10</th>
      <th>v_11</th>
      <th>v_12</th>
      <th>v_13</th>
      <th>v_14</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>736</td>
      <td>20040402</td>
      <td>30.0</td>
      <td>6</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>60</td>
      <td>12.5</td>
      <td>...</td>
      <td>0.235676</td>
      <td>0.101988</td>
      <td>0.129549</td>
      <td>0.022816</td>
      <td>0.097462</td>
      <td>-2.881803</td>
      <td>2.804097</td>
      <td>-2.420821</td>
      <td>0.795292</td>
      <td>0.914762</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2262</td>
      <td>20030301</td>
      <td>40.0</td>
      <td>1</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>15.0</td>
      <td>...</td>
      <td>0.264777</td>
      <td>0.121004</td>
      <td>0.135731</td>
      <td>0.026597</td>
      <td>0.020582</td>
      <td>-4.900482</td>
      <td>2.096338</td>
      <td>-1.030483</td>
      <td>-1.722674</td>
      <td>0.245522</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14874</td>
      <td>20040403</td>
      <td>115.0</td>
      <td>15</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>163</td>
      <td>12.5</td>
      <td>...</td>
      <td>0.251410</td>
      <td>0.114912</td>
      <td>0.165147</td>
      <td>0.062173</td>
      <td>0.027075</td>
      <td>-4.846749</td>
      <td>1.803559</td>
      <td>1.565330</td>
      <td>-0.832687</td>
      <td>-0.229963</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>71865</td>
      <td>19960908</td>
      <td>109.0</td>
      <td>10</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>193</td>
      <td>15.0</td>
      <td>...</td>
      <td>0.274293</td>
      <td>0.110300</td>
      <td>0.121964</td>
      <td>0.033395</td>
      <td>0.000000</td>
      <td>-4.509599</td>
      <td>1.285940</td>
      <td>-0.501868</td>
      <td>-2.438353</td>
      <td>-0.478699</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>111080</td>
      <td>20120103</td>
      <td>110.0</td>
      <td>5</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>68</td>
      <td>5.0</td>
      <td>...</td>
      <td>0.228036</td>
      <td>0.073205</td>
      <td>0.091880</td>
      <td>0.078819</td>
      <td>0.121534</td>
      <td>-1.896240</td>
      <td>0.910783</td>
      <td>0.931110</td>
      <td>2.834518</td>
      <td>1.923482</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 31 columns</p>
</div>




```python
Test_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SaleID</th>
      <th>name</th>
      <th>regDate</th>
      <th>model</th>
      <th>brand</th>
      <th>bodyType</th>
      <th>fuelType</th>
      <th>gearbox</th>
      <th>power</th>
      <th>kilometer</th>
      <th>...</th>
      <th>v_5</th>
      <th>v_6</th>
      <th>v_7</th>
      <th>v_8</th>
      <th>v_9</th>
      <th>v_10</th>
      <th>v_11</th>
      <th>v_12</th>
      <th>v_13</th>
      <th>v_14</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>200000</td>
      <td>133777</td>
      <td>20000501</td>
      <td>67.0</td>
      <td>0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>101</td>
      <td>15.0</td>
      <td>...</td>
      <td>0.236520</td>
      <td>0.000241</td>
      <td>0.105319</td>
      <td>0.046233</td>
      <td>0.094522</td>
      <td>3.619512</td>
      <td>-0.280607</td>
      <td>-2.019761</td>
      <td>0.978828</td>
      <td>0.803322</td>
    </tr>
    <tr>
      <th>1</th>
      <td>200001</td>
      <td>61206</td>
      <td>19950211</td>
      <td>19.0</td>
      <td>6</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>73</td>
      <td>6.0</td>
      <td>...</td>
      <td>0.261518</td>
      <td>0.000000</td>
      <td>0.120323</td>
      <td>0.046784</td>
      <td>0.035385</td>
      <td>2.997376</td>
      <td>-1.406705</td>
      <td>-1.020884</td>
      <td>-1.349990</td>
      <td>-0.200542</td>
    </tr>
    <tr>
      <th>2</th>
      <td>200002</td>
      <td>67829</td>
      <td>20090606</td>
      <td>5.0</td>
      <td>5</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>120</td>
      <td>5.0</td>
      <td>...</td>
      <td>0.261691</td>
      <td>0.090836</td>
      <td>0.000000</td>
      <td>0.079655</td>
      <td>0.073586</td>
      <td>-3.951084</td>
      <td>-0.433467</td>
      <td>0.918964</td>
      <td>1.634604</td>
      <td>1.027173</td>
    </tr>
    <tr>
      <th>3</th>
      <td>200003</td>
      <td>8892</td>
      <td>20020601</td>
      <td>22.0</td>
      <td>9</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>58</td>
      <td>15.0</td>
      <td>...</td>
      <td>0.236050</td>
      <td>0.101777</td>
      <td>0.098950</td>
      <td>0.026830</td>
      <td>0.096614</td>
      <td>-2.846788</td>
      <td>2.800267</td>
      <td>-2.524610</td>
      <td>1.076819</td>
      <td>0.461610</td>
    </tr>
    <tr>
      <th>4</th>
      <td>200004</td>
      <td>76998</td>
      <td>20030301</td>
      <td>46.0</td>
      <td>6</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>116</td>
      <td>15.0</td>
      <td>...</td>
      <td>0.257000</td>
      <td>0.000000</td>
      <td>0.066732</td>
      <td>0.057771</td>
      <td>0.068852</td>
      <td>2.839010</td>
      <td>-1.659801</td>
      <td>-0.924142</td>
      <td>0.199423</td>
      <td>0.451014</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 30 columns</p>
</div>



任务2：对数据字段进行理解，并对特征字段依次进行数据分析

使用Pandas对比赛数据集进行分析
分析每个字段的取值、范围和类型结合比赛页面中具体字段的含义，对字段的取值分布进行分析

2.1 查看数据结构


```python
Train_data.info()
Test_data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 150000 entries, 0 to 149999
    Data columns (total 31 columns):
     #   Column             Non-Null Count   Dtype  
    ---  ------             --------------   -----  
     0   SaleID             150000 non-null  int64  
     1   name               150000 non-null  int64  
     2   regDate            150000 non-null  int64  
     3   model              149999 non-null  float64
     4   brand              150000 non-null  int64  
     5   bodyType           145494 non-null  float64
     6   fuelType           141320 non-null  float64
     7   gearbox            144019 non-null  float64
     8   power              150000 non-null  int64  
     9   kilometer          150000 non-null  float64
     10  notRepairedDamage  150000 non-null  object 
     11  regionCode         150000 non-null  int64  
     12  seller             150000 non-null  int64  
     13  offerType          150000 non-null  int64  
     14  creatDate          150000 non-null  int64  
     15  price              150000 non-null  int64  
     16  v_0                150000 non-null  float64
     17  v_1                150000 non-null  float64
     18  v_2                150000 non-null  float64
     19  v_3                150000 non-null  float64
     20  v_4                150000 non-null  float64
     21  v_5                150000 non-null  float64
     22  v_6                150000 non-null  float64
     23  v_7                150000 non-null  float64
     24  v_8                150000 non-null  float64
     25  v_9                150000 non-null  float64
     26  v_10               150000 non-null  float64
     27  v_11               150000 non-null  float64
     28  v_12               150000 non-null  float64
     29  v_13               150000 non-null  float64
     30  v_14               150000 non-null  float64
    dtypes: float64(20), int64(10), object(1)
    memory usage: 35.5+ MB
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 50000 entries, 0 to 49999
    Data columns (total 30 columns):
     #   Column             Non-Null Count  Dtype  
    ---  ------             --------------  -----  
     0   SaleID             50000 non-null  int64  
     1   name               50000 non-null  int64  
     2   regDate            50000 non-null  int64  
     3   model              50000 non-null  float64
     4   brand              50000 non-null  int64  
     5   bodyType           48496 non-null  float64
     6   fuelType           47076 non-null  float64
     7   gearbox            48032 non-null  float64
     8   power              50000 non-null  int64  
     9   kilometer          50000 non-null  float64
     10  notRepairedDamage  50000 non-null  object 
     11  regionCode         50000 non-null  int64  
     12  seller             50000 non-null  int64  
     13  offerType          50000 non-null  int64  
     14  creatDate          50000 non-null  int64  
     15  v_0                50000 non-null  float64
     16  v_1                50000 non-null  float64
     17  v_2                50000 non-null  float64
     18  v_3                50000 non-null  float64
     19  v_4                50000 non-null  float64
     20  v_5                50000 non-null  float64
     21  v_6                50000 non-null  float64
     22  v_7                50000 non-null  float64
     23  v_8                50000 non-null  float64
     24  v_9                50000 non-null  float64
     25  v_10               50000 non-null  float64
     26  v_11               50000 non-null  float64
     27  v_12               50000 non-null  float64
     28  v_13               50000 non-null  float64
     29  v_14               50000 non-null  float64
    dtypes: float64(20), int64(9), object(1)
    memory usage: 11.4+ MB
    

数据一共30列，其中未知列有15列


```python
# 查看有缺失值情况
Train_data.isnull().sum()

```




    SaleID                  0
    name                    0
    regDate                 0
    model                   1
    brand                   0
    bodyType             4506
    fuelType             8680
    gearbox              5981
    power                   0
    kilometer               0
    notRepairedDamage       0
    regionCode              0
    seller                  0
    offerType               0
    creatDate               0
    price                   0
    v_0                     0
    v_1                     0
    v_2                     0
    v_3                     0
    v_4                     0
    v_5                     0
    v_6                     0
    v_7                     0
    v_8                     0
    v_9                     0
    v_10                    0
    v_11                    0
    v_12                    0
    v_13                    0
    v_14                    0
    dtype: int64




```python
# 训练数据缺失情况
missing = Train_data.isnull().sum()
missing = missing[missing>0]
missing
import matplotlib.pyplot as plt
p1=plt.bar(missing.index,missing.values)
plt.bar_label(p1,label_type='edge')

```




    [Text(0, 0, '1'), Text(0, 0, '4506'), Text(0, 0, '8680'), Text(0, 0, '5981')]




    
![png](output_13_1.png)
    



```python
# 测试数据缺失情况
missing = Test_data.isnull().sum()
missing = missing[missing>0]
missing
p = plt.bar(missing.index,missing.values)
plt.bar_label(p,label_type='edge')

```




    [Text(0, 0, '1504'), Text(0, 0, '2924'), Text(0, 0, '1968')]




    
![png](output_14_1.png)
    



```python

```


```python
Train_data.describe()
Test_data.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SaleID</th>
      <th>name</th>
      <th>regDate</th>
      <th>model</th>
      <th>brand</th>
      <th>bodyType</th>
      <th>fuelType</th>
      <th>gearbox</th>
      <th>power</th>
      <th>kilometer</th>
      <th>...</th>
      <th>v_5</th>
      <th>v_6</th>
      <th>v_7</th>
      <th>v_8</th>
      <th>v_9</th>
      <th>v_10</th>
      <th>v_11</th>
      <th>v_12</th>
      <th>v_13</th>
      <th>v_14</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>5.000000e+04</td>
      <td>50000.00000</td>
      <td>50000.000000</td>
      <td>48496.000000</td>
      <td>47076.000000</td>
      <td>48032.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>...</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
      <td>50000.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>224999.500000</td>
      <td>68505.606100</td>
      <td>2.003401e+07</td>
      <td>47.64948</td>
      <td>8.087140</td>
      <td>1.793736</td>
      <td>0.376498</td>
      <td>0.226953</td>
      <td>119.766960</td>
      <td>12.598260</td>
      <td>...</td>
      <td>0.248147</td>
      <td>0.044624</td>
      <td>0.124693</td>
      <td>0.058198</td>
      <td>0.062113</td>
      <td>0.019633</td>
      <td>0.002759</td>
      <td>0.004342</td>
      <td>0.004570</td>
      <td>-0.007209</td>
    </tr>
    <tr>
      <th>std</th>
      <td>14433.901067</td>
      <td>61032.124271</td>
      <td>5.351615e+04</td>
      <td>49.90741</td>
      <td>7.899648</td>
      <td>1.764970</td>
      <td>0.549281</td>
      <td>0.418866</td>
      <td>206.313348</td>
      <td>3.912519</td>
      <td>...</td>
      <td>0.045836</td>
      <td>0.051664</td>
      <td>0.201440</td>
      <td>0.029171</td>
      <td>0.035723</td>
      <td>3.764095</td>
      <td>3.289523</td>
      <td>2.515912</td>
      <td>1.287194</td>
      <td>1.044718</td>
    </tr>
    <tr>
      <th>min</th>
      <td>200000.000000</td>
      <td>1.000000</td>
      <td>1.991000e+07</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.500000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-9.119719</td>
      <td>-5.662163</td>
      <td>-8.291868</td>
      <td>-4.157649</td>
      <td>-6.098192</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>212499.750000</td>
      <td>11315.000000</td>
      <td>1.999100e+07</td>
      <td>11.00000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>75.000000</td>
      <td>12.500000</td>
      <td>...</td>
      <td>0.243436</td>
      <td>0.000035</td>
      <td>0.062519</td>
      <td>0.035413</td>
      <td>0.033880</td>
      <td>-3.675196</td>
      <td>-1.963928</td>
      <td>-1.865406</td>
      <td>-1.048722</td>
      <td>-0.440706</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>224999.500000</td>
      <td>52215.000000</td>
      <td>2.003091e+07</td>
      <td>30.00000</td>
      <td>6.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>110.000000</td>
      <td>15.000000</td>
      <td>...</td>
      <td>0.257818</td>
      <td>0.000801</td>
      <td>0.095880</td>
      <td>0.056804</td>
      <td>0.058749</td>
      <td>1.632134</td>
      <td>-0.375537</td>
      <td>-0.138943</td>
      <td>-0.036352</td>
      <td>0.136849</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>237499.250000</td>
      <td>118710.750000</td>
      <td>2.007110e+07</td>
      <td>66.00000</td>
      <td>13.000000</td>
      <td>3.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>150.000000</td>
      <td>15.000000</td>
      <td>...</td>
      <td>0.265263</td>
      <td>0.101654</td>
      <td>0.125470</td>
      <td>0.079387</td>
      <td>0.087624</td>
      <td>2.846205</td>
      <td>1.263451</td>
      <td>1.775632</td>
      <td>0.945239</td>
      <td>0.685555</td>
    </tr>
    <tr>
      <th>max</th>
      <td>249999.000000</td>
      <td>196808.000000</td>
      <td>2.015121e+07</td>
      <td>246.00000</td>
      <td>39.000000</td>
      <td>7.000000</td>
      <td>6.000000</td>
      <td>1.000000</td>
      <td>19211.000000</td>
      <td>15.000000</td>
      <td>...</td>
      <td>0.291176</td>
      <td>0.153403</td>
      <td>1.411559</td>
      <td>0.157458</td>
      <td>0.211304</td>
      <td>12.177864</td>
      <td>18.789496</td>
      <td>13.384828</td>
      <td>5.635374</td>
      <td>2.649768</td>
    </tr>
  </tbody>
</table>
<p>8 rows × 29 columns</p>
</div>



2.2 查看数据异常值


```python
Train_data['notRepairedDamage'].value_counts()
Test_data['notRepairedDamage'].value_counts()
import numpy as np
Train_data['notRepairedDamage'].replace('-',np.nan,inplace = True)
Train_data['notRepairedDamage'].value_counts()
# 空值率
Train_data['notRepairedDamage'].isnull().sum()/len(Train_data['notRepairedDamage'])
```




    0.16216




```python
Test_data['notRepairedDamage'].replace('-',np.nan,inplace = True)
Test_data['notRepairedDamage'].value_counts()
Test_data['notRepairedDamage'].isnull().sum()/len(Train_data['notRepairedDamage'])
```




    0.05379333333333333




```python
name_p=Train_data['name'].value_counts()
# p1=plt.bar(name_p.index,name_p.values)


```


```python

```


```python
Train_data['regDate'].value_counts()
```




    20000008    180
    20000011    158
    20000010    157
    20000004    157
    20000002    155
               ... 
    20151201      1
    20140009      1
    20151106      1
    19910902      1
    19911211      1
    Name: regDate, Length: 3894, dtype: int64




```python
Train_data['model'].value_counts()
```




    0.0      11762
    19.0      9573
    4.0       8445
    1.0       6038
    29.0      5186
             ...  
    240.0        2
    209.0        2
    245.0        2
    242.0        2
    247.0        1
    Name: model, Length: 248, dtype: int64




```python
Train_data['brand'].value_counts()
```




    0     31480
    4     16737
    14    16089
    10    14249
    1     13794
    6     10217
    9      7306
    5      4665
    13     3817
    11     2945
    3      2461
    7      2361
    16     2223
    8      2077
    25     2064
    27     2053
    21     1547
    15     1458
    19     1388
    20     1236
    12     1109
    22     1085
    26      966
    30      940
    17      913
    24      772
    28      649
    32      592
    29      406
    37      333
    2       321
    31      318
    18      316
    36      228
    34      227
    33      218
    23      186
    35      180
    38       65
    39        9
    Name: brand, dtype: int64




```python
Train_data['bodyType'].value_counts()
```




    0.0    41420
    1.0    35272
    2.0    30324
    3.0    13491
    4.0     9609
    5.0     7607
    6.0     6482
    7.0     1289
    Name: bodyType, dtype: int64




```python
Train_data['fuelType'].value_counts()
```




    0.0    91656
    1.0    46991
    2.0     2212
    3.0      262
    4.0      118
    5.0       45
    6.0       36
    Name: fuelType, dtype: int64




```python
Train_data['gearbox'].value_counts()
```




    0.0    111623
    1.0     32396
    Name: gearbox, dtype: int64




```python
Train_data['power'].value_counts()
```




    0       12829
    75       9593
    150      6495
    60       6374
    140      5963
            ...  
    513         1
    1993        1
    19          1
    751         1
    549         1
    Name: power, Length: 566, dtype: int64




```python
Train_data['kilometer'].value_counts()
```




    15.0    96877
    12.5    15722
    10.0     6459
    9.0      5257
    8.0      4573
    7.0      4084
    6.0      3725
    5.0      3144
    4.0      2718
    3.0      2501
    2.0      2354
    0.5      1840
    1.0       746
    Name: kilometer, dtype: int64




```python
Train_data['regionCode'].value_counts()
```




    419     369
    764     258
    125     137
    176     136
    462     134
           ... 
    6377      1
    7994      1
    7973      1
    7975      1
    8117      1
    Name: regionCode, Length: 7905, dtype: int64




```python
Train_data['seller'].value_counts()
# 数据严重倾斜，可删除
```




    0    149999
    1         1
    Name: seller, dtype: int64




```python
Train_data['offerType'].value_counts()
# 数据严重倾斜，可删除
```




    0    150000
    Name: offerType, dtype: int64




```python
Train_data['creatDate'].value_counts()
```




    20160403    5848
    20160404    5606
    20160320    5485
    20160312    5383
    20160402    5382
                ... 
    20160130       1
    20150909       1
    20150810       1
    20160213       1
    20151227       1
    Name: creatDate, Length: 96, dtype: int64




```python
Train_data['price'].value_counts()
```




    500      2337
    1500     2158
    1200     1922
    1000     1850
    2500     1821
             ... 
    9395        1
    81900       1
    16699       1
    11998       1
    14780       1
    Name: price, Length: 3763, dtype: int64




```python
del Train_data["seller"]
del Train_data["offerType"]
del Test_data["seller"]
del Test_data["offerType"]
# Train_data.drop('seller',inplace=True) 

```


```python
# 了解预测值的分布
import scipy.stats as st
import seaborn as sns
price_p = Train_data['price']
plt.figure(1);plt.title('johnsom SU')
sns.distplot(price_p,kde=False,fit=st.johnsonsu)
plt.figure(2);plt.title('normal')
sns.distplot(price_p,kde=False,fit=st.norm)
plt.figure(3);plt.title('log normal')
sns.distplot(price_p,kde=False,fit=st.lognorm)

```

    D:\ProgramData\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    D:\ProgramData\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    D:\ProgramData\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    




    <AxesSubplot:title={'center':'log normal'}, xlabel='price'>




    
![png](output_36_2.png)
    



    
![png](output_36_3.png)
    



    
![png](output_36_4.png)
    



```python
# 查看偏度和峰度
# import matplotlib.pyplot as plt
# help(plt.dist)
sns.distplot(Train_data['price'])
print('偏度：',Train_data['price'].skew())
print('峰度：',Train_data['price'].kurt())
```

    D:\ProgramData\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    

    偏度： 3.3464867626369608
    峰度： 18.995183355632562
    


    
![png](output_37_2.png)
    



```python

Train_data.skew(),Train_data.kurt()
```




    (SaleID                0.000000
     name                  0.557606
     regDate               0.028495
     model                 1.484388
     brand                 1.150760
     bodyType              0.991530
     fuelType              1.595486
     gearbox               1.317514
     power                65.863178
     kilometer            -1.525921
     notRepairedDamage     2.430640
     regionCode            0.688881
     creatDate           -79.013310
     price                 3.346487
     v_0                  -1.316712
     v_1                   0.359454
     v_2                   4.842556
     v_3                   0.106292
     v_4                   0.367989
     v_5                  -4.737094
     v_6                   0.368073
     v_7                   5.130233
     v_8                   0.204613
     v_9                   0.419501
     v_10                  0.025220
     v_11                  3.029146
     v_12                  0.365358
     v_13                  0.267915
     v_14                 -1.186355
     dtype: float64,
     SaleID                 -1.200000
     name                   -1.039945
     regDate                -0.697308
     model                   1.740483
     brand                   1.076201
     bodyType                0.206937
     fuelType                5.880049
     gearbox                -0.264161
     power                5733.451054
     kilometer               1.141934
     notRepairedDamage       3.908072
     regionCode             -0.340832
     creatDate            6881.080328
     price                  18.995183
     v_0                     3.993841
     v_1                    -1.753017
     v_2                    23.860591
     v_3                    -0.418006
     v_4                    -0.197295
     v_5                    22.934081
     v_6                    -1.742567
     v_7                    25.845489
     v_8                    -0.636225
     v_9                    -0.321491
     v_10                   -0.577935
     v_11                   12.568731
     v_12                    0.268937
     v_13                   -0.438274
     v_14                    2.393526
     dtype: float64)




```python
# 查看预测值的频数
plt.hist(Train_data['price'],bins=None)
```




    (array([1.23906e+05, 1.89270e+04, 4.91800e+03, 1.34000e+03, 4.71000e+02,
            1.88000e+02, 1.24000e+02, 6.00000e+01, 4.80000e+01, 1.80000e+01]),
     array([1.10000e+01, 1.00098e+04, 2.00086e+04, 3.00074e+04, 4.00062e+04,
            5.00050e+04, 6.00038e+04, 7.00026e+04, 8.00014e+04, 9.00002e+04,
            9.99990e+04]),
     <BarContainer object of 10 artists>)




    
![png](output_39_1.png)
    



```python
plt.hist(np.log(Train_data['price']),bins=None)
```




    (array([   56.,   223.,  1508.,  6232., 22319., 35387., 39059., 33184.,
            11123.,   909.]),
     array([ 2.39789527,  3.30939729,  4.22089931,  5.13240133,  6.04390335,
             6.95540537,  7.86690739,  8.77840941,  9.68991143, 10.60141345,
            11.51291546]),
     <BarContainer object of 10 artists>)




    
![png](output_40_1.png)
    


计算特征字段与标签的相关性



```python
# 提取数值类型特征值的名称
```


```python
numerical_col = Train_data.select_dtypes(exclude='object').columns

numerical_col

```




    Index(['SaleID', 'name', 'regDate', 'model', 'brand', 'bodyType', 'fuelType',
           'gearbox', 'power', 'kilometer', 'regionCode', 'creatDate', 'price',
           'v_0', 'v_1', 'v_2', 'v_3', 'v_4', 'v_5', 'v_6', 'v_7', 'v_8', 'v_9',
           'v_10', 'v_11', 'v_12', 'v_13', 'v_14'],
          dtype='object')




```python
object_col = Train_data.select_dtypes(include='object').columns
object_col
```




    Index(['notRepairedDamage'], dtype='object')




```python
# 特征分为类别特征和数字特征，对类别特征查看unique分布
```


```python
a=Train_data.corr()
np.abs(a['price']).sort_values(ascending = False)
```




    price         1.000000
    v_3           0.730946
    v_12          0.692823
    v_8           0.685798
    v_0           0.628397
    regDate       0.611959
    kilometer     0.440519
    gearbox       0.329075
    v_11          0.275320
    v_10          0.246175
    bodyType      0.241303
    power         0.219834
    v_9           0.206205
    fuelType      0.200536
    v_5           0.164317
    v_4           0.147085
    model         0.136983
    v_2           0.085322
    v_6           0.068970
    v_1           0.060914
    v_7           0.053024
    brand         0.043799
    v_14          0.035911
    regionCode    0.014036
    v_13          0.013993
    creatDate     0.002955
    name          0.002030
    SaleID        0.001043
    Name: price, dtype: float64



选择特征字段中与标签强相关的3个字段，绘制其余标签的分布关系图


```python
# 和price强相关的3个特征是v3,v12,v8
cor=Train_data[['price','v_3','v_12','v_8']].corr()
sns.heatmap(cor)
```




    <AxesSubplot:>




    
![png](output_48_1.png)
    



```python
numeric_features = ['power', 'kilometer', 'v_0', 'v_1', 'v_2', 'v_3', 'v_4', 'v_5', 'v_6', 'v_7', 'v_8', 'v_9', 'v_10', 'v_11', 'v_12', 'v_13','v_14']

categorical_features = ['name', 'model', 'brand', 'bodyType', 'fuelType', 'gearbox', 'notRepairedDamage', 'regionCode']
```


```python
for i in categorical_features:
    
    n = Train_data[i].value_counts()
    print(i + "的特征分布如下：")
    print('{}有{} 个不同值：'.format(i,Train_data[i].nunique()))
    print(n)

```

    name的特征分布如下：
    name有99662 个不同值：
    708       282
    387       282
    55        280
    1541      263
    203       233
             ... 
    119983      1
    63443       1
    104410      1
    154956      1
    177672      1
    Name: name, Length: 99662, dtype: int64
    model的特征分布如下：
    model有248 个不同值：
    0.0      11762
    19.0      9573
    4.0       8445
    1.0       6038
    29.0      5186
             ...  
    240.0        2
    209.0        2
    245.0        2
    242.0        2
    247.0        1
    Name: model, Length: 248, dtype: int64
    brand的特征分布如下：
    brand有40 个不同值：
    0     31480
    4     16737
    14    16089
    10    14249
    1     13794
    6     10217
    9      7306
    5      4665
    13     3817
    11     2945
    3      2461
    7      2361
    16     2223
    8      2077
    25     2064
    27     2053
    21     1547
    15     1458
    19     1388
    20     1236
    12     1109
    22     1085
    26      966
    30      940
    17      913
    24      772
    28      649
    32      592
    29      406
    37      333
    2       321
    31      318
    18      316
    36      228
    34      227
    33      218
    23      186
    35      180
    38       65
    39        9
    Name: brand, dtype: int64
    bodyType的特征分布如下：
    bodyType有8 个不同值：
    0.0    41420
    1.0    35272
    2.0    30324
    3.0    13491
    4.0     9609
    5.0     7607
    6.0     6482
    7.0     1289
    Name: bodyType, dtype: int64
    fuelType的特征分布如下：
    fuelType有7 个不同值：
    0.0    91656
    1.0    46991
    2.0     2212
    3.0      262
    4.0      118
    5.0       45
    6.0       36
    Name: fuelType, dtype: int64
    gearbox的特征分布如下：
    gearbox有2 个不同值：
    0.0    111623
    1.0     32396
    Name: gearbox, dtype: int64
    notRepairedDamage的特征分布如下：
    notRepairedDamage有2 个不同值：
    0.0    111361
    1.0     14315
    Name: notRepairedDamage, dtype: int64
    regionCode的特征分布如下：
    regionCode有7905 个不同值：
    419     369
    764     258
    125     137
    176     136
    462     134
           ... 
    6377      1
    7994      1
    7973      1
    7975      1
    8117      1
    Name: regionCode, Length: 7905, dtype: int64
    


```python
Train_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SaleID</th>
      <th>name</th>
      <th>regDate</th>
      <th>model</th>
      <th>brand</th>
      <th>bodyType</th>
      <th>fuelType</th>
      <th>gearbox</th>
      <th>power</th>
      <th>kilometer</th>
      <th>...</th>
      <th>v_5</th>
      <th>v_6</th>
      <th>v_7</th>
      <th>v_8</th>
      <th>v_9</th>
      <th>v_10</th>
      <th>v_11</th>
      <th>v_12</th>
      <th>v_13</th>
      <th>v_14</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>736</td>
      <td>20040402</td>
      <td>30.0</td>
      <td>6</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>60</td>
      <td>12.5</td>
      <td>...</td>
      <td>0.235676</td>
      <td>0.101988</td>
      <td>0.129549</td>
      <td>0.022816</td>
      <td>0.097462</td>
      <td>-2.881803</td>
      <td>2.804097</td>
      <td>-2.420821</td>
      <td>0.795292</td>
      <td>0.914762</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2262</td>
      <td>20030301</td>
      <td>40.0</td>
      <td>1</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>15.0</td>
      <td>...</td>
      <td>0.264777</td>
      <td>0.121004</td>
      <td>0.135731</td>
      <td>0.026597</td>
      <td>0.020582</td>
      <td>-4.900482</td>
      <td>2.096338</td>
      <td>-1.030483</td>
      <td>-1.722674</td>
      <td>0.245522</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14874</td>
      <td>20040403</td>
      <td>115.0</td>
      <td>15</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>163</td>
      <td>12.5</td>
      <td>...</td>
      <td>0.251410</td>
      <td>0.114912</td>
      <td>0.165147</td>
      <td>0.062173</td>
      <td>0.027075</td>
      <td>-4.846749</td>
      <td>1.803559</td>
      <td>1.565330</td>
      <td>-0.832687</td>
      <td>-0.229963</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>71865</td>
      <td>19960908</td>
      <td>109.0</td>
      <td>10</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>193</td>
      <td>15.0</td>
      <td>...</td>
      <td>0.274293</td>
      <td>0.110300</td>
      <td>0.121964</td>
      <td>0.033395</td>
      <td>0.000000</td>
      <td>-4.509599</td>
      <td>1.285940</td>
      <td>-0.501868</td>
      <td>-2.438353</td>
      <td>-0.478699</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>111080</td>
      <td>20120103</td>
      <td>110.0</td>
      <td>5</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>68</td>
      <td>5.0</td>
      <td>...</td>
      <td>0.228036</td>
      <td>0.073205</td>
      <td>0.091880</td>
      <td>0.078819</td>
      <td>0.121534</td>
      <td>-1.896240</td>
      <td>0.910783</td>
      <td>0.931110</td>
      <td>2.834518</td>
      <td>1.923482</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 29 columns</p>
</div>


