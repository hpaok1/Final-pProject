# Final-pProject

"""
Create a GIF with Python using imageio

HOW TO USE THIS FILE

1. Install Python 3 on your computer.
2. Install the imageio library from a terminal or command prompt:

   pip install imageio
   (or)
   pip3 install imageio

3. Put this file (create_gif.py, for example) in a folder.
4. Put your images in the same folder.
5. Update the FILENAMES list below so the names match your image files.
6. From the terminal, go to the folder and run:

   python create_gif.py
   (or)
   python3 create_gif.py

7. A GIF file will be created in the same folder.
"""

import imageio.v3 as iio  # Library to read and write images

# ---------------------------------------------------------------------------
# CONFIGURATION SECTION
# ---------------------------------------------------------------------------

# List of image files to use in the GIF.
# Replace these names with the actual names of your files.
# The order in this list is the order in which they will appear in the GIF.
FILENAMES = [
    "photo1.png",
    "photo2.png",
    "photo3.png",
]

# Name of the output GIF file that will be created.
OUTPUT_GIF = "my_gif.gif"

# Duration of each frame in milliseconds.
# Example: 300 means each image is shown for 0.3 seconds.
DURATION_MS = 300

# Number of times the GIF should loop.
# 0 means infinite loop.
# 1 means play once.
# 2 means play twice, and so on.
LOOP_COUNT = 0

# ---------------------------------------------------------------------------
# MAIN LOGIC
# ---------------------------------------------------------------------------

def create_gif(filenames, output_path, duration_ms, loop_count):
    """
    Create a GIF from a list of image file names.

    filenames   : list of strings with image file names
    output_path : name/path of the GIF file to create
    duration_ms : duration of each frame in milliseconds
    loop_count  : how many times the GIF should loop (0 = infinite)
    """
    # This list will hold the image data after we read each file.
    images = []

    # Go through each file name in the list.
    for filename in filenames:
        # Read the image from the file.
        image = iio.imread(filename)

        # Add the image data to the list.
        images.append(image)

    # Write all images to a single GIF file.
    iio.imwrite(
        output_path,      # Output GIF file name
        images,           # List of all images
        duration=duration_ms,
        loop=loop_count,
    )

    print(f"GIF created successfully: {output_path}")


# ---------------------------------------------------------------------------
# ENTRY POINT
# ---------------------------------------------------------------------------

if __name__ == "__main__":
    create_gif(
        filenames=FILENAMES,
        output_path=OUTPUT_GIF,
        duration_ms=DURATION_MS,
        loop_count=LOOP_COUNT,
    )
