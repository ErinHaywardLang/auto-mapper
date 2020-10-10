# auto-mapper
Program to predict the property of a given product name. 

Ex: "Star Wars The Black Series The Mandalorian Toy 6 Inch Scale Collectible Action Figure" -> The Mandalorian

## Terminology
Document - A string of text that is used in the classification

Corpus - A set of documents

Stop words - Words that bear little relevance to the classification. Ex: "a", "the", "to", "from".

## Learning process:
• Loads two given Excel files; one for training, one for testing. Testing can have both mapped and unmapped products in them. Training must be entirely mapped.

• Takes both sets of data and extracts the product names or documents in each. Each document is split into individual terms and stop words are removed.

• Using the training data counts occurences of each unique term in entire corpus, then counts occurences for each property in entire data set.

• Finally, for each product in the training data set, assigns each term's number of occurences in the document to the product's mapped property. Dictionary is outputted where keys are unique properties and each contain a "sub-dictionary" of terms and their occurences within that property.


## Classification process:
For the classification of a single product:

• For each term in the document we check if that term is occurs under each property, if the term occurs under a certain property, the number of occurences that term has under said property is then added to that property's "score".

• _(Method still under review)_ If the current term has a high score under a property that the previous term also had a high score then we (Method 1) multiply the current term's score into the current property score OR (Method 2) multiply the current term's score into the score of the previous property and add it to the property's score.

• In order to gauge a level of "certainty" of the classification; the highest scoring property is then checked against the second highest scoring property, the two scores are divided (Property1/Property2) and if the result is below the threshold then the product is ignored and left unmapped, the same occurs if only one or no property scores in the entire product.

• The highest scoring property of the product is then selected as the predicted property and then returned.
