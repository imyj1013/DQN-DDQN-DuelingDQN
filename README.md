### DQN, DDQN, DuelingDQN 성능 비교
#### 실험 개요 및 방법
- DQN, DDQN, Dueling DQN의 이론적 탐구 및 선행 연구 파악
- Open ai gym의 cartpole, lunar lander 환경을 이용한 성능 비교 실험 진행
- Open ai gym, Pytorch, Matplotlib, numpy 활용

#### 실험 결과 및 분석
| DQN | DDQN | Dueling DQN |
|----|----|----|
|![Image](https://github.com/user-attachments/assets/5da7561e-dea9-4c6c-b384-12f492b83b19)|![Image](https://github.com/user-attachments/assets/d3ff344a-d7e2-45a6-8328-ba38fa21b514)|![Image](https://github.com/user-attachments/assets/916954e4-457a-4639-b5c5-98343853c65c)|
|![Image](https://github.com/user-attachments/assets/eed2f25c-d404-414a-af95-ce441e2a65ac)|![Image](https://github.com/user-attachments/assets/390c4d5d-1819-454a-b02c-277cda1c23d3)|![Image](https://github.com/user-attachments/assets/e3408c5c-c5dd-4340-9966-d28e2a63dc27)|


카트폴과 Lunar lander 실험 결과 카트폴 실험에서 Dueling DQN, DDQN, DQN 순으로 학습을 완료했고 Lunar lander 실험에서 Dueling DQN, DDQN, DQN 순으로 평균 reward가 높게 나왔다. 

Lunar lander 실험에서 Dueling DQN은 value function과 advantage function을 분리하여 계산하므로 Q-value 추정에 안정적이다. 
DDQN은 두 개의 네트워크를 사용하여 action을 평가할 때는 -greedy 정책을 적용하지 않아 DQN보다 안정적인 Q-value를 추정한다. 
실험을 여러번 반복하였을 때 DQN에 비해 일정한 Average score가 나왔다. 그러므로 3개의 알고리즘 중 Dueling DQN과 DDQN이 DQN보다 학습의 안정성이 높다는 것을 알 수 있다.

카트폴 실험에서 DDQN은 두 개의 네트워크를 사용하여 안정적인 학습을 진행하였다.
Dueling DQN의 value function과 advantage function을 분리하여 더하는 것이 Q value를더 효율적으로 계산하는 것이고 학습의 안정성을 증대시키기에 학습도 빠르게 이루어졌음을 알 수 있다.
종합적으로 분석하면 DDQN은 DQN의 Q value 과대적합 문제를 해결하여 학습의 안정성이 높아졌고 학습의 강건성을 증대시켰다. 
Dueling DQN은 state value와 advantage value를 각각 계산하며 더 정확한 Q value를 도출함으로써 학습의 안정성이 높아졌고 효율적으로 학습을 진행하여 속도 역시 빠른 것을 알 수 있다.
