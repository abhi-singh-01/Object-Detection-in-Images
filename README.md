# Object-Detection-in-Images
Detecting object into the images using Python library  ultralytics

#Code
First we run this to install the library required for it 
pip install ultralytics opencv-python matplotlib

from ultralytics import YOLO
import cv2
import matplotlib.pyplot as plt
def display_image(image, title="Image"):
    """Display an image using matplotlib."""
    plt.figure(figsize=(10, 10))
    plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    plt.title(title)
    plt.axis("off")
    plt.show()

# Load the YOLOv5 model (you can use 'yolov5s', 'yolov5m', etc.)
model = YOLO('yolov8n.pt')  #specify a custom model path.

# Load an image for object detection
image_path = '/content/OIP.jpeg'
image = cv2.imread(image_path)

# Perform object detection
results = model(image)

# Visualize results on the image
annotated_image = results[0].plot()

# Display the annotated image
display_image(annotated_image, title="Detected Objects")

# Save the annotated image
output_path = "output_image.jpg"
cv2.imwrite(output_path, annotated_image)
print(f"Annotated image saved to {output_path}")

