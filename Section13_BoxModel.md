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
