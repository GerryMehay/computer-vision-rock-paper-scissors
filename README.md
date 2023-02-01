# Computer Vision RPS

Rock-paper-scissor RPS is a game in which players show one of the three hand gestures simultaneously, representing rock, paper, or scissors. Rock beats scissors. Scissors beats paper. Paper beats rock. The player who shows the first option that beats the other player's option wins. This is an implementation of an interactive Rock-Paper-Scissors game, in which the user can play with the computer using the camera. 

## Milestone 1
* A Github repository is created to track changes and save code online

## Milestone 2
* this code created a computer vision in which the model detecs wether the user is showing rock, paper or scissors to the camera. 
* the model was created using a technology called Teachable Machine where different classes are made to represent the rock, paper or scissor.
* to train each class to represent the RPS a lot of pictures were takes in different angles to make the outcome more accurate.

## Milestone 3
* Before you can use the model, you need to install the libraries that it depends on.
Create a conda environment and then install the necessary requirements. You need opencv-python, tensorflow, and ipykernel
Start by creating the environment, activate it, and then install pip by running the following command in your terminal conda install pip. Then, to install the rest of the libraries, run pip install <library>.
Where my_env is the name of the environment you want to create.
After that, the libraries you have to install are the ones mentioned above.
* And finally, make sure you install ipykernel by running the following command:
pip install ipykernel
Once you installed everything (regardless of the operating system) create a requirements.txt file by running the following command:
pip list > requirements.txt
This file enables any other user that wants to use your computer to easily install these exact dependencies by running pip install requirements.txt.
* Run this code just to check the model you downloaded is working as expected
 ```
  import cv2
from keras.models import load_model
import numpy as np
model = load_model('keras_model.h5')
cap = cv2.VideoCapture(0)
data = np.ndarray(shape=(1, 224, 224, 3), dtype=np.float32)

while True: 
    ret, frame = cap.read()
    resized_frame = cv2.resize(frame, (224, 224), interpolation = cv2.INTER_AREA)
    image_np = np.array(resized_frame)
    normalized_image = (image_np.astype(np.float32) / 127.0) - 1 # Normalize the image
    data[0] = normalized_image
    prediction = model.predict(data)
    cv2.imshow('frame', frame)
    # Press q to close the window
    print(prediction)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
 ```
 
Make sure that you have the correct name for the model, the correct name for the labels, and that the model and this file are in the same folder.

## Milestone 4
* This code needs to randomly choose an option (rock, paper, or scissors) and then ask the user for an input.
File called manual_rps.py that will be used to play the game without the camera.
You will need to use the random module to pick a random option between rock, paper, and scissors and the input function to get the user's choice.
Create two functions: get_computer_choice and get_user_choice.
The first function will randomly pick an option between "Rock", "Paper", and "Scissors" and return the choice.
The second function will ask the user for an input and return it.

* Using if-elif-else statements, the script should now choose a winner based on the classic rules of Rock-Paper-Scissors.
For example, if the computer chooses rock and the user chooses scissors, the computer wins.
Wrap the code in a function called get_winner and return the winner.
This function takes two arguments: computer_choice and user_choice.
If the computer wins, the function should print "You lost", if the user wins, the function should print "You won!", and if it's a tie, the function should print "It is a tie!".

* All of the code you've programmed so far relates to one thing: running the game - so you should wrap it all in one function.
Create and call a new function called play.
Inside the function you will call all the other three functions you've created (get_computer_choice, get_user_choice, and get_winner)
Now when you run the code, it should play a game of Rock-Paper-Scissors, and it should print whether the computer or you won.
  
## Milestone 5
