## Web Font란?

방문자의 로컬 컴퓨터에 폰트 설치 여부와 관계없이 온라인의 특정 서버에 위치한 폰트 파일을 다운로드하여 화면에 표시해주는 웹 전용 폰트

`typeface` : 굵기나 스타일(서체) <br />
`font` : 서체의 단일 굵기와 스타일이며 글꼴은 특정 크기, 굵기 및 스타일을 포함하여 제공(글꼴)

### Web Font의 장, 단점
- 사용자에게 해당 폰트가 없더라도 디자이너가 의도한 대로 원하는 디자인을 모두에게 동일하게 제공할 수 있음
- 용량이 무겁고 웹에서 폰트를 불러와서 적용시키는 것이기 때문에 웹에 전반적인 속도 감소 유발

### Web Font의 확장자
`TTF` : 구형 안드로이드 버전(4.4)에서 필요.<br />
`WOFF` : 대부분의 모던 브라우저에서 지원<br />
`WOFF2` : WOFF보다 압축률이 30% 정도 더 좋음<br /><br />
![image](https://user-images.githubusercontent.com/101608868/178479554-14f1b28c-c180-4dc4-8596-360753fcaa2f.png)
<br />

```css
@font-face {
  font-family: 'Roboto';
  src: url(/font/Roboto-Regular.eot), 
       url(/font/Roboto-Regular.woff2) format("woff2"), 
       url(/font/Roboto-Regular.woff) format("woff"),
       url(/font/Roboto-Regular.ttf) format("truetype");
}
```

### 웹 폰트 확장자는 순서에 맞게 적용

woff2를 가장 앞에 적용합니다. 브라우저는 선언된 순서대로 지원 가능한 파일 형식을 다운로드하기 때문에 압축률이 가장 좋은 woff2를 먼저 선언합니다.
format()은 반드시 써야 합니다. 쓰지 않으면 브라우저는 지원 가능한 파일 형식이 나올 때까지 순서대로 다운을 받게 됩니다.
<br /><br />

### [preload](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types/preload) 옵션으로 먼저 로딩

<link> 태그의 rel 속성에 preload 옵션을 사용하면 해당 리소스를 다른 리소스보다 빨리 로딩합니다. <br />
페이지에서 중요도가 높은 자원을 의도적으로 먼저 로딩할 때 주로 사용합니다.

### [font-display](https://developer.mozilla.org/ko/docs/Web/CSS/@font-face/font-display) 사용하기
`auto` : 브라우저의 기본동작에 맡기는 방식입니다.<br />
`block` : 웹 폰트가 로딩되지 않았을 때는 텍스트를 렌더링하지 않습니다.<br />
`swap` : 우선 폴백 폰트로 글자를 렌더링하고, 웹 폰트 로딩이 완료되면 웹 폰트로 전환 합니다.<br />
`fallback` : font face에 매우 작은 차단 기간과 짧은 교체 기간을 부여합니다.<br />
`optional` : 100ms 내외의 시간 동안만 block을 하고 기본폰트를 보여줍니다.<br /><br />

<img width="676" alt="스크린샷 2022-07-12 오후 7 58 58" src="https://user-images.githubusercontent.com/101608868/178482657-de8c9ced-07c4-4c5f-80b7-ebad740139d0.png">

