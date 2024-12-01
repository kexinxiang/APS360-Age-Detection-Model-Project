# Age Detection Model with Deep Learning

This academic project for the course APS360 explores the use of deep learning techniques to predict whether an individual is under or over 16 years old based solely on their facial image. Using a dataset from Kaggle, we processed, trained, and evaluated models to achieve accurate classification results.

<img width="739" alt="Age Verification Model" src="https://github.com/user-attachments/assets/6665995a-1cb1-49da-b43d-fe8711677090">

## Data Cleaning and Processing

The dataset, sourced from Kaggle, contains facial images categorized by age. We focused on ages 8 to 60 to align with the project's goal of protecting adolescents in online environments. Key steps in the data cleaning process included:

1. **Preprocessing**: Images were resized to 200x200 pixels and normalized to standardize dimensions.
2. **Categorization**: Images were sorted into two categories — below 16 and above 16.
3. **Balancing**: Class distributions were adjusted to ensure approximately 1500 images per category.

After cleaning, the data was split into training (75%), validation (15%), and test (15%) sets. An additional test set of 102 manually collected images was prepared to simulate real-world scenarios.

## Baseline Model

The baseline model is a simple CNN architecture with:

- 2 convolutional layers
- 2 max-pooling layers
- 2 fully connected layers

<img width="615" alt="Screenshot 2024-11-30 at 10 13 44 PM" src="https://github.com/user-attachments/assets/7f4eee75-0388-4637-8805-673ab83cd6c4">

This model achieved a training accuracy of 100%, but validation and test accuracies were lower, indicating possible overfitting. Final metrics:

- **Validation Accuracy**: 85.55%
- **Test Accuracy**: 85.3%

<img width="680" alt="Screenshot 2024-11-30 at 10 14 56 PM" src="https://github.com/user-attachments/assets/41c9abae-097f-4e1d-8ba0-f1cb4238d7ac">

## Transfer Learning with VGG19

For the primary model, we utilized transfer learning with a pre-trained VGG19 model. Feature maps were extracted and passed through a custom classifier. The final architecture includes:

- Pre-trained VGG19 for feature extraction
- A custom classifier with two fully connected layers for binary classification

This approach significantly improved generalization:

- **Training Accuracy**: 96.49%
- **Validation Accuracy**: 87.28%
- **Test Accuracy**: 86.45%

<img width="705" alt="VGG19 training curve" src="https://github.com/user-attachments/assets/80a5d5a1-21b3-49b9-93a6-4b19eb1752c2">

## Results

## Qualitative results

Qualitative analysis revealed the model's robustness in correctly classifying diverse test set images, demonstrating its potential for real-world applications.

<img width="718" alt="Screenshot 2024-11-30 at 10 23 12 PM" src="https://github.com/user-attachments/assets/01d6dc7c-8bee-4ac1-9792-a720fbe5c023">

## Model Evaluation on New Data

To double ensure the accuracy of our results, we’ve taken care to evaluate our models on our own new, unseen data. We collected a separate set of real-life photos, distinct from our training and validation data, to form an independent test dataset. This dataset, not used during model training or tuning, serves as an unbiased measure of our models’ real-world performance.

Using our primary model, we achieved an overall accuracy of **73.47%**, with:
- **83.67% accuracy** for the "below 16" class
- **63.27% accuracy** for the "over 16" class.

We observed reduced accuracy in the "over 16" class, which can be attributed to the model's challenges in distinguishing ages within the range of 13 to 19. Since we collected the data ourselves, the photos used for the "over 16" class predominantly featured individuals around 17 and 18 years old, with youthful facial features. This likely contributed to the model's misclassification of these photos as "below 16."

<img width="651" alt="Screenshot 2024-11-30 at 10 18 03 PM" src="https://github.com/user-attachments/assets/98358776-0673-4c9f-b139-9bb6a4afa36e">

For example, as shown above, predictions based on our own photos classified all four individuals (around 17–18 years old) as "below 16."

## Future Steps

To further enhance performance, the next step is **fine-tuning the VGG19 model** to better fit the task of human facial recognition. This involves unfreezing some of the later layers of VGG19 and training them on the facial age dataset to improve the model's sensitivity to age-specific features.

---

### References

- Dataset: [Kaggle Facial Age Dataset](https://www.kaggle.com/datasets/frabbisw/facial-age)
