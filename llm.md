
word - > tokenise
tokenise - > embeding (vectorisation)
embeding -> transformer()
transformer -> take output

vectors are just numbers assigned to a token so that it can be well recognised 
and this process is embedding

"cat"  → [0.12, -0.85, 0.44, ...]
"dog"  → [0.10, -0.80, 0.50, ...]
"car"  → [-0.70, 0.25, 0.11, ...]

The exact numbers don't matter.
The important idea is:

"cat" and "dog" get similar vectors because they are related.
"cat" and "car" get very different vectors.

You can imagine words as points in a huge space:
cat ----- dog

           car

embeddings are usefull bcoz model can take out relationships 
King - Man + Woman ≈ Queen

suppose if I searched for some word, according to its vector further predictions can be done , predicated ans will be having similar vectors bcoz they are related

An LLM includes:

1. Transformer architecture
2. Billions of learned parameters
3. Training on massive datasets
4. Fine-tuning and alignment

Transformers 

A Transformer is the neural network design/architecture that powers models like:
ChatGPT
GPT-4
Gemini
Claude

basically its a brain which takes vrctor as input and predict the output
at training phase parameter fixing/adjusting is done in transformers (optimisarion algo tunes the parameters)
which is afterward used as inference 

flow
When you type a prompt:
1 Your words are turned into vectors.
2 The Transformer processes them all at once using self-attention.
3 The data flows through the locked-in parameters (the billions of tuned dials).
4 The Transformer calculates the highest mathematical probability for what the next vector (word) should be, and predicts it.

And historically, not all language models used Transformers — older ones used RNNs, LSTMs etc.

halusination

to stop it we train model in such way, while in training phase if model is giving diff ans every time , nuerons value is so uncertain every time (4-5 time) then we tell model to return i dont know orwe tell model to use tools and search in browser nd fetch the info

parameters to llm
T temparate : controls the randomess
less T means more deterministic ans, Low Temperature (0.0 - 0.3)
more T means more cretive ans ,High Temperature (0.8 - 1.5)

llm = ChatGoogleGenerativeAI(
    model="gemini-2.5-flash",
    temperature=0.0
)

Top p

Instead of considering all possible next words, the model only considers the most likely words whose cumulative probability reaches p.

| Word     | Probability |
| -------- | ----------- |
| Ronaldo  | 0.50        |
| Messi    | 0.20        |
| Football | 0.15        |
| Cricket  | 0.10        |
| Banana   | 0.05        |

top_p=0.8
Ronaldo + Messi + Football
because their probabilities add up to 0.85.

Top K
only top K ans are picked

flow: 
All words
   ↓
Top K
   ↓
Top P
   ↓
Temperature chooses

ex.
from langchain_google_genai import ChatGoogleGenerativeAI

llm = ChatGoogleGenerativeAI(
    model="gemini-2.5-flash",
    temperature=0.7,
    top_p=0.95,
    top_k=40
)

