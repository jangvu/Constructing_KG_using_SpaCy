# Constructing_KG_using_SpaCy
A knowledge graph is a large semantic network. It consists of nodes that are entities such as persons, places, events, or companies, and edges that represent formalized relations between those nodes.
This project aims to an overview of constructing a KG step by step. The pipeline of this project is shown below.
![KG](https://github.com/jangvu/Constructing_KG_using_SpaCy/assets/50269219/595b6895-2075-4afb-bf98-8be0739640d6)

Step 1: Sentences Segmentation
Step 2: Entities Extraction
In order to extract the entities, we applied a rule-based approach
- Chunk 1
Defined a few empty variables in this chunk. prv_tok_dep and prv_tok_text will hold the dependency tag of the previous word in the sentence and that previous word itself, respectively. prefix and modifier will hold the text that is associated with the subject or the object.
- Chunk 2
Next, we will loop through the tokens in the sentence. We will first check if the token is a punctuation mark or not. If yes, then we will ignore it and move on to the next token. If the token is a part of a compound word (dependency tag = “compound”), we will keep it in the prefix variable. A compound word is a combination of multiple words linked to form a word with a new meaning (example – “Football Stadium”, “animal lover”).
As and when we come across a subject or an object in the sentence, we will add this prefix to it. We will do the same thing with the modifier words, such as “nice shirt”, “big house”, etc.
- Chunk 3
Here, if the token is the subject, then it will be captured as the first entity in the ent1 variable. Variables such as prefix, modifier, prv_tok_dep, and prv_tok_text will be reset.
- Chunk 4
Here, if the token is the object, then it will be captured as the second entity in the ent2 variable. Variables such as prefix, modifier, prv_tok_dep, and prv_tok_text will again be reset.
- Chunk 5
Once we have captured the subject and the object in the sentence, we will update the previous token and its dependency tag.
Step 3: Relation Extraction
Many basic implementations of knowledge graphs make use of a concept we call triple, that is a set of three items(a subject, a predicate and an object) that we can use to store information about something. The triple is represented as 2 connected nodes.
![Relation drawio](https://github.com/jangvu/Constructing_KG_using_SpaCy/assets/50269219/01a505f0-8b8d-485b-b9b7-cf3822679b9d)
A rule-based matching is used to extract the main verb of the sentence or predicate
Step 4 Constructing KG
![image](https://github.com/jangvu/Constructing_KG_using_SpaCy/assets/50269219/2b5f319f-43a4-4b96-a99b-7b28fdf1952c)

