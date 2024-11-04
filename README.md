# javascript-lotto-precourse

# **로또**

## **과제 진행 요구 사항**

- 미션은 [로또](https://github.com/woowacourse-precourse/javascript-lotto-7) 저장소를 포크하고 클론하는 것으로 시작한다.
- **기능을 구현하기 전 `README.md`에 구현할 기능 목록을 정리**해 추가한다.
- Git의 커밋 단위는 앞 단계에서 `README.md`에 정리한 기능 목록 단위로 추가한다.
  - [AngularJS Git Commit Message Conventions](https://gist.github.com/stephenparish/9941e89d80e2bc58a153)을 참고해 커밋 메시지를 작성한다.
- 자세한 과제 진행 방법은 프리코스 진행 가이드 문서를 참고한다.

## **기능 요구 사항**

간단한 로또 발매기를 구현한다.

- 로또 번호의 숫자 범위는 1~45까지이다.
- 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
- 당첨 번호 추첨 시 **중복되지 않는 숫자 6개와 보너스 번호 1개**를 뽑는다.
- 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
  - 1등: 6개 번호 일치 / 2,000,000,000원
  - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
  - 3등: 5개 번호 일치 / 1,500,000원
  - 4등: 4개 번호 일치 / 50,000원
  - 5등: 3개 번호 일치 / 5,000원
- 로또 구입 금액을 입력하면 구입 금액에 해당하는 만큼 로또를 발행해야 한다.
- 로또 1장의 가격은 1,000원이다.
- 당첨 번호와 보너스 번호를 입력받는다.
- 사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료한다.
- 사용자가 잘못된 값을 입력할 경우 "[ERROR]"로 시작하는 메시지와 함께 `Error`를 발생시키고 해당 메시지를 출력한 다음 해당 지점부터 다시 입력을 받는다.

### **입출력 요구 사항**

### **입력**

- 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 **예외 처리**한다.

```
14000
```

- 당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다. **예외 입력값이 숫자가 아니거나 범위 내의 숫자가 아닐 때**

```
1,2,3,4,5,6
```

- 보너스 번호를 입력 받는다. **예외 위와 같다**

```
7
```

### **출력**

- 발행한 로또 수량 및 번호를 출력한다. 로또 번호는 오름차순으로 정렬하여 보여준다.

```prolog
8개를 구매했습니다.
[8, 21, 23, 41, 42, 43]
[3, 5, 11, 16, 32, 38]
[7, 11, 16, 35, 36, 44]
[1, 8, 11, 31, 41, 42]
[13, 14, 16, 38, 42, 45]
[7, 11, 30, 40, 42, 43]
[2, 13, 22, 32, 38, 45]
[1, 3, 5, 14, 22, 45]
```

- 당첨 내역을 출력한다.

```
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
```

- 수익률은 소수점 둘째 자리에서 반올림한다. (ex. 100.0%, 51.5%, 1,000,000.0%)

```erlang
총 수익률은 62.5%입니다.
```

- 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.

```prolog
[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.
```

### **실행 결과 예시**

```prolog
구입금액을 입력해 주세요.
8000

8개를 구매했습니다.
[8, 21, 23, 41, 42, 43]
[3, 5, 11, 16, 32, 38]
[7, 11, 16, 35, 36, 44]
[1, 8, 11, 31, 41, 42]
[13, 14, 16, 38, 42, 45]
[7, 11, 30, 40, 42, 43]
[2, 13, 22, 32, 38, 45]
[1, 3, 5, 14, 22, 45]

당첨 번호를 입력해 주세요.
1,2,3,4,5,6

보너스 번호를 입력해 주세요.
7

당첨 통계
---
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 62.5%입니다.
```

## 구현할 기능 목록

1. 사용자에게 입력 받기

- 구입 금액
  **구입 금액 관련 에러**
  - 구입 금액이 1천원 단위가 아닐 경우 에러 발생
- 6자리 당첨 번호
  **당첨 번호 관련 에러**
  - 입력한 당첨 번호간 중복될 경우
  - 당첨 번호 입력시 1 ~ 45 사이의 숫자가 아닌 경우
  - 쉼표로 구분되지 않는 경우
  - 숫자가 아닌 경우
- 보너스 번호
  **보너스 번호 관련 에러**
  - 당첨 번호와 중복될 경우
  - 1 ~ 45 사이의 숫자가 아닌 경우

2. 로또 발행하기

- 랜덤하게 6개의 숫자 뽑기
- 중복 여부 확인
- 중복될 경우 다른 숫자 뽑기
- 뽑은 숫자 오름차순 정렬하기

3. 당첨 확인하기

- 당첨 번호, 보너스 번호와 대조하기
- 일치하는 케이스 분류하기

4. 당첨 통계 계산하기

- 일치하는 케이스를 통해 수익 금액 계산하기
- 수익 금액과 구입 금액 간 계산하기

5. 사용자에게 출력하기

- 발행한 로또 갯수 출력하기
- 발행한 로또 출력하기
- 4번에서 계산한 당첨 통계 출력하기