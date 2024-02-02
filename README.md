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
      - <a href="#1.2">2- Qual o tipo de papel é mais negociado levando em conta a proporção da quantidade de papeis?</a>
      - <a href="#1.3">3. Qual a variação percentual dos papéis por tipo?</a>
      - <a href="#1.4">4. Qual a média de negociação dentro de cada setor?</a>
      - <a href="#1.5">5. Qual a disposição dos dados nas colunas 'volume', 'close' e 'market_cap'?</a>
    - <a href="#2.0">Questões Específicas</a>
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

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/5043830e-e3be-41ff-9e78-6909a74e0cdb)

### 1.2 Qual o tipo de papel é mais negociado levando em conta a proporção da quantidade de papeis?
Com esta análise é possível observar que os 3 tipos de papeis tem uma quantidade razoavelmente próxima de papeis disponíveis no mercado, porém, quando se trata de volume negociado as ações se destacam totalmente, sendo os papeis mais negociados da bolsa.

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/735d4ddd-035e-400d-b82b-d5da0f39ca7e)


### 1.3 Qual a variação percentual dos papéis por tipo?
Aqui é possivel verificar os 'outliers' de variação percentual para cada tipo de papel. Para garantir uma boa vizualização, fixei o range de visualização para 40 pontos percentuais (de -20% a 20%), para papéis que utrapassem esse valor percentual será realizado outras análises abaixo.

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/6403adb1-721c-4b25-a426-d1fea9e51c2d)

### 1.4 Qual a média de negociação dentro de cada setor?

![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/34e1e11c-47b6-4018-9192-fe9ab6844b7f)

### 1.5 Qual a disposição dos dados nas colunas 'volume', 'close' e 'market_cap'?
Após responder essa pergunta verifiquei que os dados desses campos contém valores muito espaçados e concentrados em faixas específicas.    
Para tratar essas questões estou estudando algumas formas de segmentar esses dados, sendo elas:    
- **Utilização de Percentis**    
- **Transformação Logarítmica**    
    
![image](https://github.com/MateusNaza/Analise_de_acoes_com_bibliotecas_python/assets/127886025/4d106fd7-32ea-4824-8cf0-76faed941b6d)

## 2.0 Questões específicas de cada tipo de papel

## Próximos_passos
Pretendo elaborar questões específicas de papeis do tipo 'Ação', pois é o que mais me interessa dentro dessa análise. Porém, para prosseguir com as análises vou precisar tratar os campos 'volume', 'close' e 'market_cap'.    
Já estou estudando as maneiras como posso tratar desses campos e provavelmente esse será meu próximo passo.    

**Questões que ainda quero responder:**    
- Existe alguma relação entre o preço da ação ('close') e o volume negociado ('volume')?
- Quais foram as ações que mais subiram no dia? E as que mais caíram?
- Quais foram os setores que mais subiram no dia? E os que mais caíram?
- Existe alguma correlação entre uma determinada ação e seu setor?
- Existe alguma correlação entre setores?
- Quanto o mercado fracionado impacta quando comparado ao mercado tradicional? (ainda vou planejar em qual indicador posso medir) 
