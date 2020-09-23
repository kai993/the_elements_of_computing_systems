# ブール論理

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

