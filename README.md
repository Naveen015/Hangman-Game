# Hangman-Game
The aim is to develop an algorithm to play the game of hangman. Hangman is a guessing game where the player has to guess all the letters of a word, with a limited number of wrong guesses. The game ends either when the player has guessed all the letters of the word or when the player has made 6 wrong guesses. 

## Model - N-gram probabilistic model
The intuition was to learn the patterns of letters occurring together. The pattern can be of any size.  N-gram model is used to learn the patterns of the word. N-gram is basically predicting the Nth letter given N-1 neighboring letters. It calculates the probability of all characters to occur in the masked word given the neighboring characters and picks the character which has the highest probability. 

## Approach
Take a letter and iterate it throughout the masked word to calculate the probability of that letter occurring in each index. Add the probabilities over all the indices of the mask. Calculate these probabilities for all the available letters. Then finally take the character which has the maximum probability. 
N-gram model stores all the patterns of letters occurring together along with its count. A bigram model learns the patterns of size two, trigram learns patterns of size three and respectively for others. We use these counts to calculate the probability as shown below.  

 $P (X=x|L_1^{n-1}) = C (L_1^{n-1}x) / C (L_1^{n-1}) $       
 Where: $L_1^{n-1}x$ = Pattern obtained with n-1 neighboring letters with ‘x’ at masked space         
	$L_1^{n-1}$  = All patterns obtained with n-1 neighboring letters (i.e., any letter at masked space)         
	C ( )      = Count function   
	
Initially we start guessing with unigram model as there won’t be any neighboring characters revealed beforehand. Then we proceed on to bigram model then trigram and further on. After some guesses, most of the letters will be revealed and we can use a bigger N-gram model to predict the remaining letters. 

## Observations
Accuracy was increasing with increasing the N (size of N-gram model). But the learning was saturated after sixgram and there was not a much difference in accuracy between sixgram model and sevengram model. Hence, I stopped at N=7 and finally used a sevengram model to get a better accuracy.  

## Inference
The model can learn the patterns of letters up to size six. After that, there’s not much learning in the model. It may be because of less frequency of patterns with size greater than 6.   
