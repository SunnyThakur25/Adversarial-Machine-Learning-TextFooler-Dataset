# Adversarial-Machine-Learning-TextFooler-Dataset
Overview
This dataset, adversarial_machine_learning_textfooler_dataset.jsonl, is designed for research and evaluation in adversarial machine learning, specifically focusing on text-based adversarial attacks. It contains pairs of original and adversarial text samples, primarily generated using the TextFooler attack method, along with other adversarial techniques such as Homoglyph, Number Substitution, Typo, Emoji, Semantic Shift, Paraphrase, and Zero-Width character injections. The dataset is intended for testing the robustness of natural language processing (NLP) models against adversarial perturbations.
Dataset Description
The dataset is stored in JSON Lines (.jsonl) format, where each line represents a single record with the following fields:

original_text: The original, unaltered text input.
adversarial_text: The perturbed text after applying an adversarial attack.
true_label: The sentiment or classification label of the original text (positive, negative, or neutral).
is_adversarial: Boolean indicating whether the text is adversarial (true for all entries in this dataset).
attack_type: The type of adversarial attack applied (e.g., TextFooler, Homoglyph, Number Substitution, Typo, Emoji, Semantic Shift, Paraphrase, Cyrillic Homoglyph, Zero-Width Space, etc.).

Example Record
{
  "original_text": "This was surprisingly good.",
  "adversarial_text": "This was surprisingly excellent.",
  "true_label": "positive",
  "is_adversarial": true,
  "attack_type": "TextFooler"
}

  

Dataset Statistics

Total Records: 400+ (exact count depends on final dataset size after deduplication).
Label Distribution:
Positive: ~50%
Negative: ~40%
Neutral: ~10%


Attack Types:
TextFooler: Synonym-based word replacement.
Homoglyph: Substitution with visually similar characters (e.g., Cyrillic or Greek letters).
Number Substitution: Replacing letters with numbers (e.g., e with 3).
Typo: Intentional misspellings.
Emoji: Addition of emoji characters.
Semantic Shift: Rewording with similar meaning but different phrasing.
Paraphrase: Complete rephrasing of the sentence.
Zero-Width Space/Non-Joiner/Joiner: Injection of invisible Unicode characters.
Cyrillic/Greek Homoglyph: Use of non-Latin characters resembling Latin ones.



Usage
This dataset is ideal for:

Adversarial Robustness Testing: Evaluate NLP models (e.g., sentiment classifiers) against adversarial attacks.
Attack Detection: Develop methods to detect adversarial perturbations in text inputs.
Model Hardening: Train models to improve resilience against adversarial attacks.
Research: Study the impact of various adversarial attack types on NLP model performance.

Loading the Dataset
You can load the dataset using Python with libraries like json or pandas:
import json

dataset = []
with open("adversarial_machine_learning_textfooler_dataset.jsonl", "r") as file:
    for line in file:
        dataset.append(json.loads(line))

# Example: Print first record
print(dataset[0])

Example Analysis
To analyze the dataset, you can use Python to compute statistics or visualize attack type distribution:
import pandas as pd
from collections import Counter
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_json("adversarial_machine_learning_textfooler_dataset.jsonl", lines=True)

# Count attack types
attack_counts = Counter(df["attack_type"])
plt.bar(attack_counts.keys(), attack_counts.values())
plt.xticks(rotation=45)
plt.title("Distribution of Attack Types")
plt.xlabel("Attack Type")
plt.ylabel("Count")
plt.savefig("attack_type_distribution.png")

Installation and Dependencies
To work with this dataset, ensure you have the following Python libraries:

json: For parsing JSON Lines format.
pandas: For data manipulation and analysis.
matplotlib: For visualization (optional).

Install dependencies:
pip install pandas matplotlib

Notes

Deduplication: Some records may be duplicated due to repetitive attack patterns. It is recommended to deduplicate the dataset before use.
Ethical Considerations: This dataset is for research purposes only. Do not use it to create or deploy malicious adversarial attacks in production systems.
Limitations: The dataset focuses on English text and may not generalize to other languages. Some attack types (e.g., Zero-Width characters) may be less effective on certain NLP models.

Contributing
Contributions to expand the dataset with new attack types or additional samples are welcome. Please submit a pull request or contact the maintainers for collaboration.
License
This dataset is released under the MIT License.
Contact
For questions or issues, please open an issue on the repository or contact the dataset maintainers at [your-email@example.com].
