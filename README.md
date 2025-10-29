**GestureSpeak — ASL ➜ English (Swift + CoreML + Vision)**

![demo1](https://github.com/user-attachments/assets/ff8570f6-34c3-44b4-a28e-28c778c1cd45)              ![demo2](https://github.com/user-attachments/assets/f79f3612-facd-4142-9df6-c588da21b834)


Why this repo?

This codebase is a starting point for building better ASL→English mobile apps. It adapts Apple’s sample “Detecting Human Actions in a Live Video Feed” to hand signs:
	•	The original Apple sample uses Vision + CoreML to detect 3 exercise actions (an action classifier over full-body motion).
	•	GestureSpeak repurposes that flow for hand sign classification (a sign/gesture classifier) and updates the Vision pipeline to use hand + finger key landmarks instead of whole-body pose.
	•	Video capture & frame processing are intentionally kept the same as the Apple sample for simplicity and reliability.

Upstream reference: Apple Developer Documentation — Detecting Human Actions in a Live Video Feed
https://developer.apple.com/documentation/CreateML/detecting-human-actions-in-a-live-video-feed

⸻
