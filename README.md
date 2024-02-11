# TI_Projekt
Bounding_box and handwritting

# Bounding_box Datei
Die Datenvorverarbeitung ist ähnlich in den 3 Bounding_box training notebooks. es ändert sich manche Sachen je nachdem was man beim Training errecihen will. Die verschiedene Ziele werden erklärt.

## ssd_testing_sub_box_Restnet_und_mobilenet.ipynb
das Hauptziel diese Notebook ist zu untersuchen, welche Unterschied es geben wird, wenn ein Restnet oder ein MobileNet als Backbone zum Training verwendet wird.

 Bemerkung: die Predictions ändert sich nicht wirklich der einzige merkbare Unterschied ist Trainingszeit der länger für ein Restnet ist.

## bbox_training-all_subbox.ipynb
in dieser Notebook wurde das Model auf 2 verschiedene Art und Weise trainiert, einerseits auf alle Main Boxes und andererseits auf alle Sub Boxes. In diesem Fall hat die Predictions gar nicht gut funktioniert. Daher kam die Idee das Training in 4 Teile für jede main Box zu unterteilen.

## Sub_box_training.ipynb

diese Notebook enthält das Training von 4 Modele jede Model wird mit einem main Box aus dem ersten Seiten des Bafög Antrags.
Model_1 Training main Box "Ausbildung"
Model_2 Training main Box "Person"
Model_3 Training main Box "Wohnsitz"
Model_4 Training main Box "Wohnsitz_während_ausbildung"

aus diesem Unterteilung kamen die beste Ergebnisse, die mit SSD Model zu sehen ist. Das Model wurde weiter nicht entwickelt, demzugolge sind die ERgenisse nicht optimal.

# Handwritting Datei 
##### Aufgabe 1 -> training with IAM Sentences alone 
##### Aufgabe 1a -> training with IAM Sentences with GRU instead of LSTM  
##### Aufgabe 1b -> training with IAM Sentences with Efficientnet instead of LSTM
##### Aufgabe 2 -> training with a dataset of numbers only from BAFÖG 
##### Aufgabe 3 -> training with a dataset of numbers and words  from BAFÖG 
##### Aufgabe 4 -> training with a dataset of numbers and words and IAM dataset

## Bafög_IAM_sentence_Indentification_LSTM.ipynb


## Bafög_sentences_Indentification_EfficientNet.ipynb
enthält eine Efficientnet Ansatz zur Texterkennung 
