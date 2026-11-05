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

## User Mode & Kernel Mode

- **User Mode:** 일반 애플리케이션이 실행되는 제한된 권한의 모드입니다.
- **Kernel Mode:** 운영체제가 하드웨어와 시스템 자원에 접근할 수 있는 특권 모드입니다.
- **Mode Switch:** System Call, Interrupt, Exception 등을 통해 CPU의 실행 모드가 전환됩니다.

User Process는 System Call을 통해 Kernel의 기능을 요청할 수 있습니다.

## System Call

System Call은 User Process가 Kernel의 기능을 요청하는 인터페이스입니다.

- **System Call Interface:** User Space에서 Kernel 기능을 호출하는 진입점
- **Mode Switch:** System Call 실행 시 User Mode에서 Kernel Mode로 전환
- **System Call Handler:** Kernel에서 요청된 작업을 처리하는 함수

Linux에서는 `read()`, `write()`, `fork()` 등의 기능을 System Call을 통해 이용할 수 있습니다.

## CPU Scheduling

CPU Scheduling은 여러 Process 중 CPU를 사용할 대상을 선택하는 운영체제의 기능입니다.

주요 평가 지표:
- **CPU Utilization:** CPU가 작업을 수행하는 시간의 비율
- **Throughput:** 단위 시간당 완료된 작업 수
- **Waiting Time:** Ready Queue에서 대기한 총 시간
- **Response Time:** 도착 후 최초로 CPU를 할당받기까지 걸린 시간
- **Turnaround Time:** 도착부터 작업 완료까지 걸린 시간

Scheduling Policy에 따라 시스템의 효율성과 응답성이 달라집니다.

## FCFS (First-Come First-Served)

FCFS는 Process가 Ready Queue에 도착한 순서대로 CPU를 할당하는 Non-preemptive Scheduling 알고리즘입니다.

## SJF (Shortest Job First)

SJF는 CPU Burst Time이 가장 짧은 Process를 우선 선택하는 Scheduling 알고리즘입니다.

- **장점:** 모든 작업이 동시에 도착하고 실행 시간을 알고 있다면 평균 Waiting Time을 최소화할 수 있습니다.
- **단점:** 긴 작업이 계속 대기하는 Starvation이 발생할 수 있으며, 정확한 CPU Burst Time을 예측하기 어렵습니다.
- **특징:** Non-preemptive SJF에서는 실행 중인 Process가 CPU를 반환할 때까지 다른 Process가 선점할 수 없습니다.

- **장점:** 구현이 간단하고 도착 순서에 따라 공정하게 처리합니다.
- **단점:** 긴 작업이 먼저 실행되면 짧은 작업의 대기 시간이 증가하는 Convoy Effect가 발생할 수 있습니다.
- **특징:** CPU를 할당받은 Process는 자발적으로 CPU를 반환하거나 작업을 완료할 때까지 실행합니다.
