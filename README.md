# 🥗 AI Nutrition Coach

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-Web_App-black?logo=flask)
![IBM watsonx.ai](https://img.shields.io/badge/IBM-watsonx.ai-052FAD?logo=ibm)
![Meta Llama 4](https://img.shields.io/badge/Meta-Llama_4_Maverick-0467DF?logo=meta&logoColor=white)

Upload a photo of your meal and get an instant, AI-powered calorie and nutrient insights

## 📖 Overview

AI Nutrition Coach is a Flask web app that uses a multimodal Large Language Model(LLM) to analyze food photos. Upload an image of a meal, ask a question such as *"How many calories are in this food?"*, and receive a structured nutritional assessment in seconds.

## ✨ Features

- 📷 Upload any food image with an instant live preview
- 💬 Ask custom questions about the meal
- 🍽️ Automatic food identification with portion size estimates
- 🔥 Per-item and total calorie estimates
- 🥦 Nutrient breakdown: protein, carbs, fats, vitamins, minerals
- ❤️ Short health evaluation and a built-in nutrition disclaimer

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| Backend | Python, Flask |
| AI Model | `meta-llama/llama-4-maverick-17b-128e-instruct-fp8` |
| AI Platform | IBM watsonx.ai (`ibm-watsonx-ai` SDK) |
| Frontend / Images | HTML5, CSS3, JavaScript, Jinja2, Pillow, Base64 |

## 🧠 How It Works

1. The user uploads a food image and submits a question through the Flask form.
2. The image is read and **Base64-encoded** (`input_image_setup`).
3. The image plus a detailed *expert nutritionist* prompt are sent to Llama 4 Maverick via watsonx.ai (`generate_model_response`).
4. The model replies in a fixed template: identification, calories, totals, nutrients, evaluation, disclaimer.
5. The reply is converted to clean HTML (`format_response`) and rendered on the page.

## 📂 Project Structure

```text
ai-nutrition-coach/
├── app.py               # Flask routes, model call, response formatting
├── templates/
│   └── index.html       # Main page: form, image preview, results
├── static/
│   └── style.css        # Styling
└── images/              # Sample food photos for testing
```

## 🚀 Getting Started

**1. Clone the repository and install dependencies**
```bash
git clone https://github.com/<your-username>/ai-nutrition-coach.git
cd ai-nutrition-coach
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install flask requests pillow ibm-watsonx-ai
```

**2. Configure credentials**
The original IBM Skills Network lab injects credentials automatically. To run it elsewhere, add your own in `app.py`:

```python
credentials = Credentials(
    url="https://us-south.ml.cloud.ibm.com",
    api_key="<YOUR_API_KEY>",
)
project_id = "<YOUR_PROJECT_ID>"
```

**3. Run the app**
```bash
python app.py
```

Open **http://127.0.0.1:5000**, choose an image from `images/`, keep or edit the question, and click **Tell me the total calories**.

## 📸 Example Output

```text
Identification:    Grilled chicken, broccoli, strawberries, cheese
Total Calories:    ~450 kcal
Protein:           chicken (30g) + cheese (7g) = ~37g
Health Evaluation: A balanced, protein-rich meal with fiber and vitamins.
```

## ⚠️ Limitations

- Estimates are approximate and based on visual analysis only.
- Not a substitute for advice from a qualified nutritionist or healthcare provider.

## 🔮 Future Improvements
- Meal history and daily calorie tracking
- Online deployment (Render, AWS, or Hugging Face Spaces)

## 👤 Author
**Samuel**, Data Scientist · AI Engineer
