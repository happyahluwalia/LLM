### LLM Output Configuration ###
source - https://drive.google.com/file/d/13PXk5hmgoTeFyKCKCKroE4pz7AoFoyjS/view
**Temperature: **
  This controls the randomness of the output. If temperature is near zero then everytime the output will be the same. If higher temperature then the LLM will be more creative and answer will be different each time. 
  Temperature of 0 (greedy decoding) is deterministic. The top probablistic answer is always taken. If 2 answers have same probability then based on how tie breaking is implemented it will give that as output.
  Temperature of max output is random. 

**Top-K**
  In Top-K the top k answers are taken into consideration. Higher the Top-K that means more tokens/answers are considered and more creative the output of model can be.
  Lower Top-K that means the "eligible" answers are restrictive. Top-K of 1 is like greedy decoding. Think of Top-K as give me Top 5 of the tokens that meet the requirement and now from these Top 5 I will chose the one to give to user. 

**Top-P**
   Top-P is "similar" to Top-K but in it it picks the tokens whose probability totals up to "P". It works by model sorting the words by their probabilities and starts adding sum. Once it reaches P it stops. Now it randomly samples from this set of words. Top-P allows the model flexibility.

At extreme settings one configuration cancels out impact of other configuration.
**Temperature at 0** : This makes top-k and top-p irrelevant as the next probable token is chosen. 
**Temperature at Max**: This means the whole set is probable and that makes temperatue at max irrelevant. It will pick based on setting of topk & topp
**TopK at 1**: This makes Top P and Temperature irrelevant as only the top 1 token is in the set to be chosen.
**TopK at Max**: If max is set to say the size of LLM vocabulary, that means all the words are in the set to be selected and none will be left out. Fall back to TopP
**TopP at 0** : That means the Token with the most probability will be chosen, making temperature and TopK irrelevant. 
**TopP at 1**: That means any token that has some probablility will be part of the set and none will be left out. 

**Scenarios**
**Coherent results with bit of creativity**: Temperature of 0.2 (dont be too creative), Top-P of .99 (most of the words), TopK of 30 (pick from top 30)
**Creative results**: Temperature of 0.9 (be creative), Top-P of 0.99 (most of words), Topk of 40 (pick from top 40)
**Deterministic results (like math problems)**: Temperature of 0, Top-p of 0.1 (the top probabilistic result), Topk of 1 (top 1)
