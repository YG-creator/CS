# Queue 종류

* Job Queue : 현재 시스템 내에 있는 모든 프로세스의 집합
* Ready Queue : 현재 메모리 내에 있으면서 CPU 를 잡아서 실행되기를 기다리는 프로세스의 집합
* Device Queue : Device I/O 작업을 대기하고 있는 프로세스의 집합



# 스케줄러 종류



## 장기스케줄러

* too many 프로세스 -> Disk에 임시저장(new) -> 장기스케줄러 -> 일부 메모리 할당(ready)
* 한번에 너무 많거나 적게 프로세스에 메모리 할당하면 성능저하
* time sharing system에는 장기스케줄러가 없어서 곧바로 ready 상태가됨



## 단기스케줄러

* 메모리(ready) -> 단기스케줄러 -> CPU 할당(running)



## 중기스케줄러

* 메모리(ready) -> 중기스케줄러 -> 다 디스크로 쫓아냄(suspended)

* blocked vs suspended

  blocked : 다시 ready 상태 될 수 있음

  suspended : 다시 ready 상태 될 수 없음

  

# CPU 스케줄링 종류

Ready Queue에 있는 프로세스 스케줄링



## FCFS

* 먼저 온 순서대로 처리
* 앞 프로세스가 오래걸리면 효율성이 떨어짐(convoy effect)

* 비선점형(못뺏음)

  

## SJF

* CPU burst time이 짧은 프로세스부터 처리

* 효율성은 좋지만 긴 프로세스는 영원히 처리 못할 수도 있음

* 비선점형

  

## SRTF

* 처리중인 프로세스 남은 시간 > 새로운 프로세스 처리 시간  -> 새로운 프로세스 처리
* 프로세스 처리 완료시간을 예측할 수 없음
* 선점형(뺏을 수 있음)



## Priority Scheduling

* 우선순위가 높은거 부터 처리(숫자가 낮을수록 우선순위 높음)

* 선점형 : 실행중인것보다 높은게 오면 뺏기

* 비선점형 : Ready Queue의 Head에 넣기

* 실행준비는 되어도 CPU를 무기한 대기할 수도 있음 

  

## Round Robin

* 프로세스마다 동일한 시간동안 CPU를 할당함
* 시간이 지나면 ready queue 맨뒤에 줄섬
* CPU 사용시간이 랜덤한 프로세스들이 섞여있을 때 효율적
* context save가ㄴ으해서 RR 가능해짐
* 적절한 할당시간(time quantum)이 중요
  * 할당시간이 너무 커지면 FCFS와 같아짐
  * 할당 시간이 너무 적으면 context switch로 overhead 발생