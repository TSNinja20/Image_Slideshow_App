# Image_Slideshow_App
A simple Python image slideshow viewer using Tkinter. Input your image paths, and the app resizes them to 1080x1080 pixels, displaying each image for 3 seconds. Click the "Play Slideshow" button to start. Requires `PIL/Pillow`. Perfect for showcasing photos in a seamless loop. Contributions welcome!

**Image Slideshow Viewer**

**Description**
This Python application creates a simple image slideshow viewer using Tkinter. The application displays a sequence of images from a specified list of file paths, resizing them to a consistent size and cycling through them at a fixed interval.

**Features**
Display images in a slideshow format.
Resize images to a specific resolution (1080x1080 pixels).
Start the slideshow with a play button.

**Requirements**
Python 3.x
PIL/Pillow library
tkinter library

**Installation**
Install the required libraries using pip:
pip install pillow

**Usage**
Add the paths of the images you want to include in the slideshow to the image_paths list.
Run the script.
Click the "Play Slideshow" button to start the slideshow.

**Example Code**

from itertools import cycle
from PIL import Image, ImageTk
import time
import tkinter as tk

# Initialize the Tkinter root
root = tk.Tk()
root.title("Image Slideshow Viewer")

# List of Image Paths
image_paths = [
    r"C:\Users\NINJA\OneDrive\Pictures\PHOTOS\1637671808717.jpg",
    r"C:\Users\NINJA\OneDrive\Pictures\PHOTOS\1637672226586.jpg",
    r"C:\Users\NINJA\OneDrive\Pictures\PHOTOS\IMG_3678.jpg",
    r"C:\Users\NINJA\OneDrive\Pictures\PHOTOS\IMG20221021142252.jpg",
]

# Resize the images to 1080x1080
image_size = (1080, 1080)
images = [Image.open(path).resize(image_size) for path in image_paths]
photo_images = [ImageTk.PhotoImage(image) for image in images]

# Create and pack the label widget
label = tk.Label(root)
label.pack()

# Function to update the image
def update_image():
    for photo_image in photo_images:
        label.config(image=photo_image)
        label.update()
        time.sleep(3)

# Cycle through the images
slideshow = cycle(photo_images)

# Function to start the slideshow
def start_slideshow():
    for _ in range(len(image_paths)):
        update_image()

# Create and pack the play button
play_button = tk.Button(root, text='Play Slideshow', command=start_slideshow)
play_button.pack()

# Start the Tkinter event loop
root.mainloop()
Customization
Image Paths: Add or modify the paths in the image_paths list to include your images.
Image Size: Adjust the image_size variable to change the resolution of the displayed images.
Interval: Modify the time.sleep(3) line in the update_image function to change the time interval between images.
