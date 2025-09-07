

# 🎯 Auto-Tagging Support Tickets Using Zero-Shot Classification  

## 📌 Objective  
The goal of this project is to automatically **categorize IT support tickets** into predefined groups (e.g., *Hardware, Access, Purchase, HR Support*) without the need for training a custom model.  
This is achieved using **Zero-Shot Learning** with Hugging Face Transformers.  

---

## 🛠️ Methodology / Approach  

1. **Dataset**  
   - Source: Kaggle – *IT Service Ticket Classification Dataset* (`IT_Ticket_Dataset.xlsx`).  
   - Columns used:  
     - `Document` → renamed to `ticket_text`  
     - `Topic_group` → renamed to `true_label`  

2. **Preprocessing**  
   - Removed missing values in `ticket_text`.  
   - Extracted unique categories from `true_label` for classification.  

3. **Model**  
   - Used **Hugging Face Zero-Shot Classifier** (`facebook/bart-large-mnli`).  
   - No training required → directly predicts labels based on text similarity with categories.  

4. **Prediction**  
   - **Top-1 Prediction** → most likely category per ticket.  
   - **Top-3 Predictions** → top 3 most probable categories per ticket.  

5. **Evaluation**  
   - Calculated **Precision, Recall, and F1-score**.  
   - Plotted:  
     - Confusion Matrix  
     - Category Distribution  
     - Top-3 Coverage (how often the true label is in top-3 predictions).  

---

## 📊 Key Results / Observations  

- ✅ **Confusion Matrix** shows most errors occur between semantically close categories (e.g., *Access* vs *Account Management*).  
- ✅ **Top-1 Accuracy** is moderate due to dataset complexity.  
- ✅ **Top-3 Coverage** is significantly higher (often >80%), making it practical for real-world auto-suggestions.  
- ✅ The system works without training → fast deployment for new datasets.  

---

## 🚀 How to Run (Google Colab)  

1. Upload the dataset (`IT_Ticket_Dataset.xlsx`) when prompted.  
2. Run the notebook cells sequentially.  
3. Outputs:  
   - Classification report  
   - Confusion Matrix  
   - Plots  
   - Predictions saved in `ticket_predictions.csv`  

---

## 📂 Project Structure  
├── AutoTagging_Tickets.ipynb # Main Colab notebook
├── IT_Ticket_Dataset.xlsx # Dataset (Kaggle)
├── ticket_predictions.csv # Predictions with top-1 and top-3
└── README.md # Project documentation

## 📂 Project Structure  

