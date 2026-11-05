# Operating Systems

고려대학교 **Operating Systems (COSE341)** 수업의 학습 내용과 프로젝트 진행 과정을 기록하는 저장소입니다.

## Learning Objectives
- Linux Kernel 구조 및 동작 원리 이해
- Process, Thread 및 System Call 학습
- CPU Scheduling 알고리즘 구현 및 분석
- Concurrency와 Synchronization 이해

## Projects
- **Project #1:** Linux Kernel System Call 구현
- **Project #2:** Virtual CPU 기반 FCFS, SJF, RR Scheduling 구현 및 분석

## Development Environment
- **OS:** Ubuntu (WSL2)
- **Language:** C
- **Tools:** GCC, Git, GitHub

> 과제 Source Code는 공개하지 않으며, 학습 내용과 구현 과정만 기록합니다.

## Process & Thread

- **Process:** 실행 중인 프로그램으로, 독립적인 가상 주소 공간과 자원을 가집니다.
- **Thread:** Process 내부의 실행 단위로, 같은 Process의 다른 Thread와 Code, Data, Heap을 공유합니다.
- 각 Thread는 독립적인 Program Counter, Register, Stack을 가집니다.

Multi-threading은 자원 공유를 통해 효율적인 Concurrent Execution을 지원합니다.
