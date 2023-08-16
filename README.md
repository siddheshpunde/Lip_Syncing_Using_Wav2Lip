# Lip_Syncing_Using_Wav2Lip
Welcome to the Lip Syncing Using Wav2Lip GitHub repository! This project focuses on the exciting task of lip syncing using the Wav2Lip model. With this repository, you can easily synchronize speech from an audio source with the lip movements of a target video.
# Steps to run
* Step 1
Install libraries and Download pre-Trained model
* Step 2
  Upload video
  Trim your video
* Step 3
  Resize your video
* Step 4
  upload your audio file directly to your colab notebook

The length of video file and audio file should be same.

Make the changes in your inference.py file /content/Wav2Lip/inference.py add the below code to the main function to process with the non-face detected frames.

Add this code from line no 265 in inference.py file

        for p, f, c in zip(pred, frames, coords):
            if len(c) == 0:  # Check if there are no face coordinates (no face detected)
                out.write(f)  # Write the original frame without lip-syncing
            else:
                if len(c) == 4:  # Check if there are four values in the coordinates
                    y1, y2, x1, x2 = c
                    p = cv2.resize(p.astype(np.uint8), (x2 - x1, y2 - y1))
                    f[y1:y2, x1:x2] = p
                else:
                    print("Invalid coordinates:", c)  # Print a message for debugging purposes
        
                out.write(f)  # Write the lip-synced frame to the output video
* Step 5
  * Give the path of your audio and video files after preprocessing.
  * Change the value of pad_top, pad_bottom, pad_left, Pad_right as per your input video.
  * pad_top = 0
  * pad_bottom = 4
  * pad_left = 0
  * pad_right = 50
  * rescaleFactor = 1
  * nosmooth = False
  * Strat training your model
# Input Video

https://github.com/siddheshpunde/Lip_Syncing_Using_Wav2Lip/assets/59832099/ae03eb35-759d-48ca-a614-429a479a14d4

# Output Video

https://github.com/siddheshpunde/Lip_Syncing_Using_Wav2Lip/assets/59832099/7ce42070-4778-4a86-b800-fc8dc33d8163

