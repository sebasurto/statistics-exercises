Ejercicios de estadística discreta e inferencial en R
================

# 1 Estadística Descriptiva

## 1.1 Distribución Binomial

La distribución binomial describe el número de éxitos en una serie de
ensayos independientes y de idéntica distribución de probabilidad, cada
uno con dos posibles resultados (éxito o fracaso), con una probabilidad
de éxito p en cada ensayo. Se puede representar con la siguiente
fórmula:

$$P(X=k) = {n\choose k} p^k (1-p)^{n-k}$$

Donde:

- X es el número de éxitos en n ensayos independientes.

- k es el número de éxitos que se desea obtener.

- p es la probabilidad de éxito en cada ensayo.

- (1-p) es la probabilidad de fracaso en cada ensayo.

- ${n\choose k}$ es el coeficiente binomial, que se utiliza para
  calcular el número de formas diferentes en que se pueden obtener k
  éxitos en n ensayos.

Una forma de presentar la distribución binomial en R eso:

    dbinom(k, size = n, prob = p)

Donde:

- k es el número de éxitos que se desea obtener.

- n es el número de ensayos independientes.

- p es la probabilidad de éxito en cada ensayo.

Esta función devuelve la probabilidad de obtener exactamente k éxitos en
n ensayos independientes, cada uno con una probabilidad de éxito p.

### 1.1.1 Ejercicios

1)  Un plato de dulces contiene 100 gomitas frijolitos y 80 gomitas
    pastillas. Se recogen cincuenta caramelos al azar. ¿Cuál es la
    probabilidad de que 35 de los 50 sean gomitas pastillas?

    Resolución: En este caso, podemos utilizar la distribución binomial
    para calcular la probabilidad de recolectar 35 gomitas pastillas en
    50 intentos. La probabilidad de elegir una gomita pastilla es de
    80/180 = 4/9 y la probabilidad de elegir una gomita frijol es de
    100/180 = 5/9. Entonces la probabilidad de elegir 35 gomitas
    pastillas en 50 intentos sería:

    $$P(X=35) = {50\choose 35} {({\frac{4}{9}})}^{35} {({\frac{5}{9}})}^{15}$$

    Código en R:

    ``` r
    p_pastilla <- 80 / (100 + 80)  #Probabilidad de obtener una pastilla
    p_pastilla
    ```

        ## [1] 0.4444444

    ``` r
    p_pastillas <- dbinom(35, size = 50, prob = p_pastilla)
    p_pastillas
    ```

        ## [1] 0.0001573501

        ## La probabilidad de elegir 35 gomitas pastillas en 50 intentos sería:  0.01573501 %

2)  Un pequeño distrito electoral tiene 101 votantes femeninos y 95
    votantes masculinos. Se extrae una muestra aleatoria de 10 votantes.
    ¿Cuál es la probabilidad de que exactamente 7 de los votantes sean
    mujeres?

    Resolución:

3)  En los últimos 100 años, ha habido 93 terremotos que miden 6.0 o más
    en la escala de Richter. ¿Cuál es la probabilidad de tener 3
    terremotos en el mismo año que todos midan 6.0 o más?

4)  El neuroblastoma, una forma rara de tumor maligno, ocurre en 11 de
    un millón de niños. En los 12,439 niños de Oak Park, Illinois, se
    reportan 4 casos de neuroblastoma. Suponiendo que no haya nada
    especial en Oak Park, donde la probabilidad de neuroblastoma es
    mayor de lo normal, encuentre la probabilidad de ver más de un caso
    de neuroblastoma en una población de este tamaño. ¿Qué es probable
    que puedas concluir?

5)  En un pequeño estanque hay 50 peces, 10 de los cuales han sido
    marcados. La captura de un pescador consta de 7 peces (suponga que
    su captura es una selección aleatoria realizada sin reemplazo).
    ¿Cuál es la probabilidad de que se capturen exactamente 2 peces
    marcados?

6)  Si el 95% de los hogares tienen TV y se encuestaron 8 casas, ¿cuál
    es la probabilidad de que más de 6 tengan TV?

# 2 Estadística inferencial

## 2.1 GitHub Documents

1)  
2)  

## 2.2 Including Code

You can include R code in the document as follows:

``` r
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

## 2.3 Including Plots

You can also embed plots, for example:

![](Exercises-distributions_files/figure-gfm/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.
