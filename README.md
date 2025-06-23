# Markdown
0623 자율주행 AI
![칼럼1](https://github.com/user-attachments/assets/2ddb2a99-f72b-4d56-bc4d-c7cd77d1cff2)
``` sudo install python3 ```

# 자율주행 관련한 Python 코드

일단 필요한 라이브러리를 설치
``` pip install opencv-python numpy ```

간단한 예제 : 자율주행 시뮬레이터용 간단한 경로 추종 제어 (PID 컨트롤러)
``` class PIDController:
    def __init__(self, kp, ki, kd):
        self.kp = kp
        self.ki = ki
        self.kd = kd
        self.prev_error = 0
        self.integral = 0

    def control(self, target, current):
        error = target - current
        self.integral += error
        derivative = error - self.prev_error

        output = self.kp * error + self.ki * self.integral + self.kd * derivative
        self.prev_error = error

        return output

pid = PIDController(kp=1.0, ki=0.01, kd=0.1)
steering_angle = pid.control(target=0.0, current=lane_center_offset)  # offset은 좌우 차선 기준 중심에서의 거리
```
