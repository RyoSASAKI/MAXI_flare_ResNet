# MAXI_flare_ResNet
(last updade : 2019 Dec 10)

You can judge whether some transient are there or not from one orbit image of MAXI.
To construct a learned model, I prepared 20,000 images. 
The half of these image are MAXI one-orbit image of X Per.
I set the X Per as correct data (I deal them as a flare).
The others are MAXI one-orbit image of Lockman Hole. Lockman Hole is no-source region in the universe.
I set the Lockman Hole image as incorrect data.


To learn this residual network, I used Google Colaboratory.
This program made layers as bellow


As a result of this program, I got the cross-validation score is about 98 percent.

This program is still improving.
