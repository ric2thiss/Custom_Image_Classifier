# Custom_Image_Classifier

## Laboratory Work 3 Activity — Building a Custom Image Classifier with TensorFlow Using Personal Image Datasets from Google Drive

Colab link : https://colab.research.google.com/drive/1hKpAt7FQ6lf5StBUYslJ235XWdkmAwod?usp=sharing

1. Dataset Preparation

○ How did you organize your dataset in Google Drive?
  - I organize the dataset in Google drive by putting it in one folder and under the one folder, there are different folders for each class or plant that will be use for training and validation.

○ Why is folder structure important for TensorFlow image loading?
  - The folder structure acts as an automatic labeling system, allowing TensorFlow to use your subfolder names as class labels while efficiently mapping and batching the images for training.
    
2. Model Training
○ What is the role of convolutional layers in image classification?
- They act as "feature extractors" by scanning images for patterns, starting with simple edges and shapes in the first layers and building up to complex objects (like leaves or petals) in deeper layers.

○ Why do we split data into training and validation sets?
  - We do this to make sure the model isn't just "memorizing" the answers. The training set is like the textbook the model studies, and the validation set is a surprise quiz with new images to see if it actually understands what it's looking at.
    
3. Performance Analysis

○ What accuracy did your model achieve?
  - My model achieved a validation accuracy of about 83.86%. This means that when the model was tested on new images it hadn’t seen during training, it correctly identified the plant variety nearly 84% of the time. My training accuracy was even higher (around 94%), showing that the model learned the patterns in my dataset very well.

○ How did the number of images affect the model’s performance?
  - Since I used a large dataset of 5,175 images across 20 different classes, the model had enough examples to learn the specific details of each plant. Having more images generally makes the model more "intelligent" because it can see a variety of lighting, angles, and leaf shapes. If I had used fewer images, the accuracy would likely be lower because the model wouldn't have enough data to tell the difference between similar-looking plants.
    
4. Critical Thinking

○ What challenges did you encounter while using your own dataset?
  - One of the main challenges was making sure all the images were high quality and correctly sorted into the right folders. Since I used a large dataset of over 5,000 images, it took time to ensure there were no "misfits" or corrupted files that could confuse the model. Another challenge was the long training time; because I had so many classes (20 different types), I had to make sure my Google Colab didn't disconnect while the model was processing all that data.

○ How can data augmentation improve your model?
  - Data augmentation helps by creating "new" versions of my existing photos through random changes like flipping, rotating, or zooming. This makes the model more flexible because it learns to recognize the plant from many different angles and lighting conditions, rather than just memorizing the exact photos I uploaded. It essentially gives the model more variety to study from, which leads to better accuracy in the real world.

5. Application

○ Suggest a real-world application for your trained model.
  - I would use this model to create a Smart Plant Care App specifically for Aglaonema collectors. Since I trained the model on 20 different varieties, it can help users identify exactly which type of plant they have. This is very useful in the real world because different varieties might need different amounts of sunlight or water. Instead of guessing, a gardener could just snap a photo to get the correct name and care instructions instantly.

○ How can this system be integrated into a mobile or web application?
  - To make this work in an app, I would first convert my model into a smaller, faster format like TensorFlow Lite. For a mobile app, I would add a camera feature where the model runs directly on the phone to identify plants in real-time. For a web application, I would create a simple "upload" button where a user can pick a photo from their gallery; the website would then send that image to a server, run the model, and display the plant's name and details back to the user's screen.

_____________________________________________________

Visualization & Overfitting
1. What signs indicated overfitting in your first model?
The primary sign was a large gap between the training accuracy and validation accuracy. Specifically, the training accuracy would continue to climb toward 100%, while the validation accuracy would plateau or even begin to decrease. This indicated the model was memorizing specific details (noise) of the training set rather than learning general features.

2. How did data augmentation affect validation accuracy?
Data augmentation typically causes validation accuracy to increase and stabilize. By showing the model varied versions of the same image (rotated, flipped, zoomed), the model can no longer "memorize" a specific pixel layout. This forces the model to learn the actual shape and essence of the object, leading to better performance on "unseen" data.

Model Improvement
3. What is the purpose of dropout layers?
The purpose of Dropout is to prevent neural co-dependency. By randomly "turning off" a percentage of neurons during each training step, the model is forced to find multiple independent pathways to the correct answer. This makes the network more robust and prevents it from over-relying on a small set of specific features.

4. Why does data augmentation improve generalization?
It improves generalization by increasing the effective size and diversity of the training dataset. It teaches the model "invariance"—the idea that a cat is still a cat whether it is upside down, zoomed in, or shifted to the left. This exposure to variety prepares the model for the unpredictability of real-world images.

Performance Comparison
5. Compare accuracy before and after improvements.

Before: High training accuracy but low/unstable validation accuracy (Classic Overfitting). The model was fast to train but poor at predicting new images.

After: Training accuracy might be lower than before (because the task is now harder), but validation accuracy is higher and more consistent, meaning the model is actually more useful.

6. Which technique contributed most to improvement?
Usually, Data Augmentation provides the most significant boost for small datasets, while Dropout provides the most stability for the architecture. If you have a very small dataset, Data Augmentation is almost always the "MVP" of improvements.

Deployment & Application
7. Why is saving the model important?
Training a model can take hours, days, or even weeks depending on the complexity. Saving the model (usually as an .h5 or .keras file) allows you to export the learned "weights" so you can use the model for "Inference" (making predictions) later or on different devices without needing to re-train it.

8. How can this model be deployed in a real-world system?

Web Application: Using TensorFlow.js to run the model directly in a browser.

Mobile App: Using TensorFlow Lite to identify objects via a smartphone camera.

Cloud API: Deploying the model to a server (like AWS or Google Cloud) where a website sends an image and receives a prediction via an API.
