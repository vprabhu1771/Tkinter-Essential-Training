To implement Optical Character Recognition (OCR) using a webcam in a `tkinter` interface, we can use `OpenCV` to capture frames from the webcam, `PIL` to convert frames into images, and `Tesseract OCR` to perform the text recognition.

Here is the complete implementation of OCR using a webcam:

### Prerequisites:
1. **OpenCV**: For capturing the webcam video.
2. **Pillow**: For image manipulation.
3. **Tesseract**: For OCR functionality. Install Tesseract OCR:
   - Windows: [Download and install Tesseract](https://github.com/tesseract-ocr/tesseract/wiki).
   - Linux (Ubuntu): `sudo apt-get install tesseract-ocr`.
4. **Pytesseract**: Python wrapper for Tesseract OCR.

Install the necessary Python libraries using pip:
```bash
pip install opencv-python-headless pillow pytesseract
```

### OCR using Webcam in Tkinter

```python
import tkinter as tk
import cv2
from PIL import Image, ImageTk
import pytesseract

# If you're on Windows, provide the path to your tesseract executable
# pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe"

def ocr_from_frame(frame):
    """Converts an OpenCV frame to grayscale and extracts text using Tesseract OCR."""
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)  # Convert to grayscale
    # Use Tesseract to do OCR on the grayscale image
    pil_image = Image.fromarray(gray)
    text = pytesseract.image_to_string(pil_image)
    return text

def update():
    """Capture frames from the webcam and update the canvas."""
    ret, frame = vid.read()
    if ret:
        photo = ImageTk.PhotoImage(image=Image.fromarray(frame))
        canvas.image = photo  # Store reference to avoid garbage collection
        canvas.create_image(0, 0, image=photo, anchor=tk.NW)

        # Perform OCR on the current frame and display the text
        text = ocr_from_frame(frame)
        text_box.delete(1.0, tk.END)  # Clear the text box
        text_box.insert(tk.END, text)  # Insert the recognized text
    window.after(delay, update)

# Tkinter window setup
window = tk.Tk()
window.title("Webcam OCR")

# Open the webcam
video_source = 0
vid = cv2.VideoCapture(video_source)

# Create a canvas to display the webcam feed
canvas = tk.Canvas(
    window,
    width=vid.get(cv2.CAP_PROP_FRAME_WIDTH),
    height=vid.get(cv2.CAP_PROP_FRAME_HEIGHT),
)
canvas.pack()

# Create a text box to display OCR results
text_box = tk.Text(window, height=10, width=60)
text_box.pack()

# Millisecond delay between frame updates
delay = 15
update()

window.mainloop()
```

### Explanation:
1. **Webcam Capture**: `OpenCV` captures frames from the webcam.
2. **Grayscale Conversion**: The captured frame is converted to grayscale using `cv2.cvtColor` to improve the OCR results.
3. **Tesseract OCR**: The `ocr_from_frame` function converts the frame into a format that `pytesseract` can process and extracts text from it.
4. **Tkinter Interface**: The `tkinter` window displays the webcam feed on a canvas and shows the recognized text in a text box.

### Note:
- If you're using Windows, make sure to specify the path to `tesseract.exe` using `pytesseract.pytesseract.tesseract_cmd = r"path_to_tesseract"`.
- The accuracy of OCR will depend on the quality of the webcam feed and the clarity of the text.