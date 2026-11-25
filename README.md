# TrafficPulse AI

Real-time vehicle counting per lane from a camera feed with YOLOv5, as the sensing step of an adaptive traffic signal.

<!-- screenshot: docs/lane_view.png -->

## What it does

- Detects cars, trucks and buses in a live webcam or CCTV feed (YOLOv5s, confidence 0.4)
- Splits the frame into left and right lanes and counts the vehicles in each every 5 seconds
- Overlays the lane divider and live counts on the video, and logs a timestamped count to the console
- `Identification.py`: plain GPU detection view with all YOLO classes drawn, for testing the camera and model

The per-lane counts are what a signal controller would use to give the busier lane a longer green phase.

## Tech stack

Python · PyTorch · YOLOv5 (torch.hub) · OpenCV · pandas

## Run

```bash
pip install torch torchvision opencv-python pandas ultralytics
python main.py            # lane counting, press q to quit
python Identification.py  # detection view (CUDA GPU)
```

The YOLOv5s weights are downloaded automatically by `torch.hub` on the first run.
