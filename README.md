# ACIDENTES DE TRÂNSITO
## PROJETO DE ANALISE DE DADOS ESTÁCIO

[![NPM](https://img.shields.io/npm/l/react)](https://github.com/Macaulylimacode/projetoestacio/blob/main/LICENSE) 

# Sobre o projeto

Uma possível solução poderia interessar a diversos grupos, como por exemplo: motoristas, órgãos públicos, 
concessionárias de rodovias e empresas do segmento logístico. A partir disso, algumas perguntas aparecem dentro deste contexto:
° Onde podemos alocar investimentos e recursos de forma a aumentar a segurança nas estradas?
° Neste momento, quais os pontos mais prováveis de ocorrer um acidente? 
° Dado um acidente qualquer, podemos prever a gravidade do acidente?

Como é possivel observar no gráfico abaixo, possuimos diversas variáveis nulas. Poderiamos, para solucionar esse problema,
apenas dropar os valores, porém o gráfico nos mostra que grande parte dos dados faltantes não possuem relação com a falta
de outras colunas, o que iria gerar uma perda grande de dados no nosso dataset. Assim sendo, optamos por tratar esses dados.


![1](https://github.com/Macaulylimacode/projetoestacio/blob/main/Captura%20de%20tela%202024-05-01%20191804.png)



Em relação as colunas tracado_via quanto sexo, possuimos uma quantidade de dados relevantes, e os mesmos serão tratados. Assim,
chegamos na conclusão de substituir os dados faltantes de forma igualitária, onde os dados faltantes irão receber proporcionalmente
valores conforme os já preenchidos corretamente (não nulos).
Sabendo a proporção de dados presentes no dataset, precisamos saber qual será o valor necéssario em cada variável para continuar com
a mesma proporção. Sabendo que teremos 65676 dados para serem substituidos.
Criamos um nova variavel, para receber as mudanças, que receberá o nome temp. 
```bash
temp = df_ind.copy()
```
Então, para resolver o problema, foi desenvolvido uma função com a intenção de substituir os valores de forma aleatória no nosso dataset,
para assim, não ser gerado nenhum viés durante a reposição de dados
```bash
def replace_randomly_nan(df_to_replace,column,new_value,size_to_replace):
    
    df_sample_na = df_to_replace.loc[df_to_replace[column].isnull(),column].sample(size_to_replace).copy()

    for i in df_sample_na.index:
        #print(i)
        df_to_replace.loc[df_to_replace.index == i,column] = new_value
```
Como nossa função obteve sucesso, a mesma foi utilizada para as outras variáveis. Onde era preciso substituir: 
* Curva                    11320.0
* Interseção de vias        3571.0
* Desvio Temporário         2089.0
* Rotatória                 1381.0
* Retorno Regulamentado      835.0
* Viaduto                    495.0
* Ponte                      411.0
* Túnel                       70.0   4      71.0

![1](https://github.com/Macaulylimacode/projetoestacio/blob/main/Captura%20de%20tela%202024-05-01%20191917.png)

Assim, concluimos a limpeza dos nosso dados, e também a correção dos dados que apresentaram algum tipo de problema.

![1](https://github.com/Macaulylimacode/projetoestacio/blob/main/Captura%20de%20tela%202024-05-01%20192002.png)

![visual](https://img.shields.io/badge/Visual_Studio-5C2D91?style=for-the-badge&logo=visual%20studio&logoColor=white)              ![python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
