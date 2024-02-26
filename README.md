# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
import time
import random

WINDOW_SIZE = 4  # Window size for the sliding window protocol

def send_frame(frame):
    print(f"Sending frame: {frame}")
    time.sleep(1)  # Simulating transmission delay
    return True  # Simulating successful transmission

def receive_ack(expected_ack):
    time.sleep(1)  # Simulating transmission delay
    ack = random.choice([expected_ack, None])  # Simulating ACK loss with 50% probability
    if ack == expected_ack:
        print(f"Received ACK for frame {expected_ack}")
        return True
    else:
        print(f"Timeout! Resending frames from {expected_ack} onwards...")
        return False

def sliding_window(frame_size):
    frames_sent = 0
    next_frame_to_ack = 0
    while frames_sent < frame_size:
        while frames_sent - next_frame_to_ack < WINDOW_SIZE and frames_sent < frame_size:
            frame = f"Frame {frames_sent}"
            if send_frame(frame):
                frames_sent += 1
            else:
                print("Transmission failed! Resending frames...")
        
        if receive_ack(next_frame_to_ack):
            next_frame_to_ack += 1

if __name__ == "__main__":
    frame_size = int(input("Enter the number of frames to send: "))
    sliding_window(frame_size)

```
## OUTPUT
![image](https://github.com/arbasil05/2b_SLIDING_WINDOW_PROTOCOL/assets/144218037/ecaca571-cb5b-48f5-b302-07b09ba9d562)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
