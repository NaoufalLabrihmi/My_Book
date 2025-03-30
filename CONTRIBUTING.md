# Guide de contribution au projet "Mathématiques - Tronc Commun Scientifique"

Ce document fournit des instructions détaillées pour contribuer au projet de manuel mathématique. Il est destiné aux collaborateurs techniques qui souhaitent ajouter ou modifier du contenu, comprendre l'architecture du code ou personnaliser le style du document.

## Table des matières

- [Structure technique](#structure-technique)
- [Classe LaTeX personnalisée](#classe-latex-personnalisée)
- [Environnements disponibles](#environnements-disponibles)
- [Commandes personnalisées](#commandes-personnalisées)
- [Styles et mise en page](#styles-et-mise-en-page)
- [Typographie mathématique](#typographie-mathématique)
- [Démonstrations et preuves](#démonstrations-et-preuves)
- [Gestion des références](#gestion-des-références)
- [Modifications avancées](#modifications-avancées)
- [Flux de travail recommandé](#flux-de-travail-recommandé)
- [Exemples pratiques](#exemples-pratiques)

## Structure technique

Le projet est basé sur la classe personnalisée `backagBook.cls`, qui est une modification de la classe "Legrand Orange Book". Le document principal est `main.tex`, qui charge cette classe et définit la structure du manuel.

### Hiérarchie du document

```
frontmatter/
  - Page de titre
  - Copyright
  - Remerciements
  - À propos
  - Table des matières

mainmatter/
  - Premier Semestre
    - Analyse Réelle
    - Éléments In-text
  - Deuxième Semestre
    - Algèbre Linéaire
  - Devoirs
    - Énoncés
    - Solutions
  - Problèmes d'Olympiade

backmatter/
  - Bibliographie
  - Index
```

## Classe LaTeX personnalisée

La classe `backagBook.cls` définit la structure, le style et les fonctionnalités du document. Voici ses composants principaux :

### Configuration de base

```latex
\NeedsTeXFormat{LaTeX2e}
\ProvidesClass{backagBook}[2025/03/26 The backagBook Class v3.0]
```

La classe est basée sur la classe standard `book` avec plusieurs options configurées :

```latex
\DeclareOption{twoside}{\PassOptionsToClass{\CurrentOption}{book}}
\DeclareOption{oneside}{\PassOptionsToClass{\CurrentOption}{book}}
\LoadClass{book}
```

### Packages chargés

La classe charge plusieurs packages essentiels :

- `graphicx` : inclusion d'images
- `float` : positionnement des flottants
- `xcolor` : gestion des couleurs
- `geometry` : marges et dimensions
- `fancyhdr` : en-têtes et pieds de page personnalisés
- `titlesec` : formatage des titres de sections
- `hyperref` : liens et métadonnées PDF
- `amsmath`, `amsfonts`, `amssymb`, `amsthm` : support mathématique
- `mdframed` : boîtes colorées pour théorèmes
- `tikz` : dessins et positionnement absolus

### Couleurs du thème

Le document utilise une palette de couleurs personnalisée définie dans `main.tex` :

```latex
\definecolor{primary}{RGB}{41,67,92}% Deep lake blue
\definecolor{secondary}{RGB}{187,201,215}% Sunset orange
\definecolor{accent1}{RGB}{28,53,56}% Dark teal
\definecolor{accent2}{RGB}{67,108,132}% Misty blue
\definecolor{accent3}{RGB}{12,28,37}% Deep shadow
\definecolor{accent4}{RGB}{187,201,215}% Misty light
```

La couleur principale `ocre` est définie comme équivalente à `primary` :

```latex
\definecolor{ocre}{RGB}{41,67,92}
```

## Environnements disponibles

### Théorèmes et environnements mathématiques

La classe définit plusieurs environnements pour le contenu mathématique, chacun avec son propre style visuel :

| Environnement   | Description                           | Style                                          |
|-----------------|---------------------------------------|------------------------------------------------|
| `theorem`       | Pour énoncer des théorèmes            | Boîte avec fond gris et bordure ocre           |
| `definition`    | Pour définir des concepts             | Boîte avec barre verticale gauche ocre         |
| `example`       | Pour donner des exemples              | Sans boîte, avec marqueur noir                 |
| `remark`        | Pour ajouter des remarques            | Texte légèrement indenté avec icône 'R'        |
| `corollary`     | Pour les corollaires                  | Boîte avec barre verticale gauche grise        |
| `proposition`   | Pour les propositions                 | Texte simple avec numérotation ocre            |
| `exercise`      | Pour les exercices                    | Boîte avec fond légèrement ocre                |
| `solution`      | Pour les solutions d'exercices        | Boîte avec fond légèrement bleu                |
| `vocabulary`    | Pour introduire du vocabulaire        | Texte avec numérotation noire                  |
| `notation`      | Pour expliquer les notations          | Texte avec numérotation noire                  |
| `problem`       | Pour les problèmes plus complexes     | Boîte similaire à celle des théorèmes          |

### Utilisation des environnements

Pour utiliser ces environnements, suivez cette syntaxe :

```latex
\begin{definition}[Limite d'une fonction]
Soit $f: D \to \mathbb{R}$ une fonction et $a$ un point d'accumulation de $D$. On dit que $L$ est la limite de $f$ en $a$ si:
\[\forall \varepsilon > 0, \exists \delta > 0, \forall x \in D, 0 < |x-a| < \delta \Rightarrow |f(x)-L| < \varepsilon\]
\end{definition}

\begin{exercise}
Montrer que $\sqrt{2}$ est irrationnel.
\end{exercise}

\begin{solution}
Démonstration par l'absurde:
\begin{enumerate}
    \item Supposons que $\sqrt{2}$ est rationnel
    \item Alors $\sqrt{2} = \frac{p}{q}$ avec $p,q$ entiers premiers entre eux
    \item Donc $2q^2 = p^2$
    \item Donc $p^2$ est pair, donc $p$ est pair
    \item Posons $p = 2k$, alors $2q^2 = 4k^2$
    \item Donc $q^2 = 2k^2$
    \item Donc $q$ est pair
    \item Contradiction car $p$ et $q$ sont premiers entre eux
\end{enumerate}
\end{solution}
```

## Commandes personnalisées

### Images de chapitres

Pour définir l'image d'arrière-plan d'un chapitre :

```latex
\chapterimage{pic1.jpg}
```

### Espacement des chapitres

Pour ajuster l'espace au-dessus et en-dessous du titre de chapitre :

```latex
\chapterspaceabove{5.8cm}
\chapterspacebelow{6cm}
```

### Icônes FontAwesome

Le document utilise `fontawesome5` pour les icônes. Exemples d'utilisation :

```latex
\faClipboardCheck  % Icône de presse-papiers
\faCalculator      % Icône de calculatrice
\faVectorSquare    % Icône de vecteur
\faLightbulb       % Icône d'ampoule
\faTrophy          % Icône de trophée
\faBookOpen        % Icône de livre ouvert
\faEdit            % Icône d'édition
\faTasks           % Icône de tâches
```

## Styles et mise en page

### Structure des parties

Chaque partie du document est créée avec :

```latex
\part{Titre de la partie}
```

La classe génère automatiquement une page de partie avec un fond coloré, le numéro de partie en grand format, et une mini table des matières.

### Structure des chapitres

Les chapitres sont définis par :

```latex
\chapterimage{image.jpg}  % Définir l'image d'arrière-plan (optionnel)
\chapter{Titre du chapitre}
```

Chaque chapitre a un design avec une boîte de titre sur l'image d'arrière-plan.

### Sections et sous-sections

Les sections et sous-sections suivent la syntaxe standard LaTeX avec un style personnalisé :

```latex
\section{Titre de la section}
\subsection{Titre de la sous-section}
\subsubsection{Titre de la sous-sous-section}
```

## Typographie mathématique

### Modes mathématiques

Le document utilise l'option `fleqn` pour aligner les équations à gauche. Il y a plusieurs façons d'insérer des mathématiques :

1. **Mode en ligne** : Utilisez `$...$` pour les formules dans le texte
   ```latex
   Soit $f(x) = x^2$ une fonction.
   ```

2. **Mode équation** : Utilisez `\[...\]` pour les équations centrées sur leur propre ligne
   ```latex
   \[f(x) = \int_{0}^{x} t^2 \, dt\]
   ```

3. **Environnement d'équation numéroté** : Utilisez `equation` pour les équations numérotées
   ```latex
   \begin{equation}
   E = mc^2
   \end{equation}
   ```

### Symboles mathématiques courants

Le document utilise les packages `amsmath`, `amsfonts` et `amssymb` pour accéder à une large gamme de symboles mathématiques :

```latex
% Ensembles
$\mathbb{R}$   % Ensemble des réels
$\mathbb{Z}$   % Ensemble des entiers
$\mathbb{N}$   % Ensemble des entiers naturels
$\mathbb{Q}$   % Ensemble des rationnels
$\mathbb{C}$   % Ensemble des complexes

% Opérateurs
$\sum_{i=1}^{n}$   % Somme
$\prod_{i=1}^{n}$  % Produit
$\int_{a}^{b}$     % Intégrale
$\lim_{x \to a}$   % Limite

% Symboles logiques
$\forall$    % Pour tout
$\exists$    % Il existe
$\implies$   % Implique
$\iff$       % Si et seulement si
$\land$      % Et logique
$\lor$       % Ou logique
$\neg$       % Négation

% Espaces
$a\,b$       % Petit espace
$a\;b$       % Espace moyen
$a\quad b$   % Grand espace
$a\qquad b$  % Très grand espace
```

### Matrices et tableaux

Pour les matrices et tableaux d'équations :

```latex
% Matrice simple
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}

% Matrice avec crochets
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}

% Système d'équations
\begin{cases}
2x + 3y = 5 \\
x - y = 1
\end{cases}
```

## Démonstrations et preuves

### Structure de démonstration

Pour les démonstrations, utilisez l'environnement `proof` :

```latex
\begin{proof}
Supposons que $f$ admette deux limites $L_1$ et $L_2$ en $a$.
Soit $\varepsilon > 0$. Il existe $\delta_1, \delta_2 > 0$ tels que:
\begin{align*}
|x-a| < \delta_1 &\Rightarrow |f(x)-L_1| < \frac{\varepsilon}{2} \\
|x-a| < \delta_2 &\Rightarrow |f(x)-L_2| < \frac{\varepsilon}{2}
\end{align*}
Donc pour $|x-a| < \min(\delta_1,\delta_2)$:
\[|L_1-L_2| \leq |f(x)-L_1| + |f(x)-L_2| < \varepsilon\]
Comme ceci est vrai pour tout $\varepsilon > 0$, on a $L_1 = L_2$.
\end{proof}
```

### Types de démonstration

Différentes approches de démonstration peuvent être utilisées :

1. **Démonstration directe** : Une preuve pas à pas
2. **Démonstration par l'absurde** : Supposer le contraire et arriver à une contradiction
3. **Démonstration par récurrence** : Base et étape d'induction
4. **Démonstration par contraposée** : Prouver que non-B implique non-A

### Exemple de démonstration par récurrence

```latex
\begin{proof}
Nous allons procéder par récurrence sur $n$.

\textbf{Base de récurrence :} Pour $n=1$, nous avons $\sum_{i=1}^{1} i = 1 = \frac{1 \cdot (1+1)}{2}$, donc la formule est vérifiée.

\textbf{Hypothèse de récurrence :} Supposons que pour un certain $k \geq 1$, on a $\sum_{i=1}^{k} i = \frac{k(k+1)}{2}$.

\textbf{Étape d'induction :} Montrons que la formule est vraie pour $n = k+1$.
\begin{align*}
\sum_{i=1}^{k+1} i &= \sum_{i=1}^{k} i + (k+1)\\
&= \frac{k(k+1)}{2} + (k+1) \quad \text{(par hypothèse de récurrence)}\\
&= (k+1)\left(\frac{k}{2} + 1\right)\\
&= (k+1)\frac{k+2}{2}\\
&= \frac{(k+1)(k+2)}{2}
\end{align*}

Donc $\sum_{i=1}^{k+1} i = \frac{(k+1)(k+2)}{2} = \frac{(k+1)((k+1)+1)}{2}$, ce qui correspond bien à la formule pour $n = k+1$.

Par le principe de récurrence, la formule est vraie pour tout $n \geq 1$.
\end{proof}
```

## Gestion des références

### Références bibliographiques

Le document utilise `biblatex` avec le backend `biber`. Pour ajouter une référence :

1. Ajoutez l'entrée dans `sample.bib` :
   ```bibtex
   @book{reference:2025,
     title = {Titre du livre},
     author = {Nom, Prénom},
     year = {2025},
     publisher = {Éditeur}
   }
   ```

2. Citez-la dans le texte :
   ```latex
   \cite{reference:2025}
   ```

### Références croisées

Pour les références croisées internes :

1. Ajoutez un label à l'élément à référencer :
   ```latex
   \section{Titre}\label{sec:mon-label}
   ```

2. Référencez-le ailleurs :
   ```latex
   Voir section~\ref{sec:mon-label}
   ```

## Modifications avancées

### Personnalisation des environnements

Pour modifier un environnement existant, vous pouvez redéfinir son style dans le préambule de `main.tex`. Par exemple :

```latex
\mdfdefinestyle{mystyle}{
    linecolor=blue,
    backgroundcolor=blue!10,
    frametitlerule=true,
    frametitlebackgroundcolor=blue!20,
    innertopmargin=\topskip
}
\renewenvironment{definition}{\begin{mdframed}[style=mystyle]}{\end{mdframed}}
```

### Ajout de nouveaux packages

Pour ajouter un nouveau package, ajoutez-le au préambule de `main.tex` :

```latex
\usepackage{nouveaupackage}
```

### Modification de la classe

Si vous devez modifier la classe `backagBook.cls`, assurez-vous de comprendre les conséquences sur l'ensemble du document. Documentez vos modifications et testez-les soigneusement.

## Flux de travail recommandé

1. **Examiner la structure** : Comprendre où votre contribution s'intègre
2. **Créer une branche** : Si vous utilisez Git, créez une branche pour vos modifications
3. **Modifications localisées** : Testez vos modifications dans une section restreinte
4. **Compilation complète** : Compilez l'ensemble du document pour vérifier les effets globaux
5. **Documentation** : Documentez vos modifications dans les commentaires et le journal des modifications

### Bonnes pratiques

- Commentez votre code LaTeX pour expliquer les parties complexes
- Utilisez des indentations cohérentes pour améliorer la lisibilité
- Fractionnez les longues sections en fichiers séparés et utilisez `\input{fichier}` ou `\include{fichier}`
- Testez régulièrement la compilation complète
- Utilisez `%TODO: commentaire` pour marquer les parties inachevées

## Exemples pratiques

### Exemple 1 : Création d'un nouveau chapitre

```latex
\chapterimage{pic1.jpg}
\chapter{Géométrie Euclidienne}

\section{Notions de base}

\begin{definition}[Droite]
Une droite est l'ensemble des points alignés dans une direction donnée.
\end{definition}

\begin{theorem}[Thalès]
Si deux droites sont coupées par des droites parallèles, alors les segments déterminés sur une droite sont proportionnels aux segments correspondants déterminés sur l'autre droite.
\end{theorem}

\begin{proof}
[Esquisse de démonstration]
On considère un repère adapté...
\end{proof}
```

### Exemple 2 : Ajout d'un exercice avec solution

```latex
\section{Exercices avec Solutions}\label{sec:exercices-geometrie}

\begin{exercise}
Soit $ABC$ un triangle rectangle en $A$. Démontrer le théorème de Pythagore : $BC^2 = AB^2 + AC^2$.
\end{exercise}

\begin{solution}
Nous allons utiliser les propriétés des triangles semblables.
\begin{enumerate}
    \item Soit $H$ le pied de la hauteur issue de $A$
    \item Les triangles $ABH$ et $ACH$ sont semblables au triangle $ABC$
    \item Par les relations de similitude, on obtient $\frac{AB^2}{BC \cdot BH} = 1$ et $\frac{AC^2}{BC \cdot HC} = 1$
    \item En additionnant, $AB^2 + AC^2 = BC \cdot BH + BC \cdot HC = BC \cdot (BH + HC) = BC^2$
\end{enumerate}
\end{solution}
```

### Exemple 3 : Formules mathématiques complexes

```latex
\begin{align}
\nabla \times \vec{E} &= -\frac{\partial \vec{B}}{\partial t}\\
\nabla \times \vec{B} &= \mu_0 \vec{J} + \mu_0 \varepsilon_0 \frac{\partial \vec{E}}{\partial t}\\
\nabla \cdot \vec{E} &= \frac{\rho}{\varepsilon_0}\\
\nabla \cdot \vec{B} &= 0
\end{align}

\begin{remark}[Équations de Maxwell]
Ces quatre équations constituent les équations de Maxwell, qui décrivent complètement l'électromagnétisme classique.
\end{remark}
```

### Exemple 4 : Structure de devoirs

```latex
\section{\protect\faCalculator\ Analyse Réelle}

\subsection{Devoir 1}

\subsubsection{Type A}
\begin{exercise}
Étudier la convergence de la suite définie par:
\[u_n = \left(1 + \frac{1}{n}\right)^n\]
\end{exercise}

\begin{solution}
\textbf{Solution de l'Exercice 1:}
\begin{enumerate}
    \item On montre d'abord que la suite $(u_n)$ est croissante
    \item Puis on montre qu'elle est majorée
    \item On utilise le développement en série:
          \begin{align*}
          \left(1 + \frac{1}{n}\right)^n &= \sum_{k=0}^{n} \binom{n}{k}\frac{1}{n^k} \\
          &= 1 + 1 + \sum_{k=2}^{n} \frac{n(n-1)\cdots(n-k+1)}{k!} \cdot \frac{1}{n^k}
          \end{align*}
    \item On montre que $\lim_{n\to\infty} u_n = e$
\end{enumerate}
\end{solution}
```

## Résolution de problèmes spécifiques

### Pages vides entre les parties

La classe a été modifiée pour éviter les pages vides entre les parties et les chapitres. Si ce problème persiste :

```latex
% Dans backagBook.cls
\makeatletter
\def\@endpart{\vfil\penalty9999\relax}
\makeatother
```

### Référence non résolue

Si certaines références ne se résolvent pas correctement, assurez-vous de :
1. Compiler plusieurs fois (pdflatex → biber → pdflatex → pdflatex)
2. Vérifier que les labels sont uniques
3. Vérifier l'absence d'erreurs LaTeX qui pourraient interrompre le processus

### Problèmes d'alignement dans les formules mathématiques

Le document utilise l'option `fleqn` pour aligner les équations à gauche. Pour des alignements spécifiques, utilisez les environnements de `amsmath` :

```latex
\begin{align}
a &= b + c\\
  &= d + e
\end{align}
```

---

Pour toute question supplémentaire ou assistance, contactez l'équipe de développement via les informations fournies dans le README. 