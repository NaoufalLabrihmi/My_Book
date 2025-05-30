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

### Gestion de la taille des formules

> **Note importante**: Les commandes ci-dessous sont disponibles grâce au package `amsmath` qui est déjà inclus dans la classe `backagBook.cls`. Vous n'avez donc **pas besoin** d'ajouter ce package vous-même.

Si les fractions ou les racines apparaissent trop petites, utilisez ces solutions :

#### Pour les fractions trop petites en mode en ligne

```latex
% Fraction en mode en ligne (petite taille par défaut)
$\frac{a}{b}$

% Fraction de taille normale même en mode en ligne
$\dfrac{a}{b}$

% Fraction forcée en petite taille
$\tfrac{a}{b}$

% Forcer le style d'affichage même en mode en ligne
$\displaystyle \frac{a}{b}$
```

#### Pour les indices ou exposants trop petits

```latex
% Indice normal
$a_i$

% Indice avec contenu complexe
$a_{i+j}$  

% Indice avec fraction (problème de taille)
$a_{\frac{i}{j}}$

% Solution: utiliser \displaystyle dans l'indice
$a_{\displaystyle\frac{i}{j}}$
```

#### Pour les racines avec contenu complexe

```latex
% Racine standard
$\sqrt{x+y}$

% Racine avec fraction (peut être petite)
$\sqrt{\frac{x}{y}}$

% Solution: utiliser \displaystyle
$\sqrt{\displaystyle\frac{x}{y}}$
```

#### Ajustement général de la taille de l'équation

```latex
% Taille normale
$\sum_{i=1}^n i$

% Grande taille (style d'affichage)
$\displaystyle \sum_{i=1}^n i$

% Pour l'ensemble de l'équation
\begin{equation}
    \displaystyle \int_0^1 \frac{x^2}{\sqrt{1-x^2}} \, dx
\end{equation}
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

### Licence

Le projet est distribué sous licence MIT, comme spécifié dans le fichier `LICENSE`. Assurez-vous de conserver l'attribution à l'auteur original (Naoufal Labrihmi) lorsque vous réutilisez ou distribuez ce code.
