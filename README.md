# face_detect_with_opencv

### Installation

Install the dependencies and devDependencies and start the server.

```sh
$ git clone https://github.com/gururajjeerge/face_detect_with_opencv.git
$ cd face_detect_with_opencv
$ pip3 install -r requirements.txt
```

Now open code face_detect.py with your favorite editor and change 

```
cap = cv2.VideoCapture('VIDEO_FILE_TO_PROCESS.mp4')
```

Running Code

```
python3 face_detect.py
```

Output of program will be output.mp4 in same folder

### Production

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import cv2

cap = cv2.VideoCapture('VIDEO_FILE_TO_PROCESS.mp4')
face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
fourcc = cv2.VideoWriter_fourcc(*'MP4V')
out = cv2.VideoWriter('output.mp4', fourcc, 20.0, (768, 432))

while(cap.isOpened()):
    ret, frame = cap.read()
    if ret is True:
        gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        faces = face_cascade.detectMultiScale(gray, 1.1, 4)

        for (x, y, w, h) in faces:
            cv2.rectangle(frame, (x, y), (x + w, y + h), (255, 0, 0), 2)
        out.write(frame)
    else:
        break

cap.release()
out.release()
cv2.destroyAllWindows()


```

License
----

MIT


**Free Software, Hell Yeah!**