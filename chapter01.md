# ブール論理
- 全てのデジタル機器はパソコンであれ、携帯電話であれ、ネットワークであれ情報の保存と処理を行うために設計された回路からできている。
- 論理ゲート
  - 情報の保存と処理を行うための回路
  - 形状や携帯は異なる
  - 物理的には論理ゲートを作るための材料や製造方法はたくさん存在する
  - 論理的には同じ論理ゲートであれば、振る舞い、インタフェースは全てのコンピューターで同じ
- ブールゲート(boolean gate)はブール関数を物理的に実現したもの
- ブール代数はブール値(バイナリ値・2値とも呼ばれる)を扱う
- ブール値には`true/false`、`1/0`、`on/off`などのラベルが使われる
- ブール関数を表現する単純な方法はブール関数の真理値表による表現

    | x | y | z | f(x,y,z) |
    |---|---|---|----------|
    | 0 | 0 | 0 | 0        |
    | 0 | 0 | 1 | 0        |
    | 0 | 1 | 0 | 1        |
    | 0 | 1 | 1 | 0        |
    | 1 | 0 | 0 | 1        |
    | 1 | 0 | 1 | 0        |
    | 1 | 1 | 0 | 1        |
    | 1 | 1 | 1 | 0        |

- 関数の入力としてバイナリ値の変数の組み合わせは2^n通りになる。
- ブール関数はブール式(boolean expression)で記述することもできる。
  - ブール式の基本はAnd, Or, Notの3つ
    - `x*y` : x AND yはxとyの両方が1の時だけ1
    - `x + y` : x Or yはxまたはyのどちらかがまたはその両方が1の時だけ1
    - `^x`(xの上に横線): Not xはxが0の時だけ1になる
- どのようなブール関数でも1つの正規表現(canonical representation)と呼ばれるブール式で表せる
  - 真理値表で関数の出力が1である行だけに注目する
  - 各行に入力されるリテラルをAndで結合して新たな項を作成する
  - その行の変数の値が`x=0`, `y=1`, `z=0`だとすると、次の項を作る

      ```
      # 上の真理値表でいうと次になる
      _ _  __   _
      xyz xyz xyz
      ```

  - これらの項を全てOrで結合することで真理値表と等しいブール式が得られる

      ```
                 _ _    __     _
      f(x,y,z) = xyz + xyz + xyz
      ```

## 論理ゲート
- ゲート(gate)はブール関数を実装するための物理デバイス
- 論理ゲートの入力と出力は全て0と1からなる要素である
- 例えば、3入力のブール関数で`And(a,b,c)`実装を考える
  - ブール代数を用いると、`a・b・c = (a・b)・c`となる
  - また、前置表記法の場合`And(a,b,c) = And(And(a,b),c)`と表すことができる
- 論理設計(logic design)とは、ゲートのつなぎ方に関する技法であり、それによって複雑な機能をもった複合ゲートを構成することができる
- 論理ゲートは2つの異なる視点から捉えることができる
  - 内部 : ゲートの内部に関するアーキテクチャ、つまり実装
  - 外部 : ゲートのインターフェイス
- `Xor(a,b) = Or(And(a,Not(b)), And(Not(a), b))`

## ハードウェア記述言語(HDL)
- コンピュータ上でハードウェア記述言語を用いて、回路のアーキテクチャを設計し、最適化について考えることができる

XorゲートのHDLによる実装

  - HDLプログラム(`Xor.hdl`)

      ```
      /* Xor (exclusive or) gate:
         If a<>b out=1 else out=0. */
      CHIP Xor {
        IN a, b;
        OUT out;
        PARTS:
        NOT(in=a, out=nota);
        NOT(in=b, out=notb);
        And(a=a, b=notb, out=w1);
        And(a=nota, b=b, out=w2);
        Or(a=w1, b=w2, out=out);
      }
      ```

  - テストスクリプト(`Xor.tst`)

      ```
      load Xor.hdl,
      output-list a, b, out;
      set a 0, set b 0,
      eval, output;
      set a 0, set b 1,
      eval, output;
      set a 1, set b 0,
      eval, output;
      est a 1, set b 1,
      eval, output;
      ```

  - 出力ファイル(`Xor.out`)

      ```
      a  | b  | out
      - - - - - - -
      0  | 0  | 0
      0  | 1  | 1
      1  | 0  | 1
      1  | 1  | 0
      ```

## 実装
実際にコードを書くのは次
```bash
$ fd -e hdl . projects | xargs grep -e 'Put you code here' -e 'Put your code here'
projects/01/And.hdl:    // Put your code here:
projects/01/And16.hdl:    // Put your code here:
projects/01/DMux.hdl:    // Put your code here:
projects/01/DMux4Way.hdl:    // Put your code here:
projects/01/DMux8Way.hdl:    // Put your code here:
projects/01/Mux.hdl:    // Put your code here:
projects/01/Mux16.hdl:    // Put your code here:
projects/01/Mux4Way16.hdl:    // Put your code here:
projects/01/Mux8Way16.hdl:    // Put your code here:
projects/01/Not.hdl:    // Put your code here:
projects/01/Not16.hdl:    // Put your code here:
projects/01/Or.hdl:    // Put your code here:
projects/01/Or16.hdl:    // Put your code here:
projects/01/Or8Way.hdl:    // Put your code here:
projects/01/Xor.hdl:    // Put your code here:
projects/02/ALU.hdl:   // Put you code here:
projects/02/Add16.hdl:   // Put you code here:
projects/02/FullAdder.hdl:    // Put you code here:
projects/02/HalfAdder.hdl:    // Put you code here:
projects/02/Inc16.hdl:   // Put you code here:
projects/03/a/Bit.hdl:    // Put your code here:
projects/03/a/PC.hdl:    // Put your code here:
projects/03/a/RAM64.hdl:    // Put your code here:
projects/03/a/RAM8.hdl:    // Put your code here:
projects/03/a/Register.hdl:    // Put your code here:
projects/03/b/RAM16K.hdl:    // Put your code here:
projects/03/b/RAM4K.hdl:    // Put your code here:
projects/03/b/RAM512.hdl:    // Put your code here:
projects/05/CPU.hdl:    // Put your code here:
projects/05/Computer.hdl:    // Put your code here:
projects/05/Memory.hdl:    // Put your code here:
```

## tool
```bash
$ chmod u+x ./tools/*.sh

# ハードウェアシュミレータ起動
$ sh ./tools/HardwareSimulator.sh

# CPUエミュレータ起動
$ sh ./tools/CPUEmulator.sh

# アセンブラ起動
$ sh ./tools/Assembler.sh

# VMエミュレータ起動
$ sh ./tools/VMEmulator.sh

# Jackコンパイラ起動
$ sh ./tools/JackCompiler.sh
```

