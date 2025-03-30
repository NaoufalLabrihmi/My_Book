# Guide des commandes LaTeX - Aide-mémoire

## Structure du document

```latex
\part{Titre de la partie}

\chapter{Titre du chapitre}

\section{Titre de la section}

\subsection{Titre de la sous-section}

\subsubsection{Titre de la sous-sous-section}
```

## Environnements mathématiques

### Théorèmes et définitions

```latex
\begin{definition}[Titre optionnel]
    Texte de la définition...
\end{definition}

\begin{theorem}[Titre optionnel]
    Énoncé du théorème...
\end{theorem}

\begin{proposition}[Titre optionnel]
    Énoncé de la proposition...
\end{proposition}

\begin{corollary}[Titre optionnel]
    Énoncé du corollaire...
\end{corollary}

\begin{proof}
    Démonstration...
\end{proof}

\begin{vocabulary}[Titre optionnel]
    Définition du vocabulaire...
\end{vocabulary}

\begin{notation}[Titre optionnel]
    Explication de la notation...
\end{notation}

\begin{remark}
    Texte de la remarque...
\end{remark}

\begin{example}[Titre optionnel]
    Texte de l'exemple...
\end{example}
```

### Exercices et problèmes

```latex
\begin{exercise}
    Énoncé de l'exercice...
\end{exercise}

\begin{solution}
    Solution de l'exercice...
\end{solution}

\begin{problem}[Titre optionnel]
    Énoncé du problème... prblm est pour olympiad 
\end{problem}
```

## Formules mathématiques

### Formule en ligne

```latex
Texte avec une formule $f(x) = x^2$ en ligne.
```

### Formule centrée sans numéro

```latex
\[
    f(x) = \int_0^x t^2 \, dt
\]
```

### Formule centrée avec numéro

```latex
\begin{equation}
    E = mc^2
\end{equation}
```

### Système d'équations

```latex
\begin{cases}
    x + y = 1 \\
    2x - y = 3
\end{cases}
```

### Équations alignées

```latex
\begin{align}
    (x+1)^2 &= (x+1)(x+1) \\
            &= x^2 + 2x + 1
\end{align}
```

## Listes

### Liste à puces

```latex
\begin{itemize}
    \item Premier élément
    \item Deuxième élément
    \item Troisième élément
\end{itemize}
```

### Liste numérotée

```latex
\begin{enumerate}
    \item Premier élément
    \item Deuxième élément
    \item Troisième élément
\end{enumerate}
```

### Liste de description

```latex
\begin{description}
    \item[Terme 1] Description du premier terme
    \item[Terme 2] Description du deuxième terme
\end{description}
```

## Symboles mathématiques essentiels

> **Note importante**: Les commandes ci-dessous nécessitent les packages `amsmath`, `amsfonts` et `amssymb` qui sont déjà inclus dans la classe `backagBook.cls`. Vous n'avez donc **pas besoin** d'ajouter ces packages vous-même.

### Ensembles

```latex
$\mathbb{R}$ - Ensemble des réels
$\mathbb{Z}$ - Ensemble des entiers
$\mathbb{N}$ - Ensemble des entiers naturels
$\mathbb{Q}$ - Ensemble des rationnels
$\mathbb{C}$ - Ensemble des complexes
```

### Opérateurs

```latex
$\sum_{i=1}^{n}$ - Somme
$\prod_{i=1}^{n}$ - Produit
$\int_{a}^{b}$ - Intégrale
$\lim_{x \to a}$ - Limite
```

### Logique

```latex
$\forall$ - Pour tout
$\exists$ - Il existe
$\implies$ - Implique
$\iff$ - Si et seulement si
```

### Symboles grecs

```latex
$\alpha, \beta, \gamma, \delta$ - Lettres grecques minuscules
$\Gamma, \Delta, \Theta, \Lambda$ - Lettres grecques majuscules
$\Pi, \Sigma, \Phi, \Psi, \Omega$ - Autres lettres grecques majuscules
$\epsilon, \varepsilon$ - Deux versions de epsilon
$\theta, \vartheta$ - Deux versions de theta
$\pi, \rho, \sigma, \tau$ - Autres lettres grecques courantes
$\omega, \Omega$ - Oméga minuscule et majuscule
```

### Opérateurs spéciaux

```latex
$\sqrt{x}$ - Racine carrée
$\sqrt[n]{x}$ - Racine n-ième
$\frac{a}{b}$ - Fraction
$\partial$ - Dérivée partielle
$\nabla$ - Nabla/gradient
$\infty$ - Infini
$\approx$ - Approximativement égal
$\sim$ - Similaire à
$\cong$ - Congruent à
$\propto$ - Proportionnel à
$\neq$ - Différent
$\leq$ - Inférieur ou égal
$\geq$ - Supérieur ou égal
$\in$ - Appartient à
$\subset$ - Inclus dans
$\cup$ - Union
$\cap$ - Intersection
$\setminus$ - Différence d'ensembles
$\times$ - Produit vectoriel
$\cdot$ - Produit scalaire
```


## Problèmes d'olympiade

```latex
\part{Problèmes d'Olympiade}

\chapter{Olympiades Internationales}

\begin{problem}[IMO 2019]
    Énoncé du problème...
\end{problem}

\begin{solution}
    Solution du problème...
\end{solution}
```

## Conseils importants

1. **Toujours** terminer chaque environnement avec `\end{...}`
2. **Ne pas** oublier les $ autour des formules mathématiques
3. **Ne pas** modifier les styles prédéfinis
4. **Respecter** la structure du document existant
5. **Placer** les images dans le dossier `Images/`

## Git et versionnement

### Fichier .gitignore

Le projet inclut un fichier `.gitignore` configuré pour ne suivre que les fichiers source essentiels. Voici comment il fonctionne :

```
# Ignorer tous les fichiers par défaut
/*

# Suivre uniquement les fichiers source
!/.gitignore
!*.md                # Tous les fichiers markdown (README.md, etc.)
!LICENSE            # Fichier de licence
!main.tex            # Le document principal
!backagBook.cls      # La classe LaTeX personnalisée
!sample.bib          # La bibliographie
!indexstyle.ist      # Le style d'index
!/Images/            # Le dossier des images
!/Images/*.pdf       # Les images PDF
!/Images/*.jpg       # Les images JPG
!/Images/*.png       # Les images PNG
```

Cette configuration garantit que:
- Seuls les fichiers source importants sont suivis par Git
- Tous les fichiers générés lors de la compilation sont ignorés
- Les images nécessaires au document sont incluses

### Licence

Le projet est distribué sous licence MIT, comme spécifié dans le fichier `LICENSE`. Assurez-vous de conserver l'attribution à l'auteur original (Naoufal Labrihmi) lorsque vous réutilisez ou distribuez ce code.

### Commandes Git essentielles
