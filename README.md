# Analise de ações utilizando bibliotecas Python 📊
Estou realizando uma análise de mercado com Ações, Fundos e BDR's da Bolsa de Valores Brasileira(B3). 
O projeto ainda está em andamento, e conforme for progredindo irei atualizando esse repo.

## Indice  
- <a href="#Ferramentas">Ferramentas</a>  
- <a href="#Extração">Extração dos Dados</a> 
- <a href="#Limpeza">Limpeza de Dados</a>  

## Ferramentas
Utilizei para rodar os códigos o ambiente Databricks e as Libs que usei foram:
- Pandas
- Matplotlib
- Seasborn


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
