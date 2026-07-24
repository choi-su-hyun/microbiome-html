# Microbiome Report 디자인 시스템

이 문서는 리포트의 색상 시맨틱 토큰과 사용 기준을 정의한다. 실제 CSS 변수는 `common/styles/colors.css`에 정의되어 있다. 새 페이지를 만들거나 기존 페이지의 디자인을 수정할 때 해당 파일을 불러오고 원시 색상값 대신 시맨틱 변수를 사용한다.

## Brand

| 토큰 | 원시 토큰 | 용도 |
| --- | --- | --- |
| `brand/primary` | `yellow-400` | 프로젝트 전반에서 사용하는 메인 브랜드 색상 |

## Status

| 토큰 | 원시 토큰 | 용도 |
| --- | --- | --- |
| `status/positive` | `blue-green-600` | 긍정 상태 |
| `status/negative` | `red-600` | 부정 상태 |

## Data

수치·측정값·결과 등 데이터의 상대적 상태인 범위, 수준, 방향을 표현한다.

| 상태 | 의미 | Dark | Medium | Light |
| --- | --- | --- | --- | --- |
| `bad` | 건강 등급 미흡, 위험도 높음, 데이터 수치 기준치 초과 또는 높음 | `red-500` | `red-200` | `red-100` |
| `normal` | 건강 등급 보통, 위험도 주의, 데이터 수치 주의 | `yellow-600` | `yellow-200` | `yellow-100` |
| `good` | 건강 등급 우수, 위험도 낮음, 데이터 수치 기준치 미달 | `blue-600` | `blue-200` | `blue-100` |
| `best` | 건강 등급 최우수, 위험도 보통, 데이터 수치 기준치 이내 | `blue-green-500` | `blue-green-200` | `blue-green-100` |
| `common` | 수치의 높낮이와 상관없이 데이터를 강조 | `green-600` | `green-200` | `green-100` |
| `baseline` | 데이터의 기준이 되는 기본 색상 | `mono-400` | `mono-300` | `mono-100` |

## Text

텍스트 콘텐츠의 정보 위계와 가독성을 표현한다.

| 토큰 | 원시 토큰 | 용도 |
| --- | --- | --- |
| `text/title` | `mono-900` | 화면 또는 섹션의 주제를 나타내는 가장 높은 위계의 텍스트 |
| `text/primary` | `mono-800` | 주요 정보 전달을 위한 기본 본문 텍스트. 가장 많이 사용하는 기본값 |
| `text/secondary` | `mono-700` | 보조 정보 또는 맥락 설명용 본문 텍스트 |
| `text/tertiary` | `mono-600` | 우선순위가 낮은 정보, 시간 정보, 부수적인 설명 |
| `text/emphasis` | `brand/primary` | 링크 등 일부를 시각적으로 강조하는 텍스트. 상태나 데이터 의미에는 사용하지 않음 |
| `text/on` | `white` | 어두운 배경 위의 흰색 텍스트 |
| `text/status/positive` | `status/positive` | 긍정 상태 텍스트 |
| `text/status/negative` | `status/negative` | 부정 상태 텍스트 |

## Surface

콘텐츠가 실제로 놓이는 면을 표현하여 정보 구조와 시각적 위계를 구분한다.

| 토큰 | 원시 토큰 | 용도 |
| --- | --- | --- |
| `surface/base` | `yellow-100` | 카드, 리스트, 섹션 등 주요 정보 컨테이너 |
| `surface/base-mono` | `mono-100` | 주요 정보 컨테이너의 무채색 대안 |
| `surface/subtle` | `yellow-200` | 시각적 강조를 최소화하면서 영역을 구분하는 배경 |
| `surface/subtle-mono` | `mono-200` | 영역 구분용 무채색 배경 |
| `surface/on` | `white` | 화면을 구성하는 가장 기본적인 흰색 면 |
| `surface/emphasis` | `yellow-600` | 화면에서 가장 강조되어야 하는 면 |
| `surface/inverse` | `mono-800` | 화면에서 가장 강조되어야 하는 어두운 면 또는 툴팁 |
| `surface/status/positive` | `blue-green-100` | 긍정 상태 배경 |
| `surface/status/negative` | `red-100` | 부정 상태 배경 |

## Border

요소의 경계를 정의하여 컴포넌트 형태와 콘텐츠 간 구조를 구분한다. Border 자체는 의미의 주체가 아니며 상태나 데이터 의미를 보조적으로 표현한다.

| 토큰 | 원시 토큰 | 용도 |
| --- | --- | --- |
| `border/default` | `mono-300` | 기본 경계 |
| `border/strong` | `mono-500` | 상태 변화 없이 기본 경계를 더 강하게 표현 |
| `border/light` | `mono-200` | 상태 변화 없이 기본 경계를 더 약하게 표현 |
| `border/emphasis` | `brand/primary` | 상태나 데이터와 무관한 브랜드 또는 인터랙션 강조 |
| `border/on` | `white` | 어두운 배경 위의 경계 |
| `border/status/positive` | `blue-green-500` | 긍정 상태 경계 |
| `border/status/negative` | `red-500` | 부정 상태 경계 |

## Icon

아이콘 색상은 텍스트 시맨틱 토큰과 같은 원리로 사용하되 비교적 단순한 위계만 적용한다.

| 토큰 | 참조 토큰 | 용도 |
| --- | --- | --- |
| `icon/primary` | `text/secondary` | 주요 정보 전달용 기본 아이콘 |
| `icon/secondary` | `text/secondary` | 보조 정보 또는 맥락 설명용 아이콘 |
| `icon/emphasis` | `text/emphasis` | 상태나 데이터와 무관한 브랜드 또는 인터랙션 강조 |
| `icon/on` | `white` | 어두운 배경 위의 아이콘 |
| `icon/status/positive` | `status/positive` | 긍정 상태 아이콘 |
| `icon/status/negative` | `status/negative` | 부정 상태 아이콘 |

## Category

### 분석 콘텐츠

| 카테고리 | 용도 | Special | Dark | Medium | Light |
| --- | --- | --- | --- | --- | --- |
| `child-birth` | 분만 분석 | `#CF69AA` | `pink-600` | `pink-300` | `pink-100` |
| `feeding` | 수유 분석 | `#2B8142` | `green-600` | `green-200` | `green-100` |
| `fret` | 보챔·가스 분석 | — | `blue-600` | `blue-200` | `blue-100` |
| `poop` | 배변·소화 분석 | — | `yellow-600` | `yellow-200` | `yellow-100` |
| `sleep` | 수면 분석 | — | `purple-600` | `purple-200` | `purple-100` |
| `skin` | 피부민감도 분석 | — | `red-500` | `red-200` | `red-100` |

### 맞춤 가이드 태그

| 카테고리 | 용도 | Dark | Light |
| --- | --- | --- | --- |
| `diet` | 식단 태그 | `green-600` | `green-200` |
| `exercise` | 운동 태그 | `yellow-600` | `yellow-200` |
| `surrounding` | 환경 태그 | `blue-600` | `blue-200` |
| `habit` | 습관 태그 | `purple-600` | `purple-200` |

### 종합 가이드 단계

| 단계 | Dark | Light |
| --- | --- | --- |
| `total-guide/lv1` | `brand/primary` | `yellow-100` |
| `total-guide/lv2` | `blue-green-400` | `blue-green-100` |
| `total-guide/lv3` | `green-400` | `green-100` |

## 구현 원칙

- 같은 의미의 텍스트, 아이콘, Surface, Border에는 대응하는 동일 시맨틱 토큰을 일관되게 적용한다.
- 상태에는 `positive`와 `negative`를 사용하고, 측정 결과 단계에는 `bad`, `normal`, `good`, `best`, `common`, `baseline`을 사용한다.
- 카테고리 콘텐츠와 태그에는 해당 카테고리 팔레트를 사용한다.
- 명도 단계는 정보 위계, 배경과의 대비, 인쇄 가독성을 고려하여 선택한다.
- 공통 색상 토큰은 `common/styles/colors.css`의 CSS 사용자 정의 속성으로 관리한다.
- 페이지 전용 CSS에서 같은 원시 색상값을 반복하거나 임의의 새 색상값을 만들지 않는다.
- 기존 구현과 이 문서가 충돌하면 이 문서를 기준으로 맞추되, 접근 가능한 대비와 인쇄 결과를 함께 확인한다.

## Typography

실제 CSS 변수와 재사용 클래스는 `common/styles/typography.css`에 정의되어 있다. 문서의 기본 폰트는 `common/styles/common.css`에서 `--font-family-base`로 적용하며, Display와 Heading Primary처럼 지정된 제목에만 `--font-family-heading-primary`를 적용한다. `Hakgyoansim Dunggeunmiso`는 해당 CSS의 `@font-face`를 통해 웹폰트로 제공한다. 네트워크에 연결되지 않은 PDF 제작 환경에서는 웹폰트 대신 설치된 폰트 또는 fallback이 사용될 수 있으므로 최종 출력 전 로딩 여부를 확인한다.

### Foundation

#### Font family

| 토큰 | CSS 변수 | 값 | 용도 |
| --- | --- | --- | --- |
| `heading-primary` | `--font-family-heading-primary` | `Hakgyoansim Dunggeunmiso` | Display, Heading Primary |
| `heading-secondary` | `--font-family-heading-secondary` | `SUIT Variable` | Heading Secondary |
| `base` | `--font-family-base` | `SUIT Variable` | Body, Caption, Label 및 그 외 텍스트 |

#### Font weight

| 토큰 | CSS 변수 | 값 |
| --- | --- | --- |
| `regular` | `--font-weight-regular` | `400` |
| `medium` | `--font-weight-medium` | `500` |
| `bold` | `--font-weight-bold` | `700` |
| `extrabold` | `--font-weight-extrabold` | `800` |

본문은 `regular`를 기본으로 사용하고, 중요도에 따라 다른 weight를 적용한다.

#### Font scale

기본 크기 토큰은 `6px`, `7px`, `8px`, `9px`, `10px`, `11px`, `12px`, `13px`, `14px`, `15px`, `16px`, `18px`, `20px`, `24px`이다. Display 전용 크기는 `40px`와 `56px`이다. CSS 변수 이름은 `--font-size-{number}`이며 Display 전용 변수는 `--font-size-display-small`, `--font-size-display-large`이다.

#### Line height

| 용도 | CSS 변수 | 값 |
| --- | --- | --- |
| Display | `--line-height-display` | `120%` (`1.2`) |
| Heading Primary | `--line-height-heading-primary` | `120%` (`1.2`) |
| Heading Secondary | `--line-height-heading-secondary` | `140%` (`1.4`) |
| Body | `--line-height-body` | `140%` (`1.4`) |
| Caption | `--line-height-caption` | `130%` (`1.3`) |
| Label | `--line-height-label` | `100%` (`1`) |
| Label Relaxed | `--line-height-label-relaxed` | `130%` (`1.3`) |

기초 설명의 본문 150%보다 아래 상세 프리셋에 명시된 140%를 우선한다.

#### Letter spacing

| 용도 | CSS 변수 | 디자인 값 | CSS 값 |
| --- | --- | --- | --- |
| Display | `--letter-spacing-display` | `-3%` | `-0.03em` |
| Heading Primary, Heading Secondary, Body, Caption, Label | `--letter-spacing-default` | `-1%` | `-0.01em` |

CSS의 `letter-spacing`에는 퍼센트가 유효하지 않으므로 같은 비율의 `em` 단위로 변환한다.
기초 표에는 Heading Primary가 `-3%`로 안내되어 있지만 상세 Heading Primary 표의 `-1%`를 우선 적용한다.

### Semantic presets

표의 클래스는 `strong`이 없는 경우 Normal 스타일을 뜻한다.

#### Display

화면에서 가장 큰 텍스트로 표지와 배너 등에 사용한다.

| 스타일 | 클래스 | 크기 | Weight | Family | Line height | Letter spacing |
| --- | --- | --- | --- | --- | --- | --- |
| Large Strong | `.type-display-large-strong` | `56px` | `700` | Heading Primary | `120%` | `-3%` |
| Large | `.type-display-large` | `56px` | `400` | Heading Primary | `120%` | `-3%` |
| Small | `.type-display-small` | `40px` | `400` | Heading Primary | `120%` | `-3%` |

#### Heading Primary

페이지 또는 모듈 단위의 주요 제목에 사용한다.

| 스타일 | 클래스 | 크기 | Strong / Normal | Family | Line height | Letter spacing |
| --- | --- | --- | --- | --- | --- | --- |
| Large | `.type-heading-primary-large-strong`, `.type-heading-primary-large` | `20px` | `800` / `400` | Heading Primary | `120%` | `-1%` |
| Medium | `.type-heading-primary-medium-strong`, `.type-heading-primary-medium` | `18px` | `800` / `400` | Heading Primary | `120%` | `-1%` |

#### Heading Secondary

| 스타일 | 클래스 접두사 | 크기 | Strong / Normal | Family | Line height | Letter spacing |
| --- | --- | --- | --- | --- | --- | --- |
| Large | `.type-heading-secondary-large` | `14px` | `800` / `500` | Base | `140%` | `-1%` |
| Medium | `.type-heading-secondary-medium` | `13px` | `800` / `500` | Base | `140%` | `-1%` |
| Small | `.type-heading-secondary-small` | `12px` | `800` / `500` | Base | `140%` | `-1%` |
| XSmall | `.type-heading-secondary-xsmall` | `11px` | `800` / `500` | Base | `140%` | `-1%` |

Strong 클래스에는 각 접두사 뒤에 `-strong`을 붙인다.

#### Body

| 스타일 | 클래스 접두사 | 크기 | Strong / Normal | Line height | Letter spacing |
| --- | --- | --- | --- | --- | --- |
| Large | `.type-body-large` | `11px` | `800` / `400` | `140%` | `-1%` |
| Medium | `.type-body-medium` | `10px` | `800` / `400` | `140%` | `-1%` |
| Small | `.type-body-small` | `9px` | `800` / `400` | `140%` | `-1%` |

#### Caption

서브 텍스트와 주석 등 가장 보조적인 텍스트에 사용한다. 이탤릭이 필요하면 HTML의 `<em>` 또는 별도의 `font-style: italic`을 사용한다.

| 스타일 | 클래스 접두사 | 크기 | Strong / Normal | Line height | Letter spacing |
| --- | --- | --- | --- | --- | --- |
| Large | `.type-caption-large` | `8px` | `800` / `500` | `130%` | `-1%` |
| Medium | `.type-caption-medium` | `7px` | `800` / `500` | `130%` | `-1%` |
| Small | `.type-caption-small` | `6px` | `800` / `500` | `130%` | `-1%` |

#### Label

컴포넌트 구성 내 수치 강조, label, placeholder, 그래프 수치, 범례와 태그 등에 사용한다.

| 스타일 | 클래스 접두사 | 크기 | Strong / Normal | Line height | Letter spacing |
| --- | --- | --- | --- | --- | --- |
| XXXLarge | `.type-label-xxxlarge-strong` | `18px` | `800`만 사용 | `100%` | `-1%` |
| XXLarge | `.type-label-xxlarge` | `13px` | `800` / `500` | `100%` | `-1%` |
| XLarge | `.type-label-xlarge` | `12px` | `800` / `500` | `100%` | `-1%` |
| Large | `.type-label-large` | `11px` | `800` / `500` | `100%` | `-1%` |
| Medium | `.type-label-medium` | `10px` | `800` / `500` | `100%` | `-1%` |
| Small | `.type-label-small` | `9px` | `800` / `500` | `100%` | `-1%` |
| XSmall | `.type-label-xsmall` | `8px` | `800` / `500` | `100%` | `-1%` |
| Small Relaxed | `.type-label-small-relaxed` | `8px` | `800` / `500` | `130%` | `-1%` |
| XXSmall | `.type-label-xxsmall` | `7px` | `800` / `500` | `100%` | `-1%` |

전달된 표에는 8px·130% 스타일의 이름도 `small`로 중복 표기되어 있어, CSS에서는 충돌을 피하기 위해 `small-relaxed`로 구분한다. XXXLarge는 Strong 클래스인 `.type-label-xxxlarge-strong`만 제공한다.
