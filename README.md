## Project: Skin Condition Detection AI

Skin Condition Detection AI's main goal is to simplify the diagnosis of common skin conditions through the use of Artificial intelligence. In today's day and age, almost everything that normally needed to be completed in person can be done online. Since healthcare is limited and many people can't even afford to have a medical diagnosis, this AI will allow people to diagnose skin conditions from home or anywhere in the world, as long as they have access to the internet.

Impacts: This AI can help notify a patient about possible skin conditions that they weren't aware of prior to the use of the AI, effectively helping to uncover any growing health problems or to prevent the transmission of contagious diseases.

## The Algorithm
skinDetection AI aims to simplify the diagnosis of skin conditions through image classification. It uses a retrained model of resnet-18 and also the imagenet.py program to classify our 2 classes of skin conditions ( Melanoma and Acne ) + Healthy Skin.

An example of a successfully classified image (Melanoma): 

<img width="200" alt="b_test" src="https://github.com/Invincible-51/Skin-Condition-Detector/assets/141347812/a930868e-d8dc-4a60-b3ae-3fabbf115e72">



Datasets (3): Melanoma, Acne, and Healthy Skin ( to prevent inaccurate diagnosis of actual skin conditions for people who don’t actually have any)

Accuracy ( based on results after training 30 images of each test dataset ): Melanoma: 80% Accuracy.  Acne: 90% Accuracy.  Healthy Skin: 96.67% Accuracy

Image Quantity: Train ( Avg for all 3 classifications ): 306.  Test ( all 3 classifications ): 30.  

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

8. Use the scp command ( as listed below ) to look up the image in the host computer.

   Windows:
scp <nanousername>@192.168.55.1:/home/<nanousername>/jetson-inference/python/training/classification/cat.jpg C:\Users\<hostusername>\Desktop

   Mac:
scp <nanousername>@192.168.55.1:/home/<nanousername>/jetson-inference/python/training/classification/cat.jpg ./

    
10. (Optional) if you want to test your own image of a skin condition ( must be either Acne, Melanoma, or Healthy Skin ) add it to the test directory into any classification folder you like ( or put it in the correct one if you want to be organized ) and proceed to step 9.

Project Video: https://youtu.be/EXyd0CnVtxA
