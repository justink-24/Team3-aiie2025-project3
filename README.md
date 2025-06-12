# Comic Strip Writer with Generative AI and Google Gemini
By: Justin Kpana - Isaac Younes - Carl Forman
* This project uses Generative AI (Large Lanuage and Vision Models) to create comic book panels that include both illustrations and dialogue. Users can input a comic topic/prompt and a desired number of panels, and then the system generates matching visuals and text which simulate the skills of a human comic artist and writer.
  
# Problem Statement
* To develop a generative AI system that creates a multi-panel comic strip, when given a prompt and a number of desired panels. Each panel will include a generated image and a dialogue caption which follows narrative consistency throughout.

## Imported Libraries and Modules
* Gemini by Google
* Python
* PIL (Pillow)
* IPython Display
* NumPy
* BAse64
* Wave
* Google Generatiev AI SDK (google.generativeai)

# Model
## Generative Models
* Text Model - Gemini Pro is used to generate:
  * Image scene descrptions for each comic panel
  * Panel dialogue/captions

* Image Model - Gemini 2.0 Flash (experimental image model) is used to generate:
  * Comic-style illustrations from Gemini-generated text prompts

* Input - Text

* The generative system applies a sequence of steps necessary for content creation:
  1. Text prompt input by user ("What should we make a comic about: "; "How many panels should it be: ")
  2. Image scene description generated via 

## Image Processing
* Our Vehicle Type Recognition dataset featured four folders (Bus, Car, Truck, motorcycle) each with 100 images (total of 400 files in our dataset).

* The Car and motorcycle folders were moved to a separate "test" and "train" directory where we split the photos accordingly for each trial.

* The splits used for this experiment include:
  * 80 : 20 = 80% (160 files) for training and 20% (40 files) for testing
  * 70 : 30 = 70% (140 files) for training and 30% (60 files) for testing
  * 60 : 40 = 60% (120 files) for training and 40% (80 files) for testing
  * 50 : 50 = 50% (100 files) for training and 50% (50 files) for testing
  * 85 : 15 = 85% (175 files) for training and 15% (30 files) for testing

* Since CNNs require a fixed input size for inputted images, we decided to test out three different image sizes to be fed into the model. These sizes include 150 x 150, 128 x 128, and 224 x 224.

## Model Pictures
![image](https://github.com/user-attachments/assets/3d8c9a47-4601-4af1-b7ad-fc45c516b9e1)

![image](https://github.com/user-attachments/assets/d24b9f42-845c-4d1e-8eb8-c25cfbbbdd0f)

![image](https://github.com/user-attachments/assets/c176c995-16d3-439c-9a76-b6f4853ebde5)


## Model Performance Table

| Epoch | Layers | Batch Size | Train/Test Split          | Accuracy | Image Size |
|-------|--------|------------|---------------------------|----------|------------|
| 3     | 11     | 32         | 80% train, 20% test       | 50%      | 150 x 150  |
| 10    | 11     | 32         | 80% train, 20% test       | 82%      | 150 x 150  |
| 20    | 11     | 32         | 80% train, 20% test       | 95%      | 150 x 150  |
| 3     | 9      | 16         | 60% train, 40% test       | 69%      | 128 x 128  |
| 10    | 9      | 16         | 60% train, 40% test       | 75%      | 128 x 128  |
| 20    | 9      | 16         | 60% train, 40% test       | 88%      | 128 x 128  |
| 3     | 15     | 64         | 70% train, 30% test       | 50%      | 224 x 224  |
| 10    | 15     | 64         | 70% train, 30% test       | 53%      | 224 x 224  |
| 20    | 15     | 64         | 70% train, 30% test       | 78%      | 224 x 224  |
| 30    |  9     | 32         | 50% train, 50% test       | 94%      | 150 x 150  |
| 10    | 13     | 32         | 85% train, 15% test       | 73%      | 150 x 150  |
| 30    | 13     | 32         | 85% train, 15% test       | 91%      | 150 x 150  |
| 50    | 9      | 32         | 85% train, 15% test       | 94%      | 150 x 150  |

## Results
![results chart](https://github.com/user-attachments/assets/42e703a5-b2e8-4778-9e51-ed73abaf5640)

* The trial that yielded our greatest accuracy percentage (95%) featured 20 epochs, 11 layers, a batch size of 32, an 80:20 train-test split, and an expected image size of 150 x 150.
* Two trials yielded our lowest accuracy percentage of 50%, which is essentially the AI model's version of guessing. Both trials featured 3 epochs yet differed in all other attributes.
* Our best results (95%, 94%, 94%) came from 150x150 image size, high layer counts (20-50), and a moderate batch size (11-13) with standard splits (80:20, 85:15).
* Our poorest performing configurations (69%, 50%, 50%) featured very few epochs (3), larger image sizes (128x128, 224x224), and a lack of model depth. Due to the small number of epochs in those three trials, our machine learning model experienced underfitting (when a model is too simple to capture the underlying patterns provided in training data). Additionally, larger image sizes were used without the corresponding required deeper models, which in turn leads to a drop in performance. Increased image resolution + lack of corresponding model depth = poor performance.
* In conclusion, our best results came from a combination of a moderate image size such as 150x150, a sufficient model depth (20-30 layers), balanced train/test splits (80:20, 85:15) and a moderately small number of layers (~11 -13). Trials with too few layers or large input sizes without deep models convincingly underperformed.

* Final Model – A CNN with 11 layers, trained for 20 epochs using a batch size of 32, an 80:20 train-test split, and fixed input image size of 150×150.
  
## Links to Google Colab Notebooks
* 80:20 split = https://colab.research.google.com/drive/1Ng7Ce1vYFirSZeHEQ9JfkaCo7JqxBPt5?usp=sharing
* 70:30 split = https://colab.research.google.com/drive/10s4Q-cvGm-MrF8D7zg2WOVY8_HBedFQo?usp=sharing
* 60:40 split = https://colab.research.google.com/drive/1PiHsfhQMgLMYloThjE6qAj8tdc6GwPhp?usp=sharing
* 50:50 split = https://colab.research.google.com/drive/1w-8C-cUREOqzPfSk_ZQX3Dr9UEomwDuB?usp=sharing
* 85:15 split = https://colab.research.google.com/drive/1wmzZYqvsNKXAVRmucWe4GPjkLB8y8j_e?usp=sharing

