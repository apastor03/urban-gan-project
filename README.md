# 🛰️ UrbanGAN: Generating Future Satellite Images of City Growth

UrbanGAN is a generative machine learning project that predicts how cities evolve over time using satellite imagery.
Given a satellite image from a year in the past, say 2015, the model generates a realistic approximation of a future image of that city.
This project explores how deep learning models can capture spatial patterns in urban development, such as infrastructure expansion, land use changes, and density growth.

---

The goal of this project is to map past satellite images to generate futuristic satellite images. Using image-to-image translation techniques,
the model predicts how a city’s layout changes over time.

---

## Methods

### Model
- Convolutional Neural Network (CNN)
- U-Net–style architecture with skip connections (for spatial preservation)
- Residual learning to model changes instead of full images

### Training
- Input: Satellite images from 2015  
- Target: Satellite images from 2020  
- Loss Function: L1 Loss (pixel-wise reconstruction)  
- Optimizer: Adam  

### Key Design Choices
- Paired dataset (aligned by city and year)
- Image normalization for stable training
- Residual output (`output = input + prediction`) for better realism

---

## Dataset
I used a large dataset consisting of tens of thousands of different cities in the US and their corresponding information. The most crucial
variables in the dataset that were used were the cities' longitude and latitude coordinates, as these were used to pinpoint the precise location
of the area where we need to obtain the satellite image.

THe images are then pulled into a Google Drive folder, which are then downloaded manually and sorted into a series of directories matching the city name and the year
that the photos were taken in. Images are paired by order to align temporal changes.

---

## Important Features

- Generate future satellite images from past inputs
- Evaluate model performance using **SSIM (Structural Similarity Index)**
- Save generated images automatically
- User input system to select a city
- End-to-end pipeline from data loading → generation → evaluation

---

## Results

The model is able to capture general spatial structure (roads, layout, density) and create raw futuristic images of those cities and approximate their urban growth patterns.

Limitations:
- Outputs may appear blurry due to L1 loss
- Fine details are not perfectly reconstructed
- Performance depends on training duration and dataset size

---

## How to Run

### 1. Clone the repository

git clone https://github.com/YOUR_USERNAME/urban-gan-project.git

cd urban-gan-project


### 2. Install dependencies

pip install torch torchvision matplotlib pandas scikit-image


### 3. Run the pipeline

python your_script_name.py


### 4. Enter a city name when prompted
Example:

Enter a city name: for example, Chicago


The model will:
- Generate a future satellite image
- Print evaluation metrics (SSIM)
- Save the output image

---

## Evaluation

Model performance is evaluated using:

- **SSIM (Structural Similarity Index)**  
  Measures similarity between generated and real images  

---

## Future Improvements

- Implement Pix2Pix GAN for sharper outputs  
- Use diffusion models for higher realism  
- Add multi-year prediction (e.g., 2010 → 2020 → 2030)  
- Incorporate external data (population, zoning, etc.)  

---

## Acknowledgements

- PyTorch for deep learning framework  
- scikit-image for evaluation metrics  
- Public satellite imagery datasets  

---

## References

- Isola et al. (2017). *Image-to-Image Translation with Conditional Adversarial Networks*  
- Goodfellow et al. (2014). *Generative Adversarial Networks*  

---

## Author
Adam Pastor  
Quantitative Sciences & Physics 
