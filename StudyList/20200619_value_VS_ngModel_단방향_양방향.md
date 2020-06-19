# 앵귤러 value VS ngModel (단방향,양방향)

1. 엥귤러 데이터 바인딩하다보니, value , ngModel 둘다 써도 되는데, ngModel과의 차이점을 찾아봄   
  > value는 단방향, ngModel은 양방향 이란다..   
  > 단방향은 값을 한번 던져주고, 끝이고,   
  > 양방향은 데이터값을 바꿨을때, 다른부분도 그 값에 맞게 변경이 된다.   
2. Value 단방향
```JavaScript
<mat-card>
  <mat-card-content>
    <h2></h2>
    <section>
      <mat-radio-group [value]='color'>
        <mat-radio-button value="primary">Primary</mat-radio-button><br>
        <mat-radio-button value="accent">Accent</mat-radio-button><br>
        <mat-radio-button value="warn">Warn</mat-radio-button>
      </mat-radio-group>
    </section>
  </mat-card-content>
</mat-card>
<mat-card>
  <mat-card-content>
    <h2>Result</h2>
    <mat-progress-spinner [color]="color" [value]="value"></mat-progress-spinner>
  </mat-card-content>
</mat-card>
```

3.ngModel 양방향
```JavaScript
<mat-card>
  <mat-card-content>
    <h2></h2>
    <section>
      <mat-radio-group [(ngModel)]='color'>
        <mat-radio-button value="primary">Primary</mat-radio-button><br>
        <mat-radio-button value="accent">Accent</mat-radio-button><br>
        <mat-radio-button value="warn">Warn</mat-radio-button>
      </mat-radio-group>
    </section>
  </mat-card-content>
</mat-card>
<mat-card>
  <mat-card-content>
    <h2>Result</h2>
    <mat-progress-spinner [color]="color" [value]="value"></mat-progress-spinner>
  </mat-card-content>
</mat-card>
 ```
-------------------
* 양방향으로 하면, 위에 radio버튼이 바뀌었을때, 밑에 색깔도 변경되는것을 볼 수있다.
  - 양방향 바인딩을 하면 html에서 값을 변경하면, ts파일의 값도 변한다.

참고 : https://myjamong.tistory.com/30
