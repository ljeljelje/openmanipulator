# Pick-and-Place using X330 Manipulator

## 1. 프로젝트 소개

본 프로젝트는 ROS 환경에서 OpenManipulator 기반 로봇 매니퓰레이터를 이용하여  
AR Marker를 인식하고, 물체를 집어서 지정된 위치에 놓는 Pick-and-Place 동작을 수행하는 예제입니다.

로봇은 현재 조인트 상태, 그리퍼 위치, 엔드이펙터의 위치 정보를 받아오고,  
AR Marker의 위치를 기준으로 물체를 잡은 뒤 미리 정의된 place pose로 이동합니다.

---

## 2. 주요 기능

- OpenManipulator 조인트 제어
- 그리퍼 열림/닫힘 제어
- 작업공간 좌표 기반 엔드이펙터 이동
- AR Marker 위치 인식
- Pick-and-Place 자동 시퀀스 수행
- 키보드 입력을 통한 동작 모드 선택

---

## 3. 동작 구조

본 코드는 다음과 같은 ROS service client와 subscriber를 사용합니다.

### Service Client

| Service | 설명 |
|---|---|
| `goal_joint_space_path` | 조인트 공간 경로 제어 |
| `goal_tool_control` | 그리퍼 제어 |
| `goal_task_space_path` | 작업공간 위치 제어 |

### Subscriber

| Topic | 설명 |
|---|---|
| `states` | OpenManipulator의 이동 상태 확인 |
| `joint_states` | 현재 조인트 각도 확인 |
| `gripper/kinematics_pose` | 그리퍼의 현재 위치 확인 |
| `/ar_pose_marker` | AR Marker 위치 정보 수신 |

---

## 4. 파일 구성

```text
openmanipulator/
├── README.md
├── open_manipulator_pick_and_place.cpp
├── open_manipulator_pick_and_place_중간.cpp
└── open_manipulator_pick_and_place - 원본.cpp
