---
title: Jekyll Navigation 수정하기
tags: jekyll
---
> *TeXt 테마를 기준으로 작성하였습니다.*

# 👍 Navigation에 Home을 추가
이제 갓 만든 블로그지만 내 입맛에 맞게 조금씩 수정하고 있는데, 첫번째로 메인에서 Navigation이 거슬렸다.
![Alt text](/assets/images/post/20210712/2.PNG)
>*TeXt 에서 제공하는 예시 페이지*

나도 이런식으로 홈, 카테고리, 태그 등 여러 Navigation을 제공하고 싶은데

![Alt text](/assets/images/post/20210712/1.PNG)
현재 내 블로그는 초기 세팅값으로 아카이브, 소개만 있다.

# ✌️ navigation.yml 수정
![Alt text](/assets/images/post/20210712/3.PNG)

 [여기](https://tianqi.name/jekyll-TeXt-theme/docs/en/navigation)를 보면 **data/navigtaion.yml** 파일을 수정하라고 되어있다. 
 
 ![Alt text](/assets/images/post/20210712/4.PNG)
 
 **_data 폴더** 를 보면 yml파일이 여러 개 있는데(아직 나머지는 어떻게 사용하는지 모른다) 그중 **Navigation.yml** 을 열어 수정한다.
 
 ![Alt text](/assets/images/post/20210712/5.PNG)
 
 딱 봐도 알수 있듯이 **Title** 은 보여지는 이름이고 **URL**  은 눌렀을 때 이동 할 주소이다.
 그러나 기존에 작성되어있던 아카이브를 보면 **Tltle** 을 **영어버전, 한글버전** 등으로 나누어 작성할 수 있는 것을 확인할 수 있는데, 나도 따라서 **EN 버전, KR 버전**으로 나누었다. 
 
 ![Alt text](/assets/images/post/20210712/6.PNG)
 
 이렇게 작성하고 저장한 뒤에 서버를 켜 테스트해보면
 
 ![Alt text](/assets/images/post/20210712/7.PNG)
 
 정상적으로 **Home** 버튼이 생긴 것을 확인할 수 있다 !
 
# 😎 끝 !
블로그를 만들고 처음으로 md를 작성중이라 이 짧은 글을 쓰는데도 시간이 굉장히 오래 걸렸다. 지금은 맥에서 기본프로그램으로 연결되어 있는 Xcode로 작성중인데 더 빠르게 쓸 수 있는데 md 작성 툴이 있는지도 찾아봐야겠다. 

<!--more-->

---
