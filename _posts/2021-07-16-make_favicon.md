---
title: "[Jekyll] 블로그 아이콘 변경하기"
subtitle: Change favicon + .svg
tags: Jekyll
published: true
---
> **이 글은 TeXt theme 기준이므로 개인마다 조금씩 다를 수 있습니다.**

<br>
<br>
<br>

# 0. 블로그 내꺼만들기
![12](https://user-images.githubusercontent.com/60254939/125879671-ea94d69f-ed8e-4524-b653-f0c5e2e60bdc.png){:.border.rounded.shadow}
포스트를 하기에 앞서 블로그를 들어올때마다 기본스러운 UI들이 마음에 안들었다.

네비게이션부터 시작해 색상 등 마음에 안드는 것들 투성이었지만 우선 가장 눈에 띈 건 저 은행잎 파비콘이었다.

기본 파비콘이다보니 아직 내 블로그가 아닌 느낌

그래서 파비콘을 수정하기로 했다 !

<br>
<br>
<br>

# 1. 이미지 다운로드
![1](https://user-images.githubusercontent.com/60254939/125879441-7879519d-cbae-4bdc-9963-2de018f9fb7a.png){:.border.rounded.shadow}
우선 구글에서 원하는 이미지의 `.png` 확장자 파일을 다운받아야 합니다.

*저는 Siri의 영롱한 디자인에 꽂혔습니다..*

<br>
<br>
<br>

# 2. PNG to ICO
```
<!-- start favicons snippet, use https://realfavicongenerator.net/ -->
{%- include snippets/prepend-baseurl.html path='/assets/apple-touch-icon.png' -%}
<link rel="apple-touch-icon" sizes="180x180" href="{{ __return }}">

{%- include snippets/prepend-baseurl.html path='/assets/favicon-32x32.png' -%}
<link rel="icon" type="image/png" sizes="32x32" href="{{ __return }}">

{%- include snippets/prepend-baseurl.html path='/assets/favicon-16x16.png' -%}
<link rel="icon" type="image/png" sizes="16x16" href="{{ __return }}">

{%- include snippets/prepend-baseurl.html path='/assets/site.webmanifest' -%}
<link rel="manifest" href="{{ __return }}">

{%- include snippets/prepend-baseurl.html path='/assets/safari-pinned-tab.svg' -%}
<link rel="mask-icon" href="{{ __return }}" color="#fc4d50">

{%- include snippets/prepend-baseurl.html path='/assets/favicon.ico' -%}
<link rel="shortcut icon" href="{{ __return }}">

<meta name="msapplication-TileColor" content="#ffc40d">

{%- include snippets/prepend-baseurl.html path='/assets/browserconfig.xml' -%}
<meta name="msapplication-config" content="{{ __return }}">

<meta name="theme-color" content="#ffffff">
<!-- end favicons snippet -->
```
`includes/head/favicon.html` 에 가보면 위와 같은 코드를 볼 수 있는데

![2](https://user-images.githubusercontent.com/60254939/125882064-257a49b6-a6e3-494f-91ec-1de4de7fd975.png){:.border.rounded.shadow}

`/assets` 폴더에 가보면 코드에서 언급한 파일들이 있는 걸 볼 수 있습니다.

`favicon.html` 에서 `/assets` 폴더 안에 있는 파일들을 불러오는 것 같네요

이제 다운받은 `.png` 이미지를 각 브라우저 및 OS별 사이즈 및 `.ico` 로 바꿔야 하는데, 

파비콘 변환 사이트들에서 바꿀 수 있습니다.

> 구글에 파비콘만 검색해도 다양한 변환 사이트가 나오는데, 전 주석에 써있는대로 [여기](https://realfavicongenerator.net/) 를 이용했습니다
> 
> ![image](https://user-images.githubusercontent.com/60254939/125883095-3d1281c2-ff81-465b-a339-0b11269b8aaa.png){:.border.rounded.shadow}

![image](https://user-images.githubusercontent.com/60254939/125898000-62f4bec5-2841-460d-a7d4-cc36917a3629.png){:.border.rounded.shadow}

![image](https://user-images.githubusercontent.com/60254939/125883306-782dddd7-1d4e-49b2-a82c-d098a0093c89.png){:.border.rounded.shadow}

**Select Your Fabicon image** 버튼을 눌러 변환한 다음 **Favicon Package** 를 눌러보면

![image](https://user-images.githubusercontent.com/60254939/125883610-5ff96410-d815-4f1d-a9b2-f8c6589afa93.png){:.border.rounded.shadow}

이렇게 필요한 파일이 전부 들어있네요 !

<br>
<br>
<br>

# 3. /assets 덮어쓰기

> **전 작업환경이 달라서 깃에서 바로 작업했습니다.**

![image](https://user-images.githubusercontent.com/60254939/125883987-d0804d1f-4ba3-4459-a109-857be87f9fa9.png){:.border.rounded.shadow}

`/assets` 폴더안에 전부 붙여넣습니다.

<br>
<br>
<br>

# 4. custom.html 수정

![image](https://user-images.githubusercontent.com/60254939/125892444-663c8a85-aeba-45b6-a343-7013ace37859.png){:.border.rounded.shadow}

다음과 같이 html 코드를 복사한 뒤 `/includes/head/custom.html` 에 붙여넣습니다.

붙여넣을 때 `href` 앞부분에 `/assets/` 를 붙여줍니다.

```html
<!-- start custom head snippets -->
<link rel="apple-touch-icon" sizes="180x180" href="/assets/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="/assets/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/assets/favicon-16x16.png">
<link rel="manifest" href="/assets/site.webmanifest">
<link rel="mask-icon" href="/assets/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">
<!-- end custom head snippets -->
```

<br>
<br>
<br>

# 😎 파비콘 완성 !

![image](https://user-images.githubusercontent.com/60254939/125898517-0342e400-35ab-4760-90b7-97355e479184.png){:.border.rounded.shadow}

이렇게 파비콘이 잘 들어간 걸 확인할 수 있습니다 !

<br>
<br>
<br>

**추가+**

<br>
<br>
<br>

# 타이틀 옆 마크 변경(.svg)

![image](https://user-images.githubusercontent.com/60254939/125900004-c00b2719-f13b-482e-819e-bef1846a295a.png){:.border.rounded.shadow}

`/includes/svg/logo.svg` 
타이틀 옆 마크는 `.svg` 확장자를 가지고 있습니다.

넣고 싶은 이미지를 구글에 **png to svg**로 검색해서 변환해줍니다. 

> 전 [여기](https://anyconv.com/ko/png-to-svg-byeonhwangi/) 에서 변환했습니다.

![image](https://user-images.githubusercontent.com/60254939/125900093-b9575ab4-f73f-44a7-965b-90bd2d26d3f8.png){:.border.rounded.shadow}

![image](https://user-images.githubusercontent.com/60254939/125900154-923ae895-10bd-40bc-900a-04491f5235c0.png){:.border.rounded.shadow}


이름을 `logo.svg` 로 바꿔주고 `/includes/svg/logo.svg` 에 덮어씌워줍니다.

<br>
<br>
<br>

# 진짜 끝 !

![image](https://user-images.githubusercontent.com/60254939/125900338-8fd49fdc-15fc-49f6-9a92-13c5c86e9daa.png){:.border.rounded.shadow}


<!--more-->

---
