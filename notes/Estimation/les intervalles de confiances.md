# **Intervalle de Confiance de la Moyenne** :

ahna on estime toujours la moyenne ( called m or u ) bel X bar 

L'**intervalle de confiance** (IC) pour la **moyenne** d'une population est une plage de valeurs dans laquelle on pense que la véritable moyenne de la population se situe, avec un certain niveau de confiance (par exemple, 95 % ou 99 %).

#### **Formules de l'Intervalle de Confiance :**

1. **Lorsque l'écart-type de la population est connu (\( \sigma \))** :
   $$
   IC = \left[\overline{X} - Z_{\alpha/2} \times \frac{\sigma}{\sqrt{n}}, \overline{X} + Z_{\alpha/2} \times \frac{\sigma}{\sqrt{n}}\right]
   $$
   Où :
   - \( overline{X} \) = moyenne de l'échantillon.
   - \( \sigma \) = écart-type de la population.
   - \( n \) = taille de l'échantillon.
   - \( Z_{\alpha/2} \) = valeur critique de la loi normale (par exemple, \( Z = 1.96 \) pour un niveau de confiance de 95 %).


2. **Lorsque l'écart-type de la population est inconnu (\( \sigma \))** :
   On utilise l'estimateur \( S \) de l'écart-type et la **loi de Student** pour ajuster l'incertitude introduite par l'estimation de \( \sigma \) :
   $$
   IC = \left[\overline{X} - t_{\alpha/2} \times \frac{S}{\sqrt{n}}, \overline{X} + t_{\alpha/2} \times \frac{S}{\sqrt{n}}\right]
   $$
   Où :
   - \( S \) = écart-type de l'échantillon.
   - $$( t_{\alpha/2} ) = valeur  critique de la loi de Student (avec ( n-1 ) degrés de liberté). $$

---

### **Pourquoi utiliser la loi de Student dans ce cas ?**

- Lorsque l'écart-type de la population est **inconnu** et qu'on utilise l'**écart-type de l'échantillon** \( S \), la moyenne d'échantillon \( \overline{X} \) suit une **loi de Student** plutôt qu'une loi normale.
  
  - La loi de Student prend en compte l'incertitude supplémentaire introduite par l'utilisation de l'estimateur \( S \), surtout pour des **échantillons de petite taille**. Cela rend l'intervalle plus large par rapport à la loi normale, afin de mieux refléter la variabilité introduite par l'estimation de \( \sigma \).

---

### **Le Théorème Central Limite (TCL)** :

Le **théorème central limite** (TCL) stipule que, peu importe la forme de la distribution de la population, la **moyenne des échantillons** \( \overline{X} \) suivra une **distribution normale** si l'échantillon est suffisamment grand, généralement lorsque \( n \geq 30 \).

- **Si la population suit déjà une loi normale** (ou si l'échantillon est suffisamment grand pour appliquer le TCL), alors la moyenne d'échantillon \( \overline{X} \) suit une loi **normale**. Dans ce cas, on peut directement utiliser la loi normale pour l'intervalle de confiance, sans avoir besoin de la loi de Student, même si \( \sigma \) est inconnu.

  **Exemple** : Si la population suit une loi normale \( \mathcal{N}(\mu, \sigma^2) \), alors pour n'importe quel échantillon, \( \overline{X} \) suit une loi normale avec moyenne \( \mu \) et écart-type \( \frac{\sigma}{\sqrt{n}} \). L'intervalle de confiance peut être calculé en utilisant la **loi normale** :
  $$
  IC = \left[\overline{X} - Z_{\alpha/2} \times \frac{\sigma}{\sqrt{n}}, \overline{X} + Z_{\alpha/2} \times \frac{\sigma}{\sqrt{n}}\right]
  $$

---

### **Résumé final :**

- **Loi de Student** : On l'utilise **lorsque l'écart-type de la population est inconnu** et que l'on doit utiliser l'estimateur \( S \). La loi de Student est nécessaire, en particulier pour **petits échantillons**, car elle prend en compte l'incertitude supplémentaire liée à l'estimation de \( \sigma \).
  
- **Loi normale (via TCL)** : Si **la moyenne suit déjà une loi normale** ou si l'échantillon est suffisamment grand (d'après le TCL), la moyenne d'échantillon \( \overline{X} \) suit une loi normale. Dans ce cas, on peut utiliser directement la **loi normale** pour calculer l'intervalle de confiance, même si \( \sigma \) est inconnu, tant que \( n \) est suffisamment grand.

---

### **Interprétation de l'intervalle de confiance :**
Un **intervalle de confiance à 95 %** signifie que si l'on répétait l'expérience de nombreuses fois, environ 95 % des intervalles calculés contiendraient la véritable moyenne de la population.

**Exemple** : Si un intervalle de confiance pour la moyenne est \( [24, 26] \), cela signifie que nous sommes confiants à 95 % que la véritable moyenne de la population se situe entre 24 et 26.

---

# **Intervalle de Confiance de la Variance**

L'**intervalle de confiance** (IC) pour la **variance** d'une population est une plage de valeurs dans laquelle on pense que la véritable variance de la population se situe, en fonction d'un échantillon.

---

### **Formule pour l'intervalle de confiance de la variance :**

L'intervalle de confiance pour la variance \( \sigma^2 \) est basé sur la **distribution du chi-carré** (ou **chi-square**). Cette distribution est utilisée pour estimer la variance d'une population, particulièrement dans les cas où l'on connaît la **distribution normale** de la population.

#### **Étapes de calcul :**

1. **Si la population suit une loi normale**, la statistique suivante suit une loi du **chi-carré** avec \( n-1 \) degrés de liberté :
   $$
   \chi^2 = \frac{(n-1)S^2}{\sigma^2}
   $$
   Où :
   - $$( S^2 ) = variance de l'chantillon. $$
   - $$( \sigma^2 ) = variance de la population (que nous voulons estimer). $$
   - \( n \) = taille de l'échantillon.

2. **Intervalle de confiance pour \( \sigma^2 \) :**
   L'intervalle de confiance pour la **variance** \( \sigma^2 \) est donné par :
   $$
   \left[ \frac{(n-1)S^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)S^2}{\chi^2_{1-\alpha/2, n-1}} \right]
   $$
   Où :
   - $$( S^2 ) = variance de l'échantillon. $$
   - $$( \chi^2_{\alpha/2, n-1} ) et ( \chi^2_{1-\alpha/2, n-1} ) sont les quantiles de la **distribution chi-carré** à ( \alpha/2 ) et ( 1-\alpha/2 ), respectivement, avec ( n-1 ) degrés de liberté. $$

#### **Interprétation :**
- **Confiance** : Un **intervalle de confiance à 95 %** pour la variance signifie que si l'on répétait l'expérience de nombreuses fois, environ 95 % des intervalles calculés contiendraient la véritable variance de la population.
- **Exemple** : Si l'intervalle de confiance pour la variance est \( [4.5, 8.2] \), cela signifie que nous sommes confiants à 95 % que la véritable variance de la population se situe entre 4.5 et 8.2.

---

### **Pourquoi utiliser la distribution chi-carré ?**

La **distribution chi-carré** est utilisée dans l'estimation de la variance car elle est liée à la somme des carrés des variables aléatoires normales indépendantes. Plus précisément :

- **Pour une population normale**, la statistique \( \frac{(n-1)S^2}{\sigma^2} \) suit une loi du chi-carré avec \( n-1 \) degrés de liberté. 
- Cela signifie que **l'estimation de la variance** à partir de l'échantillon suit cette distribution, ce qui permet de construire un intervalle de confiance à partir des quantiles de cette loi.

---

### **Conditions pour utiliser cet intervalle de confiance :**
- **La population doit suivre une loi normale**. Si cette condition est remplie, la statistique suit une distribution du chi-carré et permet d'obtenir un intervalle de confiance fiable.
- Si la population **n'est pas normale**, l'estimation de la variance peut être biaisée, et les résultats peuvent ne pas être aussi fiables.

---

### **Résumé des points clés pour l'intervalle de confiance de la variance :**

1. **L'intervalle de confiance de la variance** est basé sur la **distribution du chi-carré**.
2. **Formule** : L'intervalle pour la variance \( \sigma^2 \) est :
   $$
   \left[ \frac{(n-1)S^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)S^2}{\chi^2_{1-\alpha/2, n-1}} \right]
   $$
3. **Hypothèse de normalité** : La population doit suivre une loi normale pour que l'intervalle de confiance soit valide.
4. **Interprétation** : L'intervalle de confiance donne un intervalle dans lequel la vraie variance de la population est estimée se situer avec un certain niveau de confiance (ex. 95 %).

---

### **Exemple :**
Supposons qu'un échantillon de taille \( n = 25 \) a une variance d'échantillon de \( S^2 = 10 \). Pour un niveau de confiance de 95 %, avec 24 degrés de liberté, les quantiles de la distribution chi-carré sont \( \chi^2_{0.025, 24} = 13.848 \) et \( \chi^2_{0.975, 24} = 36.415 \).

L'intervalle de confiance pour la variance serait :
$$
IC = \left[ \frac{(25-1) \times 10}{36.415}, \frac{(25-1) \times 10}{13.848} \right] = [6.56, 17.16]
$$
Cela signifie que, avec 95 % de confiance, la véritable variance de la population se situe entre 6.56 et 17.16.
