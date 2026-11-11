


Proiect la materia **Rețele Neuronale și Logică Fuzzy (RNLF)**.
Clasificare de imagini cu rețele neuronale convoluționale (CNN), în Python și PyTorch:
dintr-o imagine cu fața șoferului, programul stabilește dacă este **somnolent** (Drowsy) sau **treaz** (Non Drowsy).

> **Stadiu:** în lucru. Momentan este finalizată explorarea setului de date.

## Autori
- Titerlea Cristian
- Calinu Alexandru

## Setul de date
- **Driver Drowsiness Dataset (DDD)**, Kaggle: https://www.kaggle.com/datasets/ismailnasri20/driver-drowsiness-dataset-ddd
- 41.793 de imagini RGB cu fețe de șoferi, de 227 × 227 pixeli, în 2 clase:
  - Drowsy: 22.348 imagini
  - Non Drowsy: 19.445 imagini
- Clasele sunt aproape echilibrate (aprox. 53% / 47%).
- Setul **nu este inclus în repo**. Se descarcă de pe Kaggle, apoi se setează calea în variabila `DATA_DIR` din scripturi.

### Observații din explorarea datelor
- Numele fișierelor au forma `prefix + număr` (de exemplu `A0001.png`, `a0001.png`). Există 54 de prefixe, iar **niciun prefix nu apare în ambele clase**: prefixele cu literă mare sunt doar în Drowsy, cele cu literă mică doar în Non Drowsy.
- Presupunere: un prefix corespunde unui grup de cadre din același video. Cadrele consecutive sunt foarte asemănătoare, deci o împărțire aleatoare a imaginilor în train/validare/test ar pune cadre aproape identice în seturi diferite (*data leakage*) și ar umfla artificial rezultatele.
- Decizie: împărțirea în seturi se va face **pe grupuri (prefixe)**, nu pe imagini individuale.

## Ce s-a făcut până acum
- [x] Configurare mediu (Python, PyTorch, PyCharm)
- [x] Explorarea setului de date: clase, numărul de imagini, dimensiuni, exemple vizuale
- [x] Analiza structurii numelor de fișiere și a riscului de *data leakage*
- [ ] Împărțirea pe grupuri în train / validare / test
- [ ] Preprocesare (redimensionare, normalizare, augmentare)
- [ ] Arhitectură CNN proprie, antrenare, analiza curbelor de învățare
- [ ] Comparație cu o arhitectură consacrată (ResNet / MobileNet, cu fine-tuning)
- [ ] Interfață grafică
- [ ] Prezentare PowerPoint și demonstrație practică

## Structura repo-ului
- `check.py`: verifică instalarea PyTorch și disponibilitatea GPU (eu voi folosi Google Colab deoarece nu am GPU compatibil)
- `explore.py`: încarcă setul de date, afișează clasele, numărul de imagini și un grid de exemple
- `inspect_files.py`: inspectează numele fișierelor și dimensiunea imaginilor
- `check_prefixes.py`: numără imaginile pe prefixe și pe clase

