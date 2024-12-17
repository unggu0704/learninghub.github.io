# Process Control Block

> 프로세스의 데이터들을 저장해 놓은 곳 프로세스의 정보 그 자체
> 
- Mulit process 환경에 있어서 스케줄링을 위해 프로세스에 대한 정보를 가지고 있는 meta data가 필요
- 각 프로세스가 가지고 있는 고유한 PCB를 생성
    
    ![Untitled](Process%20Control%20Block%2045a8d0cf57c84995931dc6e03c3d16f7/Untitled.png)
    
    - 언제든지 다시 작업 시작할 때 보는 메모장 같은 존재

### PCB의 관리 방식

- LInked List 방식으로 관리한다.
- 주소값으로 서로 연결되어 있기에 중간에 삽입 삭제에 용이함

이렇게 프로세스를 변경 할 때 CPU의 정보가 변경되는 것을 `Context Switching` 이라고 함

프로레스가 Ready → Running 되거나 또는 Running → Wating 등일 때 발생

→ **Overhead** 유발 가능성이 높음