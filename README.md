from PIL import Image
import os

# Define the folder path containing the images
folder_path = 'C:/Users/ronel/Desktop/spearted' #Change accordingly

# List of degrees to rotate
rotations = [90, 180, 270]

# Loop through all files in the folder
for filename in os.listdir(folder_path):
    # Check if the file is an image (you can add more image formats if needed)
    if filename.endswith(('.png', '.jpg', '.jpeg', '.bmp', '.gif')):
        # Open the image file
        img_path = os.path.join(folder_path, filename)
        img = Image.open(img_path)

        # Loop through each rotation angle
        for angle in rotations:
            # Rotate the image
            rotated_img = img.rotate(angle, expand=True)

            # Create a new filename for the rotated image
            new_filename = f"{os.path.splitext(filename)[0]}_rotated_{angle}{os.path.splitext(filename)[1]}"
            new_img_path = os.path.join(folder_path, new_filename)

            # Save the rotated image
            rotated_img.save(new_img_path)

        # Close the image file
        img.close()

print("Images have been rotated and saved successfully.")
