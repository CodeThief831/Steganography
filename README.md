# Steganography

Certainly! Here's the content `README.md` file:

---

# Image Steganography README

## Encryption (Sender):

```python
import cv2
import os

# Load the original image
img = cv2.imread("cat.jpg")  # Replace with the correct image path

# Get the secret message and passcode from the user
msg = input("Enter secret message:")
password = input("Enter a passcode:")

# Create dictionaries for character-to-integer and integer-to-character mapping
d = {}
c = {}
for i in range(255):
    d[chr(i)] = i
    c[i] = chr(i)

# Initialize variables for image traversal
m = 0
n = 0
z = 0

# Embed the message in the image using RGB channels
for i in range(len(msg)):
    img[n, m, z] = d[msg[i]]
    n = n + 1
    m = m + 1
    z = (z + 1) % 3

# Save the encrypted image
cv2.imwrite("encryptedImage.jpg", img)
os.system("start encryptedImage.jpg")  # Open the image on Windows
```

**Points to Highlight:**
- **Image Loading**: Original image loaded using OpenCV.
- **User Input**: User prompted for a secret message and passcode.
- **Dictionaries**: Dictionaries created for character-to-integer and integer-to-character mapping.
- **Image Traversal**: Message embedded into the image using RGB channels.
- **Saving Image**: Encrypted image saved as "encryptedImage.jpg."
- **Image Display**: The encrypted image opened on Windows.

## Decryption (Receiver/Decoder):

```python
import cv2
import os

# Load the encrypted image
img = cv2.imread("encryptedImage.jpg")

# Get the passcode for decryption
pas = input("Enter passcode for Decryption")

# Check if the passcode matches
if password == pas:
    # Initialize variables for image traversal
    n = 0
    m = 0
    z = 0

    # Retrieve the hidden message from the image
    message = ""
    for i in range(len(msg)):
        message = message + c[img[n, m, z]]
        n = n + 1
        m = m + 1
        z = (z + 1) % 3

    # Print the decrypted message
    print("Decryption message:", message)
else:
    print("YOU ARE NOT auth")
```

**Points to Highlight:**
- **Image Loading**: Encrypted image loaded using OpenCV.
- **User Input**: User prompted for the passcode for decryption.
- **Passcode Verification**: Checks if the provided passcode matches the original.
- **Image Traversal**: Hidden message retrieved from the image using RGB channels.
- **Decrypted Message Display**: Decrypted message printed if the passcode is correct.

---
