---
title: "[JS] defer/async 의 차이"
sidebar_main: true
layout: single
categories: 
  - JavaScript
tag: [js]
---

![테스트 이미지]({{ site.url }}{{ site.baseurl }}/assets/images/common/js_logo.jpg)



## defer/async 가 나오기 이전에

<br/>

![테스트 이미지]({{ site.url }}{{ site.baseurl }}/assets/images/2021-11/24_1.png)

html을 파싱하다가 css, js를 만나면 중간에 html 파싱이 중지되고 css,js의 파싱/실행이 진행된이후에 다시 html파싱이 이어진다. 그러므로 DomApi를 사용할때 Dom생성이 완료되기 전에 js를 실행시킨다면 문제가 발샐할 수 있다.

또한 js를 html중간에 넣으면 html파싱완료 속도가 느려져 페이지가 보여지기까지 시간이 더 걸린다.

그래서 이런 문제를 피하기 위해 js를 가장 아래 위치 시켜왔다.

<br/>

## defer/async 어트리뷰트

( 참고로 말하자면 async/defer은 외부 js를 로드하는 경우에만 사용가능하다. 인라인에서는 사용이 불가능 하다. )

```html
<script async src="./main.js"></script>
<script defer src="./main.js"></script>
```

async와 defer모두 html파싱과 외부 자바스크립트 파일의 로드가 비동기적으로 동시에 진행된다. 하지만 js실행 시점에서의 차이점이 있다.

### async 어트리뷰트

![테스트 이미지]({{ site.url }}{{ site.baseurl }}/assets/images/2021-11/24_2.png)

html 파싱과 js 파일이 비동기적으로 로드된다.
단, js의 파싱과 실행은 js로드가 완료된 직후 진행 되며, 이때 html 파싱이 중단되다.

![테스트 이미지]({{ site.url }}{{ site.baseurl }}/assets/images/2021-11/24_3.png)

여러개의 script 태그에 async를 지정하면 ,
js순서와 상관 없이 로드 완료순으로 js가 실행이 되어 실행 순서가 보장되지 않는다.

<br/>

### defer 어트리뷰트

![테스트 이미지]({{ site.url }}{{ site.baseurl }}/assets/images/2021-11/24_4.png)

async와 마찬가지로 비동기적으로 로드가 이루어진다.
단, html의 파싱이 모두 완료된 직후(Dom생성완료 직후) js가 실행이된다.

<br/>
<br/>

**결론** :  js로 DomApi를 이용,  html의 파싱속도 문제 때문에 거의 defer을 쓰지 async를 쓸 일은 거의 없어보인다.

<br/>
<br/>
<br/>
<br/>
