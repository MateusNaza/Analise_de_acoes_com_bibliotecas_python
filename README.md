# Analise de ações utilizando bibliotecas Python 📊
Estou realizando uma análise de mercado com Ações, Fundos e BDR's da Bolsa de Valores Brasileira(B3). 
O projeto ainda está em andamento, e conforme for progredindo irei atualizando esse repo.

## Indice  
- <a href="#Ferramentas">Ferramentas</a>  
- <a href="#Extração">Extração dos Dados</a> 
- <a href="#Limpeza">Limpeza de Dados</a>  
- <a href="#Análises">Análises e Gerações de gráficos</a>
    - <a href="#1.0">Questões Gerais</a>
      - <a href="#1.1">1. Quantos papeis tem por cada setor e tipo de papel? (Ação, BDR, Fundo)</a>
      - <a href="#1.2">2. Qual o tipo de papel é mais negociado levando em conta a proporção da quantidade de papeis?</a>
      - <a href="#1.3">3. Qual a variação percentual dos papéis por tipo?</a>
      - <a href="#1.4">4. Qual a média de negociação dentro de cada setor?</a>
      - <a href="#1.5">5. Qual a disposição dos dados nas colunas 'volume', 'close' e 'market_cap'?</a>
        
    - <a href="#2.0">Questões específicas de ações</a>
      - <a href="#1.5">1. O volume diário está concentrado em quais faixas de valores?</a>

- <a href="#Próximos_passos">Próximos Passos</a>
    
## Ferramentas
Utilizei para rodar os códigos o ambiente Databricks e as Libs que usei foram:
- Pandas
- Matplotlib
- Seaborn


## Extração
Para extrair os dados utilizei a API da Brapi: https://brapi.dev/ com o seguinte EndPoint:

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/91948ec2-f67d-438e-92b3-b75840f8a9bd)


Aproveitei de resursos que esse próprio Endpoint disponibiliza para ordenar por volume de negociação e armazenei esses dados em um DataFrame Pandas.
Aqui já é possivel verificar quais foram os 10 papeis mais negociados do dia:

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/d629253d-6557-4fbf-8c55-f94ea9733ddc)


## Limpeza

### Coluna Change 📈
Tendo em vista que utilizarei futuramente análises com o campo 'Change', verifiquei se esse campo possui alguma linha nula e já tratei esse caso.

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/a6ad69cd-819b-4de5-9e94-a3639349e496)


### Colunas Sector e Type
Essas colunas continham valores em inglês, para facilitar a análise decidi mudar os valores para português.

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/6e8bbae8-3eb7-4e38-9f61-23d889fce89e)

### Coluna Stock
Existe uma classe de ativos que são vendidos em forma fracionada, no caso dessa análise essa classe não é bem vinda e pode sujar os dados analisados, então removi todos esses ativos. Eles são identificados por uma letra F ao fim do ticker, sabendo disso usei esse código para excluir esses ativos:

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/9a9a8a30-8d20-4726-a136-708bf02e8144)

## Análises

## 1.0 Questões Gerais dos dados
### 1.1 Quantos papeis tem por cada setor e tipo de papel? (Ação, BDR, Fundo)
Atravéz dessa análise é possivel visualizar como estão distribuidos os papéis dentro de cada setor, trazendo tanto a quantidade de papéis em cada setor, como também a proporção dos tipos (Ações, Fundos e BDR's).

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/9ada25e6-538a-40d9-b0fd-6260dbe4e41f)

### 1.2 Qual a distribuição dos papeis por tipo e seus respectivos volumes?
Com esta análise é possível observar que os 3 tipos de papeis tem uma quantidade razoavelmente próxima de papeis disponíveis no mercado, porém, quando se trata de volume negociado as ações se destacam totalmente, sendo os papeis mais negociados da bolsa.

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/735d4ddd-035e-400d-b82b-d5da0f39ca7e)


### 1.3 Qual a variação percentual dos papéis por tipo?
Aqui é possivel verificar os 'outliers' de variação percentual para cada tipo de papel. Para garantir uma boa vizualização, fixei o range de visualização para 40 pontos percentuais (de -20% a 20%), para papéis que utrapassem esse valor percentual será realizado outras análises abaixo.

Essa análise é interessante pois de forma rápida é possivel observar dentro de cada tipo de papel se tem alguma tendencia definida (Alta ou Baixa).

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/973958dd-a367-41e8-85e0-b2ad97a2004f)

### 1.4 Qual a média de negociação dentro de cada setor?
Com esta análise é possivel observar em ordem quais setores estão sendo mais negociados no dia.

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/8cf38742-e52e-4710-9a65-a5278480918d)

### 1.5 Qual a disposição dos dados nas colunas 'volume', 'close' e 'market_cap'?
Após responder essa pergunta verifiquei que os dados desses campos contém valores muito espaçados e concentrados em faixas específicas.    
Para tratar essas questões descobri e estudei algumas formas de segmentar esses dados, sendo elas:    
- **Utilização de Percentis**    
- **Transformação Logarítmica**

Em análises futuras, posso utilizar desses métodos para tornar mais visuais as análises dessas colunas.
    
![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/bbfc8d83-18b0-4f85-88a3-a358b00f0986)
