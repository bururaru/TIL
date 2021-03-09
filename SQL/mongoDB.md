## mongoDB

cmd 실행 : `mongod --dbpath c:\mongo\data\db`



### Not Only SQl (NoSQL)

- 특징
  - 정해진 규칙이 없다 (Schema X)
  - JOIN X
  - key / value 로 이루어진 데이터를 담는다
  - Database -> collection(table) -> document(row)



#### shell 명령어

- `show dbs` : db 목록 표시

- `use 'db_name'` : 사용할 db 지정

- `db` : 

- `db.createCollection('collection_name')` : 새로운 collection 생성

- `db.collection_name.insertOne()` : 새로운 데이터 추가

  ```shell
  db.collection_name.insertOne(       # 데이터 한개 추가
  {
     user_id : 'jslim',
     gender : 'm' 
  })
  
  db.collection_name.insertMany(      #여러게 추가 (리스트 형식으로 딕셔너리 묶어서)
  [{
     user_id : 'jslim',
     gender : 'm' 
  }, 
  {
     user_id : 'jslim2',
     gender : 'f' 
  }])
  ```

- `db.collection_name.find({}, {user_id : 1})` : 특정 데이터만 불러오기

  ``` shell
  db.collection_name.find({}) #전체 데이터 가져오기
  
  db.collection_name.find({}, {user_id : 1})  #user_id 만 가져오기
  
  db.collection_name.find({gender : 'm'}, {})  #gender 가 m인 데이터만 가져오기
  
  db.collection_name.find({gender : 'm', user_id : 'jslim'}, {})  #gender 가 m 이고, user_id 가 jslim인 데이터만 가져오기 (AND)
  
  db.collection_name.find({$or : [{gender : 'm'}, {user_id : 'jslim'}]}, {})  #gender 가 m 이거나, user_id 가 jslim인 데이터만 가져오기 (OR)
  ```

- 수정

  ```shell
  db.collection_name.updateOne({where}, {set})
  
  db.collection_name.updateOne({user_id : 'jslim'}, {$set : {gender: 'f'} }) #user_id 가 jslim 인 데이터를 찾아서 gender를 f로 수정
  
  db.collection_name_updateMany({where}, {set})
  ```

  

- 삭제

  ```shell
  db.collection_name.removeOne({where})   # 조건에 맞는 데이터 삭제
  db.collection_name.removeMany({})       # 전체 삭제
  ```

  

#### jupyter 사용

- connection mongoDB

  ```python
  #local
  conn = mongo.MongoClient()
  #remote
  conn = mongo.MongoClient(server, 27017)
  ```

- database create

  ```python
  articleDB = conn.articleDB      #이름이 articleDB인 DB 생성 후 변수에 할당
  
  articleCollection = articleDB['article']   #이름이 article인 Collection 생성 후 변수에 할당
  ```

- document insert

  ```python
  articleCollection.insert_one()            #파이썬에서 할당한 변수에 붙여서 사용
  articleCollection.insert_many()
  ```

- document 탐색

  ```python
  cursor = articleCollection.find()
  for doc in cursor:
      print(doc)
      
  cursor = articleCollection.find({'author':'campus','view' : {'$gte' :100}}) #100이상이면서 author가 일치하는 데이터 탐색
  
  cursor = articleCollection.find({'author':'campus','view' : {'$gte' :100}}, {'author': 1})  #조건에 맞는 데이터중 author column만 가져오기(id 포함)
  
  cursor = articleCollection.find({'author':'campus','view' : {'$gte' :100}}, {'author': 1, '_id' : 0}) #조건에 맞는 데이터중 author column만 가져오기
  ```

- document 수정

  ```python
  articleCollection.update_one({'author':'campus'}, {'$set' : {'view': 150}})
  # $set 사용해서 변경
  
  articleCollection.update_many()
  ```

- document 삭제

  ```python
  articleCollection.delete_one({'author':'campus'})
  
  articleCollection.delete_many()
  ```

  

