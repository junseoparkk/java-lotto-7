# java-lotto-precourse

## 3주차 - 로또

---
## 🎯 목표
### 1. Java 기능 적극 활용하기
- Enum
- Functional Interface
- Stream API

### 2. TDD 적용하기
- 구현 단계에서 발생 가능한 버그를 미리 발견하고 방지하기 위해 적용해보고자 함
- 최대한 `Red-Green-Refactor` 사이클을 준수하고, 작은 단위로 커밋 메시지 작성
    - 🔴 : `test`
    - 🟢 : `feat`
    - 🔵 : `refactor`
- 모든 기능에 대한 테스트를 먼저 작성하고, 테스트 커버리지를 점차 확장

### 3. 그 외
- 비즈니스 로직이 복잡해진 로또 미션에서 service, repository 추가 고려
- 처음엔 도메인 로직부터 구현했지만, 시간이 오래 걸리고 수정이 빈번해짐. 이에 프로그램 흐름 순서로 구현 시도
- 코드 리뷰 및 공통 피드백의 내용을 바탕으로 부족한 부분을 보완하고자 함

---
## ⌛️ 프로그램 흐름
1. 구입 금액 입력
2. 구매한 금액 만큼 로또 생성 및 결과 출력
3. 당첨 번호 입력
4. 보너스 번호 입력
5. 당첨 통계 출력

---
## 🚀 기능 목록

### 1. 로또 번호 기능
- [X] 로또 번호를 검증한다.
    - [X] `예외사항`: 로또 번호가 6개의 숫자가 아니라면 예외 발생
    - [X] `예외사항`: 로또 번호가 1~45 사이의 숫자가 아니라면 예외 발생
    - [X] `예외사항`: 로또 번호에 중복된 숫자가 존재하면 예외 발생
- [X] 로또 번호를 오름차순으로 정렬한다.

### 2. 로또 번호 생성 기능
- [ ] 로또 번호를 생성한다.
    - [ ] 중복되지 않는 6개의 숫자를 뽑는다.
    - [ ] 각 숫자는 1~45 사이의 숫자여야 한다.

### 3. 로또 발행 기능
- [ ] 1개의 로또를 발행한다.
- [ ] 구입 금액에 해당하는 만큼 로또를 발행한다.
    - [ ] 로또 1장의 가격은 1,000원이다.

### 4. 로또 구매 기능
- [ ] 사용자로부터 구입 금액을 입력 받는다.
    - [ ] `예외사항`: 숫자가 아니라면 예외 발생
    - [ ] `예외사항`: 1,000원 단위가 아니라면 예외 발생
    - [ ] `예외사항`: 100,000원을 초과하면 예외 발생 (1회 최대 구입 금액)

### 5. 로또 번호 입력 기능
- [ ] 사용자로부터 당첨 번호를 입력 받는다.
    - [ ] `예외사항`: 쉼표(,)로 구분할 수 없다면 예외 발생
- [ ] 사용자로부터 보너스 번호를 입력 받는다.
    - [ ] `예외사항`: 숫자가 아니라면 예외 발생
    - [ ] `예외사항`: 1~45 사이의 숫자가 아니라면 예외 발생
    - [ ] `예외사항`: 당첨 번호에 포함된 숫자라면 예외 발생

### 6. 로또 결과 계산 기능
- [ ] 구매한 로또로부터 순위와 당첨 금액을 계산한다.
    - 1등: 6개 번호 일치 / 2,000,000,000원
    - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
    - 3등: 5개 번호 일치 / 1,500,000원
    - 4등: 4개 번호 일치 / 50,000원
    - 5등: 3개 번호 일치 / 5,000원
- [ ] 당첨 금액으로부터 총 수익률을 계산한다.
    - [ ] 수익률 = (당첨 금액 / 구매 금액) * 100
    - [ ] 수익률은 소수 둘째 자리에서 반올림한다.

### 7. 로또 결과 출력 기능
- [ ] 당첨 통계를 출력한다.
  > 3개 일치 (5,000원) - 1개 <br>
  4개 일치 (50,000원) - 0개 <br>
  5개 일치 (1,500,000원) - 0개 <br>
  5개 일치, 보너스 볼 일치 (30,000,000원) - 0개 <br>
  6개 일치 (2,000,000,000원) - 0개 <br>
- [ ] 총 수익률을 출력한다.
    - [ ] 콤마(,)를 통해 숫자를 3자리씩 구분한다.

### 8. 그 외
- [ ] 사용자가 잘못된 값을 입력할 경우 `IllgalArgumentException`을 발생시키고, 다시 입력 받는다.
- [ ] 에러가 발생할 경우 `[ERROR]`로 시작하는 에러 메시지를 출력한다.
- [ ] 제공된 라이브러리를 사용한다.
    - `camp.nextstep.edu.missionutils.Randoms` 의 `pickUniqueNumbersInRange()`
    - `camp.nextstep.edu.missionutils.Console` 의 `readLine()`

---
## ⚙️ 테스트 목록
### 규칙
> ❌ : 실패하는 테스트만 작성된 상태 <br>
> ✅ : 기능 구현 후 테스트를 통과한 상태 <br>
> 모든 테스트가 통과하면 TO-DO 에 체크 표시하기

### 1. 로또 번호 기능 테스트
- [X] 로또 번호 검증 기능을 테스트한다.
    - ✅ `예외사항`: 로또 번호가 6개의 숫자가 아니라면 예외 발생
    - ✅ `예외사항`: 로또 번호가 1~45 사이의 숫자가 아니라면 예외 발생
    - ✅ `예외사항`: 로또 번호에 중복된 숫자가 존재하면 예외 발생
- [X] 로또 번호이 오름차순으로 정렬되었는지 테스트한다.

### 2. 로또 번호 생성 기능 테스트
- [ ] 로또 번호 생성 기능을 테스트한다.
    - [ ] 중복되지 않는 6개의 숫자를 뽑는다.
    - [ ] 각 숫자는 1~45 사이의 숫자여야 한다.

### 3. 로또 발행 기능 테스트
- [ ] 1개의 로또를 발행하는 기능을 테스트한다.
- [ ] 구입 금액에 해당하는 만큼 로또를 발행하는 기능을 테스트한다.
    - [ ] 로또 1장의 가격은 1,000원이다.

### 4. 로또 구매 기능 테스트
- [ ] 구입 금액 검증 기능을 테스트한다.
  - [ ] `예외사항`: 숫자가 아니라면 예외 발생
  - [ ] `예외사항`: 1,000원 단위가 아니라면 예외 발생
  - [ ] `예외사항`: 100,000원을 초과하면 예외 발생 (1회 최대 구입 금액)

### 5. 로또 번호 입력 기능 테스트
- [ ] 당첨 번호 검증 기능을 테스트한다.
  - [ ] `예외사항`: 쉼표(,)로 구분할 수 없다면 예외 발생
- [ ] 보너스 번호 검증 기능을 테스트한다.
  - [ ] `예외사항`: 숫자가 아니라면 예외 발생
  - [ ] `예외사항`: 1~45 사이의 숫자가 아니라면 예외 발생
  - [ ] `예외사항`: 당첨 번호에 포함된 숫자라면 예외 발생

### 6. 로또 결과 계산 기능 테스트
- [ ] 구매한 로또로부터 순위와 당첨 금액을 계산하는 기능을 테스트한다.
  - 1등: 6개 번호 일치 / 2,000,000,000원
  - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
  - 3등: 5개 번호 일치 / 1,500,000원
  - 4등: 4개 번호 일치 / 50,000원
  - 5등: 3개 번호 일치 / 5,000원
- [ ] 당첨 금액으로부터 총 수익률을 계산하는 기능을 테스트한다.
  - [ ] 수익률 = (당첨 금액 / 구매 금액) * 100
  - [ ] 수익률은 소수 둘째 자리에서 반올림한다.