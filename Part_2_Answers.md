# Part 2 – Answers

---

## Q1: Choosing the Right Approach

**Answer:**  
I would use **object detection**. The reason is that the products are visually similar, and we need to locate **where the label is** (or missing). Detection allows the model to identify the presence and position of the label, rather than just saying “labeled” or “unlabeled” for the whole image.  

**Fallback:**  
If detection doesn’t work well, I would try **image classification** on a cropped region of the product where the label should be. This way, the model focuses on the label area instead of the whole product.

---

## Q2: Debugging a Poorly Performing Model

**Answer:**  
Checklist/experiment to debug:  

1. **Check dataset quality:** Are the images from the factory visually different (lighting, angles, background) than training images?  
2. **Visualize predictions:** Run the model on a few new images and see where it fails.  
3. **Class balance:** Make sure there are enough examples of each class (labeled/missing label).  
4. **Augmentation:** Test adding variations like brightness, rotation, and scale to handle real-world differences.  
5. **Overfitting check:** Evaluate if the model performs well on the training set but poorly on new images.  

---

## Q3: Accuracy vs Real Risk

**Answer:**  
Accuracy is **not the right metric** here. Missing even a few defective products can be costly. I would look at:  

- **Recall (Sensitivity):** How many defective products are correctly detected.  
- **Precision:** How many predicted defects are actually defective.  
- Possibly **F1-score** to balance precision and recall.  

The goal is to **minimize missed defective products**, even if it means some false positives.

---

## Q4: Annotation Edge Cases

**Answer:**  
- **Partially visible or blurry objects:** I would **usually keep them** if they represent realistic conditions on the factory line, because the model needs to handle real-world scenarios.  
- **Trade-offs:**  
  - Keeping them may slightly reduce overall model performance on clear images.  
  - Removing them may make the model fail in real-life blurry or occluded cases.  

So, keeping some edge cases helps the model **generalize better**.

