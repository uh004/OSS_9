# OSS-Chapter 9장 복귀 내용 정리

## 📌9.1 되돌리기
```
깃을 이용하여 버전을 관리하는 목적은 만일의 사태를 대비하기 위해서이다.
깃을 사용하면 언제든지 원하는 시점으로 전체 코드를 되돌릴 수 있습니다. 마치 코드 복구 시스템과 같습니다.
```

### 9.1.1 다시 시작
깃에서 코드 작업을 되돌리는 방법은 **reset**과 **revert** 두 가지가 있다. 간단한 실습을 통해 되돌리기를 알아보겠습니다.

실습 저장소 생성하기
```
$ mkdir gitstudy09 -- 새 폴더 만들기
$ cd gitstudy09 -- gitstudy09 이동
$ git init -- 저장소 초기화 
```

menu.htm 파일을 생성하고 내용을 입력
```
$ code menu.htm -- VS Code 실행
```

menu.htm
```
<ul>
</ul>
```

파일을 저장했다면 add 명령어로 등록 후 커밋
```
$ git add menu.htm -- 등록
$ git commit -m 'first' -- 커밋
```

menu.htm 파일에 menu1~menu5를 차례대로 커밋을 해보겠습니다.
```
<ul>
    <li>menu1</li>
</ul>
```

첫번째 menu1 커밋 하기
```
$ git commit -am 'menu1' -- menu1 등록 및 커밋
```

menu.htm 두번째 menu2 추가
```
<ul>
    <li>menu1</li>
    <li>menu2</li>
</ul>
```

두번째 커밋 하기
```
$ git commit -am 'menu2' -- menu2 등록 및 커밋
```

menu.htm 세번째 menu3 추가
```
<ul>
    <li>menu1</li>
    <li>menu2</li>
    <li>menu3</li>
</ul>
```

세번째 커밋 하기
```
$ git commit -am 'menu3' -- menu3 등록 및 커밋
```

menu.htm 네번째 menu4 추가
```
<ul>
    <li>menu1</li>
    <li>menu2</li>
    <li>menu3</li>
    <li>menu4</li>
</ul>
```

네번째 커밋 하기
```
$ git commit -am 'menu4' -- menu4 등록 및 커밋
```

menu.htm 다섯번째 menu5 추가
```
<ul>
    <li>menu1</li>
    <li>menu2</li>
    <li>menu3</li>
    <li>menu4</li>
    <li>menu5</li>
</ul>
```

다섯번째 커밋 하기
```
$ git commit -am 'menu5' -- menu5 등록 및 커밋
```

**총 여섯 단계에 거쳐 커밋을했습니다. 소스트리에서 확인 할 수 있습니다.**

![화면 캡처 2022-11-17 145246](https://user-images.githubusercontent.com/105197524/202367323-62b716f9-591e-4d68-8ea9-ea90b2291df8.png)

## 📌9.2 리셋
**리셋은 커밋을 기준으로 이전 코드로 되돌리는 방법으로, 기록한 커밋을 취소합니다. 커밋을 취소하는 만큼 리셋할 때는 항상 신중하게 작업해야 합니다.**

### 9.2.1 복귀 시점
**복귀는 어떤 시점으로 돌아가는 것을 의미한다.**<br>

현재 로그 확인하기
```
$ git log --oneline -- 로그확인
```
![화면 캡처 2022-11-17 150035](https://user-images.githubusercontent.com/105197524/202368475-8848bb24-034a-4b5c-b1fb-2e5a8a0cc1b5.png)

## 9.2.2 reset 명령어
**reset 명령어를 사용하면 지정된 커밋 코드로 되돌아갑니다.**

reset 사용법
```
$ git reset 옵션 커밋ID
```
reset 명령어는 옵션을 사용해야 하며 세 가지 옵션이 있다.
```
soft: 스테이지 영역을 포함한 상태로 복원
mixed: 기본 옵션 값은 mixed이다. reset 명령어를 사용할 때 옵션을 지정하지 않으면 기본값 mixed로 선택
hard: 실제 파일이 삭제된 이전 상태로 복원
```

### 9.2.3 soft 옵션
**soft 옵션은 가장 낮은 단계의 리셋 동작이다.**<br>

마지막 menu5 커밋이 사라지고 **커밋하지 않은 변경 사항**이 보입니다.
```
$ git reset --soft HEAD~ -- 이전 커밋으로 soft 옵션을 사용한 리셋
```
![화면 캡처 2022-11-17 151101](https://user-images.githubusercontent.com/105197524/202369905-eada3f80-c720-44ec-892b-cefb64dd3845.png)

리셋 한후 menu.htm 확인해보면 menu5가 있는것을 확인 할 수 있다.<br><br>
menu.htm
```
<ul>
    <li>menu1</li>
    <li>menu2</li>
    <li>menu3</li>
    <li>menu4</li>
    <li>menu5</li> -- menu5가 남아있음
</ul>
```


git diff 명령어로 비교해보겠습니다.

![화면 캡처 2022-11-17 151416](https://user-images.githubusercontent.com/105197524/202370453-600a3cdc-06dd-4428-9bec-885dbd862f74.png)
- diff 명령어를 실행한 결과 menu.htm 파일에 새로운 menu5가 추가된 것으로 나오게 됩니다.

깃의 상태 확인하기

![화면 캡처 2022-11-17 151731](https://user-images.githubusercontent.com/105197524/202371033-9738b4db-0ac6-463e-8dd8-97e26a3edbe5.png)

- 메뉴 파일은 수정된 상태입니다. **수정된 파일은 스테이지 영역에 등록되어 있습니다.** <br>

다시 실습을 위해 다시 meun5를 등록해서 커밋하겠습니다.
```
$ git commit -m 'menu5' -- 다시 커밋
```
![화면 캡처 2022-11-17 152118](https://user-images.githubusercontent.com/105197524/202371713-7e15a633-0575-4a1a-9701-42df9cf37903.png)
- 여기서 주의할 점은 커밋할 때마다 커밋의 해시 값이 변경된 점을 확인 할 수 있다.

![화면 캡처 2022-11-17 145246](https://user-images.githubusercontent.com/105197524/202368475-8848bb24-034a-4b5c-b1fb-2e5a8a0cc1b5.png)
```
$ git log --oneline -- 로그 확인
```

![화면 캡처 2022-11-17 152437](https://user-images.githubusercontent.com/105197524/202372214-58f6a181-d0a8-4581-b9e0-d6fe321785c7.png)

### 9.2.4 mixed 옵션
**reset 명령어의 기본값은 mixed 옵션이다.**

```
$ git reset --mixed 커밋ID
$ git reset 커밋ID -- mixed 생략 가능
```

이번에는 mixed 옵션을 실습해 보겠습니다.
```
$ git reset --mixed HEAD~ -- mixed 옵션을 사용한 리셋 실행
Unstaged changes after reset:
M       menu.htm
```
- mixed 옵션은 soft 옵션과 달리 **리셋한 후 스테이지 상태까지 복원하지 않습니다.**<br>

깃의 상태 확인하기
```
$ git status -- 상태 확인
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   menu.htm

no changes added to commit (use "git add" and/or "git commit -a")
```
- soft 옵션은 스테이지 상태까지 복원하기 때문에 바로 commit이 가능하지만 mixed 옵션은 커밋하려면 add 명령어를 먼저 실행해야한다.<br>

리셋 후 html.htm 파일 확인하기
```
$ code menu.htm -- VS Code 실행
```

menu.htm
```
<ul>
  <li>menu1</li>
  <li>menu2</li>
  <li>menu3</li>
  <li>menu4</li>
  <li>menu5</li>
</ul>
```
리셋 후에도 menu5 소스 코드가 남아있는 것을 확인 diff 명령어로 좀더 확인해보기

![화면 캡처 2022-11-17 153705](https://user-images.githubusercontent.com/105197524/202374166-e74751d1-7be8-45cd-aa96-f14b08194069.png)

- 새로운 menu5가 추가 되었다고 나와있고 변경 파일 내용은 워킹 디렉터리에 저장되었습니다.
![화면 캡처 2022-11-17 153919](https://user-images.githubusercontent.com/105197524/202374570-c79fd1d0-46ec-4cc6-8d14-8b98dcba6b52.png)

다시 실습 위해 menu5를 등록 해야하는데 add 후 commit을 해야합니다.
```
$ git add menu.htm -- 스테이지에 등록
$ git commit -m 'menu5' -- 커밋
```

이제 처음과 동일한 상태가 되었다.

![화면 캡처 2022-11-17 154209](https://user-images.githubusercontent.com/105197524/202375053-a44718d5-72eb-4cc5-a772-0873364667f1.png)
