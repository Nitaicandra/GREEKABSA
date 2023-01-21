# GREEKABSA
This project aims to train a model on the largest collection of Greek literature in order to gain insight into how different ancient civilizations viewed each other.
To accomplish this goal I developed a Greek Bert model that used aspect-based sentiment analysis to detect when groups of people were described positively or negatively within the corpus.

I create a custom dataset generator that procedurally pieces together greek words in order to form gramatically correct scenteces. it works by first scraping the greek wiktionary in order to decline greek nouns and verb inputs. Then it places those outputs into csv files in the local directory and uses pandas to then retrieve data from those files. it then randomly samples a few thousand nouns verbs and adjectives to create both accusative and nominative phrases.
(greek is an inflected language meaning that based on the context of the scentence the word will change forms this is why we must decline the words before using them)
|wiktionary greek word for romans declension chart|
| ------------- | 
|![image](https://user-images.githubusercontent.com/89361982/213872731-e61b0575-607b-487d-836f-8fda266e40ea.png)|
|pandas|

After the dataset is created it is then fed into pyabsa to train nlpaueb's greek bert base to detect sentiment aspect pairs. using this information we are able to tell where and when civilizations are described positivley and negativley within the greek corpus.


after only one epoch of training its able to deterimine positive and negative aspect pairs of accusative and nominative scentences with near 100%
|Input|Output|
| ------------- | ------------- |
|![image](https://user-images.githubusercontent.com/89361982/213872268-14ac2e58-f1d7-433f-b7ee-37f52e34f683.png)|![image](https://user-images.githubusercontent.com/89361982/213872254-8c9b0f88-d665-48f1-8415-de93eaaefe5f.png)|


The model was fined tuned on https://huggingface.co/nlpaueb/bert-base-greek-uncased-v1 using Pyabsa: https://github.com/yangheng95/PyABSA

