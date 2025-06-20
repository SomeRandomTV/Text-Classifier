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

I’ve noticed that inorganic (AI) text sounds a little too **formal but not genuine**—it picks stronger words and a more (I am better than you) tone OR it can sound overly sincere like when you tell if it is wrong. \
Or when you tell the AI something good and it is overly happy, cringely happy. Im seeing a pattern, AI's text is just taking the tones to the extreme. \
Compare inorganic t ext to what I’m writing now. I’m writing this as I speak aloud, whereas AI just tries to sound like a prick.

That is my analysis of AI vs. human text—onward and upward!

---

## Text Preprocessing

Next, we’ll clean the text using the Natural Language Toolkit (`nltk`):

### Stop-Word Removal

Stopwords need to be removed as they cause a lot of noise and have no meaning. Some examples of stopwords are: `the`, `a`, `is`, `for`, etc \
These words are just filler words, they have no definition, they map to nothing in any Vector Space. So we take em out, here is what that looks like \

Before: International sports events require the most well-trained athletes for each country, in order to achieve this goal countries make an effort to build infrastructure designed to train top athletes.
After: International sports events require well-trained athletes country, order achieve goal countries make effort build infrastructure designed train top athletes. Although policy indeed make fewer sports facilities ordinary people, investing best athletes vital develop competitive sports performances

