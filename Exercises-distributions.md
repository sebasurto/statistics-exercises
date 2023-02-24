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

- $n$ es el número de ensayos independientes

- $k$ es el número de éxitos que se desea obtener.

- $p$ es la probabilidad de éxito en cada ensayo.

- $(1-p)$ es la probabilidad de fracaso en cada ensayo.

- ${n\choose k}$ es el coeficiente binomial, que se utiliza para
  calcular el número de formas diferentes en que se pueden obtener k
  éxitos en n ensayos.

Una forma de presentar la distribución binomial en R es:

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

    **Resolución manual:** En este caso, podemos utilizar la
    distribución binomial para calcular la probabilidad de recolectar 35
    gomitas pastillas en 50 intentos. La probabilidad de elegir una
    gomita pastilla es de $\frac{80}{180} = \frac{4}{9}$ y la
    probabilidad de elegir una gomita frijol es de
    $\frac{100}{180} = \frac{5}{9}$. Entonces la probabilidad de elegir
    35 gomitas pastillas en 50 intentos sería:

    - $n$ = 50
    - $k$ = 35
    - $p$ = 4/9
    - $1-p$ = 5/9
      $$P(X=35) = {50\choose 35} {({\frac{4}{9}})}^{35} {({\frac{5}{9}})}^{15}$$

    **Código en R:**

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

    **Resolución manual:** La probabilidad de elegir un votante femenino
    es de $\frac{101}{196}$ y la de elegir un votante masculino es de
    $\frac{95}{196}$. Entonces la probabilidad de elegir 7 votantes
    femeninos en 10 intentos sería:

    - $n$ = 10
    - $k$ = 7
    - $p$ = 101/196
    - $1-p$ = 95/196

    $$P(X=7) = {10\choose 7} {({\frac{101}{196}})}^{7} {({\frac{95}{196}})}^{3}$$

    **Código en R:**

    ``` r
    p_mujer <- 101 / (101 + 95)  #Probabilidad de obtener una mujer votante
    p_mujer
    ```

        ## [1] 0.5153061

    ``` r
    p_mujeres <- dbinom(7, size = 10, prob = p_mujer)
    p_mujeres
    ```

        ## [1] 0.1318381

        ## La probabilidad de elegir 7 mujeres seleccionando 10 votantes sería:  13.18381 %

## 1.2 Distribución Poisson

La distribución de Poisson se utiliza para modelar la probabilidad de
que ocurra un número determinado de eventos en un intervalo de tiempo o
espacio específico, cuando estos eventos ocurren de manera aleatoria e
independiente.

La función de probabilidad de la distribución de Poisson se define de la
siguiente manera:

$$ P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!} $$

Donde:

- $k$ es el número de eventos que se desean contar

- $\lambda$ es el parámetro de la distribución, que representa el número
  esperado de eventos en el intervalo de tiempo o espacio

Una forma de presentar la distribución poisson en R es:

    dpois(x,lambda)

Donde:

- x es el número de eventos para el que se desea calcular la
  probabilidad.

- lambda es el parámetro de la distribución de Poisson.

### 1.2.1 Ejercicios

1)  En los últimos 100 años, ha habido 93 terremotos que miden 6.0 o más
    en la escala de Richter. ¿Cuál es la probabilidad de tener 3
    terremotos en el mismo año que todos midan 6.0 o más?

    **Resolución manual:** En este caso, necesitamos calcular la
    probabilidad de tener 3 terremotos en un año, dado que necestiamos
    la tasa de terremotos de 6.0 o más en los últimos 100 años, podemos
    calcular: $\frac{93}{100} = 0.93$ terremotos por año.

    - $k$ = 3
    - $\lambda = 0.93$ $$ P(X = 3) = \frac{e^{-0.93} 0.93^3}{3!} $$

    **Código en R:**

    ``` r
    p_terremoto <- 93 / 100  #tasa de terremotos por año
    p_terremoto
    ```

        ## [1] 0.93

    ``` r
    p_terremotos <- dpois(3, p_terremoto)
    p_terremotos
    ```

        ## [1] 0.05289367

        ## La probabilidad de que 3 terremotos en el mismo año midan más de 6.0 es:  5.289367 %

2)  El neuroblastoma, una forma rara de tumor maligno, ocurre en 11 de
    un millón de niños. En los 12,439 niños de Oak Park, Illinois, se
    reportan 4 casos de neuroblastoma. Suponiendo que no haya nada
    especial en Oak Park, donde la probabilidad de neuroblastoma es
    mayor de lo normal, encuentre la probabilidad de ver más de un caso
    de neuroblastoma en una población de este tamaño. ¿Qué es probable
    que puedas concluir?

3)  En un pequeño estanque hay 50 peces, 10 de los cuales han sido
    marcados. La captura de un pescador consta de 7 peces (suponga que
    su captura es una selección aleatoria realizada sin reemplazo).
    ¿Cuál es la probabilidad de que se capturen exactamente 2 peces
    marcados?

4)  Si el 95% de los hogares tienen TV y se encuestaron 8 casas, ¿cuál
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
