# Object Detection and OCR

This project implements an object detection model combined with Optical Character Recognition (OCR) to detect objects (such as license plates or any text-containing objects) in images and recognize the text on them.

## Overview

The system uses a combination of:
- **Object Detection**: To identify and locate objects (e.g., license plates) within an image.
- **OCR (Optical Character Recognition)**: To extract the text from the detected objects.

The recognized text is then saved in a CSV file, where each image's recognized text is mapped to individual character columns.

## Features
- Detects objects (like license plates) in images using an object detection model.
- Uses an OCR model to recognize the text from the detected object.
- Saves the recognized text in a CSV file where each character from the detected text is stored in a separate column.
- Supports batch processing of images in a folder.

## Requirements
- Python 3.8+
- TensorFlow
- OpenCV
- NumPy
- Pandas
- Matplotlib

## Setup

### 1. Clone the repository
Clone this repository to your local machine:
```bash
git clone https://github.com/yourusername/Object-Detection-OCR.git
cd Object-Detection-OCR
2. Install the dependencies
Install the required Python packages using pip:

bash
Copy code
pip install -r requirements.txt
3. Prepare the dataset
Ensure that your dataset is structured with images in a folder. The images should be in a format supported by OpenCV and Pillow (e.g., .jpg, .png).

4. Run the notebook
Launch the Jupyter notebook:

bash
Copy code
jupyter notebook
Open the provided .ipynb file (Object_Detection_and_OCR.ipynb) in the Jupyter interface.

5. Process the images and save the recognized text
Run the cells in the notebook to process images from your folder, detect objects, recognize the text, and save the output in a CSV file.

Example
You can process images from a folder using the following code (inside the notebook):

python
Copy code
# Import necessary libraries
import os
import pandas as pd

# Set the path to the folder containing the images
image_folder = "path/to/your/image/folder"

# Function to detect and recognize text from each image
def detect_and_recognize_from_folder(image_folder):
    recognized_texts = []
    
    # Loop through images in the folder
    for img_path in os.listdir(image_folder):
        img_full_path = os.path.join(image_folder, img_path)
        
        # Perform object detection and OCR
        text = detect_and_recognize(img_full_path)  # Assuming detect_and_recognize is your function
        recognized_texts.append((img_path, text))

    # Save results to a CSV file
    df = pd.DataFrame(recognized_texts, columns=['Image ID', 'Recognized Text'])
    df.to_csv('recognized_text.csv', index=False)

# Call the function
detect_and_recognize_from_folder(image_folder)
6. View Results
After running the notebook, the recognized text from all processed images will be saved in a recognized_text.csv file in the repository's directory.

Notebook Structure
Object Detection: The first part of the notebook loads and processes the input images, applying the object detection model to locate text-containing objects.
OCR Recognition: After detecting the objects, the notebook uses the OCR model to recognize text from the bounding boxes.
Saving the Results: The final part saves the results in a CSV file where each character from the recognized text is stored in individual columns.
Example Output (CSV)
The output recognized_text.csv will have the following format:

Image ID	0	1	2	3	4	5	6	7	8
950.jpg	A	B	C	D	E	F	G	H	I
Where Image ID is the name of the image file, and each subsequent column corresponds to a character in the recognized text from the image.

License
This project is licensed under the MIT License - see the LICENSE file for details.

markdown
Copy code

### Key Points:
1. **Repository Overview**: Describes the functionality of the object detection and OCR process.
2. **Requirements**: Lists necessary libraries (Python, TensorFlow, OpenCV, etc.).
3. **Setup Instructions**: Provides clear instructions on how to clone the repo, install dependencies, and run the Jupyter notebook.
4. **Processing Instructions**: Explains how the images can be processed and saved in a CSV file.
5. **Notebook Structure**: Outlines the flow and components of the notebook, which combines object detection and OCR.

This `README.md` should provide a clear understanding of how to set up and use your project.
