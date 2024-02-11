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
##### Model_1 Training main Box "Ausbildung"
##### Model_2 Training main Box "Person"
##### Model_3 Training main Box "Wohnsitz"
##### Model_4 Training main Box "Wohnsitz_während_ausbildung"

aus diesem Unterteilung kamen die beste Ergebnisse, die mit SSD Model zu sehen ist. Das Model wurde weiter nicht entwickelt, demzugolge sind die ERgenisse nicht optimal.

# Handwritting Datei 
##### Aufgabe 1 -> training mit IAM Sentences allein 
##### Aufgabe 1a -> training mit IAM Sentences with GRU statt LSTM  
##### Aufgabe 1b -> training mit IAM Sätze mit Efficientnet statt LSTM
##### Aufgabe 2 -> training mit Datensatz von nur Zahlen aus BAFÖG Antrag
##### Aufgabe 3 -> training mit Datensatz von Zahlen  and Sätze  aus dem BAFÖG Antrag
##### Aufgabe 4 -> training mit Datensatz von Zahlen and Sätze aus IAM dataset

3 verschiedene Datensätze wurde von mir erzeugt, wo die ROI(Regions of intrest) aus dem Bafög Antrag ausgeschnitten wurden. Es besteht aus ungefähr 300 Trainingsbilder und deren Labels die in der Text Datei "sentences_kopie_2" oder "sentences_kopie_2" usw gespeichert wurde.

## Bafög_IAM_sentence_Indentification_LSTM.ipynb
Diese Notebook enthält alle Aufgaben, die nicht mit Efficientnet zu haben.
das Model in diesem Notebook wurde in verschieden Art und Weise Trainiiert. 
##### erstens mit IAM Datensatz Trainiert.
##### zweitens mit nur Zahlen aus Bafog Antrag
##### drittens aus eine Mischung von Zahlen und Sätze aus dem Antrag
##### viertens eine Mischung von Zahlen und Teil des IAM Datensatzes
##### und zum Schluss ein Transfer Learning von den Weights mit dem Training von IAM Datensatz allein

## Bafög_sentences_Indentification_EfficientNet.ipynb
enthält einen Efficientnet Ansatz zur Texterkennung 
das Model wurde auch aus verschiende Art und Weise trainniert
##### erstens mit nur Zahlen aus dem Bafög Antrag.
##### zwietens mit eine Mischung von Zahlen und Sätze aus Bafäg Antrag
##### schließlich eine Mischung von Zahlen aus Bafäg Antrag und Teil des IAM Datensatzes
