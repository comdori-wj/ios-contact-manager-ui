# ios-contact-manager-ui
# 연락처 앱

### Table of Content

> **1️⃣ OverView**
>
> - 결과물
> - 프로젝트 참여자
> - 프로젝트 기간
>
> **2️⃣ 프로젝트 구현**
>
> - 프로젝트 설계
> - 사용 기술/구성
> - 태스크 매니지먼트
> - 프로젝트 파일 구조
> - 구현 기능
> - 구현 상세
>
> **3️⃣ 습득 지식**


## 1️⃣ OverView

### 📍 결과물
![Simulator Screen Recording - iPhone 15 Pro - 2023-10-19 at 17 35 33](https://github.com/comdori-wj/ios-contact-manager-ui/assets/76927263/191257fb-0ef7-4b13-8632-dab4e8609f1a)

### 📍 프로젝트 참여자

<table>
<tr>
<th>🧑🏻‍💻 COMDORI</th>
<th>🐠 Janine</th>
</tr>
<tr>
<td>
<img src="https://avatars.githubusercontent.com/u/22284092?v=4" width="90" height="90">
<div>@comdori-wj</div>
</td>
<td>
<img src="https://avatars.githubusercontent.com/u/76927263?v=4" width="90" height="90"> 
<div>@janine-kang</div>
</td>
</tr>
</table>

### 📍 프로젝트 기간

> 2023.10.04 ~ 2023.10.20 (3 weeks)

## 2️⃣ 프로젝트 구현

### 📍 프로젝트 설계

- 디자인 패턴: `MVC`

### 📍 사용 기술/구성

- Swift 기반 어플리케이션 작성
- UIKit framework
- Storyboard
- AutoLayout
- Git-flow 기반 협업

### 📍 태스크 매니지먼트

- Notion
- Discord

### 📍 프로젝트 파일 구조

```
ContactManager
├── Controllers
│   ├── ContactModifierViewController.swift
│   └── ContactTableViewController.swift
├── Errors
│   └── InvalidError.swift
├── Extensions
│   ├── Array.swift
│   ├── String.swift
│   ├── UIStackView.swift
│   └── UIView.swift
├── Models
│   ├── ContactInfo.swift
│   ├── ContactManager.swift
│   └── ValidateType.swift
├── Resources
│   ├── AppDelegate.swift
│   ├── Assets.xcassets
│   ├── SceneDelegate.swift
│   └── mockData.json
└── Views
    ├── Main.storyboard
    ├── ContactModifierStackView.swift
    └── ContactTableViewCell.swift
```

### 📍 기능 구현

#### 메인 화면
<table>
<tr>
<th>구동 화면</th>
<th>구현 기능</th>
</tr>
<tr>
<td>
<img src="https://github.com/comdori-wj/ios-contact-manager-ui/assets/76927263/bff6638b-d321-49a2-9a16-c4635469b5c7" width="auto" height="300" />
</td>
<td>
  <li>TableView와 TableViewCell 재사용하여 UI 표기</li>
  <li>진입 시 Json File로부터 연락처 불러오기 기능</li>
</td>
</tr>
</table>

#### 새 연락처 추가 Flow
<table>
<tr>
<th>구동 화면</th>
<th>구현 기능</th>
</tr>
<tr>
<td>
<img src="https://github.com/comdori-wj/ios-contact-manager-ui/assets/76927263/eae21efa-38dd-4846-8c4a-a019aa0dd5ca" width="auto" height="300" />
</td>
<td>
  <li>메인 화면에서 모달창을 활용하여 화면 Seguement 설정</li>
  <li>나이 Field와 연락처 Field는 숫자 외 입력 불가</li>
  <li>저장 버튼 눌렀을 때 이름, 나이, 연락처 유효성 검사 기능
  <ul>  
    <li>입력받은 이름에 공백 존재 시 제거 후 저장</li>
    <li>나이는 999살까지 입력 가능</li>
    <li>연락처는 자릿수에 따라 `-` 위치 조정
      <ul>
      <li>9자리: ##-###-####</li>
      <li>10자리: ###-###-####</li>
      <li>11자리 이상: ###-####-####...</li>
      </ul>
    </li>  
  </ul>
  </li>
  <li>유효성 검사 통과 시, 모달창 종료 및 기존 리스트에 새 연락처 추가</li>
</td>
</tr>
</table>

#### 기존 연락처 수정 Flow
<table>
<tr>
<th>구동 화면</th>
<th>구현 기능</th>
</tr>
<tr>
<td>
<img src="https://github.com/comdori-wj/ios-contact-manager-ui/assets/76927263/a2e3c14f-6494-43a7-b84b-e269e72d72d3" width="auto" height="300" />
</td>
<td>
  <li>기존 연락처 리스트 선택 시 메인 화면에서 모달창을 활용하여 화면 이동</li>
  <li>선택한 연락처 정보 Default 값으로 세팅</li>
  <li>새 연락처 추가 Flow와 동일</li>
  <li>유효성 검사 통과 시, 모달창 종료 및 기존 연락처 데이터 업데이트</li>
</td>
</tr>
</table>

#### 연락처 삭제 Flow
<table>
<tr>
<th>구동 화면</th>
<th>구현 기능</th>
</tr>
<tr>
<td>
<img src="https://github.com/comdori-wj/ios-contact-manager-ui/assets/76927263/d9b5e76d-703a-425c-a0d0-4ba9273e712a" width="auto" height="300" />
</td>
<td>
  <li>삭제하고자 하는 연락처 좌측으로 스와이프 시 삭제 버튼 나타남</li>
  <li>삭제 버튼 클릭 또는 좌측 끝으로 밀었을 때 연락처 삭제</li>
</td>
</tr>
</table>

#### Dynamic Type
<table>
<tr>
<th>구동 화면</th>
<th>구현 기능</th>
</tr>
<tr>
<td>
<img src="https://github.com/comdori-wj/ios-contact-manager-ui/assets/76927263/68a6b23f-0b8e-4604-8b98-d4a706412f34" width="auto" height="300" />
</td>
<td>
  <li><code>Dynamic Type</code>을 고려하여 글자 크기에 대한 <code>Accessibility</code> 대응</li>
  <li>CHCR 이용하여 <code>Multi-Line</code>code을 제한</li>
</td>
</tr>
</table>

#### 검색 Flow
<table>
<tr>
<th>구동 화면</th>
<th>구현 기능</th>
</tr>
<tr>
<td>
<img src="https://github.com/comdori-wj/ios-contact-manager-ui/assets/76927263/d914e725-71c5-4fc8-bb3b-130da0a39d3e" width="auto" height="300" />
</td>
<td>
  <li>상단에 <code>SearchBar</code> 추가하여 검색 기능 추가</li>
  <li>검색창 내 문자 없을 때 전체 리스트 나타남</li>
  <li>이름/나이/연락처 내 일치하는 값 있는 연락처 검색
    <ul>
    <li>이름은 대소문자 구분 없이 검색 가능</li>
    <li>연락처는 <code>-</code> 포함 여부와 관계 없이 검색 가능</li>
    </ul>
  </li>
</td>
</tr>
</table>

### 📍 구현 상세

- `Codable`, `Decodable` 프로토콜을 이용해 Json 파일 불러오기 기능 추가
- Json File 내 데이터를 위한 `DTO` 생성
- 코드를 통한 UI 및 `AutoLayout` 구현
- `Delegate Pattern` 이용하여 데이터 전달 및 활용
- 이름/연락처/나이가 중복되더라도 생성될 경우를 위해 `UUID` 식별자 사용
- `Array` 타입 확장을 통해 `Array Safety` 구현
- `String` 타입 확장하여 문자열 Fomatter 기능 추가
- `UIKit` 타입을 확장하여 addSubView와 같은 반복적으로 사용되는 로직을 하나의 메서드로 분리
- `Error`, `CustomStringConvertible` 프로토콜을 이용하여 상황에 맞는 `Error` 케이스 처리
- 반복되는 UI View의 로직 분리하여 재사용성 향상
- `Intrinsic Content`, `CHCR` 등을 이용해 `Dynamic Type` 대응
- 고차함수 `Filter`, `map`, `forEach` 등을 이용하여 구현
- 접근 제어

## 3️⃣ 습득 지식

<table>
<tr>
<th>🧑🏻‍💻 COMDORI</th>
<th>🐠 Janine</th>
</tr>
<tr>
<td>
<li>서브스크립트</li>
<li>model과 controller의 목적</li>
<li>private(set) 키워드</li>
<li>Modern Cell Configuration</li>
</td>
<td>
<li>Type 확장</li>
<li>Array Safety</li>
<li>Dynamic Type</li>
<li>AutoLayout
(<code>CHCR</code> / <code>Constraint</code> )</li>
<li>LLDB</li>
<li>DTO</li>
</td>
</tr>
</table>
