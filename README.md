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


Layer (type)                    Output Shape         Param     Connected to                     
==================================================================================================
input_2 (InputLayer)            (None, 32, 32, 1)    0                                            
__________________________________________________________________________________________________
conv2d_20 (Conv2D)              (None, 32, 32, 32)   832         input_2[0][0]                    
__________________________________________________________________________________________________
batch_normalization_14 (BatchNo (None, 32, 32, 32)   128         conv2d_20[0][0]                  
__________________________________________________________________________________________________
activation_8 (Activation)       (None, 32, 32, 32)   0           batch_normalization_14[0][0]     
__________________________________________________________________________________________________
max_pooling2d_3 (MaxPooling2D)  (None, 16, 16, 32)   0           activation_8[0][0]               
__________________________________________________________________________________________________
conv2d_21 (Conv2D)              (None, 16, 16, 32)   9248        max_pooling2d_3[0][0]            
__________________________________________________________________________________________________
batch_normalization_15 (BatchNo (None, 16, 16, 32)   128         conv2d_21[0][0]                  
__________________________________________________________________________________________________
activation_9 (Activation)       (None, 16, 16, 32)   0           batch_normalization_15[0][0]     
__________________________________________________________________________________________________
conv2d_22 (Conv2D)              (None, 16, 16, 32)   9248        activation_9[0][0]               
__________________________________________________________________________________________________
conv2d_23 (Conv2D)              (None, 16, 16, 32)   1056        max_pooling2d_3[0][0]            
__________________________________________________________________________________________________
batch_normalization_16 (BatchNo (None, 16, 16, 32)   128         conv2d_22[0][0]                  
__________________________________________________________________________________________________
add_7 (Add)                     (None, 16, 16, 32)   0           conv2d_23[0][0]                  
                                                                 batch_normalization_16[0][0]     
__________________________________________________________________________________________________
conv2d_24 (Conv2D)              (None, 16, 16, 32)   9248        add_7[0][0]                      
__________________________________________________________________________________________________
batch_normalization_17 (BatchNo (None, 16, 16, 32)   128         conv2d_24[0][0]                  
__________________________________________________________________________________________________
activation_10 (Activation)      (None, 16, 16, 32)   0           batch_normalization_17[0][0]     
__________________________________________________________________________________________________
conv2d_25 (Conv2D)              (None, 16, 16, 32)   9248        activation_10[0][0]              
__________________________________________________________________________________________________
conv2d_26 (Conv2D)              (None, 16, 16, 32)   1056        add_7[0][0]                      
__________________________________________________________________________________________________
batch_normalization_18 (BatchNo (None, 16, 16, 32)   128         conv2d_25[0][0]                  
__________________________________________________________________________________________________
add_8 (Add)                     (None, 16, 16, 32)   0           conv2d_26[0][0]                  
                                                                 batch_normalization_18[0][0]     
__________________________________________________________________________________________________
conv2d_27 (Conv2D)              (None, 16, 16, 32)   9248        add_8[0][0]                      
__________________________________________________________________________________________________
batch_normalization_19 (BatchNo (None, 16, 16, 32)   128         conv2d_27[0][0]                  
__________________________________________________________________________________________________
activation_11 (Activation)      (None, 16, 16, 32)   0           batch_normalization_19[0][0]     
__________________________________________________________________________________________________
conv2d_28 (Conv2D)              (None, 16, 16, 32)   9248        activation_11[0][0]              
__________________________________________________________________________________________________
conv2d_29 (Conv2D)              (None, 16, 16, 32)   1056        add_8[0][0]                      
__________________________________________________________________________________________________
batch_normalization_20 (BatchNo (None, 16, 16, 32)   128         conv2d_28[0][0]                  
__________________________________________________________________________________________________
add_9 (Add)                     (None, 16, 16, 32)   0           conv2d_29[0][0]                  
                                                                 batch_normalization_20[0][0]     
__________________________________________________________________________________________________
max_pooling2d_4 (MaxPooling2D)  (None, 8, 8, 32)     0           add_9[0][0]                      
__________________________________________________________________________________________________
conv2d_30 (Conv2D)              (None, 8, 8, 64)     18496       max_pooling2d_4[0][0]            
__________________________________________________________________________________________________
batch_normalization_21 (BatchNo (None, 8, 8, 64)     256         conv2d_30[0][0]                  
__________________________________________________________________________________________________
activation_12 (Activation)      (None, 8, 8, 64)     0           batch_normalization_21[0][0]     
__________________________________________________________________________________________________
conv2d_31 (Conv2D)              (None, 8, 8, 64)     36928       activation_12[0][0]              
__________________________________________________________________________________________________
conv2d_32 (Conv2D)              (None, 8, 8, 64)     2112        max_pooling2d_4[0][0]            
__________________________________________________________________________________________________
batch_normalization_22 (BatchNo (None, 8, 8, 64)     256         conv2d_31[0][0]                  
__________________________________________________________________________________________________
add_10 (Add)                    (None, 8, 8, 64)     0           conv2d_32[0][0]                  
                                                                 batch_normalization_22[0][0]     
__________________________________________________________________________________________________
conv2d_33 (Conv2D)              (None, 8, 8, 64)     36928       add_10[0][0]                     
__________________________________________________________________________________________________
batch_normalization_23 (BatchNo (None, 8, 8, 64)     256         conv2d_33[0][0]                  
__________________________________________________________________________________________________
activation_13 (Activation)      (None, 8, 8, 64)     0           batch_normalization_23[0][0]     
__________________________________________________________________________________________________
conv2d_34 (Conv2D)              (None, 8, 8, 64)     36928       activation_13[0][0]              
__________________________________________________________________________________________________
conv2d_35 (Conv2D)              (None, 8, 8, 64)     4160        add_10[0][0]                     
__________________________________________________________________________________________________
batch_normalization_24 (BatchNo (None, 8, 8, 64)     256         conv2d_34[0][0]                  
__________________________________________________________________________________________________
add_11 (Add)                    (None, 8, 8, 64)     0           conv2d_35[0][0]                  
                                                                 batch_normalization_24[0][0]     
__________________________________________________________________________________________________
conv2d_36 (Conv2D)              (None, 8, 8, 64)     36928       add_11[0][0]                     
__________________________________________________________________________________________________
batch_normalization_25 (BatchNo (None, 8, 8, 64)     256         conv2d_36[0][0]                  
__________________________________________________________________________________________________
activation_14 (Activation)      (None, 8, 8, 64)     0           batch_normalization_25[0][0]     
__________________________________________________________________________________________________
conv2d_37 (Conv2D)              (None, 8, 8, 64)     36928       activation_14[0][0]              
__________________________________________________________________________________________________
conv2d_38 (Conv2D)              (None, 8, 8, 64)     4160        add_11[0][0]                     
__________________________________________________________________________________________________
batch_normalization_26 (BatchNo (None, 8, 8, 64)     256         conv2d_37[0][0]                  
__________________________________________________________________________________________________
add_12 (Add)                    (None, 8, 8, 64)     0           conv2d_38[0][0]                  
                                                                 batch_normalization_26[0][0]     
__________________________________________________________________________________________________
global_average_pooling2d_2 (Glo (None, 64)           0           add_12[0][0]                     
__________________________________________________________________________________________________
dense_2 (Dense)                 (None, 2)            130         global_average_pooling2d_2[0][0] 
__________________________________________________________________________________________________
__________________________________________________________________________________________________
Total params: 275,618
Trainable params: 274,402
Non-trainable params: 1,216
________________________________________________________________________________________________






As a result of this program, I got the cross-validation score is about 98 percent.

This program is still improving.
