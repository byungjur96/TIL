## Dialog

#### dialog 생성하기

---

dialog는 angular material에서의 modal을 의미한다.

dialog를 생성하기 위해서는 modal을 위한 html 탬플릿 파일과 component 파일이 있어야 한다.

Angular에서 modal을 생성하는 가장 기본적인 방법은 아래와 같다.



```typescript
/* app.component.ts */

public modal: MatDialogRef<ModalComponent>

public ngModalOpen(){
this.modal = this.dialog.open(ModalComponent,
                              height: '',
                              width: '')
}

```

`modal`, `ngModalOpen`, `ModalComponent`는 임의로 변수명을 정해준 것이다.

`ngModalOpen()`은 탬플릿 파일 내에서 modal을 열기 위한 method이다.

`ModalComponent`는 modal을 구성하는 기본 component다.



modal.component.ts의 내용은 다음과 같다.

```typescript
/* modal.component.ts */

import {Component} from '@angular/core';
import {MatDialogModule, MatDialog, MatDialogRef, MAT_DIALOG_DATA} from '@angular/material/dialog';

@Component({
    templateUrl: './template/modal.component.html',
    styleUrls: ['./styles/news-track.component.css'],
    providers: [MatDialogModule]
})

export class ModalComponent {
}
```

참고문헌: <https://material.angular.io/components/dialog/overview>



#### Main Component 내의 data 공유하기

---

main component 내의 data를 modal에서 이용하기 위해서는 `this.dialog.open()` parameter인 `config`에 data 항목을 추가해줘야 한다.

```typescript
/* app.component.ts */

this.modal = this.dialog.open(ModalComponent, {
    height: '95%',
    width:'140%',
    data: {
        dataKey: mainData
    }
});
```

modal에서 dataKey를 이용하고, main component에서 참고할 변수가 mainData에 들어가게 된다.

뿐만 아니라 modal component에 아래와 같이 `MAT_DIALOG_DATA`를 inject 해줘야 한다.



```typescript
/* modal.component.ts */

export class ModalComponent {
    constructor(
    @Inject(MAT_DIALOG_DATA) public data: any
) {}
```

참고문헌: <https://stackoverflow.com/questions/42664974/how-to-pass-data-to-dialog-of-angular-material-2>