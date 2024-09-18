# Image-Based Unit Prediction Model

This repository contains a machine learning pipeline that predicts numerical values with defined units (e.g., kilogram, watt, meter, etc.) from product images. The pipeline utilizes a pre-trained ResNet50 model for feature extraction from images and a RandomForestRegressor for predicting values.

The code is designed to handle up to 1000 images for training and testing. Predictions are saved in a CSV file in the format required for submission, with units like "kilogram," "pound," "watt," etc., attached to the predicted values.

## Features
- Pre-trained ResNet50 model for image feature extraction.
- RandomForestRegressor model for numerical value predictions.
- Support for 10 different units, randomly assigned to predictions.
- Handles both grayscale and RGB images.
- Stops after processing 1000 images, leaving remaining rows empty as per the required format.

## Dataset
- **train.csv**: A CSV file containing the image links and corresponding entity values for training.
- **test.csv**: A CSV file containing the image links for which predictions will be made.

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/your-username/image-unit-prediction.git
    cd image-unit-prediction
    ```

2. Install the required Python packages:

    ```bash
    pip install -r requirements.txt
    ```

### Dependencies
- Python 3.x
- Torch and torchvision
- scikit-learn
- Pillow
- Requests
- Pandas
- Numpy

## Usage

1. **Prepare Training Data**: The training data should be in `train.csv` format, containing columns like `image_link` and `entity_value`.
2. **Prepare Test Data**: The test data should be in `test.csv` format, containing the `image_link` column for prediction.

2. **Run the model**:

    ```bash
    python image_prediction.py
    ```

This will:
- Download images from URLs in the CSV files.
- Preprocess the images for feature extraction.
- Train the model on the training data.
- Make predictions on the test data and randomly assign a unit to each prediction.
- Save the predictions in `test_out.csv`.

## Output

The final predictions are saved in a CSV file named `test_out.csv`. The CSV will have two columns:
- `index`: The index of the test data.
- `prediction`: The predicted numerical value with a randomly assigned unit, e.g., `"50.23 kilogram"`, `"100.78 watt"`, etc.

If the 1000 image limit is reached, the remaining rows will be left empty in the `prediction` column.

## Example CSV Output
```csv
index,prediction
0,21.90 foot
1,10.00 foot
2,
3,289.52 kilovolt
4,1078.99 kilowatt
...
