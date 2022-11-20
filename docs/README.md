# 요구사항 분석
## 프로그래밍 요구사항
- [] 함수(또는 메서드)의 길이가 10라인을 넘어가지 않도록 구현한다.(함수(또는 메서드)가 한 가지 일만 잘하도록 구현한다.)
- [] 메서드의 파라미터 개수는 최대 3개까지만 허용한다.
- [] `InputView` 에서만 `MissionUtils`의 `Console.readLine()` 을 이용해 사용자의 입력을 받을 수 있다.
- [] `BridgeGame` 클래스에서 `InputView`, `OutputView` 를 사용하지 않는다.

## 기능 요구 사항
### 게임 시작
- [] `다리 건너기 게임을 시작합니다.\n\n` 문구를 출력하며 게임을 시작한다.

- [] `다리의 길이를 입력해주세요.\n`문구를 출력하며 다리의 길이를 숫자로 입력받고 생성한다.
  - [] 다리를 생성할 때 위아래 중 건널 수 있는 칸은 0, 1 중 무작위로 정한다.
  - [] 위 칸을 건널 수 있는 경우 U, 아래 칸을 건널 수 있는 경우 D로 나타낸다.
  - [] 0인 경우 U(아래 칸), 1인 경우 D(위 칸)이 건널 수 있는 칸이 된다.

- [] `이동할 칸을 선택해주세요. (위: U, 아래: D)`문구를 출력하며 플레이어가 이동할 칸을 선택한다.
  - [] 이동할 때 위 칸은 U, 아래 칸은 D를 입력한다.
  - [] 이동한 칸을 건널 수 있다면 O로 표시. 건널 수 없다면 X로 표시

  - [] 플레이어가 입력을 마치면 입력에 대한 다리 상태를 표시한다.
    ``` md
    [ O | X ]
    [   |   ]
    ```
  - [] 다리 상태를 출력한다.
    - [] 다리의 시작은 [ 표시(뒤 공백 포함)
    - [] 다리의 끝은 ] 표시(앞 공백 포함)
    - [] 이동할 수 있는 칸은 O 표시
    - [] 이동할 수 없는 칸은 X 표시
    - [] 선택하지 않은 칸은 공백 한칸으로 표시
    - [] 다리 칸 구분은 | 로 구분(앞, 뒤 공백 포함)

### 게임 종료
- [] 다리를 건너다 실패하면 게임을 재시작 or 종료할 수 있다.
- [] 재시작해도 처음에 만든 다리로 **재사용**한다.
  - [] R을 입력하면 재시도 처리한다.
    - [] 첫번째 칸부터 다시 시작한다.
    - [] 시도 횟수를 1증가한다.
      - [] 게임 결과의 총 시도한 횟수는 **첫 시도를 포함해 게임을 종료할 때까지 시도한 횟수**를 나타낸다.
  - [] Q를 입력하면 게임을 종료한다.
    - [] 최종 결과를 보여준다.
      ``` md
      최종 게임 결과
      [ O | X ]
      [   |   ]
      ```
      - [] `게임 성공 여부: 실패`를 출력한다.
      - [] `총 시도한 횟수: 1` 문구를 출력한다.
    - [] 게임을 종료한다.
  
- [] 다리를 끝까지 건너면 게임을 종료한다.
  - [] 최종 결과를 보여준다.
      ``` md
      최종 게임 결과
      [ O | O ]
      [   |   ]
      ```
      - [] `게임 성공 여부: 성공`를 출력한다.
      - [] `총 시도한 횟수: 1` 문구를 출력한다.

### 예외 처리
- [] 사용자가 잘못된 값을 입력한 경우 `throw`문을 사용해 예외를 발생시킨다.
- [] `"[ERROR]"`로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.
- [] 3 ~ 20의 숫자가 아닌 값이 입력되면 예외 처리한다.
  - [] 숫자가 아닌 값이 입력되면 예외를 발생시킨다.
  - [] 음수가 입력되면 예외를 발생시킨다.

- [] 사용자가 이동할 칸을 입력 받는다. U(위 칸), D(아래 칸)가 아니면 예외를 발생시킨다.

- [] 게임 재시작/종료 여부를 입력 받는다. R(재시작), Q(종료)가 아니면 예외를 발생시킨다.