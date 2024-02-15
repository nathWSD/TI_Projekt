# TI_Projekt
Bounding_box and handwritting Readme

# Bounding_box Datei
Die Datenvorverarbeitung ist ähnlich in den 3 Bounding_box training notebooks. es ändert sich manche Sachen je nachdem was man beim Training erreichen will. Die verschiedene Ziele werden erklärt. 
Der meiste Teil der Datenvorverarbeitung ist von der Bounding_box Gruppe, da  das Ziel war, mit der gleichen Vorverarbeitung das YOLO mit dem SSD Model zu vergleichen.

## models
die Model Datei, in der die Weights der trainierten Model gespeichert sind. 
##### ssd_model_checkpoint_sub_1.h5 -> enthält die weights von dem Training aus der Main Boxen "Ausbildung"
##### ssd_model_checkpoint_sub_2.h5 -> enthält die weights von dem Training aus der Main Boxen "Person"
##### ssd_model_checkpoint_sub_3.h5 -> enthält die weights von dem Training aus der Main Boxen "Wohnsitz"
##### ssd_model_checkpoint_sub_4.h5 -> enthält die weights von dem Training aus der Main Boxen "Wohnsitz_während_ausbildung"

## ssd_testing_sub_box_Restnet_und_mobilenet.ipynb
das Hauptziel diese Notebook ist zu untersuchen, welche Unterschied es geben wird, wenn ein Restnet oder ein MobileNet als Backbone zum Training verwendet wird.
Die beide Modele wurden mit den sub Boxes trainiert, man hat da nicht so unterschiedliche Predictions und die Boxes sind nicht so weit von Ziel. Allerdings es wurde ein Test auf ein ganzes Bild des Antrages gemacht. Der Test war leider nicht erfolgreich, da nur 2 Boxes rauskam.

 Bemerkung: die Predictions ändert sich nicht wirklich der einzige merkbare Unterschied ist die Trainingszeit die länger für ein Restnet ist.

## bbox_training-all_subbox.ipynb
in dieser Notebook wurde das SSD_Model auf 2 verschiedene Art und Weise trainiert, einerseits auf alle Main Boxes und andererseits auf alle Sub Boxes. In diesem Fall hat die Predictions gar nicht gut funktioniert. Daher kam die Idee das Training in 4 Teile für jede main Box zu unterteilen.

## Sub_box_training.ipynb
diese Notebook enthält das Training von 4 Modele jedes Model wird mit einem main Box aus der ersten Seiten des Bafög Antrags trainiert.
##### Model_1 Training main Box "Ausbildung"
##### Model_2 Training main Box "Person"
##### Model_3 Training main Box "Wohnsitz"
##### Model_4 Training main Box "Wohnsitz_während_ausbildung"

Bemerkung: aus diesem Unterteilung kamen die beste Ergebnisse, die mit SSD Model zu sehen sind. Das Model wurde weiter nicht entwickelt, da der Ansatz mit YOLO allegemein besser war und ich wieder in der Texterkennung zurück springen musste. demzufolge sind die Ergenisse nicht optimal.

# Handwritting Datei 
##### Aufgabe 1 -> training mit IAM Sentences allein 
##### Aufgabe 1a -> training mit IAM Sentences with GRU statt LSTM  
##### Aufgabe 1b -> training mit IAM Sätze mit Efficientnet statt LSTM
##### Aufgabe 2 -> training mit Datensatz von nur Zahlen aus BAFÖG Antrag
##### Aufgabe 3 -> training mit Datensatz von Zahlen  and Sätze  aus dem BAFÖG Antrag
##### Aufgabe 4 -> training mit Datensatz von Zahlen and Sätze aus IAM dataset

3 verschiedene Datensätze wurde von mir erzeugt, wo die ROI(Regions of intrest) aus dem Bafög Antrag ausgeschnitten wurden. Es besteht aus ungefähr 300 Trainingsbilder und deren Labels die in der Text Datei "sentences", "sentences_kopie_2" und "sentences_kopie_3" gespeichert wurde.
Ein Beispiel der Sentences.txt Datei sieht so aus 
##### sentences.txt -> enthält die Labels von IAM Datensatz
##### sentences_kopie_2.txt -> enthält die Labels der eigenen Datensatz aus dem Bafög Antrag
##### sentences_kopie_3.txt -> enthält die Labels der Mischung von IAM und eigene Datensatz

###### z01-001-01 0 ok 182 19 0 0 292 18 1|1|1|1|2|0|0|4
###### a01-132x-s02-03 2 ok 166 23 292 2172 1692 96 regular|National|Assistance|grants|.
###### y01-001-45 0 ok 154 19 0 0 292 28 Person_Geburtstag|0|3|0|3|1|9|9|8

###### in diesem Format y01-001-45 ist der Pfad zu dem Bild oder ROI mit dem Name "y01-001-45.png"
###### "Person_Geburtstag|0|3|0|3|1|9|9|8" ist das Label des dazu gehörigen Bildes
###### "ok" weist darauf hin, dass das Bild ist Fehlerfrei zum Training einsetzbar und "err" wäre ein Fehler und das dazu gehörige Bild wird einfach übersprungen.
###### 154 19 0 0 zeigt die Bounding box coordinaten des Bildes, die aber nicht relevant in diesem Fall

## model_weights
##### transfer_learining_LSTM.h5 -> enthält die Weights aus dem Training von IAM_Datensatz mit dem selbst erzeugten Datensatz
##### IAM_only_conv2d_LSTM.h5 -> enthält die Weights aus dem Training von IAM_Datensatz

## Bafög_IAM_sentence_Indentification_LSTM.ipynb
Diese Notebook enthält alle Aufgaben, die nichts mit Efficientnet zu tun haben.
das Model in diesem Notebook wurde in verschieden Art und Weise Trainiert. 
##### erstens mit IAM Datensatz Trainiert.
##### zweitens mit nur Zahlen aus Bafog Antrag
##### drittens aus eine Mischung von Zahlen und Sätze aus dem Antrag
##### viertens eine Mischung von Zahlen und Teil des IAM Datensatzes
##### und zum Schluss ein Transfer Learning von den Weights mit dem Training von IAM Datensatz allein

## Bafög_sentences_Indentification_EfficientNet.ipynb
enthält einen Efficientnet Ansatz zur Texterkennung.
Das Model wurde auch in verschienden Art und Weise trainiert
##### erstens mit nur Zahlen aus dem Bafög Antrag.
##### zwietens mit eine Mischung von Zahlen und Sätze aus Bafäg Antrag
##### schließlich eine Mischung von Zahlen aus Bafäg Antrag und Teil des IAM Datensatzes

Bemerkung: einfache conv2D Layers scheint besser zu sein im Vergleich zu einem Ansatz mit Efficientnet. Weil die Bildgröße sehr klein ist und man in diesem Fall nur mit Grayscale Bilder zu tun hat, ist Efficientnet zu komplex ein Model für diese Aufgabe.

Allgemeine Bemerkung: da meine Ansätze nicht die beste waren, wurden sie nicht in ganzem Projekt übernommen, obwohl ich nah daran war.
