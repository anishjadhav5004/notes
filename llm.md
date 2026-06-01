
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


Transformers 

A Transformer is the neural network architecture that powers models like:
ChatGPT
GPT-4
Gemini
Claude

