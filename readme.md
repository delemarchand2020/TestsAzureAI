Le notebook "PoC_0_shot_classification.ipynb" met en œuvre un processus de classification de documents à l'aide d'Azure Vision OCR et OpenAI. Ce processus comprend plusieurs étapes clefs, utilisant des techniques modernes de traitement d'images et de textes. Voici un résumé détaillé des fonctionnalités et principes impliqués :

### Installation et Configuration
- **Librairies utilisées** : Des bibliothèques telles que `azure-ai-vision-imageanalysis`, `gradio`, `pdf2image`, `docx2pdf`, et `openai` sont installées. Ces outils permettent l'analyse d'image, la conversion de documents, l'interaction utilisateur, et l'accès à l'API de OpenAI.
- **Chargement des API keys** : Les clés pour Azure et OpenAI sont chargées depuis des fichiers pour configurer les services utilisés.

### Fonctionnalités Principales
1. **Conversion de Documents** : Les documents PDF et DOCX sont convertis en images JPEG pour permettre l'analyse OCR. Cela est réalisé via les fonctions `convert_pdf_to_jpg` et `convert_docx_to_pdf`.
   
2. **Extraction et Analyse de Texte** :
   - Utilisation de `ImageAnalysisClient` d'Azure pour extraire du texte et des étiquettes des images par OCR.
   - Les fonctions `get_all_words` et `get_all_tags` servent à traiter et extraire les résultats pertinents de l'analyse.

3. **Prétraitement de Texte** :
   - Application de regex pour nettoyer et filtrer les textes extraits, en retirant la ponctuation et autres caractères non désirés pour améliorer l'analyse textuelle.

4. **Embeddings et Classification 0-Shot** :
   - Les embeddings textuels sont générés à l'aide de l'API OpenAI. Ces embeddings permettent d'évaluer la similarité entre le texte des documents et des catégories prédéfinies sans nécessiter un entraînement spécifique sur des exemples de ces catégories (0-shot classification).
   - La fonction `cosine_similarity` calcule la similarité entre les vecteurs d'embeddings pour classer les documents.

### Catégorisation des Documents
- Le notebook défini une liste de sous-types de documents et les associe à des catégories plus larges telles que "Preuve de scolarité", "Billet du médecin", et "Facture". Cette mapping structurel aide à classifier de manière plus cohérente et organisée.

### Interface Utilisateur
- Un interface interactive Gradio permet aux utilisateurs de charger des documents, de voir les résultats de la classification, et d'interagir avec le système de façon conviviale.

### Principe de 0-Shot Classification
- Cette méthode de classification tire parti de la compréhension profonde des modèles de langage pré-entraînés pour classer des textes selon des descriptions de catégories sans avoir été formés spécifiquement sur des exemples de ces catégories. Elle illustre l'efficacité des modèles linguistiques modernes pour la compréhension et la catégorisation de contenus variés.

Ce notebook démontre l'utilisation intégrée de technologies de pointe en vision par ordinateur et traitement automatique du langage naturel pour analyser, traiter et classifier des documents de manière efficace et automatisée.
