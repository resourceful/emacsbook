%
% Taesoo Kim
%
% title: 이맥스 설치 및 실행
%
% abstract: 시작하기에 앞서 이맥스를 설치하고, 작업환경을 갖춘다. 또한 설치된
% abstract: 이맥스의 디렉토리 구조를 개관적으로 살펴보고, 앞으로 사용할 용어를
% abstract: 정의한다.
%

자 이맥스의 세계에 온것을 환영한다. 많은 프로그래머들이 한번쯤 호기심에서 배워
보려고 하지만 번번히 실패하고 좌절하게 만드는 이맥스. 어떻게 하면 프로그래머들이
이맥스의 기본 원리와 개념을 올바로 이해할 수 있을까? 어떻게 하면 우리가 잘 알고
있는 지식들을 활용해 빠르게 습득할수 있을까? 필자가 독자들보다 조금 더 일찍
이맥스를 사용하기 시작했기에, 위의 질문들에 먼저 답을 해보았고, 그러한 선행
경험들을 바탕으로 독자들이 이맥스를 이해하는 과정에서 조금이나마 도움을 주고자
한다.

그럼 설치해볼까나?

# 설치하기

필자가 가장 즐겨쓰고 있는 우분투 배포판을 기준으로 설명하도록한다. 우분투 (데비안
계열) 배포판에서는 아래와 같이 최신 버젼의 이맥스를 설치할 수 있다.

    $ sudo apt-get install emacs23 emacs23-el emacs-goodies-el

이맥스는 오랜기간동안 사람들이 선호하는 기호에 따라 여러종류의 이맥스가 파생되어
개발이 되고 있다. 그 중 앞으로 초점을 맞추어 살펴보게 될 이맥스는 리차드스톨만이
처음 개발하고 일관된 철학으로 지금까지도 많은 사람들이 활발하게 사용하고
개발하고있는 그누이맥스이다.

간략하게 우리가 무엇을 설치하고 있는지 알아보면,

emacs23
:   이맥스 바이너리 및 컴파일된 기본 리습파일

emacs23-el
:   기본 리습 소스파일

emacs-goodies-el
:   추가적인 리습 라이브러리

한가지더, 이맥스의 소스파일을 추가적으로 다운받아 놓자.

    $ apt-get source emacs23
    
현재 디렉토리에 다운받아진 emacs23-[ver] 디렉토리를 ([ver]은 "23.2+1"와 같은
배포판에 종속적인 문자열) 원하는 곳으로 (예를 들면, /usr/src/emacs-[ver]) 옮겨
놓도록하자. 우리가 관심있게 살펴볼 소스코드들은 "emacs23-[ver]/src" 디렉토리에
모여 있다. 각각의 관심있는 소스파일들은 앞으로 필요할때마다 하나씩 천천히
알아보도록하자.

마지막으로, 우리는 무엇을 설치했는가?

/usr/share/emacs/[ver]/lisp
:   컴파일된 리습파일(.elc)과 압축된 리습파일(.el.gz)이 모여있는 디렉토리

/usr/share/emacs/[ver]/site-lisp
:   추가적인 리습라이브러리(예를 들면, emacs-goodies-el)이 모여있는 디렉토리

/usr/lib/emacs/[ver]/[arch]/
:   이맥스에서 내부적으로 사용되는 실행 파일들(예를 들면, hexl)이 모여있는 디렉토리

/usr/bin/emacs[ver]
:   이맥스 실행파일

기본적인 작업환경이 이해되었다면 본격적으로 이맥스에 대해 알아보자.

# 시작하기

흥미진진한 역사, 철학, 종교(?)적인 이야기는 아쉽지만 뒤로하고, 설치한 이맥스를
다음과 같은 명령으로 실행해 보자.

    $ emacs

![\n{img} 이맥스 GUI](\s{snap -s 80x33 -c -o emacs-gui-init.png})

실행된 GUI 버전의 이맥스를 종료하기전에 \m{File->Quit} 메뉴를 살펴보면 \k{C-x
C-c:종료}의 단축키가 적혀있는걸 볼 수 있다. 이맥스에서는 단축키를 아래와 같은 규칙을
가지고 나타낸다.

    C-[char]
    M-[char]

컨트롤(Ctrl)키는 알파벳 **C**로 메타(Meta)키는 **M**으로 나타내는데, 메타키는
일반 키보드의 Esc키와 Alt키를 의미한다. 즉 \k{C-x}는 컨트롤키를 **누른 상태**에서
키보드의 "x" 자판을 입력하는것을 의미하고, \k{C-x C-c}는 (반복하면) 컨트롤키를
**누른 상태**에서 "x" 자판을 입력하고, (여전히) 컨트롤키를 *누르고 있는 상태*에서
"c" 자판을 입력하는것이다.

다시 이맥스를 실행하자. 

    $ emacs -nw

![\n{img} 이맥스 CUI](\s{snap -o emacs-cui-init.png -e emacs-terminal.sh})

필자는 종종 간단한 설정파일을 수정하기위해서 위의 명령으로 터미널에서 이맥스를
실행하곤한다. (-nw는 --__n__o-__w__indow의 약자로 쉽게 기억할수 있다.) 터미널에서
실행되고 있는 CUI 이맥스가 이전에 실행시킨 GUI 이맥스와 유사해 보이지만, 터미널
안의 이맥스를 종료하려고하면 직관적인 방법으로는 종료할 수 없음을 알 수
있을것이다. (\k{C-c}를 연달아 입력해도 정의되지 않았다는 에러 메시지만 보일
뿐이다.) 여느 이맥스 사용자와 마찬가지로, 필자는 또한 처음 이맥스를 실행한후
종료하지 못해 당황한 적이있다. 그 이후 오랫동안 이맥스를 배우려고 하지 않았기
때문에 독자들에게 가장먼저 알려주고 싶었던 것이 "종료"하는 방법이었다. 터미널 속
이맥스 역시 \k{C-x C-c}로 종료할 수 있다. 두 가지 버전의 이맥스는 동일한
프로그램으로 그래픽에 종속적인 기능들을 제외하고는 동일하게 동작한다.

# 용어 통일하기

명확한 의사 전달을 위해서는 사용할 용어를 먼저 정의하는게 가장 중요하다. 앞으로
사용할 기본적인 용어들을 정리하면,

![\n{img} 이맥스 구성 \t{+add a layer}](\s{snap -o emacs-screen-org.png
  -a "--no-init script/snap.sh" M-x "\"flyspell-prog-mode\"" RET C-x C-f TAB})

버퍼
:   **기본적인 편집의 장소** (파일 <-> 버퍼 <-> 이맥스).
    버퍼는 이맥스가 편집을 할 수 있는 공간이고, 파일은 버퍼라는 형태로 이맥스
    안에서 처리된다. 사용자는 여러개의 버퍼를 가질수 있지만, 오직 하나의 버퍼만
    수정할 수 있다. 

윈도우
:   **버퍼의 출력** (버퍼 <-> 윈도우 <-> 사용자).
    버퍼는 윈도우를 통해야만 사용자에게 보여질 수 있다. 다른 두개의 윈도우가
    하나의 버퍼를 출력할수있다. 하지만 하나의 윈도우는 반드시 하나의 버퍼만을
    나타낼 수 있다.

프레임
:   **윈도우의 배열** (윈도우 <-> 프레임 <-> 사용자).
    프레임은 여러 윈도우를 가질 수 있고, 이들의 배열을 결정한다. 즉 프레임의
    윈도우 배열을 수정하여 윈도우를 수직/수평으로 나열할 수 있다.

미니버퍼
:   **사용자 입력 및 메시지 출력**
    복잡한 사용자의 입력을 받고, 입력 상태(에코)를 나타내주는 특별한 윈도우이다.

상태바
:   **버퍼의 상태(정보)** (파일이름, 커서위치, 모드 ..)등을 출력

메이저 모드
:   **옵션들의 집합**. 하나의 버퍼는 하나의 메이저 모드를 갖는다. 예를 들면
    각각의 프로그램 언어는 일반적으로 하나의 메이저 모드로 정의된다. (c-mode,
    python-mode, etc)

마이너 모드
:   **독립적인 옵션들의 집합**. 메이저 모드와 달리 하나의 버퍼는 사용자의 기호에
    따라 여러 마이너 모드를 쓸 수 있다. 예를 들면 스팰링 체크 (flyspell-mode)와 
    자동 줄내림 (auto-fill-mode)등 각각의 기능들이 하나의 마이너 모드로 정의된다.

앞으로 사용할 기본적인 용어들을 정의했다. 하지만, 더욱 자세하고 명확한 용어들에
대한 정의를 보고 싶을때는 \m{Help->Search Document->Emacs Terminology}를 통해서
꼭 확인해 보기 바란다.

# Lisp 맛보기

확장성이 뛰어난, 그래서 프로그램가능한 에디터는 어떻게 만들수 있을까? 필자와 같이
조그만한 에디터를 디자인해보자. 필자가 생각하는 에디터는 키보드입력을 처리하는
부분과 이를 출력하는 부분, 크게 두개의 부분으로 구성이 된다. 그러면 에디터를
어떻게 C언어로 구현할 수 있을까? 키보드 입력부분에서 OS를 통해 자판코드를
읽어오면, 룩업테이블(코드 -> 함수)을 찾아 해당 함수를 호출하게 할것이다. 호출된
함수에서는 나의 입력을 처리하고 화면에 그 결과를 출력해 주면 될것이다.

이렇게 디자인한 에디터가 확장성이 있을까? 만약 에디터가 사용하는 프로그램언어에
따라 다른 기능을 제공하고 싶으면 어떻게 룩업테이블을 디자인하면 좋을까? 아마도
에디터가 지원하는 언어들에 해당하는 각각의 룩업테이블을 만들고 사용하고 있는
언어에 따라 키보드 입력부분에서 해당 룩업테이블을 사용하면 될것이다. 이맥스는
필자가 설명하고 있는 하나하나의 작업들을 모두 사용자에게 이맥스리습이라는 언어로
노출하고 있다. 

이맥스를 다시 실행하고 \k{C-x b:버퍼변경}을 입력해보자. 다시한번, \k{C-x b}는
컨트롤키를 *누른상태*에서 **c**을 누르고, (컨트롤키를 *때고*) **b**을 누르면
된다. \k{C-x b}를 실행하면 "Switch to buffer" 프롬프트가 미니버퍼에 나타난것을
볼 수 있다. 여기서 Tab키를 눌러보자. 화면에 아래와 같은 버퍼 목록을 볼 수 있다.

    *Messages*
    *scratch*

![\n{img} 이맥스 버퍼](\s{snap -s 80x25 -o switching-buffers.png -c 
   C-x b "\"*sc\"" TAB RET "\"(message \\\"hello world\\\")\"" 
   C-j C-x b "\"*\"" TAB})

이맥스에서는 관행적으로 파일로 매핑되어 있지 않는 특별한 버퍼이름 앞에 \*를 붙여
관리 한다. 기본적으로 이맥스는 위에 나열된 두개의 특별한 버퍼를 생성한다.
Message 버퍼는 이맥스가 출력했던 메시지들이 기록되며, Scratch (스크레치북의
스크레치) 버퍼는 저장하지 않을 목적으로 노트하거나, (더욱 중요하게) 이맥스함수를 
evaluate하기 위한 목적으로 사용된다.

자 그럼 이맥스리습을 맛보기위해서 scratch 버퍼를 열어 보자. \k{C-x b}후
\*scr[TAB]으로 자동완성해서 scratch 버퍼를 선택하자. 그리고 첫 lisp 프로그램을
만들어 보자.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.cl}
(message "hello world")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

위의 표현식을 evaluate하기 위해서 마지막 괄호 다음에 커서를 두고 \k{C-j}를
눌러보자.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.cl}
(message "hello world")
"hello world"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

표현식 아래 결과(리턴)값과 미니버퍼 (스크린 아래)에 "hello world"가 출력됨을 알
수 있다. 그럼 위의 표현식이 어떤 의미를 하는지 알아보자.

    +--- 표현식의 시작
    v
    (message "hello world")
      함수       문자열     ^
                          |
           표현식의 끝 -----+

우리가 쉽게 추측해 볼 수 있듯, 위의 표현식은 message라는 함수를 "hello world"의
문자열을 인자로하여 호출한 것이다. 사실 이것이 lisp의
syntax의 전부이다. lisp에서는 일반 imperative 언어에서 특별하게 여겨지는 표현식,
제어문 등 또한 하나의 함수 호출의 형태를 띄고있다. 그러면 우리가 호출할 수 있는
함수는 무엇이며 어떻게 사용할 수 있을까?

# 정리

이번 장에서는 간략하게 어떻게 이맥스가 구성되는지 알아보았다. 혹시 독자가 이맥스의
기능들을 어떻게 추상화(abstraction)시켜 리습이라는 언어가 자유롭게 접근할 수 있게
되었을까? 그리고 왜 리습이라는 언어이어야만 했을까? 라는 의문이 들었다면, 필자의
목적이 충분히 전달되었다고 생각된다.

다음 장으로 넘어가기전에 두가지 *반드시* 해야되는 숙제가 있다.

 - 이맥스 튜토리얼 \m{Help->Tutorial} 따라하기
 - 이맥스 가이드투어 훑어보기 \l{http://www.gnu.org/software/emacs/tour/}
 - (선택) 이맥스 논문 훑어보기 \l{http://www.gnu.org/software/emacs/emacs-paper.html}
