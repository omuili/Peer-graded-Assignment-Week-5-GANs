# Monet-Style Transfer using CycleGAN

This repository contains my submission for the Kaggle "I'm Something of a Painter Myself" GAN competition, which involves transforming regular photos into the style of Claude Monet's paintings.

## Project Overview

In this project, I implemented a CycleGAN (Cycle-Consistent Adversarial Network) to perform unpaired image-to-image translation between photographs and Monet paintings. The goal is to generate Monet-style images from regular photos while preserving the content and structure of the original images.

## Dataset

The dataset provided by Kaggle consists of:
- A collection of Claude Monet's paintings (around 300 images)
- A collection of photographs (around 7,000 images)
- Test photographs for submission (around 1,000 images)

## Implementation

### Architecture

The CycleGAN model consists of:
- Two generators:
  - Generator G: Transforms photos to Monet-style paintings
  - Generator F: Transforms Monet paintings to photos (for cycle consistency)
- Two discriminators:
  - Discriminator X: Distinguishes real photos from generated photos
  - Discriminator Y: Distinguishes real Monet paintings from generated Monet paintings

The generators follow a U-Net architecture with skip connections, while the discriminators use a PatchGAN architecture to classify if image patches are real or fake.

### Loss Functions

The model is trained using several loss components:
- Adversarial loss: Ensures generated images look realistic
- Cycle consistency loss: Ensures the original content is preserved
- Identity loss: Helps preserve color composition

### Training Process

The model was trained for 50 epochs on the dataset, with the following hyperparameters:
- Batch size: 8
- Learning rate: 2e-4
- Beta1: 0.5
- Cycle consistency weight (λ): 10.0
- Identity loss weight: 0.5

## Results

### Sample Transformations

![Sample Results](test_comparison.png)

### Analysis

The model successfully captures several key characteristics of Monet's style:
1. Softer edges and reduced detail
2. Color palette shifts toward Monet's typical colors
3. Introduction of brush stroke-like textures
4. Impressionistic rendering of scenes




## Repository Structure

- `monet_cyclegan.ipynb`: Main notebook with model implementation and training
- `eda_notebook.ipynb`: Exploratory data analysis notebook
- `submission/`: Generated Monet-style images for submission
- `generated_images/`: Sample outputs during training
- `checkpoints/`: Model checkpoints saved during training
- `README.md`: This file

## Installation and Usage

1. Clone this repository:
```
git clone https://github.com/your-username/monet-cyclegan.git
cd monet-cyclegan
```

2. Install the required packages:
```
pip install -r requirements.txt
```

3. Download the data from Kaggle:
```
kaggle competitions download -c gan-getting-started
unzip gan-getting-started.zip
```

4. Run the notebooks:
```
jupyter notebook
```

## Requirements

- TensorFlow 2.x
- NumPy
- Matplotlib
- OpenCV
- tqdm
- scikit-learn

## Acknowledgments

This project is based on the CycleGAN paper by Jun-Yan Zhu et al. (2017) and is part of the Kaggle GAN competition.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
