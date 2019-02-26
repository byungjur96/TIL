## Date Picker

#### Date Picker 구현하기

---

datePicker는 `<input>`, `<mat-datepicker-toggle>`, `<mat-datepicker>` 3개의 tag로 이루어져 있다.

기본적인 코드 구성은 아래와 같다.

```html
<mat-form-field>
  <input matInput [matDatepicker]="picker" [(ngModel)]="dateSelector">
  <mat-datepicker-toggle matSuffix [for]="picker"></mat-datepicker-toggle>
  <mat-datepicker #picker></mat-datepicker>
</mat-form-field>
```

`[(ngModel)]`을 이용해서 데이터 바인딩이 가능하다.



input 태그의 `[matDatepicker]` 값과 `mat-datepicker-toggle 태그의 [for]` 값, 그리고 mat-datepicker 태그 안의 `id`를 모두 동일하게 지정해주어야 datePicker가 정상적으로 작동한다.



참고자료: <https://material.angular.io/components/datepicker/overview>