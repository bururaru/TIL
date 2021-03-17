### 학습 관련 용어 정리

- Accuracy (맞게 예출한 비율)
- Precision (P로 예측한 것 중 실제 P의 비율)
- Sensitivity(Recall) (실제 P를 P로 예측)
- Specificity (실제 N을 N로 예측)
- Error (잘못 예측한 비율)
- F1 Score (precision과 recall의 평균)









## Scikit-learn

#### DecisionTreeClassifier

파라미터

- min_samples_split : 노드를 분리하기 위한 최소한의 샘플 수( 과적합 제어 )  기본값은 2
- min_samples_leaf : leaf 노드가 되기 위한 최소 샘플의 수 지정
- max_features : 
- max_depth : 트리의 최대 깊이
- max_leaf_nodes : 리프노드의 최대 수



#### GridSearchCv : 교차검증과 hyper parameter 탐색을 동시에 진행할 수 있음

파라미터

- estimator : 어떤 분류 알고리즘을 사용할것인가?
- param_grid : {param : value, param : value}
- scoring : 평가 방법을 지정
- refit : True -> 최적의 hyper parameter를 찾는 재학습 과정 진행



### LogisticRegression

파라미터

- max_iter : 반복 횟수

```python
from sklearn.linear_model import LogisticRegression

X_train,X_test,y_train,y_test = train_test_split(cancer.data,cancer.target)

model = LogisticRegression(max_iter=10000)
model.fit(X_train,y_train)

score = model.score(X_test,y_test)         #predict 없이 .score로 바로 정확도 확인
```





#### KFold, StratifiedKFold

파라미터

- n_splits : 몇개로 나눌것인가?

- random_state : random seed

- shuffle : 나누기 전에 섞을것인가? (기본값 True)

  ```python
  fold = StratifiedKFold(n_splits=20,
               random_state = 10,
               shuffle = True)
  ```

KFold : 그냥 아무생값없이 데이터 나눔

StratifiedKFold : 원본 데이터와 나누어진 후의 데이터의 Label 비율이 동일하게 나눔



#### cross_validate

파라미터

- estimator : 예측 모델

- X : feature data 세트

- y : label data 세트

- cv : 교차검증 폴드 수

- scoring : 지정된 파라미터 값에 맞게 성능 지표를 배열 형태로 반환

  ```python
  result = cross_validate(model, X_train, y_train, cv=fold, scoring= scoring)
  ```

  



#### Data encoding

##### label encoding 

숫자에 따라 가중치가 부여되는 알고리즘에서는 사용하면 안된다.

```python
from sklearn.preprocessing import LabelEncoder

items = ['TV', '냉장고', '전자렌지', '컴퓨터', '선풍기', '선풍기', '믹서', '믹서']

encoder = LabelEncoder()
encoder.fit(items)
labels = encoder.transform(items)
# labels : [0 1 4 5 3 3 2 2]
```



##### one-hot encoding

입력 데이터가 2차원 형식이어야 한다.

```python
items = pd.DataFrame(['TV', '냉장고', '전자렌지', '컴퓨터', '선풍기', '선풍기', '믹서', '믹서'], columns=['items'])

pd.get_dummies(items)
```

