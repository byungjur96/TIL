## Drag/Drop

#### Drag/Drop이란

---

Angular 7부터 angular material에서 Drag and Drop 기능을 지원한다.

Drag and Drop은 angular material의 component에 속해있지 않고 CDK에 속해 있다.

CDK는 <u>*Component Developer's Kit의 줄임말*</u> 이다.



#### Dr이g/Drop 구현하기

---

1. `npm install @angular/material @angular/cdk` 명령어를 통해서 프로젝트에 cdk를 설치한다.

2. DragDropModule를 *@ngModule*에 추가해준다. (추가해주지 않으면 속성값을 넣어줘도 실행이 되지 않는다.)

3. 아래와 같은 html 탬플릿 코드를 작성한다. (cdkDrag 속성을 넣어준다.)

```html
<div class="drag-box" cdkDrag>
  drag me
</div>
```



####  이동 축 고정하기

---

cdkDrag 속성이 있는 태그에 *cdkDragLockAxis* 속성을 넣어주면 드래그 할 수 있는 축이 고정된다.

예를 들어 `cdkDragLockAxis="y"` 라는 속성값을 주면 위/아래로만 움직이고,`cdkDragLockAxis="x"`라는 속성값을 주면 좌우로만 움직인다.



#### 리스트 재배열

---

string array에 대해서 아래의 코드를 적용하면 드래그로 순서를 바꾸는 리스트를 만들 수 있다.

```html
<div cdkDropList class="example-list">
    <div class="example-box" *ngFor="let movie of movies" cdkDrag>{{movie}}</div>
</div>
```

드래그를 할 컨텐츠들에 `cdkDrag` 속성을, 컨텐츠들을 모두 담는 태그에 `cdkDropList` 속성값을 적용하면 Drag/Drop으로 재배열이 가능한 array를 만들 수 있다.

다만, 단순히 위의 속성값들을 적용할 경우 재배열된 array의 순서가 저장되지 않는다.

재배열된 array를 저장하기 위해서는 아래의 코드처럼 `cdkDropListDropped`를 사용해야 한다.

```html
<div cdkDropList class="example-list" (cdkDropListDropped)="drop($event)">
  <div class="example-box" *ngFor="let movie of movies" cdkDrag>{{movie}}</div>
</div>
```



이때 `drop($event)`의 경우 TypeScript에서 메서드를 설정해 준다.

```typescript
drop(event: CdkDragDrop<string[]>) {
    moveItemInArray(this.movies, event.previousIndex, event.currentIndex);
  }
```

이 메서드를 사용하기 위해서 `moveItemInArray`를 컴포넌트 내에서 import 해주어야 한다.

```typescript
import {CdkDragDrop, moveItemInArray} from '@angular/cdk/drag-drop';)
```



#### Preview 기능 구현하기

---

CSS를 통해 preview 기능을 구현할 수 있다.

preview 기능이란 컨텐츠를 drag할 때 drop할 위치에 가상으로 위치를 보여주는 기능이다.

![](https://github.com/byungjur96/TIL/blob/master/Angular/Angular%20Material/angular-7-drag-drop-example-custom-placeholder.gif)



위의 이미지에서 파란색 선이 나타나는 것을 preview 기능이라고 한다.

preview 기능을 구현하기 위해서는 CSS 파일에 아래 코드를 적용해주면 된다.

```css
.cdk-drag-preview {
    box-shadow: 0 3px 3px -3px #0084ff;
}
```



#### 두 개의 리스트 사이에서 컨텐츠 이동시키기

---

![](https://github.com/byungjur96/TIL/blob/master/Angular/Angular%20Material/angular-7-drag-drop-example-transfer-lists-item.gif)

두 개의 리스트 사이에서 리스트 내의 컨텐츠를 이동시킬 수 있다.

```html
<div
     cdkDropList
     #firstList = "cdkDropList"
     [cdkDropListData] = "firstListName"
     [cdkDropListConnectedTo] = "[secondList]"
     class = "example-list"
     (cdkDropListDropped) = "drop($event)">
    <div class="example-box" *ngFor="let item of firstListName" cdkDrag>{{item}}</div>
</div>

<div
     cdkDropList
     #secondList = "cdkDropList"
     [cdkDropListData]="secondListName"
     [cdkDropListConnectedTo]="[firstList]"
     class="example-list"
     (cdkDropListDropped)="drop($event)">
    <div class="example-box" *ngFor="let item of secondListName" cdkDrag>{{item}}</div>
</div>
```

위와 같이 DropList 2개를 생성하여 두 개의 리스트 간의 데이터를 이동할 수 있다.

`[cdkDropListData]`에는 DropList에 표시될 데이터가 들어가게 된다.

`#<divIdName>="cdkDropList"`의 divIdName에 해당 div에 해당해 줄 id 이름을 입력해주고,  `[cdkDropListConnectedTo]="[connectedDivIdName]"`에서 `connectedDivIdName`에 연결될 DropList의 id 이름을 입력해주면 된다.



```typescript
drop(event: CdkDragDrop<string[]>) {
    if (event.previousContainer === event.container) {
      moveItemInArray(event.container.data, event.previousIndex, event.currentIndex);
    } else {
      transferArrayItem(event.previousContainer.data,
                        event.container.data,
                        event.previousIndex,
                        event.currentIndex);
    }
  }

```

두 개의 DropList를 연결하는 경우에는 `drop($event)` 메서드가 조금 달라진다.

`transferArrayItem`도 import 해서 위와 같은 꼴로 작성해야 한다.



참고 문헌: [공식 document](<https://material.angular.io/cdk/drag-drop/overview>), [모듈 설치 오류 해결](<https://grokonez.com/frontend/angular/angular-7/angular-7-drag-and-drop-example-angular-material-cdk>)