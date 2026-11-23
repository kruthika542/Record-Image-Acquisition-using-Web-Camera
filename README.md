# Record-Image-Acquisition-using-Web-Camera

## Aim
To write a Python program using OpenCV to capture an image from the webcam and perform the following operations:

1.Write the frame as a JPG file
2.Display the video
3.Display the video by resizing the window
4.Rotate and display the video

## 🛠️ Software Used
- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)

## ⚙️ Algorithm
Step 1:
Import the required libraries and initialize the webcam using cv2.VideoCapture().

Step 2:
Capture frames continuously from the webcam.

Step 3:
Save a frame as a JPG image using cv2.imwrite().

Step 4:
Display the live video stream using cv2.imshow().

Step 5:
Resize the frame and rotate it using OpenCV functions, then display the processed frames.

## 💻 Program

## Developed By: 
Name:Kruthika R
Register No: 212225240075

## 1.Import Libraries & Initialize Webcam
```
import cv2
cap = cv2.VideoCapture(0)
print("Webcam opened:", cap.isOpened())
```

## 2.Capture Image and Save as JPG
```
from IPython.display import display, clear_output
from PIL import Image
import time

for i in range(100):

    ret, frame = cap.read()

    if not ret:
        print("Unable to capture frame")
        break

    frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)

    clear_output(wait=True)
    display(Image.fromarray(frame))

    time.sleep(0.03)
cv2.imwrite("captured_image.jpg", frame)
print("Image saved successfully!")
```
## 3.Import Libraries and Define Functions
```
import cv2
import time
from PIL import Image
from IPython.display import display
from IPython.display import Image as DisplayImage
from io import BytesIO

def capture_frames(count=30):
    cap = cv2.VideoCapture(0)
    frames = []

    if not cap.isOpened():
        print("Webcam not detected")
        return frames

    for i in range(count):
        ret, frame = cap.read()

        if ret:
            frames.append(frame)
        else:
            break

        time.sleep(0.03)

    cap.release()
    return frames


def show_video(frames, operation="original"):
    gif_frames = []

    for frame in frames:
        if operation == "resize":
            frame = cv2.resize(frame, (640, 480))

        elif operation == "rotate":
            frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)

        frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
        gif_frames.append(Image.fromarray(frame))

    if gif_frames:
        buffer = BytesIO()

        gif_frames[0].save(
            buffer,
            format="GIF",
            save_all=True,
            append_images=gif_frames[1:],
            duration=100,
            loop=0
        )

        display(DisplayImage(data=buffer.getvalue()))
```

## 4.Display the Video
```
frames = capture_frames(30)
print("Original Video")
show_video(frames, "original")
```
## 5.Display the Video by Resizing the Window (640 × 480)
```
print("Resized Video (640 x 480)")
show_video(frames, "resize")
```

## 6.Rotate and Display the Video (90° Clockwise)
```
print("Rotated Video (90 Degrees Clockwise)")
show_video(frames, "rotate")
```
## 7.Release Webcam
```
print("All video processing operations completed successfully!")
cap.release()
print("Webcam released successfully")
```

## Output

## Displaying image
<img width="807" height="597" alt="image" src="https://github.com/user-attachments/assets/d42fb173-70b8-4416-9f6a-25f06946cb50" />

## Displaying the video

https://github.com/user-attachments/assets/0f12c5ab-58f1-4776-a4b5-b98d5fdc126a

##  Displaying the Resized Video (640 x 480)

https://github.com/user-attachments/assets/f5d0b089-086a-4e1f-802a-265f4e68de42

##  Displaying the Rotated Video (90 Degrees Clockwise)

https://github.com/user-attachments/assets/82f163e2-5bde-422d-b9be-bb81980d6713

## Result
Thus, the image is successfully captured from the webcam and various video processing operations such as saving, displaying, resizing, and rotating are performed using OpenCV.

