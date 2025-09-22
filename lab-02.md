Lab 02 - Plastic waste
================
kadio morokro mathieu-marie
22/09/2025

## Chargement des packages et des données

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read_csv("data/plastic-waste.csv")
```

Commençons par filtrer les données pour retirer le point représenté par
Trinité et Tobago (TTO) qui est un outlier.

``` r
plastic_waste <- plastic_waste %>%
  filter(plastic_waste_per_cap < 3.5)
```

## Exercices

### Exercise 1

tout les continents produisent généralement entre 0 et 1 kg/jour de
déchets par habitant, l’Afrique et L’Asie ont une production plus faible
car elle sont plus concentré entre 0,00 et 0,25 . l’Europe et L’Amérique
du Nord ont une production plus élevée avec davantage pays proches de 1
. l’Océanie et l’Amérique du sud ont aussi une production faible car la
majorité est concentré vers 0,25 et peu de pays vers 0,50.

``` r
ggplot(plastic_waste , aes(x=plastic_waste_per_cap)) +
  geom_histogram(binwidth = 0.2) + 
  facet_wrap(~ continent)
```

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->

### Exercise 2

``` r
ggplot(plastic_waste , aes(x=plastic_waste_per_cap, colour = continent , fill = continent ,  )) +
  geom_density(adjust=1, alpha=0.5
              )
```

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

color et fill se règle dans aes car ils sont envoyés directement sur la
variable continent et alpha dans geom_density car il concerne tout le
graphique ,une valeur constante .

### Exercise 3

Boxplot:

``` r
ggplot(plastic_waste, aes(x=continent, y=plastic_waste_per_cap)) + 
  geom_boxplot()
```

![](lab-02_files/figure-gfm/plastic-waste-boxplot-1.png)<!-- -->

Violin plot:

``` r
ggplot(plastic_waste, aes(x=continent, y=plastic_waste_per_cap)) + 
  geom_violin()
```

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

les violins plots permettent de voir la forme de la distribution
complète alors que les boxplots résument seulement la position centrale
et la dispersion .

### Exercise 4

``` r
ggplot(plastic_waste, aes(x=plastic_waste_per_cap, y=mismanaged_plastic_waste_per_cap , colour = continent )) +
  geom_point()
```

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-1.png)<!-- -->

le graphique nous montre une relation positive et à peu près linéaire
entre la production de déchets plastiques par habitant et la quantité de
déchets plastiques mal gérés par habitant . nous remarquons une tendance
positive .

### Exercise 5

``` r
ggplot(plastic_waste, aes(x=total_pop, y= plastic_waste_per_cap )) +
  geom_point()
```

    ## Warning: Removed 10 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-population-total-1.png)<!-- -->

``` r
ggplot(plastic_waste, aes(x=coastal_pop, y= plastic_waste_per_cap )) +
  geom_point()
```

![](lab-02_files/figure-gfm/plastic-waste-population-coastal-1.png)<!-- -->

non , les deux sont parreil il n’y a pas de relation claire pour les
deux graphiques .

## Conclusion

Recréez la visualisation:

``` r
# insert code here
```
