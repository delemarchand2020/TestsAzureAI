Le notebook "PoC_0_shot_classification.ipynb" met en œuvre un processus de classification de documents à l'aide d'Azure Vision OCR et OpenAI. Ce processus comprend plusieurs étapes clefs, utilisant des techniques modernes de traitement d'images et de textes. Voici un résumé détaillé des fonctionnalités et principes impliqués :

### Installation et Configuration
- **Librairies utilisées** : Des bibliothèques telles que `azure-ai-vision-imageanalysis`, `gradio`, `pdf2image`, `docx2pdf`, et `openai` sont installées pour l'analyse d'image, la conversion de documents, l'interaction utilisateur, et l'accès à l'API de OpenAI.
- **Chargement des API keys** : Les clés pour Azure et OpenAI sont chargées depuis des fichiers, permettant la configuration nécessaire des services utilisés.

### Fonctionnalités Principales
1. **Conversion de Documents** : Les documents PDF et DOCX sont convertis en images JPEG pour permettre une analyse OCR plus efficace.
   
2. **Extraction et Analyse de Texte** :
   - Utilisation de `ImageAnalysisClient` d'Azure pour extraire du texte et des étiquettes des images.
   - Les fonctions `get_all_words` et `get_all_tags` traitent les résultats de l'OCR pour récupérer les mots et les tags pertinents.

3. **Prétraitement de Texte** :
   - Nettoyage des textes extraits par OCR en utilisant des expressions régulières pour retirer la ponctuation et autres caractères indésirables.

4. **Embeddings et Classification 0-Shot** :
   - Les embeddings textuels sont générés via l'API OpenAI. Ces embeddings permettent d'évaluer la similarité entre le texte des documents et des catégories prédéfinies, utilisant le concept de 0-shot classification.
   - La fonction `cosine_similarity` calcule la similarité entre les vecteurs d'embeddings pour classer les documents.

### Catégorisation des Documents
- Les sous-types de documents sont organisés et associés à des catégories plus larges comme "Preuve de scolarité", "Billet du médecin", et "Facture", aidant ainsi à une classification structurée et précise.

### Interface Utilisateur
- Un interface Gradio permet aux utilisateurs de charger des documents et de visualiser les résultats de classification de manière interactive.

### Définitions des Termes Techniques
- **OCR (Optical Character Recognition)** : Technologie qui permet de convertir différents types de documents, comme des documents scannés, des PDFs ou des images prises avec un appareil photo, en données textuelles éditables et consultables.
- **Embedding** : Représentation d'éléments textuels dans un espace vectoriel. Cette représentation permet de mesurer des concepts comme la similarité sémantique entre extraits de texte.
- **Cosinus Similarité** : Métrique utilisée pour mesurer la similarité entre deux vecteurs dans un espace vectoriel, en calculant le cosinus de l'angle entre eux. Cela est souvent utilisé en traitement du langage naturel pour évaluer la proximité sémantique entre documents.

Ce notebook démontre l'utilisation intégrée de technologies de pointe en vision par ordinateur et traitement automatique du langage naturel pour analyser, traiter et classifier des documents de manière efficace et automatisée.
