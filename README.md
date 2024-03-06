# Final project
video https://www.youtube.com/watch?v=PKPsuBqPRqg. deploy https://tr-1.onrender.com/










# Introduction
### Problem

Nowadays the prevalence of road traffic accidents remains a significant global concern, resulting in countless fatalities and injuries each year. Without a doubt, a key contributing factor to these accidents is the failure of drivers to recognize and adhere to traffic signs effectively. Therefore, developing a robust system for traffic sign recognition and classification is imperative to mitigate the risks associated with road safety. By implementing advanced machine learning techniques, we aim to address this pressing issue and contribute to creating safer road environments for all.

### Literature review with links
At present images carry tons of information. Computer Vision plays a pivotal role and is one of the active research fields in Deep Learning implementations, and image classification is on top of that, a basic study in Computer Science as Lihua Luo states in her research (2021).  
Deep Learning with its strong image feature extraction became a main attraction of scientists and engineers since it was proposed. Every image classification application goes through image preprocessing and feature extraction, etc. Feature extraction is an issue and an important factor, however, because it directly affects the accuracy and loss of machine models. Three features gain approval usually:

1. Color feature: Describing color characteristics. Image classification approaches often rely on color histograms or color moments to represent color features.
2. Shape feature: contour detection and shape context descriptors have been integrated with deep learning architectures to capture the geometric properties of objects in an image.
3. Texture feature: describe the repetitive patterns in an image, such as roughness or smoothness, by reflecting the surface properties.

Convolutional Neural Network is a neural network consisting of multiple layers that imitates human’s image recognition. Architecture:

- CNNs are composed of multiple layers, including convolutional layers, pooling layers, and fully connected layers.
- Convolutional layers consist of filters (also known as kernels) that slide across the input image, extracting features through convolution operations.
- Pooling layers reduce the spatial dimensions of the feature maps generated by convolutional layers through the operations of max pooling or average pooling usually.
- Fully connected layers connect every neuron in one layer to every neuron in the next layer, ultimately producing the final output.

Jou-ching (George) Sung implemented the SSD (Single Shot MultiBox Detector) in tensorflow to detect and classify traffic signs [ssd_tensorflow_traffic_sign_detection](https://github.com/georgesung/ssd_tensorflow_traffic_sign_detection/tree/master).

### Current work
Our current work focuses on the development of an intelligent machine learning algorithm for traffic sign recognition and classification. Leveraging insights from existing solutions and research papers, we are implementing state-of-the-art deep learning techniques, particularly convolutional neural networks (CNNs), to achieve accurate and robust performance in real-world scenarios. This involves extensive data preprocessing, model training, and evaluation to ensure the effectiveness of our approach in promoting road safety. Furthermore, we implemented a user-friendly interface on a web platform to facilitate model testing and evaluation by end-users. This platform allows users to upload images of traffic signs, which are then processed by the model to provide real-time classification results, including detailed information about the recognized sign's importance and associated traffic regulations.

Overall, our current work represents a comprehensive and systematic approach to developing an effective traffic sign recognition system, leveraging cutting-edge machine learning techniques and methodologies to address critical road safety concerns.

# Data and Methods

### Information about the data

Working with Dataset:

The Dataset https://universe.roboflow.com/usmanchaudhry622-gmail-com/traffic-and-road-signs

Google Drive https://drive.google.com/drive/folders/1NeJhtWPfeU8lxht_9Ud_c4Ecg6ef4FBA
The initial amount of photos for training is 7000+, so we reduced it by half by deleting unnecessary classes, redundant for Kazakhstan. Classes left:
- cycle route ahead warning
- end of all speed and passing limits
- give way
- go straight or turn left
- go straight or turn right
- no entry
- round-about
- straight ahead only
- stop sign
- truck traffic prohibited
- turn left ahead
- turn right ahead

![Screenshot 2024-03-06 200649](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/8afae8a0-54d1-4273-8ae2-c981bd2feb2c)
![Screenshot 2024-03-06 200726](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/8e058412-fc24-4b1e-86e5-81eac57e46e8)

### Description of ML/DL models
We did not make use of pre-trained models instead we build a model ourselves using the tensorflow framework
We used image_dataset_from_directory(), returns a tf.data.Dataset object, from keras utils to construct datasets for training and validation, then applied some caching buffered prefetching to facilitate the training process:
![Screenshot 2024-03-06 202112](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/b3f6e33d-c6be-4882-b4f1-970ed5275fac)
![Screenshot 2024-03-06 202506](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/171da0fe-845c-4bcb-84b0-97cbdb9888a5)

Adding data augmentation:

![Screenshot 2024-03-06 203007](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/b3a462da-feba-4cd0-9d6d-4350a6ffcc33)

Generally speaking the accuracy of a model may be improved by increasing a dataset. For example, data augmentation is a technique used to artificially create new training data from the existing dataset by applying random transformations like rotations, flips, zooms, etc.  
Model

![Screenshot 2024-03-06 203236](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/75667a58-5682-43dd-a62d-7dbe5042e9d5)

Conv2D (Convolutional layer) with no hesitations can be called as the backbone of our model. These layers apply filters (or kernels) to the inputs so they extract features and produce feature maps.
Pooling functions replace the output of the net at a certain location with a summary statistic of the nearby outputs. This helps in reducing the spatial dimensions of the feature maps result in making the model more robust.
Batch normalization helps stabilize and speed up the training process by normalizing the activations of each layer.
Flatten and Dense layers play a pivotal role. Flatten layer convert multi dimensional results from previous layers into a one dimensional array, then the layer is fed to the Dense layer which is a fully connected layer that performs classification.
Dropout is a regularization technique that boosts accuracy by at least 2%, by dropping some weights. You must consider dropout if your model is over/underfitting.

In a multi connected neural network input-output flows in the following way:

![Screenshot 2024-03-06 210309](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/da7e0daa-9a86-4a2a-a064-b7378186481b)

Input are multiplied by some weights, then their sum is passed to the activation function, which calculates the output of a node.

![Screenshot 2024-03-06 210611](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/b0a0f945-8d42-49a0-8923-2b1dd2c919a0)
![Screenshot 2024-03-06 210810](https://github.com/iliyaLL/traffic-sign-recognition/assets/111357743/242abca2-edce-46fd-aff0-92aa7de675c0)

# Results
The model was trained on 10 epoch, achieving the val_accuracy of 97% and loss of
0.0878.
The application running in the web performs good overall while still gives produces
errors.
Example of the correct recognition:

Example of the incorrect one:

# Discussion

### Critical review of results

Overall, our team successfully developed a model within the Google Colab, which was then seamlessly integrated into our web page. This facilitated user interaction with our model in real-time scenarios. Upon training our model based on dataset conducted, we achieved commendable results, boasting an impressive accuracy exceeding 97%. Furthermore, in the web page comprehensive guide for users was provided, which will be helpful for enhancing user experience. Eventually, the web page was deployed, what makes the usage of it more convenient.

### Next steps

Moving forward, our focus will be on enhancing the model's capabilities by expanding the dataset to incorporate a broader range of traffic signs. This aims to improve the model's robustness and generalization, thereby enhancing its effectiveness in real-world applications. Simultaneously, enhancements to the web page are planned, including the integration of relevant APIs to provide users with additional information about road signs. Moreover, efforts will be directed towards refining the web page's design to optimize user engagement and accessibility, ensuring a seamless experience for all stakeholders involved.

# Sources

- Luo, L. (2021). Research on Image Classification Algorithm Based on Convolutional Neural Network. Journal of Physics: Conference Series, 2083(3), 032054. https://doi.org/10.1088/1742-6596/2083/3/032054
- https://www.tensorflow.org/
- [georgesung/ssd_tensorflow_traffic_sign_detection: Implementation of Single Shot MultiBox Detector in TensorFlow, to detect and classify traffic signs (github.com)](https://github.com/georgesung/ssd_tensorflow_traffic_sign_detection/tree/master)
- https://keras.io/api/
- Géron, A. (2019). Hands-On Machine Learning with Scikit-Learn, Keras, and
  TensorFlow, 2nd Edition
