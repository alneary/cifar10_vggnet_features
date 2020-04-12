# cifar10_vggnet_features
This repository contains the programs and files necessary to use VGGNet16 to generate features for use in APML.
Files (executed in order listed below):
1) Jupyter notebook name: cifar_vggnet_xfer_model-copy2.ipynb
   Output file: cifar_vggnet_xferINv2.h5
   Description: Uses lower-level weights from the VGGNet16 model trained off ImageNet data to train a new model using Cifar10 images. This new model is contained in the 'cifar_vggnet_xferINv2.h5' file - NOTE: .h5 files contain information about the model's design and their final trained weights, BUT will not open properly on their own for viewing. If you want to inspect the architecture of or weights from the model, you will need to look at the next program.
2) Jupyter notebook name: cifar_vggnet_xfer_build_features-copy1.ipynb
   Output files: vgg_cifar10_xfer_||(textXv2, trainXv2, testYv2, trainYv2).csv*
   Description: This notebook takes the model trained in step 1, cuts off the final output layer and uses the remaining layers to create (256) features to be used later with classification. The final datasets are placed in csv format for easy use.
   *Structure of csv files:
   (a) trainXv2.csv = containes 50,000 records (observations/cases) to represent a training set, each having 256 features to be used for prediction. These features were obtained by sending the original 32x32x3 cifar10 images through a custom trained VGGNet16 network.
   (b) testXv2.csv = containes 10,000 records (observations/cases) to represent a test set, each having 256 features to be used for prediction. These features were obtained by sending the original 32x32x3 cifar10 images through a custom trained VGGNet16 network. 
   (c) testYv2.csv = One hot encoded vector representing the class of the image (10 total columns). There will be a 1 in the column inidicating the correct class. This particular csv file pertains to the correct label for the 50,000 training data records (trainXv2.csv).
   (d) trainYv2.csv = One hot encoded vector representing the class of the image (10 total columns). There will be a 1 in the column inidicating the correct class. This particular csv file pertains to the correct label for the 10,000 test data records (testXv2.csv).
   A '1' in the column number to the left indicates the image type to the right:   
             0:'airplane',
             1:'automobile',
             2:'bird',
             3:'cat',
             4:'deer',
             5:'dog',
             6:'frog',
             7:'horse',
             8:'ship',
             9:'truck'  
