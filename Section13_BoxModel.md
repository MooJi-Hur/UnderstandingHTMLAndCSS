# Section 13. Box Model

## Lecture Note

### 1. Rendering

- Render Tree Construction 브라우저가 HTML 문서와 CSS로 만든 각각의 Tree를 합쳐 하나의 Render Tree를 만드는 과정
- Rendering
  - Layout
    - Render Tree의 정보 중 보여줄 내용을 어디에 보여줄지 정하고 페이지의 틀을 만드는 과정
  - Painting
    - 어떤 컨텐츠를 각 Layout에 보여줄지 정하고, 실제로 보여주는 과정
- 브라우저는 기기 화면에 맞추어 같은 Render Tree를 다르게 보여줌

### 2. Visual Formatting Model

- 구조화된 문서 (브라우저에서는 Tree를 지칭)를 구조, 반복 가능, 일관됨을 유지하여 시각적으로 보여주는 모델
- Visual Media
  - 정적으로는 프린트된 문서부터, 동적으로는 웹사이트까지 시각화와 관련된 주체들의 의사소통
- Visual Media 즉, 각 브라우저 회사들은 빠르고 일관된 CSS 렌더링을 위해 VFM을 채택
- 다른 브라우저와 기기에서 동작하더라도 일관성을 유지한 웹사이트를 보여줄 수 있음

### 3. Box Model

- VFM은 화면을 재구성하기 위해 박스를 활용함
- 구조화된 문서의 트리를 각각의 Box로 간주

### 4. Viewport and Coordinates

- Viewport는 디바이스 화면 혹은 브라우저 창 만큼의 크기를 가진 틀
- 웹은 연속적인 하나의 페이지 (Countinuous Media)에 정보를 담고 있음
- Viewoport는 Countinuous Media의 일부분을 보여주며, 스크롤로 움직일 수 있음
- 이때, 좌표의 원점은 좌상단에 위치, Countinuous Media, Viewport, 각 박스의 원점을 염두에 두어야 함

### 5. Engin Aside: Layout

- Layout은 User Agent가 각각의 박스가 Countinuous에 어떤 크기, 위치로 있을지 계산하는 과정
- VFM에 따르며, 계산 비용이 소모됨

### 6. Conceptual Aside: Pixels, Pixel Density, and Reference Pixels

- Device Pixel: 기기가 조정 가능한 가장 작은 화면 요소의 단위
- Pixel Density: 일정한 단위 (e.g. 1inch)내에 몇 개의 픽셀이 들어가는지, 즉 밀도
- Reference Pixel
  - 기기마다 Pixel Density가 달라 너비 등의 일관성을 보장할 수 없는 문제가 있음
  - 브라우저가 Reference Pixel과 기기의 Pixel Density에 맞춰 CSS inch를 Device inch로 변환
  - Reference Pixcel:
    - Viewing Distance: 28inch (약 71cm, 화면과 사람의 거리가 하나의 팔 길이 일 때)
    - Baseline Pixel Density: 96**D**ots**P**er**I**nch
    - 즉 1 CSS inch = 96 CSS pixel
  - 참고 자료: [CSS Length Explained](https://hacks.mozilla.org/2013/09/css-length-explained/)

### 7. Units and Computed Values

- Font Size
  - 기본 font-size 값은 medium, inherit 속성으로 설정되어 있음
    - medium: 사용자가 설정해둔 기본 폰트 사이즈, h4 태그, HTML font size 3 크기에 해당
    - [1**IN**ch = 72**P**oin**T** = 2.54cm](https://www.w3.org/Style/Examples/007/units.en.html)
    - 1**P**oin**T** = 1/72inch, 16px = 12pt, 100% = 1em = 12pt (default body font-size)
    - 인쇄물의 폰트 크기 기준으로 pt를 많이 써왔기 때문에 print media와의 일관성을 위해 pt와 em을 혼합한 사용을 권장함
    - Raster화 관련 글 참고, 보통 디자인 툴에서 1DP는 1px로 설정되어 있음
      - DP: **D**ensity independent **P**, 안드로이드 OS의 논리적 픽셀
      - [UI·UX 디자이너를 위한 가이드 - DP·SP와 디스플레이](https://mesign.tistory.com/10)
  - 상대적 크기 폰트 단위
    - em: 조상 중 가장 가까운 pt 값을 기준으로 계산
      - `em = 요소의 px 값 / 부모 요소의 font-size px 값`
      - 합성: 상하위 태그가 모두 상대적인 경우가 모두 em의 배수 계산이 적용될 수 있음
    - rem: root 태그에 해당하는 태그의 pt 값을 기준으로 계산
      - body의 font-size를 62.5%로 두면 하위 태그의 em을 읽기 편하다. ex. 1.6em = 16px
        - 참고, 1em = 10px 이 브라우저의 기본 설정
