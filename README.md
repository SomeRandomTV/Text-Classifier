## AI-Generated or Human-Written Text

This is a small little project to learn some NLP with the help of Prof. `<insert-name>`.  
This is part of his class **Intro to AI and AI Agents** at Texas Tech University.

---

## Initial Stuff

Real quick, let’s get some initial details out of the way (I don’t have the assignment PDF):

- **Goal:** Develop a machine learning model that can detect AI-generated text.  
- **Data:** `AI_vs_huam_train_dataset.xlsx`  
  _(Yes, I know it’s spelled wrong—I’m just too lazy to change it.)_  
- **Given Libraries:**  
  - `pandas`  
  - `matplotlib`  
  - `seaborn`  
  - `nltk`  

---

## Data Exploration

First, I load the data into a Pandas DataFrame.

### DataFrame Structure

| Column | Type   | Description                                                             |
| ------ | ------ | ----------------------------------------------------------------------- |
| Str    | string | The text, either organic (human-written) or inorganic (AI-generated).    |
| Int64  | int    | The binary label: `0` = organic, `1` = inorganic.                       |

- **Rows:** 3,728  
- **Distribution:** Perfectly balanced (as all things should be)—1,864 examples of each label.

### Sample Texts

> **Label 0 →**  
> “International sports events require the most well-trained athletes for each country. To achieve this goal, countries make an effort to build infrastructure designed to train top athletes.”  
>
> **Label 1 →**  
> “International sports events demand that countries field their most highly trained athletes, which is why many nations invest in specialized facilities to help their top performers succeed.”

Even though both texts convey the same idea—well-trained athletes and proper facilities—the tone and word choice differ:

- **Label 0** reads more like natural speech, with a conversational flow.  
- **Label 1** is more formal and intense; it “tries too hard” to sound polished, almost condescending.

I’ve noticed that inorganic (AI) text often sounds **formal but not genuine**—it picks stronger words and a more forceful tone. Compare that to what I’m writing now: I’m writing this as I speak aloud, whereas AI just tries to sound like a prick.

That is my analysis of AI vs. human text—onward and upward!

---

## Text Preprocessing

Next, we’ll clean the text using the Natural Language Toolkit (`nltk`):

1. Remove stopwords  
2. Strip noise (punctuation, special characters)  
3. Normalize case, tokenize, etc.  

And that’s our setup! Let’s dive into coding.

