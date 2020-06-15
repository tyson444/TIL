#앵귤러 셀렉트 박스 목록 가져오기

1. 기본방법
- html에 직접 select 목록 넣는방법
```html
    <mat-form-field>
      <mat-select name="countryString" [(value)]="selectedCountry" placeholder="Country">
        <mat-option [value]="'GB'">Great Britain</mat-option>
        <mat-option [value]="'US'">United States</mat-option>
        <mat-option [value]="'CA'">Canada</mat-option>
      </mat-select>
    </mat-form-field>
```
   
   

2. component에서 Array관리
- 국가 목록 같은 경우는 공통으로 사용할거 같아서, html에 직접 쓰는것보다, array로 관리하는게 나을거 같아서, 작성해보았다.

    > Component 파일
    ```JavaScript
    //인터페이스 선언
    interface Country {
        value: string;
        viewValue: string;
        }

    //목록 Array 작성
    countries: Country[] = [
        {value: 'KR', viewValue: '한국'},
        {value: 'JP', viewValue: '일본'},
        {value: 'US', viewValue: '미국'},
        {value: 'CH', viewValue: '스위스'},
        {value: 'SE', viewValue: '스웨덴'},
        {value: 'DE', viewValue: '독일'},
    ];    
    ```
    >HTML 파일(프론트)
    ```html
            <div class="w-1/6 mr-4">
          <mat-form-field class="treo-mat-no-subscript w-full">
            <mat-label>Country</mat-label>
            <mat-select placeholder="Country" formControlName="country" [(value)]="Doc.country">
              <mat-option *ngFor="let country of countries" [value]="country.value">{{ country.viewValue }}</mat-option>
            </mat-select>
          </mat-form-field>
        </div>
    ```
    > country.value 는 실제 값이고, country.viewValue는 셀렉트 박스에 보이는 값이다.
    
<img src="/img/002_selectBoxImage.png" width="40%" height="30%" title="selectOption" alt="SelectTest"></img>
