# shop_name_detection


Summary of the Approach
The objective was to develop a system that extracts shop names from a YouTube video of a vlogger walking through a shopping mall, annotating these names on the video, and compiling the information into an Excel spreadsheet. The key tasks included downloading the video, processing it to detect shop signs, extracting text via OCR, and annotating the video with the extracted names.
Approach Breakdown:
1.	Video Downloading: Used pytube to reliably download the highest resolution stream available from YouTube.
2.	Frame Processing: Processed video frames at a reduced rate (every 10 seconds) to detect shop signs using a pre-trained YOLOv5 model.
3.	Text Extraction: Employed Pytesseract for OCR to extract text from the regions identified as shop signs.
4.	Annotation: Annotated the video with detected shop names and bounding boxes highlighting the shop signs.
5.	Output Compilation: Compiled the detected shop names along with their timestamps into an Excel spreadsheet and also generated an annotated video.
Technical Stack:
•	Python libraries: cv2 (OpenCV), pandas, pytube, yolov5, pytesseract
•	Tools: YOLOv5 model for object detection, Tesseract OCR for text extraction
Challenges and Solutions
1. Video Download Issues:
•	Challenge: Initial attempts using youtube_dl and pafy were unsuccessful due to API changes on YouTube's end that frequently broke these libraries.
•	Solution: Switched to pytube, which proved to be more reliable for downloading YouTube videos.
2. Object Detection Efficiency:
•	Challenge: The pre-trained YOLOv5 model was initially slow and detected many irrelevant objects.
•	Solution: Adjusted the confidence threshold and fine-tuned the detection frequency to every 10 seconds to balance detail and performance.
3. Text Recognition Accuracy:
•	Challenge: OCR errors were common due to complex backgrounds and varied text styles on shop signs.
•	Solution: Enhanced the image preprocessing in Tesseract (e.g., using --psm 6 configuration) and considered only high-confidence detections.
4. Performance Optimization:
•	Challenge: Processing every frame of the video was computationally expensive.
•	Solution: Limited the processing to the first 5 minutes of the video and further reduced the frame rate to one frame every 10 seconds.
Areas for Improvement and Future Work
1. Model Training:
•	Improvement: Training the YOLOv5 model specifically on a dataset of shop signs could greatly improve detection accuracy.
•	Future Work: Collect a dataset of shop signs and logos to fine-tune the model.
2. OCR Optimization:
•	Improvement: Advanced OCR techniques and better preprocessing methods can be applied to improve text accuracy.
•	Future Work: Implementing machine learning-based segmentation algorithms before applying OCR could help in isolating text more effectively.
3. Scalability:
•	Improvement: The system's processing speed needs enhancement to handle longer videos or real-time processing.
•	Future Work: Explore the use of more powerful computational resources or efficient algorithms like Fast-RCNN for object detection.
4. User Interface Development:
•	Improvement: Currently, the system operates through scripts which are not user-friendly for non-technical users.
•	Future Work: Develop a graphical user interface (GUI) where users can input video URLs, view the processed video, and download results directly.
5. Robustness to Video Quality and Styles:
•	Improvement: The system could be made more robust to different video qualities and shop sign styles.
•	Future Work: Implement adaptive thresholding techniques and use style transfer learning to handle a variety of video inputs more effectively.
Conclusion
This project showcased the integration of multiple advanced technologies including deep learning, OCR, and video processing to solve a practical problem. While effective to a certain extent, the prototype system presents numerous opportunities for enhancements in accuracy, efficiency, and user accessibility. Future iterations will focus on these areas, aiming to build a more robust and scalable solution.

