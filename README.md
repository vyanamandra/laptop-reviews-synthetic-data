# laptop-reviews-synthetic-data

* Generated using the below *

Although I wrote a little more than needed, I commented many parts to make sure I only recieve reviews text only.



```python
import random
from datetime import datetime, timedelta

# Define sample data
parts = [
    "Screen",
    "Display",
    "Keyboard",
    "Touchpad",
    "Battery",
    "Motherboard",
    "Processor",
    "CPU",
    "GPU",
    "Memory",
    "RAM",
    "Storage",
    "Drive",
    "HDD",
    "SSD",
    "hybrid-ssd",
    "CoolingSystem",
    "Fans",
    "Heat Sinks",
    "Speakers",
    "Microphone",
    "Webcam",
    "USB",
    "HDMI",
    "AudioJack",
    "PowerAdapter",
    "Charger",
    "Optical Drive",
    "Wi-Fi Card",
    "Bluetooth Module",
    "Chassis",
    "Hinges"
]

sentiments = ['positive', 'neutral', 'negative']

brands = ['HP-Students-Business-Quad-Core-Storage', 'HP-14-Laptop-Dual-Core-Processor',
          'HP-Stream-14-Quad-Core-Processor', 'HP-Chromebook-Graphics-Keyboard-14a-na0226nr',
          'HP-EliteBook-Display-i5-6300U-Windows', 'HP-Gamer-Students-Business']

processors = ['Intel Core i5', 'Intel Core i7', 'AMD Ryzen 5', 'AMD Ryzen 7']

ratings = [1, 2, 3, 4, 5]

base_texts = {
    'positive': [
        'is fantastic', 'works wonderfully', 'exceeds expectations',
        'is top-notch', 'is flawless', 'performs exceptionally',
        'is highly reliable', 'offers great value', 'is impressively durable',
        'is incredibly efficient', 'provides outstanding usability',
        'delivers superior performance', 'is remarkably comfortable',
        'is cutting-edge', 'is remarkably intuitive', 'is state-of-the-art',
        'is user-friendly', 'is aesthetically pleasing', 'is beyond satisfactory',
        'is light and portable', 'is very versatile', 'has excellent build quality',
        'is extremely fast', 'has a long battery life', 'has crystal-clear sound'
    ],
    'neutral': [
        'is acceptable', 'meets expectations', 'is decent',
        'does the job', 'is average', 'is adequate', 'serves its purpose',
        'is passable', 'is serviceable', 'is satisfactory', 'is fair',
        'is unremarkable', 'is middling', 'is commonplace', 'is standard',
        'is ordinary', 'is tolerable', 'is undistinguished', 'is sufficient',
        'is alright', 'is mediocre', 'is unexceptional', 'is functional',
        'is usable', 'is okay', 'has no major problems', 'fits basic needs',
        'is middle-of-the-road', 'is run-of-the-mill', 'is not outstanding'
    ],
    'negative': [
        'is disappointing', 'fails to meet expectations', 'has issues',
        'is problematic', 'is subpar', 'is unsatisfactory', 'is inferior',
        'is lacking', 'is deficient', 'is inadequate', 'falls short',
        'is underwhelming', 'is flawed', 'is troublesome', 'is weak',
        'is insufficient', 'is unsuitable', 'is poor', 'is unacceptable',
        'is defective', 'is faulty', 'is disappointing', 'is not worth the money',
        'has poor performance', 'suffers from frequent problems',
        'is poorly designed', 'is unreliable', 'is cumbersome',
        'has a short battery life', 'overheats easily'
    ]
}


# Function to generate a single laptop review
def generate_laptop_review():
    # brand = random.choice(brands)
    # processor = random.choice(processors)
    # rating = random.choice(ratings)
    review_parts = {}
    sampled_parts = random.sample(parts, 10)
    for part in sampled_parts:
        sentiment = random.choice(sentiments)
        base_text = random.choice(base_texts[sentiment])
        review_parts[part] = f"The {part} {base_text}."
    review_is = ' '.join(review_parts.values())
    # review_date = datetime.today() - timedelta(days=random.randint(0, 365))
    # review_date_formatted = review_date.strftime('%Y-%m-%d')

    #return f'"{brand}", "{review_is}"'
    return f'{review_is}'


# Function to generate multiple laptop reviews
def generate_multiple_laptop_reviews(num_reviews):
    return [generate_laptop_review() for _ in range(num_reviews)]


# Generate a million laptop reviews
num_reviews = 1000000
laptop_reviews = generate_multiple_laptop_reviews(num_reviews)

# Output the number of generated reviews to confirm
print(f"Generated {len(laptop_reviews)} laptop reviews.")

with open('laptop_reviews.csv', 'w') as w:
    w.write('\n'.join(laptop_reviews))
```
