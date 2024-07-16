Análise de Séries Temporais com R
Este repositório contém um guia passo-a-passo para análise de séries temporais usando o conjunto de dados AirPassengers no R. O código a seguir aborda desde a visualização inicial dos dados até a previsão utilizando modelos ARIMA e de suavização exponencial.

Instalação de Pacotes e Carregamento da Biblioteca
Primeiro, instale e carregue a biblioteca forecast:

r

install.packages("forecast")
library(forecast)
Visualização Inicial dos Dados
Os dados AirPassengers são uma série temporal de números mensais de passageiros de uma companhia aérea dos anos 1949 a 1960.

r
Copiar código
AirPassengers
start(AirPassengers)
end(AirPassengers)
frequency(AirPassengers)
Para visualizar a série temporal:

r

plot(AirPassengers)
Podemos agregar os dados por ano e plotar novamente:

r

plot(aggregate(AirPassengers))
Extraindo Subconjunto dos Dados
Vamos extrair e visualizar apenas os dados de 1960:

r

subst = window(AirPassengers, start=c(1960,1), end=c(1960,12))
subst
plot(subst)
Decomposição da Série Temporal
A decomposição da série temporal separa a série nos componentes: sazonal, tendência e ruído.

r
o
dec = decompose(AirPassengers)
dec
Para visualizar os atributos da decomposição:

r

attributes(dec)
dec$seasonal
Visualizando os componentes da decomposição:

r

plot(dec)
plot(dec$x)
plot(dec$seasonal)
plot(dec$trend)
plot(dec$random)
Suavização Exponencial
Aplicamos a suavização exponencial à série:

r
Copiar código
ets = ets(AirPassengers)
ets
Previsão com Suavização Exponencial
Fazemos a previsão para os próximos 12 meses:

r

previsao = forecast(ets, h=12)
plot(previsao)
previsao
Modelo ARIMA
Ajustamos um modelo ARIMA automaticamente:

r

arima = auto.arima(AirPassengers)
arima
Previsão com ARIMA
Fazemos a previsão para os próximos 12 meses utilizando o modelo ARIMA:

r

previsao = forecast(arima, h=12)
plot(previsao)
previsao
Conclusão
Este repositório fornece um guia básico para iniciar com análise de séries temporais no R. Sinta-se à vontade para explorar e modificar o código conforme necessário para atender às suas necessidades de análise.

Siga as instruções comentadas no código para executar cada bloco de comandos. Utilize Ctrl + Shift + Enter para executar blocos de código em RMarkdown.

Espero que este guia seja útil e facilite suas análises de séries temporais!
