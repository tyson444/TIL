#앵귤러 쿼리방법
- 앵귤러, 몽고DB사용중인데, RDB처럼 join쿼리를 만들어서 직접 만들어서 조회하는게 아니고, DB를 객체로 만들어서 조회한다고 생각하면 된다.
- JPA랑 같은 방법이다. 그래서 모델 객체를 만들고, 거기에서 필요한 조건식으로 찾으면 되는데, 기본적으로 사용하는 것에 대해서 작성해보겠다.

* book이란 모델이 있고, 가져올때 방법

```JavaScript
const books = await this.bookModel.find().sort({CreatedDate:-1}).limit(10).exec();
```
이렇게 하면, book모델에서 전체를 검색하고, CreatedDate역순으로 정렬후, 10개의 데이터만 가져온다는 말이다.
  > find() : 찾기   
  > sort() : 정렬   
  > limet() : 제한갯d수   
  > exec() : 실행   

*좀 더 자세히 조회할때 find() 안에 조건식을 넣어주면 되다.
```JavaScript
const books = await this.bookModel.find({
                status:'Published',
                $and:[
                     {PublishedDate: { $gte: moment.utc().add( -30, 'day').toDate() } },
                     {PublishedDate: { $lte: moment.utc().add( +30, 'day').toDate() } },
                ],
              })
              .sort({CreatedDate:-1})
              .limit(10)
              .exec();
```
위 같은 경우는 stuatus값이 "published'이고, $and값으로 publishedDate(출판일)일은 UTC로 변경해서 오늘날짜의 -30에서 +30일 이내의 것만 가져오는 거다.
  > {}안에 key:value 로 검색하고, 구분은 , 로 해준다.   
  > and 조건식은 $and 
  > $gte: 이상
  > $lte: 이하   
Moment같은 경우는 다음에 다루도록하겠다.

*쿼리 옵션
  > $lt : 미만   
  > $lte : 이하   
  > $gt : 초과   
  > $gte : 이상   
  > $in : 특정key값이 포함된것들 {$in:["actor","developer"]}
  
