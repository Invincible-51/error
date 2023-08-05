## Project: Skin Condition Detection AI

Skin Condition Detection AI can help doctors to save time and energy by diagnosing the patients' skin condition for them, effectively minimizing the duration of doctor appointments and ensuring accuracy at the same time. This AI may also be used at home or anywhere in the world if a patient suspects they may have a skin condition, making healthcare diagnosis more accessible to everyone.

## The Algorithm
skinDetection AI aims to simplify the diagnosis of skin conditions through image classification. It uses a retrained model of resnet-18 and also the imagenet.py program to classify our 2 classes of skin conditions ( Melanoma and Acne ) + Healthy Skin.

## How to run the project:

1. Ensure that you have a Jetson Nano.
2. Ensure that the following are already installed on your Jetson Nano:
   a. Python 3
   b. The Jetson Inference Library

3. Download these files ( model_best.pth.tar and resnet18.onnx ):
   https://drive.google.com/file/d/1jy62BAQUUxFDJUQOBKj1tcToyC9bq8jR/view?usp=sharing
   https://drive.google.com/file/d/1d_OH1yr9cGgVBsUU5Io2ZbRhuLXw6P6B/view?usp=sharing

4. Download the pre-organized image dataset:
   https://drive.google.com/drive/folders/1pFk92QhsgzjaCGGanuFlUXimN5YV1aRf?usp=sharing
   
5. Open terminal and login.

6. a. Navigate to the classification directory
   ### cd jetson-inference/python/training/classification

   b. Set the NET and DATASET variables
   ### NET=models/skin_ai_data
   ### DATASET=data/skin_ai_data

7. To process an image, use this command:
   ### imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/a_test/File_A1.jpg a_test.jpg

* Since there are 3 different test classification directories, you may replace the 'a_test/File_A1.jpg a_test.jpg' at the end of the command with 'c_test/File_C1.jpg c_test.jpg' and 'b_test/File_B1.jpg b_test.jpg' to choose images from a different test directory. To change the specific tested image, change the number AFTER the snippet 'File_A/B/C' with the numbers listed inside of the test classification directories. example: b_test/File_B4.jpg b_test.jpg

  "a_test" is for Acne,

  "b_test" is for Melanoma,

  and "c_test" is for healthy skin.

8. Use the scp command to look up the image in the host computer.

   Windows:
scp <nanousername>@192.168.55.1:/home/<nanousername>/jetson-inference/python/training/classification/cat.jpg C:\Users\<hostusername>\Desktop

   Mac:
scp <nanousername>@192.168.55.1:/home/<nanousername>/jetson-inference/python/training/classification/cat.jpg ./

    
10. (Optional) if you want to test your own image of a skin condition ( must be either Acne, Melanoma, or Healthy Skin ) add it to the test directory into any classification folder you like ( or put it in the correct one if you want to be organized ) and proceed to step 9.

Project Video: https://youtu.be/cyXDj2gxPpM
