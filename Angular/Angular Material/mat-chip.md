## mat-chip

#### mat-chip에서 color 적용하기

---

`mat-chip`의 경우 color 속성을 이용해서 아래와 같은 방법들로 색상을 적용할 수 있다.



```html
<!-- 지정된 color를 적용하는 경우 -->
<mat-chip color="accent"></mat-chip>
 
<!-- color를 binding하는 경우 -->
<mat-chip [color]="ChipColor(param)"></mat-chip>
```

하지만 단순히 위와 같은 방법으로 색상을 적용하면 적용이 되지 않는다.

`mat-chip`에 색상을 적용하기 위해서는 아래와 같이 `mat-chip`에 `selected` 속성을 적용해야합니다.



```html
<!-- 지정된 color를 적용하는 경우 -->
<mat-chip color="accent" selected></mat-chip>
 
<!-- color를 binding하는 경우 -->
<mat-chip [color]="ChipColor(param)" selected></mat-chip>
```



- 궁금증1: 지정된 색의 종류(accent, warn, primary) 외의 색을 적용하는 방법?
- 궁금증2: `selected`의 의미?



참고 문헌: <https://stackoverflow.com/questions/43363062/angular-2-material-md-chips-color-attribute-not-working>