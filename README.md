# car_licenseplate_detection
## Getting started
### First clone the repository on your device, then
### Installing the required tools and creating a conda environment
#### Tensorflow GPU(use the folowing code)
conda env create -f conda-gpu.yml

conda activate yolov4-gpu

## Using Custom Trained YOLOv4 Weights
Training yolov5 model on car license plate data and creating a model that can detect the license plate in a given image.

Use the Yolov5_custom_training.ipybn to train a custom model.

Afer training the model download the weights of the model and name it as custom.

You can also download the pre-trained weights from here : https://drive.google.com/file/d/1EUPtbtdF0bjRtNjGv436vDY28EN5DXDH/view?usp=sharing

Now copy and paste the weights in data folder.

## Custom Yolov4 model using tensorflow
Run the following commands to load and run the model.

python save_model.py --weights ./data/custom.weights --output ./checkpoints/custom-416 --input_size 416 --model yolov4 

python detect.py --weights ./checkpoints/custom-416 --size 416 --model yolov4 --images ./data/images/car.jpg

### The code above will give an image of car with bounding box on around the license plate as output.
#### This is license plate detection.
#### Now We'll use Tesseract-ocr to recognize the license plate.
## License plate Recognition using Tesseract-ocr.
Disclaimer: In order to run tesseract OCR you must first download the binary files and set them up on your local machine. Please do so before proceeding or commands will not run as expected!

Official Tesseract OCR Github Repo: tesseract-ocr/tessdoc

#### Running License Plate Recognition on Images
The license plate recognition works wonders on images. All you need to do is add the --plate flag on top of the command to run the custom YOLOv4 model.

Try it out on this image in the repository!

# Run License Plate Recognition
python detect.py --weights ./checkpoints/custom-416 --size 416 --model yolov4 --images ./data/images/car2.jpg --plate
## Resulting Image Example
![alt text](https://github.com/theAIGuysCode/yolov4-custom-functions/blob/master/data/helpers/lpr_demo.png)
