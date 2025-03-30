# Mathématiques - Tronc Commun Scientifique

Ce projet est un manuel de mathématiques pour le Tronc Commun Scientifique au Maroc, conçu comme un support pédagogique complet pour les élèves et les enseignants.

![Couverture](Images/peakpx.jpg)

## 📚 À propos du projet

Le manuel comprend une présentation structurée des concepts mathématiques fondamentaux, accompagnée d'exercices résolus, de devoirs avec solutions, et de problèmes d'Olympiade. Il a été développé sous la supervision du Pr. SARDI OTHMANE au CRMEF de Safi.

## 🔧 Structure du projet

```
LeN_ktab/
├── README.md                   # Ce fichier
├── backagBook.cls              # Classe LaTeX personnalisée
├── main.tex                    # Document principal
├── sample.bib                  # Fichier de bibliographie
├── indexstyle.ist              # Style pour l'index
└── Images/                     # Dossier contenant les images
    ├── peakpx.jpg              # Image de couverture
    ├── pic1.jpg                # Image pour les chapitres
    └── pic2.jpg                # Image pour les chapitres
```

## 🚀 Comment compiler le document

### Prérequis

- Distribution LaTeX complète (TeXLive, MiKTeX ou MacTeX)
- Éditeur LaTeX (TeXStudio, Overleaf, VS Code avec extension LaTeX Workshop, etc.)

### Compilation

Pour compiler correctement le document, suivez ces étapes dans l'ordre :

1. **Première compilation** (pour générer les fichiers auxiliaires) :
   ```
   pdflatex main.tex
   ```

2. **Génération de la bibliographie** :
   ```
   biber main
   ```

3. **Génération de l'index** :
   ```
   makeindex -s indexstyle.ist main.idx -o main.ind
   ```

4. **Compilation finale** (deux fois pour résoudre toutes les références) :
   ```
   pdflatex main.tex
   pdflatex main.tex
   ```

### Compilation automatique

Si vous utilisez un éditeur LaTeX moderne, vous pouvez configurer une commande de compilation:

- **TeXStudio** : Configurez un profil de compilation avec la séquence pdflatex → biber → makeindex → pdflatex → pdflatex
- **VS Code avec LaTeX Workshop** : Ajoutez la séquence de compilation dans settings.json
- **Overleaf** : La compilation complète est généralement automatiquement gérée

## 🔍 Structure du document

Le manuel est divisé en plusieurs parties :

1. **Premier Semestre**
   - Analyse Réelle
   - Éléments In-text

2. **Deuxième Semestre**
   - Algèbre Linéaire

3. **Devoirs**
   - Énoncés des Devoirs
   - Solutions des Devoirs

4. **Problèmes d'Olympiade**

## 🛠️ Comment contribuer

### Pour ajouter du contenu

1. **Nouveaux chapitres** : Ajoutez-les dans main.tex en suivant la structure existante :
   ```latex
   \chapter{Titre du Chapitre}
   \section{Titre de la Section}
   ```

2. **Nouveaux exercices** : Utilisez l'environnement approprié :
   ```latex
   \begin{exercise}
     Énoncé de l'exercice...
   \end{exercise}
   
   \begin{solution}
     Solution détaillée...
   \end{solution}
   ```

3. **Exemples et définitions** : Utilisez les environnements existants :
   ```latex
   \begin{definition}[Titre]
     Définition...
   \end{definition}
   
   \begin{example}[Titre]
     Exemple...
   \end{example}
   ```

### Style et conventions

- Respectez le style et la structure existants
- Utilisez les mêmes environnements pour la cohérence
- Ajoutez des images dans le dossier `Images/`
- Pour les références bibliographiques, ajoutez-les dans `sample.bib`

### Résolution des problèmes courants

- **Erreurs de compilation** : Vérifiez les logs et assurez-vous d'avoir installé tous les packages nécessaires
- **Pages vides indésirables** : La classe `backagBook.cls` a été modifiée pour éviter les pages vides entre les parties et les chapitres
- **Problèmes avec les références croisées** : Assurez-vous de compiler plusieurs fois

## 📋 Conventions de nommage

- **Fichiers images** : `descriptif-court.jpg` ou `pic{numero}.jpg`
- **Étiquettes (labels)** : Utilisez des noms explicites, par exemple: 
  ```latex
  \label{sec:analyse-reelle}
  \label{fig:graphe-fonction}
  \label{eq:equation-quadratique}
  ```

## 📝 Notes importantes

- La classe `backagBook.cls` est une version modifiée du modèle LegrandOrangeBook
- Pour les icônes, nous utilisons le package `fontawesome5`
- Le document est configuré pour être imprimé en format A4, recto-verso

## 📚 Ressources utiles

- [Documentation LaTeX (en français)](https://www.latex-project.org/help/documentation/fr/)
- [Overleaf - Guides LaTeX](https://fr.overleaf.com/learn)
- [Détexify - Identifier des symboles mathématiques](http://detexify.kirelabs.org/classify.html)

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier de licence pour plus de détails.

## 👥 Contact

Pour toute question ou suggestion concernant ce projet, veuillez contacter :

- **Naoufal Labrihmi** - [GitHub](https://github.com/NaoufalLabrihmi) 