# Deep Learning Projekt: Waldbrand-Bildklassifikation

## 1.Einführung

In diesem Deep-Learning-Projekt wurde ein neuronales Netz mit der Keras-Bibliothek entwickelt, um Bilder in zwei Klassen zu unterscheiden: "Feuer" und "Kein Feuer". Ziel war es, ein robustes Klassifikationsmodell zu erstellen, das zuverlässig erkennen kann, ob ein Feuer auf einem Bild zu sehen ist.

## 2. Datensatz
Verwendet wurde der The Wildfire Dataset von Kaggle:
🔗 https://www.kaggle.com/datasets/elmadafri/the-wildfire-dataset

Der Datensatz enthält zwei Ordner:

"train" mit Unterordnern "Feuer"und "Kein Feuer", und "test" mit derselben Struktur:

├── train/
│   ├── Feuer/
│   └── Kein Feuer/
├── test/
│   ├── Feuer/
│   └── Kein Feuer/


## 3. Python-Bibliotheken

- NumPy, Matplotlib, TensorFlow, Keras, Scikit-learn

##  4. Modellarchitektur

Das Modell besteht aus zwei Hauptkomponenten:

1) Data Augmentation Layer
   
Zur Vermeidung von Overfitting wurden augmentierte Bilder erzeugt durch:

Rotation

Translation (Verschiebung)

Spiegelung

2) Transfer Learning mit MobileNet
   
Das vortrainierte MobileNet-Modell (ImageNet-Gewichte) wurde als Feature-Extraktor eingesetzt. Die Klassifikationsschicht wurde entfernt und durch eine neue Schicht ersetzt:

'''python
keras.layers.Dense(1, activation='sigmoid')
'''

## 5. Training

- Phase 1: Das MobileNet-Basismodell wurde eingefroren und nur die neuen Schichten trainiert.

- Phase 2: Das gesamte Modell wurde feingetunt (unfreezing und weiteres Training).

- Leistungsmetriken: "Accuracy", "Loss"
  
- Weitere Methoden: "EarlyStopping" und "Learning Rate Reduction" als Callback-Mechanismen

## 6. Datenvisualisierung

Nach dem Training wurden folgende Auswertungen durchgeführt:

- Lernkurven: Visualisierung des Trainings- und Validierungsverlaufs

- Confusion Matrix: Darstellung der Modellleistung

- Prognose: Berechnung der Vorhersagen und Wahrscheinlichkeiten auf Train/Test-Daten

- Scatter Plot: Visualisierung der Prognosewahrscheinlichkeiten

## 7. Modelloptimierung: Erstellung neuer Klasse "Rauch" mit Ollama

Zur weiteren Optimierung des Modells wurde eine zusätzliche Klasse namens **„Rauch“** hinzugefügt. Dafür wurden Bilder, die ausschließlich Rauch zeigen, aus dem ursprünglichen Ordner **„Feuer“** extrahiert und neu gelabelt. Dies wurde durch das **Ollama-Framework** ermöglicht, das eine automatisierte Klassifikation und strukturierte Speicherung großer Bildmengen in neuen Klassen unterstützt.
