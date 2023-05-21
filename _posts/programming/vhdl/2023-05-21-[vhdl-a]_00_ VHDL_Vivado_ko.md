---
layout: single
title: "[VHDL-a] 00 Vivado를 이용한 VHDL"
folder: "vhdl"
categories:
  - vhdl

tags: [blog, vhdl, alzio]

author_profile: true
sidebar:
  nav: "sidebar-category"

toc: true
toc_label: "list"
toc_icon: "bars"
toc_sticky: true
classes: wide

lang: de
lang-ref: multilingual

use_math: true

date: 2023-05-21
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>

<pre>
OS    : Window
Editor: VScode, Vivado 2023</pre>
</div>

<div class="notice--warning">
Vivado 설치 부분은 자신의 pc상태와 현재 학생신분인지에 따라 다르므로.. 다른 블로그를 참고하자.
</div>

# 00 Vivado 기본설정, 간단 용어 및 확인

Vivado에서 코드작업 할 때 한글로 주석을 넣고 싶다면,

`vivado 윈도우 왼쪽 바(Flow Navigator)에서 Settings > Text Editor > Font and Colors`

상단에 적어둔 탭에 가서 폰트를 나눔 굴림이나 뉴 굴림(New Gulim) 등 다른 폰트로 변경하면 된다.

나는 vivado에서 직접 코딩작업을 하지 않고 VS Code를 사용하기 때문에 딱히 바꿀 필요는 없었다.

## 00-1 파일명과 모듈명

파일명은 말그대로 파일이름이고 당연히 해당파일을 보면 알 수 있다. Vivado의 프로젝트 파일은 `.xpr`이며 `프로젝트이름.xpr` 으로 되어 있다. 추후에 다시 해당 프로젝트를 열고 싶을 때는 해당 파일을 열면 된다. 소스파일은 vhdl이므로 확장자는 `.vhd` 이며 Vivado에서 소스파일로 불러오거나 다른 편집프로그램(VS Code)등으로 열어서 수정할 수 있다.

모듈명은 코딩에서 entity 다음에 적는 이름을 말한다. 아래에 예를 적어둔다.

```vhdl
entity and_gate is
--  Port ( );
end and_gate;
```

위에 예시코드에서 모듈명은 and_gate가 되겠다.

`기본적으로 파일명과 모듈명은 동일하게 작업하는 것이 좋다.`

<div class="notice--info">
Vivado를 통해 새 프로젝트를 생성하면 여러가지 폴더들이 생겨 폴더가 지저분해지는 경우가 많으므로 나는 소스코드만 따로 정리하는 편이다. 크게 세개로 나누는데 예를 들면,<br>
<br>
1.Vivado 파일들<br>
"vhdl파일을 모아둔 작업폴더"/"프로젝트폴더"/"vivado관련파일(프로젝트폴더를 경로로 새 프로젝트를 만들면 자동으로 만들어지는 폴더)" <br>
<br>
2.vhdl이 있는 src폴더(따로 생성)<br>
"vhdl파일을 모아둔 작업폴더"/"프로젝트폴더"/src<br>
<br>
3.modelSim을 위한 work폴더<br>
"vhdl파일을 모아둔 작업폴더"/"프로젝트폴더"/work<br>
</div>

# 01 시작

기초적인 vhdl코드부터 시작해보자. Vivado에서 새프로젝트 새파일(and_gate)을 생성하면 다음과 같은 기본적인 코드 틀을 만들어 준다. 특별한 부분은 없으니 VS Code에서 그냥 입력해도 무관하다.

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity and_gate is
--  Port ( );
end and_gate;

architecture Behavioral of and_gate is

begin


end Behavioral;
```

해당 코드는 크게 세 부분으로 나눌 수 있겠다.

**1.라이브러리 부분**

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
```

**2.입출력 포트를 설정하는 entity부분**

```vhdl
entity and_gate is
--  Port ( );
end and_gate;
```

**3.실제 동작 정의하는 architecture부분**

```vhdl
architecture Behavioral of and_gate is

begin


end Behavioral;
```

Behavioral 같은 경우는 동작의 이름을 지정하는 것인데 특별히 동작방식을 지정하는 경우가 아니기에 그대로 사용하겠다.

`코드의 보라색 부분들은 지정된 함수이름들 이므로, 작업할 때 해당 단어들은 사용하지 않도록 유의하자.`

## 01-1 간단한 게이트 작성 and-gate, or-gate

entity부분은 앞서 적은 것 처럼 입출력 포트 즉 껍데기를 표현한다고 보면 되는데 and게이트를 예를 들면 다음과 같이 적을 수 있다.

```vhdl
entity and_gate is
    Port (  a, b: in std_logic;
            c   : out std_logic);
end and_gate;
```

in 은 input이라는 의미이다.  
out 은 output이라는 의미이다.  
std_logic

```vhdl
architecture Behavioral of and_gate is

begin
    c <= a and b;
end Behavioral;
```

and게이트의 동작부분은 간단하게 위와 같이 and를 이용해서 적으면 끝이다. 당연하게도 and뿐만 아니라 xor 등을 사용 가능하다. 따라서 or게이트를 동일한 방식으로 작성하면 다음과 같다.

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity or_gate is
    Port (  d   : in std_logic;
            e   : in std_logic;
            f   : out std_logic);
end or_gate;

architecture Behavioral of or_gate is

begin
    f <= d or e;
end Behavioral;
```

process를 이용해서 직접 하나씩 정의하는 방법도 있다. architecture부분만 수정하면 되는데 아래와 같이 적으면 된다.

```vhdl
architecture Behavioral of or_gate is

begin
    process(d,e)
    begin
        if d = '1' or e ='1' then
            f <='1';
        else
            f <='0';
        end if;
    end process;
end Behavioral;
```

process를 사용하면 마찬가지로 시작과 끝을 표시하는 begin과 end도 만들어야 한다.

process가 동작을 하는 인수 값(프로세스가 돌아가기 위한 조건)들은 괄호안에 넣어준다. 예시코드에서는 인풋값이 d와 e 이므로 process(d,e)이렇게 적었다.

or-gate를 표현하기 위해서 if문을 사용했다. if문은 다른 언어들과 비슷하게 다음과 같다:

`if "조건" then "해당조건이 참일때 동작"`

다른 점은 if문이 끝나는 지점에 `end if`를 꼭 써주어야 한다는 것이다.

d와 e 둘 중에 하나라도 1이면 1이 f로 출력된다.

and게이트를 만들었던 것 처럼 간단하게 xor게이트도 만들어 주면 다음과 같다.

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity xor_gate is
    Port (  g, h: in std_logic;
            i   : out std_logic);
end xor_gate;

architecture Dataflow of xor_gate is

begin
    i <= g xor h;
end Dataflow;
```

## 01-2 게이트들을 통합하기(소자만들기)

앞서 만든 3개의 게이트를 통합하여 연결하는 소자를 만들어 보자.
새 파일로 Gate_st.vhd파일을 생성하고 다음과 같이 적어준다.

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity Gate_st is
    Port (  in0     : in std_logic;
            in1     : in std_logic;
            in2     : in std_logic;
            in3     : in std_logic;
            out0    : out std_logic);
end Gate_st;

architecture Behavioral of Gate_st is

begin

end Behavioral;
```

위의 예시코드에서는 input이 4개 output은 1개인 Gate_st모델이다.  
이전에 만든 게이트들의 총 인풋의 개수는 6개이지만, 연결해서 사라질 2개의 인풋을 제외하고 나머지 4개만 정의한 것이다.

이제 컴포넌트를 선언해 보자.  
컴포넌트를 선언한다는 것은 부속품(부품)을 선언한다는 것이다.

컴포넌트를 선언 할 때는 각 부품의 포트들도 넣어줘야한다.  
여기서 주의할 점은 and게이트(and_gate.vhd)에서 정의한 포트를 동일하게 가져와야한다.  
(이름에 변경이 없어야 하고 정의한 방식도 같아야 함. 따라서 복붙해서 가져오는 것이 좋다.)

따라서 다음과 같이 선언 할 수 있다:

```
architecture Behavioral of Gate_st is

    component and_gate
        Port (  a, b: in std_logic;
                c   : out std_logic);
    end component;

    component or_gate
        Port (  d   : in std_logic;
                e   : in std_logic;
                f   : out std_logic);
    end component;

    component xor_gate
        Port (  g, h: in std_logic;
                i   : out std_logic);
    end component;

    signal s1, s2 : std_logic;

begin

end Behavioral;
```

컴포넌트를 정의한 후에는 해당 부품들을 연결하기위해 signal도 정의해 주어야 한다.
2개의 output을 2개 의 input과 연결할 것이기 때문에 signal은 두개 필요하다. 따라서 s1,s2 이렇게 두개만 만들어주었다.
여기까지하면, 맵핑을 위한 준비는 끝이다.

이제 실제로 맵핑을 하는 부분을 작성하는데, 그 부분은 begin과 end Behavioral 사이에 작성해야 한다.
각 포트들이 어떻게 매치되어야 하는지를 작성하면 다음과 같다:

```vhdl
begin
    and_gate_connect  : and_gate port map (in0, in1, s1);
    or_gate_connect   : or_gate port map  (in2, in3, s2);
    xor_gate_connect  : xor_gate port map (s1, s2, out0);

end Behavioral;
```

매치되는 부분을 위와 같이 작성할 수 있는데, 게이트 이름뒤에 \_connect를 적어서 임의로 이름을 작성하고(아무 이름이나 상관없다. 구분을 편하게 하기 위해 그냥 \_connect를 사용했다.) 각 부품(게이트)들의 이름을 입력후, port map을 이용해 현재 소자(Gate_st)에서 작성한 4개의 인풋과 1개의 출력 그리고 2개의 signal이 어떻게 매치될지 생각하면서 입력한다. 또한 각 게이트들의 인풋과 아웃풋이 정의된 순서에 맞게 정의해 주어야 한다.

여기까지 작업이 잘 완료되었다면 Sources 윈도우에 아래와 같이 게이트들이 Gate_st에 묶여서 나타난다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/vhdl/img/00_a_sorceswindow.jpg?raw=true" />

그 후에는 왼쪽 네비게이터에서 RLT ANALYSIS > Open Elaborated Design을 눌러 최종적으로 도식화 된 이미지를 볼 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/vhdl/img/00_a_schematic.jpg?raw=true" />

## 01-3 testbench파일 만들기

testbench파일은 지금까지 작업한 것의 파형을 보기 위해 필요한 파일이다.
동일하게 src폴더에 vhd확장자의 파일을 만들면 되는데, 보기 편하게 하기 위해 일반적으로 파일명 뒤에 \_tb를 붙여서 만든다.
예시로 Gates_tb.vhd파일을 다음과 같이 만들어 보았다.

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity Gates_tb is
end Gates_tb;

architecture Behavioral of Gates_tb is

    component Gate_st
    Port (  in0     : in std_logic;
            in1     : in std_logic;
            in2     : in std_logic;
            in3     : in std_logic;
            out0    : out std_logic);
    end component;


begin


end Behavioral;
```

이전에 작업했던 Gate_st처럼 component를 정의하지만 testbench에서는 좀 더 자세하게 정의해야 한다.
즉, 초기값의 정의가 필요하다. 다음과 같이 초기값에 대한 정보를 추가한다.:

```vhdl
architecture Behavioral of Gates_tb is

    component Gate_st
    Port (  in0     : in std_logic;
            in1     : in std_logic;
            in2     : in std_logic;
            in3     : in std_logic;
            out0    : out std_logic);
    end component;

    -- inputs --
    signal in0 : std_logic := 0;
    signal in1 : std_logic := 0;
    signal in2 : std_logic := 0;
    signal in3 : std_logic := 0;

    -- outputs --
    signal out0 : std_logic;

begin


end Behavioral;
```

초기값의 대한 정의가 끝났다면, Gate_st에서 작업했던 포트들을 가져와야 한다.(맵핑)  
그 방법은 다음과 같다.

```vhdl
begin

    uut: Gate_st port map(
        in0 => in0,
        in1 => in1,
        in2 => in2,
        in3 => in3,
        out0 => out0
    );

end Behavioral;
```

이제 입력신호가 바뀌는 것에 따른 파형을 보기 위해서 시간에 따라 입력 신호를 바꿔주어야 하는데, 그 부분은 process를 만들어서 설정해 줄 수 있다. 다음의 예제 코드는 ns간격으로 신호를 나누어 넣은 모습이다.

```vhdl
begin

    uut: Gate_st port map(
        in0 => in0,
        in1 => in1,
        in2 => in2,
        in3 => in3,
        out0 => out0
    );

    stim_proc: process
    begin
        wait for 100 ns;
        in0 <=  '0',                -- 처음에 0으로 시작
                '1' after 10 ns,    -- 10ns후에 1을 넣는다.
                '0' after 20 ns,
                '1' after 30 ns;

        in1 <=  '0',
                '1' after 5 ns,
                '0' after 10 ns,
                '1' after 15 ns;

        in2 <=  '0',
                '1' after 10 ns,
                '0' after 20 ns,
                '1' after 30 ns;

        in3 <=  '0',
                '1' after 5 ns,
                '0' after 10 ns,
                '1' after 15 ns;

    end process;


end;
```

이제 왼쪽 navigator에서 run Simulation으로 파형을 확인할 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/vhdl/img/00_a_gate.jpg?raw=true" />

---

Quelle:

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
