# CS678-checkpoint2

INTRODUCTION:

--> This project titled as "Advanced profanity obfuscation using toxic comments" is a Python function that obfuscates profane words based on either profanity of individual word or contextual interpretation of a sentence.

ORIGINALITY:

--> This algorithm stands out from others by its ability to comprehend the overall essence of a sentence using machine learning, rather than simply checking words against a pre-established list.

--> Very robust to contextual meaning and intentional behaviour of misspells.

--> Can obfuscate words based on purpose of the implementation.


(1) Masks words based on interpretation of contextual offensiveness. 

      Example:
      
      input - "he is ass"
      output - "he is a*s"
      
      input - "he is not ass"
      output - "he is not ass"

(2) Masks words based on individual word interpretation in terms of its profanity.

      Example:
      
      input - "he is ass"
      output - "he is a*s"
      
      input - "he is not ass"
      output - "he is not a*s"

--> Decision of selecting which feature to use depends on the purpose of using the function.

--> Robust to contextual meaning and intentional behaviour of misspells.

DATASETS:

 --> Utilizing the A corpus of the Jisaw multilingual toxic comments dataset in English, along with their API translations in French, Spanish, Italian, and Turkish combined with modified set of traininng labels that serves the purpose of our project forms the foundation for training our model. This extensive dataset, consisting of over 200,000 Twitter comments, categorizes whether the comments contain insults or not. It serves as an exceptional resource for individuals interested in experimenting with Natural Language Processing (NLP). We express our gratitude to the creators of this dataset. For unseen profanity check, "test.csv" file was used.

OUTPUT:
 
--> Refer the last cell of the "678_checkpoint2_multilingual_robustness_submission.ipynb" file to check output.

PACKAGE REQUIREMENTS:

--> torch transformers ekphrasis checklist nltk spacy scikit-learn tqdm pandas seaborn jupyter 

DATASETS:

--> https://drive.google.com/drive/folders/1z6vJTbeXiy2aLV5rNdJtzuwlCmlvnKKB?usp=sharing.

METRICS used for Behavioural testing of our model(English predictions):

      1. Minimum Functionality test
      2. Invariance test
      3. Directional Expectation test

OUTPUT:

            c = 'This stupidd= mothrfucker has come here' 
            i = 0
            o = []
            for word in range(len(c)):
                if c[word] == ' ':
                   #print(c[i:word])
                   o.append(c[i:word])
                   i = word+1
                   #o.append(c[i:word])
            #print(c[i:len(c)])   
            o.append(c[i:len(c)])
            #print(o)
            
            sen = ''
            idx = 0
            for i in o:
                x = i
                y = predict_prob(x)
                if y[0][0] >= 0.75:
                    #print(len(x))
                    l = len(x)
                    a = np.random.randint(2,l)
                    #print(a)
                    #print(x[0:a-1]+ '*' + x[a:l])
                    i = x[0:a-1]+ '*' + x[a:l]
            
                if idx == 1:
                    sen = sen+' '+i
                if idx == 0:
                    sen = sen + i
                    idx += 1   
            print('\ninput:', c,'\n')
            print("result:",sen)

input: This stupidd= mothrfucker has come here 

result: This st*pidd= mothrfuck*r has come here            

--> Refer the last cell of the "678_checkpoint2_multilingual_robustness_submission.ipynb" file to check output.
