# GestureSpeak — ASL ➜ English (Swift + CoreML + Vision)

![demo1](https://github.com/user-attachments/assets/ff8570f6-34c3-44b4-a28e-28c778c1cd45)              ![demo2](https://github.com/user-attachments/assets/f79f3612-facd-4142-9df6-c588da21b834)


**Why this repo?**

This codebase is a starting point for building better ASL→English mobile apps. It adapts Apple’s sample “Detecting Human Actions in a Live Video Feed” to hand signs:
* The original Apple sample uses Vision + CoreML to detect 3 exercise actions (an action classifier over full-body motion).
* GestureSpeak repurposes that flow for hand sign classification (a sign/gesture classifier) and updates the Vision pipeline to use hand + finger key landmarks instead of whole-body pose.
* Video capture & frame processing are intentionally kept the same as the Apple sample for simplicity and reliability.

**Upstream reference**: Apple Developer Documentation — Detecting Human Actions in a Live Video Feed
https://developer.apple.com/documentation/CreateML/detecting-human-actions-in-a-live-video-feed

(**Important Note**: The files in the documentation folder are the one's from apple's page, as there is unfortunately no equivalent for hand sign / ASL Signs)

**What’s included / What’s not**
* ✅ Live camera preview with AVCaptureSession
* ✅ Vision requests configured for hand pose / key landmarks
* ✅ Frame-by-frame feature extraction and CoreML prediction call-site
* ✅ Example label mapping and result overlay (for demonstration)
* ✅ Clean separation between Vision (feature extraction) and CoreML (classification)
* ❌ Model file not included. The model shown in the GIFs at the top is not in this repo unfortunately as it has been lost with time. However, the model had been trained using the **WLASL Dataset** (https://www.kaggle.com/datasets/risangbaskoro/wlasl-processed), but trimmed down to only 50 classes rather than 2,000 classes that were originally there in the dataset. Moreover, due to only around 8-12 videos per class, some basic augmentations were used, and a peak validation accuracy of 76.7% was achieved.
* ❌ Labels are placeholders (e.g., banana, backpack) and are not the “top 50 ASL words,” as seen in the GIFs provided at the top of this ReadMe. 
* ❌ No training code.

**How it works (at a glance)**

	1.	Camera frames → captured via AVCaptureVideoDataOutput.
	2.	Vision Hand Pose → VNDetectHumanHandPoseRequest extracts per-frame hand/finger keypoints.
	3.	Feature building → landmarks are normalized/packed into the classifier’s expected input tensor/array.
	4.	CoreML Inference → your hand sign classifier predicts a label + confidence.
	5.	UI Overlay → predicted word appears over the live preview.

**Key changes vs Apple sample**

* Apple’s code routed pose/motion into an action classifier (e.g., “jumping jack”).
* This repo routes hand landmarks into a sign classifier (e.g., “HELLO”).
* The video/looping & timing logic stays the same for smooth real-time inference.


**Requirements**
* Xcode 15+ (recommended)
* iOS 15+ device (camera access required; on-device performance is best on A12 or newer)
* Swift 5.x
* A CoreML classifier that matches your chosen feature format (see below)

