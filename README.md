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
      - <a href="#1.2">2. Qual a variação percentual dos papéis por tipo?</a>
      - <a href="#1.3">3. Qual a média de negociação dentro de cada setor?</a>
    - <a href="#2.0">Questões Específicas</a> 
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

## 1.0
Questões Gerais dos dados
### 1.1 
Quantos papeis tem por cada setor e tipo de papel? (Ação, BDR, Fundo)

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/5043830e-e3be-41ff-9e78-6909a74e0cdb)

### 2.1 Qual a variação percentual dos papéis por tipo?
Aqui é possivel verificar os 'outliers' de variação percentual para cada tipo de papel. Para garantir uma boa vizualização, fixei o range de visualização para 40 pontos percentuais (de -20% a 20%), para papéis que utrapassem esse valor percentual será realizado outras análises abaixo.

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/6403adb1-721c-4b25-a426-d1fea9e51c2d)

### 3.1 Qual a média de negociação dentro de cada setor?

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/34e1e11c-47b6-4018-9192-fe9ab6844b7f)

## 2.0 Questões específicas de cada tipo de papel
