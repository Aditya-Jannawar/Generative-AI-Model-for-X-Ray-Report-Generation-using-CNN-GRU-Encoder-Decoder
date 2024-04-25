# X-ray Report Generation Project Readme

## Overview
This project aims to generate textual medical reports based on X-ray images using machine learning techniques. The process involves several key steps, including dataset preparation, optimization, cleaning, image preprocessing, model building, and data generation. This readme provides a concise guide to understanding and replicating the project.

## A. Data Sets
The dataset comprises chest X-ray images paired with correlated diagnostic reports. Each report is structured as an XML file containing vital information such as image IDs and medical findings. Python's XML library is utilized for efficient data extraction.

## B. Optimizing Datasets
After extracting necessary inputs from XML files, the data is processed and organized for clarity and accessibility. Uniformity in model input is maintained by selecting two images per report. Data splitting is based on individuals to prevent data leakage issues.

## C. Cleaning Dataset
Thorough cleaning and preparation of data are performed before supplying it to the model. Special strings ('SOS' and 'EOS') are used for accurate encoding during text preparation. Text tokenization is conducted using the Keras Tokenizer library to split text into word tokens, making it ready for model input.

## D. Image Preprocessing
X-ray images are prepared for input using transfer learning with CheXNet, a 121-layer convolutional neural network trained on the ChestX-ray14 dataset. Pre-trained weights are downloaded, and images are scaled to (224, 224, 3) before running through CheXNet. Features are combined and a mean pooling layer is applied for robustness. Computed features are saved in a dictionary for future analysis.

## E. Data Generators
A custom data generator is implemented to efficiently handle loading and preprocessing of X-ray image and report pairs during model training. It generates batches of data on-the-fly using a subclass of `tensorflow.keras.utils.Sequence`. The generator also implements sequence-to-sequence learning for processing input reports.

## F. Encoder Decoder Model
The encoder-decoder architecture transforms raw input data into meaningful textual output. The encoder, based on DenseNet121, extracts relevant features from X-ray images. The decoder, utilizing a Bidirectional Gated Recurrent Unit (Bi-GRU), processes encoded features sequentially to generate coherent textual reports. The model's architecture is illustrated in Figure 4.

## Conclusion
This project provides a comprehensive framework for generating textual medical reports from X-ray images, leveraging machine learning techniques and transfer learning. By following the outlined steps, users can replicate and extend the functionality of the project for various medical imaging applications.
