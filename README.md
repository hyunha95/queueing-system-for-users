**테스트 방법**
1. 로컬에서 6379번 포트로 레디스를 실행시킨다.
2. flow프로젝트를 9010번 포트에서 실행시킨다.
3. 대기열에 임의의 사용자를 등록한다.
https://github.com/hyunha95/queueing-system-for-users/blob/fe0f5e49fc60040e57acb422a0cb272e8acd1c2c/flow/src/main/java/com/fastcampus/flow/controller/UserQueueController.java#L20
```
curl -X POST "http://localhost:9010/api/v1/queue?user_id=100"
```

4. 나도 대기열에 입장한다.   
http://localhost:9010/waiting-room?user_id=5&redirect_url=https://cuwist.com   
아래와 같은 이미지기 나왔다면 성공   
![image](https://github.com/user-attachments/assets/1501c2d6-79d6-4af2-b956-6dc6d2489857)

5. 스케줄러에 의해서 앞 순번이 빠지면 3번에 명시한 redirect_url로 이동하게 된다.   
https://github.com/hyunha95/queueing-system-for-users/blob/fe0f5e49fc60040e57acb422a0cb272e8acd1c2c/flow/src/main/java/com/fastcampus/flow/service/UserQueueService.java#L82
   
