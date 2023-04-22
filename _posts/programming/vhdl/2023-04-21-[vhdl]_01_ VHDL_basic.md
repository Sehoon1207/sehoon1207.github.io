---
layout: single
title: "[VHDL] 01 VHDL 기초 구조"
folder: "vhdl"
categories:
  - vhdl

tags: [blog, vhdl]

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

date: 2023-04-21
---

"Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung."

# 00 논리(Logik)

디지털 회로를 구축함에 있어서 우리는 당연하게도 값이 두 개인 논리(zweiwerige Logik)을 기반으로 해야한다.  
모든 부분에 참 또는 거짓 두가지만 있다는 것. 
회로에서는 전압이 있는 경우를 1, 없는 경우를 0 이렇게 두 가지 상태로 두고 해석 할 수 있다.

---

# 01 계층적 디자인(Hierarchisches Design)

<img src="https://mblogthumb-phinf.pstatic.net/MjAxODA0MDhfOTEg/MDAxNTIzMTk4NTE0NTc4.EfWSoozsFNGSOkrcvVcTUT8cFa-ox9TAGno13jd1pU4g.JHf0qM5PAOrtkQ5SlZbO-O-F-1cmvih18-69_A1_h-sg.PNG.ansdbtls4067/image_6493700451523197559558.png?type=w800" width="700px">  

앞서 간단한 게이트를 만들어 봤지만, 복잡한 디지털 회로가 단순히 하나의 entity와 architecture로 이루어진 구조일리가 없다. 여러개를 나열하기도 하고 중첩해서 사용하기도 한다.


---

# 02 Syntax

이전 포스트 ([00 intro](https://sehoon1207.github.io/vhdl/vhdl-_00_intro/))에서 간단하게 entity 부분과 architecture 부분을 이야기 했었지만 여기서는 예제와 함께 더 자세히 뜯어보는게 좋겠다.

**아래는 and게이트 두개를 연결한 예제이다.**

```vhdl
library ieee;
use ieee.std_logic_1164.all;

entity andx2 is
port (i1 , i2 , i3 : in std_logic ;
o1 : out std_logic );
end entity andx2 ;

architecture netlist of andx2 is
signal s1 : std_logic ;
begin
and_1 : entity work . and ( behavior ) 
port map (  a => not i1 , 
            b => not i2 , 
            y => s1 );

and_2 : entity work . and ( behavior ) 
port map (  a => not s1 , 
            b => not i3 , 
            y => o1 );
end architecture netlist ;
```
## 02-1 package와 library(1-2. line)

```vhdl
library ieee;
use ieee.std_logic_1164.all;
```

이것은 IEEE에서 만든 VHDL 표준을 가져다 쓰겠다는 부분이다.
이 패키지 안에는 여러개의 소스로 나누어져 있고 그 중에 쓰고자 하는 것을 use를 이용해서 명시하고 있는 것이다.
  
## 02-2 일반적인 형태

일반적인 구성을 살펴보면 아래와 같다.  
  
```vhdl
  entity <library>.<component>(<architecture>)  
  [ generic map (...) ]  
  port map ( ... );  
```
`<library>:`   
컴포넌트가 속한 라이브러리 이름이다. 라이브러리가 생략되면 기본 라이브러리를 의미한다.  
ModelSIM은 "work"를 표준 라이브러리로 사용한다.  
  
`<component>:` 컴포넌트의 이름이다.  
  
`<architecture>:`    
컴포넌트의 아키텍처 이름을 지정한다. 컴포넌트는 여러 개의 아키텍처를 가질 수 있다.  
**프로젝트 디렉토리에 정확히 이 이름으로 존재해야 함!.**  
  
`generic map (...):` 컴포넌트에 전달될 제네릭(generic) 값들을 지정한다. (생략 가능)  
  
`port map (...):`
port map은 컴포넌트의 인터페이스에 정의된 포트와 연결할 값을 지정한다.   
컴포넌트를 사용하는 모듈에서는 port map을 사용하여 컴포넌트의 입력과 출력을 지정하고, 이를 연결하여 모듈을 완성한다.  


---

# 03 선언 및 할당(Deklaration und Zuweisung)

VHDL에서는 외부 신호와 내부 신호를 구분한다.   
외부 신호는 Entity와 연결되는 포트(port)를 정의하는 것으로, 내부 신호는 Entity 내부의 연결을 표현한다.

내부 신호를 선언할 때는 signal 키워드를 사용한다. 
예를 들어, s1이라는 내부 신호를 선언하려면 아래와 같이 작성한다.
  
```vhdl
signal s1 : std_logic;
```
  
std_logic은 VHDL에서 가장 많이 사용되는 데이터 타입 중 하나이다. 
signal을 선언할 때 := 연산자를 사용하여 해당 신호에 기본 값을 할당할 수 있다. 
예를 들어, s1 신호에 기본값으로 0을 할당하려면 아래와 같이 작성한다.
  
```vhdl
signal s1 : std_logic := '0';
```
이러한 신호는 Entity 내부에서 다양한 연산을 수행하기 위해 사용된다.  
내부 신호는 Entity 내부에서만 사용되므로 외부 Entity에서는 볼 수 없다.  

---

# 04 Verhalten vs. Struktur

VHDL에서는 두 가지 모델링 방법이 있다.  
하나는 Verhaltensebene(behavioral modeling)이고, 다른 하나는 Strukturebene(structural modeling)다.  
  
## 04-1 Verhaltensebene

Verhaltensebene은 Entity 내부에서 구현할 동작을 정의한다.  
이를 위해 process, if-else-elsif, case-when, function, procedure 등의 키워드를 사용하여 시퀀셜(sequential)하게 구현한다.   
이 방식은 순차 논리(sequential logic)를 구현하는 데 사용된다.  
  
## 04-2 Strukturebene

Strukturebene은 Entity 내부에서 구현한 논리회로를 구성하는 요소(기본 블록)들을 선언한다.
이를 위해 component, signal 등의 키워드를 사용한다.  
구성 요소들은 Entity 내부에서 인스턴스화된다.
Strukturebene에서는 or, and 등의 논리게이트를 사용하여 병렬 논리(parallel logic)를 구현한다.  

## 04-3 Verhalten과 Strukturebene의 예

예를 들어, Verhaltensebene에서는 process를 사용하여 if-else문을 작성하여 특정 입력신호가 어떤 값인지에 따라 다른 출력신호를 생성하는 논리를 작성한다. 반면, Strukturebene에서는 내부 블록에서 필요한 논리게이트 등의 기본 블록들을 component로 정의하고, signal을 사용하여 각 블록들 간에 신호를 연결한다.  
  
이러한 두 가지 방식은 VHDL에서 제공하는 다른 모델링 기법들과 함께 사용되어 전체 논리회로를 구성하게 된다.      Verhaltensebene과 Strukturebene은 각각의 장단점이 있기 때문에, 특정한 설계 목적에 따라 적절한 방식을 선택하여 사용한다.  
  
복잡하니 volladder로 예를 들면 아래와 같다.
  
<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/vhdl/img/01_%20volladder.jpg?raw=true" width="500px"> 

### 04-3-1 Verhaltensbeschreibung
eines Halbaddierers auf Logikebene

```vhdl
entity halfadd is
  port (A, B : in std_logic ;
        SUM , COUT : out std_logic );
end entity halfadd ;

architecture gatelevel of halfadd is
begin
  SUM <= A xor B;
  COUT <= A and B;
end architecture gatelevel ;
```

### 04-3-2 Strukturelle Beschreibung
eines Volladdieres mit zwei Halbaddierern

```vhdl
entity fulladd is
  port (A, B, CIN : in std_logic ;
        SUM , COUT : out std_logic );
end entity fulladd ;

architecture structural of fulladd is
  signal S1 , S2 , S3: std_logic ;
begin
  u1 : entity work . halfadd ( gatelevel )
          port map (A => A,
                    B => B,
                    SUM => S1 ,
                    COUT => S2 );
  u2 : entity work . halfadd ( gatelevel )
          port map (A => S1 ,
                    B => CIN ,
                    SUM => SUM ,
                    COUT => S3 );
  u3 : entity work . or2 ( logic )
          port map (A => S2 ,
                    B => S3 ,
                    Y => COUT );
end architecture structural ;

```
  
---
  
# 05 배열 Array

VHDL에서 배열(Array)은 동일한 데이터 타입의 값들의 집합이다.  
배열은 특정한 범위(range)와 해당 범위 내에서 사용되는 데이터 타입(element type)으로 정의된다.  
   
예를 들어, 아래와 같은 배열 타입 input_A를 정의할 수 있다.
```vhdl
type type_name is array (range) of element_type;

type input_A is array (0 to 8) of std_logic;
```
이 배열은 0부터 8까지의 범위 내에서 std_logic 데이터 타입의 값을 가진다.  
  
또한 배열은 선언할 때 값으로 초기화할 수 있다.   
이를 위해 배열 이름과 할당하려는 값의 범위를 지정해야 한다.   
아래와 같은 코드를 사용하여 배열을 초기화할 수 있다.    

```vhdl
ex1 <= ('0', '1', 'L', 'H', 'X', 'W', 'Z', '-', 'U');
```

배열의 각 요소는 인덱스를 사용하여 접근할 수 있다.  
예를 들어, 아래와 같이 ex2 배열의 7번째 요소에 1을 할당할 수 있다.  

```
ex2(7) <= '1';
```

배열의 일부 요소를 할당할 때는 해당 인덱스의 값을 명시적으로 지정하고, 나머지 요소에는 others 키워드를 사용하여 기본값을 할당할 수 있다.

```
ex2 <= (7 => '1', others => '0');
```

이러한 배열은 다양한 용도로 사용된다.
예를 들어, 디지털 회로에서는 배열을 사용하여 버퍼나 레지스터와 같은 구성 요소를 구현한다.


## 05-1 std_logic_vector

std_logic_vector는 IEEE 1164 라이브러리에 정의된 데이터 타입이다.  
이 데이터 타입은 std_logic 데이터 타입으로 이루어진 임의의 길이의 배열이다.  
각 요소는 논리값을 나타내며, 다음과 같은 키워드를 사용하여 정의된다.  

```vhdl
std_logic_vector ( range )

signal s1, s2, s3 : std_logic_vector(3 downto 0);
```
여기서 range는 배열의 인덱스 범위를 지정한다.   
  
이렇게 정의된 std_logic_vector 변수는 and, or와 같은 논리 연산자를 사용하여 다른 std_logic_vector 변수와 연산할 수 있다.  

예를 들어, s1 변수가 "1100" 값으로 초기화되고 s2의 0, 1, 2, 3번째 인덱스에 차례로 '0', '1', '1', '0' 값을 할당하면 s3는 "0100" 값으로 할당된다.

```vhdl
s1 <= "1100";
s2(0) <= '0';
s2(1) <= '1';
s2(2) <= '1';
s2(3) <= '0';
s3 <= s1 and s2;
```

여기서 s1과 s2는 std_logic_vector 변수이므로 and 연산자를 사용하여 논리곱을 계산할 수 있다.   
계산 결과는 새로운 std_logic_vector 변수인 s3에 할당된다.   
  
마지막으로, std_logic 변수와 std_logic_vector 변수는 각각 작은 따옴표(')와 큰 따옴표(")를 사용하여 값을 할당한다.  
  
## 05-2 std_logic_vector to integer

std_logic_vector를 integer로 변환하는 방법은 VHDL에서 자주 사용된다.  
이를 위해 ieee.numeric_std 라이브러리를 추가해야 한다.

```vhdl
library IEEE ;
use ieee . std_logic_1164 . all ;
use ieee . numeric_std . all ;          -- 추가부분
```

std_logic_vector를 integer 값으로 변환하는 예는 아래와 같다  

```vhdl
architecture foo of bar is
  ...
  signal int : integer ;
  signal slv : std_logic_vector (3 downto 0);
  ...
begin
  ...
  int <= to_integer ( unsigned ( slv ));
  ...
end architecture ;
```
int와 slv는 각각 integer 타입과 std_logic_vector(3 downto 0) 타입의 신호(signal)다.  
그리고 to_integer 함수를 사용하여 unsigned 함수로 변환된 slv 값을 int 값으로 할당한다.  
이 코드에서 unsigned 함수는 std_logic_vector 값을 unsigned로 변환한다.  
그런 다음, to_integer 함수는 unsigned 값을 integer 값으로 변환한다.
이렇게 변환된 integer 값은 계산 및 연산에 사용될 수 있다. 

**따라서 만약에 slv의 신호가 0101인 경우 변환된 integer값은 5가 되는 것이다.**

---

# 06 Kontrollstrukturen

Kontrollstrukturen은 VHDL에서 여러 개의 문장을 하나로 묶고, 특정 조건에 따라 실행 여부를 결정하는데 사용된다. VHDL에서는 다양한 종류의 Kontrollstrukturen이 제공된다.

아래에 Conditional assignment과 With-select 두 가지 Kontrollstrukturen이 사용된 예를 보겠다.

## 06-1 조건부 할당 Conditional assignment:  

```vhdl
architecture when_example of bcd is
begin
  output <= "0111111" when bcd = "0000" else
            "0000110" when bcd = "0001" else
            −− . . .
            "1000000";
end ;
```
Conditional assignment는 if-else 문을 대체하여 사용할 수 있으며, 특정 조건에 따라 신호에 값을 할당한다.   
예를 들어, output 신호에 bcd 신호의 값에 따라 다른 값을 할당할 수 있다.  
  
  
## 06-2 With-select:  
  
```vhdl
architecture with_example of bcd is
begin
  with bcd select
  bitmask <=  "0111111" when "0000",
              "0000110" when "0001",
              −− . . .
              "1000000" when others ;
end architecture with_example ;
```
With-select는 선택문(select)과 함께 사용된다.  
이 구조에서는 `선택된 변수를 기반`으로, 다양한 경우(case)에 대한 결과 값을 지정할 수 있다.  
예를 들어, bcd 신호에 대해 다양한 값에 대해 bitmask 신호를 설정할 수 있다.  
  
Kontrollstrukturen은 코드의 가독성과 유지 보수를 쉽게하기 위해 사용된다.  
이를 통해 코드를 간결하고 효율적으로 작성할 수 있다.  


---

Quelle: TU-Berlin

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
