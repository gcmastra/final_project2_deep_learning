# final_project2_deep_learning
### Student: Christopher Mastrangelo

## Word Embedding (NLP) using Neural Networks with Word2Vec for Python

This project will attempt to answer questions like these:  

"Why is it when I text people on my phone, the suggested word never guesses what I want to say next?"  Maybe not all the time, but it seems like more often than not, the word suggestions generated by an AI algorithm guess wrong.  Is it because they are trained on classic English writing sources rather than a writing style that matches my own?

Would it be possible to use examples of my own writing to train a "word embedding" algorithm (unsupervised machine learning aka neural network) to generate the list of next words? 

If I train the neural network on examples of my own writing could I get a better guess for the next suggested word? 

### Word Similarity and Word Analogy

In Natural Language Processing (NLP) theory, the areas we are exploring are called <b>Word Similarity</b> and <b>Word Analogy</b>. 

Word2Vec converts words into decimal number representations called "vectors" because neural networks only work with numeric data. In addition to creating a word embedding algorithm, the neural network uses the word vectors to group words into associations.  Words that are similar should have a shorter "distance" between their respective vectors as shown in the example.<br>

<img src="https://user-images.githubusercontent.com/86205000/143664921-d3b90053-6b75-489a-858d-603116b35933.png" width=500>

Another way to understand the relationship between words and their vectors is using something called "cosine similarity" which is another term for the Euclidian distance between two points in multi-dimensional space. This allows us to answer the question "A is to B as C is to D" (for example: Man is to King as Woman is to _____" with the answer = Queen). In theory a sufficiently trained neural network can quantify semantic relationships like these based on the vector representations.

![image](https://user-images.githubusercontent.com/86205000/142961015-928aa068-3485-4554-8b37-2b33955335de.png)

<b>More questions:</b> After training the model, what information can be learned by analyzing a vector diagram of my own writing?  Are some words more common?  Do I use  different vocabulary than the general English speaking population?  Do the associations between words make sense?  Are any of the words clustered together and if so are any of the associations unexpected?

Another question that could be a subject for future research: "Why do spell checkers never work for me?" 

To answer these questions and more, I built two machine learning models for word recognition.  
For model #3 I propose to build and train a word embedding model using a coda based on my own writings in my personal blog.

<hr>

### Overview of Project Segments

<b>Model #1: Build and Train a Neural Network</b>- The first model proves it is possible to train a neural net with a relatively small sample of sentences to produce a 2 dimension vector file; After getting the model from the article working, I trained several new copies of the model using sentences taken from examples of my own writing to produce new 2 dimensional word vector files as output. 

<b>Visualizations</b>- create a 2-dimensional model of the word vectors showing groupings of associated words. For example: 

![image](https://user-images.githubusercontent.com/86205000/143665580-c1e0dd9d-34e5-4096-936e-db142cfe09a5.png)

<b>Model #2:</b> Implement a large word embedding model using pre-trained word vector files with 100 dimensions

<b>Implementation</b> - After training the model, determine how to apply it in "real life" by implementing a simple interactive "next word guessing" program in Python.
- Word Association - find the closest related words based on the distance between points
- Word Analogy - find semantic relationships between pairs of words in the form "A is to B as C is to D"

<b>Model #3 (If there is time)</b>: Use Word2vec to transform a large "coda" made up of writing samples from my personal blog, and create a multi-dimensional vector file using the method from Model #1.  Then use the word vector file from step 1 to feed as the imput to model #2.  Using words from the coda, demonstrate the semantic relationships between words.
<hr>
  
### Data Sources

<b>Model #1: </b>The Eligijus article comes with example input file to train the model to illustrate the points in the article.  In subsequent runs I used text files that I created from samples of my own writing.<br>
https://github.com/Eligijus112/word-embedding-creation

<b>Model #2: </b>Large pre-trained vector files based on public domain "coda" like Wikipedia or Twitter are available online.  The second model is based on a pre-trained dataset that is available on the Global Vector ("GloVe") website at this URL:
<br>https://nlp.stanford.edu/projects/glove/

<b>For model #3</b>, I propose to use a coda that consists of samples of my own writing on my blog at this URL:<br>
<a href="https://gcmastra.wordpress.com/" target="_blank">https://gcmastra.wordpress.com/</a>

<hr>

### Code Sources

<b>Model #1: </b>The python code for creating and training a word embedding model was found in this GitHub repository
https://github.com/Eligijus112/word-embedding-creation

which is owned by the author (Eligijus Bujokas) of an article which explains how to build the model step  by step on a relatively small set of sentences. 
I used this as a starting point and trained it using the "classic" (King/queen) example explained in the article, then ran it again using samples of my own writing.
Here is a link to the article:

https://towardsdatascience.com/creating-word-embeddings-coding-the-word2vec-algorithm-in-python-using-deep-learning-b337d0ba17a8

The author shows how to build and train the model using a relatively simple source file and shows that even with a few sentences, semantic relationships like the "man is to king as woman is to queen" already can be understood by the model.  Then I took a sample of my own writing and after some ETL used it to train another copy of the same model, and created visualizations of both.

<b>Model #2:</b> For model #2 which uses very large pre-trained word vector files, the information on how to set up the model was found online at this URL<br>
https://www.geeksforgeeks.org/finding-the-word-analogy-from-given-words-using-word2vec-embeddings/

In order to make this part work, I had to make some modifications to the code, as well as add more dependencies to the requirements.txt file to be installed in the anaconda environment which I called "final_project" on my laptop. Specifically the version of gensim had to be reverted from the current version 4.1.2 to version 3.8.3

<hr>



## Location of files

Explanation of files found in the main branch of the repository
- <b>utils.py</b> contains python functions provided by the author of the article from his repository linked above with slight modifications I made for compatibility
- <b>requirements.txt</b> contains the dependencies that had to be installed in the ananconda environment for the models to work 
- <b>Word2Vec_Practice.ipynb</b> is a Jupyter Notebook file containing code copies from the author's master.py file and modified to break it up into manageable size chunls to run in notebook cells to make troubleshooting easier and to be able to print the contents of variable at different steps in the process
- <b>PretrainedVector_Practice.ipynb</b> and <b>PretrainedVector_MoreExamples.ipynb</b> are Jupyter Notebooks containing the implementation of Word Enbedding model #2 which uses the large pre-trained vector files downloaded from the GloVe website.
- the <b>input folder</b> contains the original sample.csv used to train the model in the example, as well as one test version of text file taken from my own email
- the <b>output folder</b> contains the vector files created by training model #1
- large pre-trained data files in GloVe and word2vec format using a 100 dimension matric were too big to upload to gitHub so I added the name of the folder where they are located to the .gitignore file in the main repo. 

## Slides

Here is the link to the Google Slides file: 
[paste the URL here]

### FOR THE GRADER
- At your suggestion I took a closer look at the detailed rubric for segment 3. 
- Two Machine Learning Models are already trained and working.
- Google slides are linked above.
- Regarding the machine learning segment of the rubric - the slides I created answer four(4) of the six questions which should qualify as "emerging." 
- The reason I can't answer the other two questions is because the choice of the model (deep learning neural network) does not fit with the train-test split format, which makes it impossible to compute an accuracy score.  Perhaps this is one of the limitations of the model choice
- Still thinking about which visualizations to include in the dashboard and the best way to get them there. I might not have time to get the dashboard working.
