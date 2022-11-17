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


