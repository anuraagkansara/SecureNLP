=========================
MALWARETEXTDBV2.0 DATASET
=========================

This folder contains the datasets that constitute MalwareTextDB-V2.0.
The dataset is used in SemEval-2018 Task 8: Semantic Extraction from CybersecUrity REports using Natural Language Processing (SecureNLP)

It contains 5 subfolders:
- train: contains the training materials released to the participants
- dev: contains the development data used in the Practice phase
- test_1: contains the gold data for SubTask 1 and 2
- test_2: contains the gold data for SubTask 3
- test_3: contains the gold data for SubTask 4

The following are the explanation of content inside each of the subfolder

plaintext/ (train only)
- contains 65 plaintext files after the APT PDF reports are processed with PDFMiner


tokenized/
- Contains the tokenized reports with the annotated labels in IOB format
- 3 different types of labels are used: Entity, Action, Modifier
- If a token is not fallen under any label type, it is labeled as O(means the outside of the labels)
- If a token is the first word of a label, then it is labeled as B-<Label_Type> (means the beginning of a label)
- If a token is the subsequent word of the text span of a label, then it is labeled as I-<Label_Type> (means the inside of a label) 

- Example,
	to O
	direct B-Action
	site B-Entity
	visitors I-Entity
   
- For more details about the IOB format, please refer http://www.nltk.org/book/ch07.html section 2.6


annotations/
- contains the plaintext files with XML tags denoting nonsentence sections such as headings and covers
- contains the annotations files (.ann) for each plaintext file; the positions of the annotations are based on character counts
- In .ann files, 3 different annotation ID types are used : T(text-bound annotation), R(relation), A(attribute) 
- Different attribute labels are ActionName, Capability, StrategicObjectives, TacticalObjectives  

- Example,

Sentence : 
The dynamic analysis showed the malware sample contacted the C&C server, but wasn't sending any URL parameters (id1, id2).

Annotations :
T34     Action 47 56    contacted
T28     Subject 28 46   the malware sample
R23     SubjAction Subject:T28 Action:T34
T30     Object 57 71    the C&C server
R24     ActionObj Action:T34 Object:T30

- more information regarding the annotation files format can be seen in http://brat.nlplab.org/standoff.html

additional_plaintext/ (train only)
- contains additional 84 plaintext files after the APT PDF reports are processed with PDFMiner
- If the participants need to generate special features such brown clusters, these textfiles can be used 
- Tokenized versions of this set of files are not provided in the tokenized folder
