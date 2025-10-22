#  Hidden Backdoor Attack on Deep Learning Models

A research-based project exploring the implementation of **Hidden Backdoor Attacks** — an advanced adversarial technique in deep learning security.  
The attack injects **stealthy poisoned data** into the training process to implant a hidden trigger that causes targeted misclassification when activated at test time.  
Unlike traditional backdoor attacks, this method hides the trigger in natural-looking samples, making it nearly undetectable.

---

##  Features

- Implements hidden backdoor attack based on *Saha et al., AAAI 2020*  
- Poisoned samples appear **visually clean and correctly labeled**  
- Achieves **>90% attack success rate** with fewer than 50 poisoned samples  
- Works under **weak adversarial conditions** (no access to training data or model)  
- Resistant to several state-of-the-art defense mechanisms  
- Demonstrates backdoor generalization across random trigger locations  

---

##  System Architecture

### **Attack Pipeline**
1. **Poison Generation:**  
   The attacker inserts a secret trigger into a small subset of images while keeping labels unchanged.  
   These poisoned images are optimized to appear visually similar to legitimate samples.

2. **Model Training:**  
   The victim fine-tunes a pre-trained classifier using the poisoned dataset.  
   The backdoor association between trigger and target class becomes embedded in the model.

3. **Attack Activation:**  
   During inference, the attacker activates the backdoor by adding the hidden trigger to new images, causing targeted misclassification.

4. **Evaluation:**  
   The model’s performance is measured using **Attack Success Rate (ASR)** and **Benign Accuracy (BA)**.

---

##  Methodology

### **Optimization Objective**
Find a poisoned image `z` that:
- Minimizes the distance between feature representations of `z` and a **patched source image** `s`
- Retains visual similarity to the target image `t`

**Loss Function:**
