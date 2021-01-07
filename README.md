# RTL_process
This is the main process of the RTL and CaD, SoC process

## 1. Specification and Planning

- system 검토
- 기능 및 input 형상화
    - by block diagram
    - data type
    - Chip clock, memory bandwidth 고려
    - CPU Performance, Power consumption

## 2. Design

- HDL programming (synthesis 가능하게)
    - Verilog, VHDL
- RTL(Register Transfer Level) : HDL source code
    - flipflop 과 combinational logic 이 잘 기술
    - 매 clock cycle 동작

## 3. RTL Verification

- Simulation
    - by HDL test bench
        - Simulation vector(input data) ⇒ output data 확인
        - Cadence ncsim, Mentor Graphic modelsim, VCS 등등
        - Slow ⇒ block test bench
    - Emulator, hardware 가속
    - FPGA prototype
        - RTL ⇒ FPGA
        - 비쌈, 동작 느림, analog 제약
        - simulation 빠름
    - ESL

## 4. Synthesis

- RTL to Hardware
- by Synopsys Design Compiler
- Synthesis tool : (design kit, RTL, timing constraint) ⇒ (gate level netlist)
    - design kit
        - Synthesis 위한 gate info(동작, 속도 등)
        - FAB 공정마다 줌
        - ISA(DK), C code(RTL) 과 비슷
    - Timing constraint
        - Chip 내부의 clock 속도
        - chip input/output delay
        - clock 연동된 signal 관계
    - hardware를 최적화
        - If not,
            - usually combinational logic 복잡
    - Gate level netlist(pre netlist, layout netlist)
        - Verilog pre-sim
    - 검증 : Formal verification

## 5. BackEnd

- 외주
- Netlist : test logic ⇒ chip test vector
- P&R(place and route)
    - 반도체 위에 place하고, wire route하는 과정
    - GDS 파일 : 반도체 Die에 놓일 material 영역을 표시한 data ⇒ FAB 전달
    - 검증
        - make post netlist : P&R 결과를 가진 netlist .sdf
        - STA : Static timing analysis 검증(clock 주파수, delay 검증)
        - post sim : too slow, use essential vector
        - ECO(Engineering Change Order) debugging
        - Sign off : tape-out, design 넘김

## 6. FAB OUT and Chip Test

- Packaging ⇒ chip
- scan test & function test 진행
- 완성 Chip을 evaluation board위에 올리고, software 개발 ⇒ Reference System
    - 잘못되면 respin : 다시
    
