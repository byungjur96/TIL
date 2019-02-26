## AutoComplete

#### AutoComplete 생성하기

---

auto-complete는 input 태그를 작성할 때 자동 완성을 도와주는 기능이다.

가장 기본적인 auto-complete의 경우는 단순히 기본에 설정되어 있는 목록을 *mat-select* 처럼 보여주는 방식이다.

입력된 텍스트와 일치하는 결과만 하단에 보여주는 auto-complete는 아래와 같다.

```html
<form class="example-form">
    <mat-form-field class="example-full-width">
        <input type="text" placeholder="Pick one" 
               matInput [formControl]="myControl" [matAutocomplete]="auto">
        <mat-autocomplete #auto="matAutocomplete">
          <mat-option *ngFor="let option of filteredOptions | async" [value]="option">
            {{option}}
          </mat-option>
    	</mat-autocomplete>
  	</mat-form-field>
</form>
```

auto-complete의 html 코드는 text를 입력하는 `input` 태그와, `mat-autocomplete` 태그 두 부분으로 나눌 수 있다.

`input` 태그의 `[matAutocomplete]="auto"`와 `mat-autocomplete` 태그의 `#auto="matAutocomplete"`을 일치시켜 줘야한다.

`mat-autocomplete` 태그 안에는 `mat-option` 태그를 통해서 자동 완성 옵션들을 넣어준다.



- 궁금점: async 파이프의 용도?



app.component.ts 파일의 코드는 아래와 같다.

```typescript
/* app.component.ts */

import {Component, OnInit} from '@angular/core';
import {FormControl} from '@angular/forms';
import {Observable} from 'rxjs';
import {map, startWith} from 'rxjs/operators';

@Component({
    selector: 'autocomplete-filter-example',
    templateUrl: 'autocomplete-filter-example.html',
    styleUrls: ['autocomplete-filter-example.css'],
})
export class AutocompleteFilterExample implements OnInit {
    myControl = new FormControl();
    options: string[] = ['One', 'Two', 'Three'];
    filteredOptions: Observable<string[]>;

    ngOnInit() {
        this.filteredOptions = this.myControl.valueChanges
            .pipe(
            startWith(''),
            map(value => this._filter(value))
        );
    }

    private _filter(value: string): string[] {
        const filterValue = value.toLowerCase();
        return this.options.filter(option => option.toLowerCase().includes(filterValue));
    }
}
```



참고문헌: https://material.angular.io/components/autocomplete