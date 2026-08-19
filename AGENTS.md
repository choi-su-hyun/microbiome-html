# Microbiome Report HTML 작업 지침

## 프로젝트 목적

이 저장소는 아기의 대변 검체와 문진 결과(모유수유, 제왕절개 등)를 바탕으로 건강 리포트 PDF를 제작하기 위한 HTML 원고를 관리한다.

최종 결과물은 여러 페이지로 구성된 책자형 PDF다. 화면용 웹페이지보다 인쇄 시의 규격, 페이지 분리, 요소 배치의 일관성을 우선한다.

## 파트와 디렉터리

| 순서 | 파트                              | 디렉터리                   | 이미지 디렉터리                                           |
| ---- | --------------------------------- | -------------------------- | --------------------------------------------------------- |
| 1    | 표지                              | `cover/`                   | `cover/cover-images/`                                     |
| 2    | 인트로                            | `intro/`                   | `intro/intro-images/`                                     |
| 3    | 핵심요약                          | `key-summary/`             | `key-summary/key-summary-images/`                         |
| 4    | 우리아이 미생물 성장 이야기       | `microbiome-growth-story/` | `microbiome-growth-story/microbiome-growth-story-images/` |
| 5    | 우리아이 상태 분석 및 맞춤 가이드 | `status-analysis-guide/`   | `status-analysis-guide/status-analysis-guide-images/`     |
| 6    | 부록                              | `appendix/`                | `appendix/appendix-images/`                               |

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

## 데이터 바인딩

동적 값은 HTML에 `##`와 `|`로 구성된 토큰으로 표시한다. 파이프라인이 바인딩 표(카테고리·키·값)의 계층을 따라 이 토큰을 JSON 데이터로 치환한다.

### 데이터 소스

- 바인딩용 JSON은 `test` 워크스페이스(예: `/Users/choisuhyun/Downloads/test/`)에 `{등록번호}.json` 형태로 둔다. 예: `32PD7PN_2.json`.
- JSON 파일명의 `{등록번호}`는 해당 파일 `visible.report_context.registration_code`와 일치한다.
- 어떤 JSON 파일의 어떤 페이지 키(`A1`, `B6` 등)를 어떤 HTML에 바인딩할지는 **사용자가 매 요청마다 지정**한다. 에이전트가 임의로 매핑하지 않는다.

### JSON 구조

```text
{
  "value": {
    "page_count": 40,
    "A1": {
      "pdf_id": "pdf_01",
      "design_pdf_number": 2,
      "part_index": 1,
      "part_count": 1,
      "response": {
        "visible": { … 페이지별 동적 데이터 … }
      }
    },
    "A2": { … },
    "B6": { … },
    …
  }
}
```

- 페이지 키는 `page_N`이 아니라 파트 문자와 순번이다. 예: `A1`, `B6`, `C3`.
- 실제 바인딩 필드는 `value.{페이지키}.response.visible` 아래에 있다.
- `pdf_id`, `page_id`, `design_pdf_number`는 페이지 식별·매핑 확인용 메타데이터다.
- `part_index` / `part_count`가 2 이상이면 한 HTML 파일이 여러 페이지 키로 나뉜다(예: 맞춤 케어 가이드, 참고 문헌).

### 토큰 문법

- 형식: `##페이지키|visible|…|필드##`
- `##`로 토큰을 감싸고, 계층은 `|`로 구분한다.
- 첫 세그먼트는 JSON의 페이지 키와 동일하다. 예: `A1`, `B6`.
- 두 번째 세그먼트부터는 `response.visible` 아래의 키 경로다. `response`는 토큰에 쓰지 않는다.
- 예: `##A1|visible|title_above##` → `value.A1.response.visible.title_above`
- 예: `##B6|visible|report_context|name##` → `value.B6.response.visible.report_context.name`
- 객체 키는 JSON에 정의된 이름 그대로 쓴다. 예: `##A2|visible|sections|A|section##`, `##B6|visible|metric_cards|branch_1_metric_label##`
- 값이 배열인 경우는 없다.(배열이 있다면 사용자에게 알린다)
- class 속성 등에도 토큰을 삽입할 수 있다. 예: `class="change-result change-result--##B6|visible|metric_cards|branch_1_current_status##"`
- 박스 배경·테두리처럼 영역 전체 색은 `status` 값을 클래스 접미사로 쓴다. JSON 값은 공백 없이 온다. 예: `class="change-summary--##B6|visible|summary_opinion|branch_sentence|status##"`

### 문장 일부 강조 (`strong`, `em`)

문장 안에서 일부만 색상을 달리할 때는 HTML에서 문장을 쪼개지 않는다. JSON 값에 태그를 넣고, 해당 필드를 토큰 하나로 바인딩한다. 한 문장에 두 스타일이 함께 올 수 있다.

- 내부 글자색은 `<strong>` / `<em>`으로 표시한다.
- 각 태그의 실제 색상은 해당 부모 클래스의 페이지 전용 CSS에서 지정한다.
- 줄바꿈이 있으면 JSON에 `<br>`을 포함한다.
- 에이전트는 강조 구간을 다른 태그로 다시 감싸지 않는다. 토큰을 문단 요소 안에 그대로 둔다.

예:

```html
<section
  class="change-summary change-summary--overview change-summary--##B6|visible|summary_opinion|branch_sentence|status##"
>
  <p class="type-body-medium">##B6|visible|summary_opinion|branch_sentence|body##</p>
</section>
```

페이지 전용 CSS에서 `em`의 기본 이탤릭은 끈다.

### 페이지별 바인딩 절차

한 페이지씩 요청·검토·승인 후 다음 페이지로 진행한다. 에이전트는 사용자가 지정한 HTML 파일 하나와 해당 JSON 페이지 키 하나만 처리한다.

#### 1. 요청 받기

사용자가 **HTML 파일**과 **JSON 데이터**를 함께 지정한다. 에이전트는 지정되지 않은 항목을 추측하지 않는다.

- JSON: `{등록번호}.json`의 페이지 키 (예: `32PD7PN_2.json` → `B6`)
- HTML: 바인딩 대상 파일 경로 (예: `key-summary/see-the-changes-beneficial-bacteria.html`)

요청 예:

- `32PD7PN_2.json B6 → key-summary/see-the-changes-beneficial-bacteria.html 바인딩`
- `intro/glossary-of-terms.html에 32PD7PN_2.json A4 데이터 바인딩`

#### 2. JSON 확인

1. 사용자가 지정한 JSON 파일 → `value.{페이지키}`를 연다.
2. `response.visible`의 키 구조를 파악한다.
3. HTML에 대응하는 모든 동적 필드를 목록으로 정리한다.
4. JSON에 없는 키는 토큰으로 만들지 않는다.

#### 3. HTML 수정

1. 사용자가 지정한 HTML 파일을 연다.
2. 화면에 보이는 동적 텍스트·수치·이름·등급·날짜 등을 `##페이지키|visible|…##` 토큰으로 교체한다. 토큰의 페이지 키는 사용자가 지정한 JSON 키와 일치해야 한다.
3. 레이블·장식 문구·고정 카피는 그대로 둔다.
4. `report_context`, `footer`, 등급 class 등 반복 필드도 JSON 키가 있으면 토큰으로 바꾼다.
5. 기존 레거시 토큰(`##page_N|visible|…##`, `##1|visible|…##`)이 남아 있으면 해당 페이지 키 형식으로 교체한다.
6. HTML 구조·CSS·레이아웃은 바인딩 목적 외에는 변경하지 않는다.

#### 4. 결과 보고

수정 후 아래 내용을 사용자에게 전달한다.

- 대상: JSON 파일 / 페이지 키 / HTML 파일 / `page_name`
- 치환한 토큰 목록(필드 경로와 HTML 위치)
- JSON 키와 HTML 요소가 1:1로 대응되지 않는 경우(객체 키 이름, 분할 페이지 등) 설명
- 미바인딩으로 남긴 항목과 이유

#### 5. 사용자 검토·승인

- 사용자가 HTML 미리보기 또는 PDF 출력으로 확인한다.
- 수정 요청이 있으면 해당 페이지 키만 다시 수정한다.
- 승인 후에만 다음 페이지 키 작업을 시작한다.

### 작업 규칙

- HTML ↔ JSON 매핑은 사용자가 지정한다. 에이전트가 매핑 표를 만들거나 추측하지 않는다.
- 한 번에 사용자가 지정한 HTML 하나·JSON 페이지 키 하나만 바인딩한다. 사용자 확인이 끝나기 전에 다음 페이지로 진행하지 않는다.
- HTML 예시 파일에 실제 개인정보를 직접 넣지 않는다. JSON의 값은 파이프라인 치환용이며, HTML에는 토큰만 남긴다.
- JSON 객체는 배열이 아닌 명명 키(`A`, `term_A`, `branch_1` 등)를 쓰는 경우가 많다. 토큰 경로는 JSON 실제 구조를 따른다.
- 분할 페이지(`part_index` > 1)는 사용자가 지정한 페이지 키의 `visible`만 참조한다. 다른 파트 데이터를 섞지 않는다.

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
