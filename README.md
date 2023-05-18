# Grafico-de-barras
---
title: "Graficos de barras"
author: "Ainoha Jimenez"
format: html
editor: visual
---
# Introduccion 
Este documento contiene visualizaciones de datos elaborados con los paquetes ggplot2 y plotly de R.

# Carga de paquetes
```{r}
#| label: carga-paquetes
#| warning: false

library(tidyverse)
library(plotly)
library(DT)
library(gapminder)
library(ggthemes)
library(hrbrthemes)
library(palmerpenguins)
```
#Grafico de barras

```{r}
grafico_barras_ggplot2 <-
gapminder |>
  filter(year == 2007) |>
  ggplot(aes(x = continent)) +
  geom_bar(
    aes(
      text = paste0(
        "Cantidad de países: ", after_stat(count)
      )
    ),    
  ) +
  ggtitle("Cantidad de países por continente") +
  xlab("Continente") +
  ylab("Cantidad de países") +
  labs(caption = "Fuente: Gapminder.org") +
  theme_economist()

# Gráfico de barras plotly
ggplotly(grafico_barras_ggplot2, tooltip = "text") |> 
  config(locale = 'es')
```

```{r}
grafico_barras_ggplot2 <-
gapminder |>
  filter(year == 2007) |>
  ggplot(aes(x = fct_infreq(continent))) +
  geom_bar(
    aes(
      text = paste0(
        "Cantidad de países: ", after_stat(count)
      )
    )    
  ) +
  ggtitle("Cantidad de países por continente") +
  xlab("Continente") +
  ylab("Cantidad de países") +
  labs(caption = "Fuente: Gapminder.org") +
  theme_solarized()

# Gráfico de barras plotly
ggplotly(grafico_barras_ggplot2, tooltip = "text") |> 
  config(locale = 'es')
```

#Diamantes grafico

```{r}
grafico_barras_ggplot2 <-
diamonds |>
  ggplot(aes(x = fct_rev(cut))) +
  geom_bar(
    aes(
      text = paste0(
        "Cantidad de diamantes: ", after_stat(count)
      )
    )
  ) +
  ggtitle("Cantidad de diamantes por corte") +
  xlab("Corte") +
  ylab("Cantidad de diamantes") +
  theme_economist()

# Gráfico de barras plotly
ggplotly(grafico_barras_ggplot2, tooltip = "text") |> 
  config(locale = 'es')
```

