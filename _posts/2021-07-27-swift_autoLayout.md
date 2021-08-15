---

title: "[iOS][Swift] 오토레이아웃 개념잡기"
subtitle: AutoLayout Constraints
tags: Swift, iOS, AutoLayout, Constraint
published: true

---

# 프로젝트 만들기

![https://user-images.githubusercontent.com/60254939/127083253-5135d3d4-e947-4cfc-9c29-3b54f54689c2.png](https://user-images.githubusercontent.com/60254939/127083253-5135d3d4-e947-4cfc-9c29-3b54f54689c2.png)

Create new XCode project 를 눌러 오토레이아웃을 공부할 새 프로젝트를 만들어 보겠습니다 !

![https://user-images.githubusercontent.com/60254939/127083972-fcdd64ad-3164-4736-a5a5-04c2acffd748.png](https://user-images.githubusercontent.com/60254939/127083972-fcdd64ad-3164-4736-a5a5-04c2acffd748.png)

카테고리는 App 으로 하고

![https://user-images.githubusercontent.com/60254939/127084031-5fbcaf15-532e-480c-b38d-dd2526ce6571.png](https://user-images.githubusercontent.com/60254939/127084031-5fbcaf15-532e-480c-b38d-dd2526ce6571.png)

이름은 PracticeAutoLayout 으로 하겠습니다.

![https://user-images.githubusercontent.com/60254939/127084390-0297accb-be60-44a4-857a-b5b109e17d22.png](https://user-images.githubusercontent.com/60254939/127084390-0297accb-be60-44a4-857a-b5b109e17d22.png)

![https://user-images.githubusercontent.com/60254939/127084647-8daa3836-a9ec-4ca1-98fa-901f8682319a.png](https://user-images.githubusercontent.com/60254939/127084647-8daa3836-a9ec-4ca1-98fa-901f8682319a.png)

저희는 스토리보드에서 AutoLayout 을 연습해볼거니까 `Main.storyboad` 로 가줍니다.

# Label 만들기

![https://user-images.githubusercontent.com/60254939/127084799-2739456c-74eb-42c7-93f5-336a8ac4f47e.png](https://user-images.githubusercontent.com/60254939/127084799-2739456c-74eb-42c7-93f5-336a8ac4f47e.png)

그다음 테스트 해 볼 `Label` 을 하나 만들고 잘 보이게 하기 위해 ~~예쁜 색~~ 백그라운드 색상을 넣어줍니다 ! 

# 오토 레이아웃 개념

`Swift` 의 `AutoLayout` 개념은 해당 뷰의 `x, y 위치` 와 해당 뷰의 `가로 세로 크기` 를 알려주면 Swift 내부에서 뷰의 위치를 계산해  동적으로 렌더링 하게 됩니다.

# 오토 레이아웃이 필요한 이유

Q. 그냥 마우스로 요소들만 필요한 위치에 갖다 놓으면 되는데 왜 오토레이아웃이 필요한가요

![https://user-images.githubusercontent.com/60254939/127085870-29ed9f06-c2c3-4a7a-ab8e-e6d39b12bef8.png](https://user-images.githubusercontent.com/60254939/127085870-29ed9f06-c2c3-4a7a-ab8e-e6d39b12bef8.png)

 보면 우리는 iPhone 11 에서 작업했기 때문에 iPhone 11 로 실행시켰을 땐 내가 배치한 곳에 잘 배치되는 것을 볼 수있습니다.

![https://user-images.githubusercontent.com/60254939/127085958-6c2fd53e-ff83-4d79-b634-233b178df4c1.png](https://user-images.githubusercontent.com/60254939/127085958-6c2fd53e-ff83-4d79-b634-233b178df4c1.png)

그러나 iPhone 8 로 실행시켜보면 사진처럼 위치가 달라지게 됩니다.

## 문제점

이러한 문제는 우리가 Constraint 제약사항 을 걸어주지 않아 생기는 문제인데요. Label 의 위치를 x, y 절대좌표로 설정해 두었기에 뷰의 크기가 바뀌거나 회전하게 된다면 위치가 달라지게 됩니다.

# 제약사항 적용 Constraint

## X 축에 대한 Constraint

![https://user-images.githubusercontent.com/60254939/127093714-7ae3862b-d27d-4365-a3fb-9246007a4447.png](https://user-images.githubusercontent.com/60254939/127093714-7ae3862b-d27d-4365-a3fb-9246007a4447.png)

사진처럼 왼쪽 `Constraint` 를 추가하면 `Swift` 는 이 `Label` 이 `Safe Area`의 왼쪽 (`.Leading`) 으로부터 100만큼 떨어져 있구나를 알게 됩니다. 

![https://user-images.githubusercontent.com/60254939/127097984-d01c6c2b-2a5d-45ca-925f-6ba8d537dd2a.png](https://user-images.githubusercontent.com/60254939/127097984-d01c6c2b-2a5d-45ca-925f-6ba8d537dd2a.png)

Safe Area 에 대한 설명

![https://user-images.githubusercontent.com/60254939/127094097-1fc54139-9e91-45e8-bbe0-5655f28dbe99.png](https://user-images.githubusercontent.com/60254939/127094097-1fc54139-9e91-45e8-bbe0-5655f28dbe99.png)

하지만 적용된 것을 자세히 보시면 위아래로 빨간 선이 생기게 되는데요. `swift` 가 "뷰의 y좌표를 모르겠어" 즉, y축에 대한 `constraint` 가 없다는 것을 알려주고 있는 것입니다.

<br>

위에서 오토레이아웃의 개념을 설명할때 `swift` 에게 `뷰의 x, y 좌표` 와 `뷰의 크기` 를 제공해주어야 한다고 했는데, 지금같은 경우엔 x좌표만 제공한 상태입니다.

<br>

따라서 우리는 `constraint` 를 걸어 y 좌표와 크기를 알려주어야 합니다.

## Y 축에 대한 constraint

![https://user-images.githubusercontent.com/60254939/127094793-2d03ae2d-063e-4964-a6c4-b4de1b20d210.png](https://user-images.githubusercontent.com/60254939/127094793-2d03ae2d-063e-4964-a6c4-b4de1b20d210.png)

아까 했던 것처럼 `Label` 의 Y축 `Constraint` 를 150 만큼 주게 되면 

![https://user-images.githubusercontent.com/60254939/127094841-2fe70b9b-41ff-4f58-bc46-8ebdd6149cb7.png](https://user-images.githubusercontent.com/60254939/127094841-2fe70b9b-41ff-4f58-bc46-8ebdd6149cb7.png)

이런 식으로 Constraint 가 잘 잡힌 것을 볼 수 있고,

![https://user-images.githubusercontent.com/60254939/127098478-229dd952-5f9f-4af4-878d-2434e548069a.png](https://user-images.githubusercontent.com/60254939/127098478-229dd952-5f9f-4af4-878d-2434e548069a.png)

이렇게 속성에서도 확인할 수 있습니다.

## 뷰의 크기 지정 Width, height

![https://user-images.githubusercontent.com/60254939/127098688-ae7e5078-8cfe-4a59-a6ba-81dada63b82e.png](https://user-images.githubusercontent.com/60254939/127098688-ae7e5078-8cfe-4a59-a6ba-81dada63b82e.png)

위에서 x, y좌표에 대한 위치를 `Constraint` 걸었다면 이번엔 `Width` 와 `Height` 에 대해 각각 200, 100 으로 걸어보겠습니다.

![https://user-images.githubusercontent.com/60254939/127098786-73066a15-2f42-49b9-a531-fab26d3d76e2.png](https://user-images.githubusercontent.com/60254939/127098786-73066a15-2f42-49b9-a531-fab26d3d76e2.png)

이제 `Swift` 에게 `뷰의 x, y 좌표` + `뷰의 크기` 를 모두 알려주었으니 위치를 계산하여 동적으로 렌더링 하게 됩니다.

## 렌더링 결과

![https://user-images.githubusercontent.com/60254939/127099389-1bae2239-a5db-49bd-84c3-7fb297f9809b.png](https://user-images.githubusercontent.com/60254939/127099389-1bae2239-a5db-49bd-84c3-7fb297f9809b.png)

![https://user-images.githubusercontent.com/60254939/127099260-41b6a195-a6d3-48a9-b647-8912c906b235.png](https://user-images.githubusercontent.com/60254939/127099260-41b6a195-a6d3-48a9-b647-8912c906b235.png)

결과를 보면 iPhone 8 에서 오른쪽으로 치우친게 보이는데, 이는 `Constraint` 를 걸 때 `Safe Area` 의 왼쪽 `.Leading` 에만 걸었기 때문에 iPhone 8 에선 100만큼 떨어지면 오른쪽으로 치우치게 됩니다. 

<br>

이를 해결하기 위한 방법으로 왼쪽 오른쪽에 모두 Constraint 를 거는 방법이 있고 또 하나는

![https://user-images.githubusercontent.com/60254939/127099764-89a277f6-348b-4048-97be-4638cf8231cc.png](https://user-images.githubusercontent.com/60254939/127099764-89a277f6-348b-4048-97be-4638cf8231cc.png)

먼저 x축에 대한 `Constraint` 를 없애고

![https://user-images.githubusercontent.com/60254939/127100080-7139e7e0-69b7-4e51-9881-e8b27af27b04.png](https://user-images.githubusercontent.com/60254939/127100080-7139e7e0-69b7-4e51-9881-e8b27af27b04.png)

![https://user-images.githubusercontent.com/60254939/127100194-65170d65-95bd-4307-8b91-7a8a5d3a5cec.png](https://user-images.githubusercontent.com/60254939/127100194-65170d65-95bd-4307-8b91-7a8a5d3a5cec.png)

`Label` 의 중앙 x 좌표 `Label.Center.X` 를 `View` 의 중앙 x 좌표 `SuperView.Center.X`  와 일치 시키겠다. 즉 Label 을 가운데로 오게하겠다 라는 뜻이 됩니다.

![https://user-images.githubusercontent.com/60254939/127100694-816264fa-f6ee-4e7c-8b1f-f1586594895f.png](https://user-images.githubusercontent.com/60254939/127100694-816264fa-f6ee-4e7c-8b1f-f1586594895f.png)

![https://user-images.githubusercontent.com/60254939/127099723-c066574d-51ab-4e82-bf26-fc568c1cba74.png](https://user-images.githubusercontent.com/60254939/127099723-c066574d-51ab-4e82-bf26-fc568c1cba74.png)

이렇게 하면 iPhone 11 과 8 모두 같은 곳에 위치하는 것을 볼 수 있습니다 !

+

잘 정리된 블로그가 있어 링크 남깁니다. [여기](https://seoyoung612.tistory.com/85)
