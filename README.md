#  HTML 멀티미디어 및 링크 태그 정리

##  멀티미디어 태그

### `<object>`
- 오디오, 비디오, PDF 등 다양한 멀티미디어 파일 삽입 가능  
- `data` 속성: `src`와 같은 역할  
- `type` 속성: MIME 타입 지정

```html
<object data="product.pdf" type="application/pdf" width="100%" height="800"></object>
```

---

### `<embed>`
- 멀티미디어 삽입 (옛날에 많이 사용)  
- 외부 콘텐츠 삽입 시 `type` 속성으로 MIME 타입 지정

```html
<embed src="spring.mp3" type="audio/mpeg">
```

---

### `<img>`
- 이미지 삽입  
- `src`: 이미지 경로  
- `alt`: 이미지 설명 (웹접근성)

```html
<img src="tangerines.jpg" alt="레드향">
<img src="경로" alt="샐러드" width="50%">
<img src="경로" alt="샐러드" width="150">
```

- `width`, `height`는 `px`, `%` 모두 가능 (단위 생략 시 `px`)  
- `height`를 줘도 **영상은 세로로 늘어나지 않음** (비율 유지됨)

---

### 이미지 파일 확장자 비교

| 확장자 | 설명 |
|--------|------|
| `.gif` | 아이콘, 불릿 등 작은 이미지에 적합 (용량 작음) |
| `.jpg`, `.jpeg` | 색상, 명암 표현 가능 |
| `.png` | 색상 표현 다양, 웹에서 가장 많이 사용 |
| `.svg` | 벡터 이미지 (크기 변경해도 깨지지 않음) |

---

### `<audio>`
- 오디오 삽입  
- 속성  
  - `controls`: 재생 버튼 등 UI 표시  
  - `loop`: 무한 반복  
  - `muted`: 음소거

```html
<audio src="spring.mp3" controls loop muted></audio>
```

---

### `<video>`
- 비디오 삽입  
- `<audio>`와 같은 속성 사용 가능 + `width`, `height`, `poster`, `autoplay`

```html
<video src="salad.mp4" controls muted loop width="50%"></video>
```

- `poster`: 비디오 썸네일 지정  
- `autoplay`: 자동재생 (보통 `muted`와 함께 사용해야 작동됨)

```html
<video src="salad.mp4" controls muted loop poster="salad.jpg"></video>
```

---

##  MIME 타입이란?

**MIME(Multipurpose Internet Mail Extensions)**  
- 브라우저가 파일을 어떻게 처리할지 결정하는 파일 형식 정보  
- `<embed>`, `<object>` 사용 시 적절한 `type` 속성 필요

#  주요 MIME 타입 정리

##  텍스트 관련
- 일반 텍스트: `text/plain`
- HTML 문서: `text/html`
- CSS 스타일시트: `text/css`
- JavaScript 파일: `application/javascript`
- JSON 데이터: `application/json`
- XML 데이터: `application/xml`

---

##  이미지 관련
- JPEG 이미지: `image/jpeg`
- PNG 이미지: `image/png`
- GIF 이미지: `image/gif`
- SVG 이미지: `image/svg+xml`
- BMP 이미지: `image/bmp`
- ICON 이미지: `image/vnd.microsoft.icon`

---

##  오디오 관련
- MP3 오디오: `audio/mpeg`
- Ogg Vorbis 오디오: `audio/ogg`
- WAV 오디오: `audio/wav`
- MIDI 오디오: `audio/midi`

---

##  비디오 관련
- MP4 비디오: `video/mp4`
- WebM 비디오: `video/webm`
- Ogg 비디오: `video/ogg`

---

##  애플리케이션 및 기타
- PDF 문서: `application/pdf`
- ZIP 파일: `application/zip`
- Microsoft Word 문서: `application/msword`
- Excel 스프레드시트: `application/vnd.ms-excel`
- PowerPoint 프레젠테이션: `application/vnd.ms-powerpoint`

#  HTML 태그별 `type` 속성 필요 여부 정리

| 태그 | `type` 속성 필요 여부 | 설명 |
|------|------------------------|------|
| `<img>` | ❌ 필요 없음 | 이미지 확장자 (`.jpg`, `.png` 등)로 자동 인식됨 |
| `<audio>` | ❌ `<audio src="">`에는 필요 없음<br>✅ `<source>` 사용 시는 권장 | 브라우저 호환성 향상을 위해 `<source type="">` 사용 권장 |
| `<video>` | ❌ `<video src="">`에는 필요 없음<br>✅ `<source>` 사용 시는 권장 | 다양한 포맷 지원을 위한 다중 소스 구성 시 사용 |
| `<source>` | ✅ **필수** | `<audio>`, `<video>` 내부에서 사용할 때 MIME 타입 명시 필수 |
| `<script>` | ⭕ 권장 (HTML5에서는 생략 가능) | 기본값은 `text/javascript`이며 보통 생략 가능 |
| `<link>` | ✅ **필수** | 외부 CSS 연결 시 `type="text/css"` 사용 (HTML5에선 생략 가능) |
| `<embed>` | ✅ **필수** | 삽입할 콘텐츠의 MIME 타입 명시해야 함 |
| `<object>` | ✅ **필수** | 오디오, 비디오, PDF 등 파일의 MIME 타입 명시 필요 |
| `<style>` | ⭕ 권장 (HTML5에서는 생략 가능) | 보통 `type="text/css"`를 명시하지만 생략 가능 |
| `<input type="">` | ✅ **필수** | `<form>` 내부에서 입력 유형을 반드시 명시해야 함 (ex. `text`, `password`, `submit`) |

---

### ✅ 요약

- 반드시 써야 하는 경우: `<object>`, `<embed>`, `<source>`, `<input>`
- HTML5 기준 생략 가능하지만 써도 괜찮은 경우: `<script>`, `<style>`, `<link>`
- 전혀 필요 없는 경우: `<img>`, `<audio src="">`, `<video src="">`

---

##  링크 태그

### `<a href="">`
- 하이퍼링크 생성  
- `href`: 이동할 링크 주소  
- `target="_blank"`: 새 창에서 열기

```html
<a href="sub2.html" target="_blank">ㅁ</a>
```

###  이미지로 링크 만들기

```html
<a href="링크주소"><img src="image.png" alt="이미지링크"></a>
```

---

##  경로 지정법

| 용어 | 설명 |
|------|------|
| 절대경로 | 파일 위치의 전체 경로 |
| 상대경로 | 현재 작업 파일 기준 경로 |

### 상대경로 예시
- `./`: 현재 위치 (생략 가능)  
- `../`: 한 폴더 상위로 이동

---

##  참고 사이트
- [Can I use](https://caniuse.com/?search=webm) — 브라우저별 확장자 및 태그 지원 여부 확인
