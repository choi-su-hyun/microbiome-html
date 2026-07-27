# Microbiome Report HTML 작업 지침

## 프로젝트 목적

이 저장소는 아기의 대변 검체와 문진 결과(모유수유, 제왕절개 등)를 바탕으로 건강 리포트 PDF를 제작하기 위한 HTML 원고를 관리한다.

최종 결과물은 여러 페이지로 구성된 책자형 PDF다. 화면용 웹페이지보다 인쇄 시의 규격, 페이지 분리, 요소 배치의 일관성을 우선한다.

## 파트와 디렉터리

| 순서 | 파트 | 디렉터리 | 이미지 디렉터리 |
| --- | --- | --- | --- |
| 1 | 표지 | `cover/` | `cover/cover-images/` |
| 2 | 인트로 | `intro/` | `intro/intro-images/` |
| 3 | 핵심요약 | `key-summary/` | `key-summary/key-summary-images/` |
| 4 | 우리아이 미생물 성장 이야기 | `microbiome-growth-story/` | `microbiome-growth-story/microbiome-growth-story-images/` |
| 5 | 우리아이 상태 분석 및 맞춤 가이드 | `status-analysis-guide/` | `status-analysis-guide/status-analysis-guide-images/` |
| 6 | 부록 | `appendix/` | `appendix/appendix-images/` |

파트 디렉터리는 숫자 접두사 없이 역할을 나타내는 영문 이름으로 관리한다. PDF 순서는 위 표의 순서를 따른다.

## 파일 배치 규칙

- HTML 파일은 해당 파트 디렉터리 바로 아래에 둔다.
- 이미지, SVG, 아이콘 등 시각 자산은 반드시 해당 파트의 `{part-name}-images/`에 둔다.
- 여러 파트에서 함께 쓰는 로고와 브랜드 자산은 `common/images/`에 둔다.
- `docs/`의 문서는 페이지에 삽입하는 자산이 아니라 프로젝트 참고 자료이므로 위 규칙의 예외로 둔다.
- 각 HTML 페이지의 전용 CSS는 같은 파트의 `styles/`에 별도 파일로 둔다.
- 여러 파트 또는 페이지에서 공통으로 사용하는 CSS만 `common/styles/`에 둔다.
- 특정 파트에서만 쓰는 스타일이나 자산을 `common/`으로 옮기지 않는다.
- 한 HTML 파일에 여러 페이지를 합치지 않는다. PDF 한 페이지를 HTML 한 파일로 관리한다.
- HTML과 전용 CSS는 같은 기본 파일명을 사용한다. 예: `page-01.html`과 `styles/page-01.css`.
- 파일명은 소문자 영문, 숫자, 하이픈만 사용한다.
- 이미지 경로와 CSS 경로는 저장소 내부의 상대 경로로 작성한다.

## 페이지 규격 및 인쇄 원칙

- 구체적인 판형이 전달되면 `@page`의 `size`를 실제 단위(`mm`)로 명시하고 모든 페이지에 동일하게 적용한다.
- 판형이 확정되기 전에는 A4 등 임의의 규격을 확정값으로 간주하지 않는다.
- 페이지 크기, 여백, 재단선 또는 도련은 공통 CSS 변수로 관리한다.
- 모든 페이지는 지정된 인쇄 영역을 넘지 않아야 하며 의도하지 않은 다음 페이지 흐름이 생기지 않도록 확인한다.
- 배경색과 배경 이미지를 PDF에 포함할 수 있도록 인쇄 색상 보정 속성을 공통 스타일에 둔다.
- 중요한 텍스트와 그래픽은 재단 가능 영역에서 충분히 떨어뜨린다.
- 페이지 단위 요소에는 필요한 경우 `break-after: page`를 사용한다.
- 웹 브라우저 미리보기와 실제 PDF 출력 결과를 모두 확인한다. 특히 폰트 대체, 줄바꿈, SVG, 이미지 해상도를 점검한다.

## HTML 및 CSS 작성 원칙

- 문서 구조에 맞는 시맨틱 HTML을 사용한다.
- 페이지 전용 CSS를 HTML의 `<style>` 태그에 작성하지 않는다.
- 공통 토큰(색상, 폰트, 판형, 여백)은 CSS 사용자 정의 속성으로 관리한다.
- 고정된 책자 레이아웃에는 인쇄 단위와 명시적인 레이아웃 규칙을 사용하되, 텍스트를 이미지로 대체하지 않는다.
- 아기와 보호자의 건강 정보가 들어갈 수 있으므로 실제 개인정보나 검체 데이터를 예시 파일에 넣지 않는다. 예시는 명백한 가상 데이터 또는 플레이스홀더만 사용한다.
- 접근 가능한 대체 텍스트를 제공하고, 장식 이미지는 빈 `alt`를 사용한다.

## 본문 페이지 기본 템플릿

모든 본문 페이지는 `intro/glossary-of-terms.html`의 문서 구조와 페이지 레이아웃을 기본 템플릿으로 사용한다.

- 새 본문 페이지를 만들거나 기존 본문 페이지의 구조를 수정하기 전에 `intro/glossary-of-terms.html`과 `intro/styles/glossary-of-terms.css`를 먼저 확인한다.
- 공통 CSS는 `reset.css`, `common.css`, `print.css`, `colors.css`, `typography.css`, 페이지 전용 CSS 순서로 불러온다.
- `<main>` 내부는 공통 `report-header`, 페이지별 본문 콘텐츠 영역, 공통 `report-footer` 순서로 구성한다.
- `report-header`의 로고와 아이 정보 구조, `report-footer`의 파트명·페이지 설명·페이지 번호 구조를 동일하게 유지한다. 두 요소의 공통 스타일은 `common/styles/report-page.css`에서 관리한다.
- 제목 영역은 본문 콘텐츠의 첫 요소로 두고, 모든 본문 페이지에서 아래 구조를 공통으로 사용한다. 페이지별 제목 문구와 설명 문구만 변경한다.

  ```html
  <section class="report-page__content">
    <header class="report-page__title-area">
      <h1 class="type-heading-primary-large-strong">페이지 제목</h1>
      <p class="type-body-large">페이지를 설명하는 한두 문장</p>
    </header>
    <!-- 페이지별 콘텐츠 -->
  </section>
  ```

- `report-page__title-area`는 제목, 설명, 하단 구분선으로 구성하며, 제목은 `type-heading-primary-large-strong`, 설명은 `type-body-large` 시맨틱 클래스를 우선 사용한다.
- 제목 영역의 여백·설명과의 간격·하단 구분선은 여러 본문 페이지에서 같은 값으로 유지한다. `common/styles/report-page.css`에서 관리하며, 해당 파일은 `typography.css` 다음·페이지 전용 CSS 전에 불러온다.
- 페이지별 콘텐츠에 맞게 시맨틱 요소와 전용 클래스는 변경할 수 있지만, 공통 인쇄 영역과 헤더·본문·푸터의 기본 배치 구조는 임의로 변경하지 않는다.
- `intro/glossary-of-terms.html`의 공통 구조를 변경하면 해당 구조를 사용하는 모든 본문 페이지에 미치는 영향을 함께 확인한다.
- 표지 등 본문이 아닌 특수 페이지는 이 규칙의 예외로 한다.

## 디자인 시스템

새 페이지를 만들거나 기존 페이지의 디자인을 수정하기 전에 반드시 `docs/design-system.md`를 읽고, 문서에 명시된 색상 및 타이포그래피 토큰과 용도를 따른다. 디자인 시스템의 단일 기준 문서는 `docs/design-system.md`이며, 토큰을 추가하거나 변경할 때 해당 문서와 `common/styles/`의 대응 파일을 함께 갱신한다.

- 색상은 임의의 값으로 새로 만들지 말고, 디자인 시스템 문서에 정의된 시맨틱 토큰을 우선 사용한다.
- 같은 의미의 텍스트, 아이콘, Surface, Border에는 각각 대응하는 동일 시맨틱 토큰을 일관되게 적용한다.
- 상태를 표현할 때는 positive/negative 토큰을, 측정 결과의 단계에는 bad/normal/good/best/common/baseline 데이터 토큰을 용도에 맞게 사용한다.
- 카테고리별 콘텐츠와 태그에는 해당 카테고리 팔레트를 사용하고, 명도 단계는 정보 위계와 배경 대비에 맞춰 선택한다.
- 구현 시 토큰을 CSS 사용자 정의 속성으로 정의하고, 페이지 전용 CSS에서 원시 색상값을 반복하지 않는다.
- 모든 HTML 페이지는 공통 색상 변수 파일인 `common/styles/colors.css`를 페이지 전용 CSS보다 먼저 불러온다.
- 모든 HTML 페이지는 공통 타이포그래피 파일인 `common/styles/typography.css`를 페이지 전용 CSS보다 먼저 불러온다.
- 모든 HTML 페이지는 공통 인쇄 규격 파일인 `common/styles/print.css`를 먼저 불러오며, A4 미리보기는 `595 × 842px`, 인쇄 규격은 `210 × 297mm`를 사용한다.
- 모든 HTML 페이지는 공통 리셋 파일인 `common/styles/reset.css`를 가장 먼저 불러온다.
- 모든 HTML 페이지는 공통 리셋 및 기본 문서 규칙 파일인 `common/styles/common.css`를 먼저 불러온다.
- 타이포그래피는 `common/styles/typography.css`의 시맨틱 클래스를 우선 사용하고, 페이지 전용 CSS에서 동일한 font-family, font-size, font-weight, line-height, letter-spacing 조합을 반복하지 않는다.
- 최종 PDF 출력 전에 `SUIT Variable`과 `Hakgyoansim Dunggeunmiso`의 실제 로딩 및 폰트 대체 여부를 확인한다.
- 디자인 시스템 문서와 기존 구현이 충돌하면 `docs/design-system.md`를 기준으로 맞추되, 인쇄 가독성과 접근 가능한 대비를 함께 확인한다.

## 새 페이지 추가 절차

1. 대상 파트의 다음 순번으로 HTML 파일을 만든다.
2. 같은 기본 이름의 CSS 파일을 파트의 `styles/`에 만든다.
3. 공통 CSS를 먼저, 페이지 전용 CSS를 나중에 불러온다.
4. 필요한 자산을 대상 파트의 이미지 디렉터리에 추가한다.
5. 브라우저와 PDF 출력에서 페이지 크기, 넘침, 글꼴, 이미지 품질을 확인한다.

## 현재 디렉터리 구조

```text
.
├── AGENTS.md
├── docs/
│   └── design-system.md
├── common/
│   ├── images/
│   │   └── logo.svg
│   └── styles/
│       ├── colors.css
│       ├── common.css
│       ├── print.css
│       ├── reset.css
│       └── typography.css
├── cover/
│   ├── cover-images/
│   └── styles/
├── intro/
│   ├── intro-images/
│   └── styles/
├── key-summary/
│   ├── key-summary-images/
│   └── styles/
├── microbiome-growth-story/
│   ├── microbiome-growth-story-images/
│   └── styles/
├── status-analysis-guide/
│   ├── status-analysis-guide-images/
│   └── styles/
└── appendix/
    ├── appendix-images/
    └── styles/
```
