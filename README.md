# cubo_gelatinoso
<img width="2480" height="254" alt="Cabecalho 3" src="https://github.com/user-attachments/assets/14f721de-0601-4f8d-9782-06dc02ec0d44" />
<h1 align="center">Classificação de Doença Cardíaca com k-NN</h1> <h4 align="center">Isabela Leme Cruz</h4> <h4 align="center">Turma 26 - 2°Semestre</h4> <h4 align="center">Ilum Escola de Ciência (CNPEM)</h4> <p style="text-align: justify;">Esse projeto corresponde à primeira entrega ("Cubo Gelatinoso") da disciplina Aprendizado de Máquina, ministrada pelo professor doutor Daniel Roberto Cassar no 2° semestre de 2026.</p>
Descrição do projeto
<p style="text-align: justify;">O projeto consiste no estudo do desempenho de modelos de k-vizinhos mais próximos (k-NN) aplicados à predição de doença cardíaca, utilizando o dataset Heart Disease (Cleveland), disponibilizado pelo UCI Machine Learning Repository.<br> São avaliados o efeito de diferentes estratégias de pré-processamento (normalização dos atributos numéricos e codificação dos atributos categóricos) e de diferentes hiperparâmetros do k-NN (número de vizinhos e função de distância) sobre o desempenho do modelo, sempre comparando os resultados com um modelo baseline.<br> Ao todo, mais de 10 combinações de hiperparâmetros são testadas, com o desempenho avaliado por meio de acurácia e matriz de confusão, dada a problemática de falsos negativos no contexto clínico.</p>
Notebooks e arquivos do projeto
<p style="text-align: justify;">README.md: Descrição do projeto.<br> heart_disease_knn.ipynb: Notebook contendo toda a análise, desde o carregamento dos dados até as conclusões, com explicações em células de texto ao longo do código.</p>
Funcionamento
Carregamento e descrição dos dados
<p style="text-align: justify;">O dataset é carregado a partir do arquivo processed.cleveland.data do UCI Machine Learning Repository, com 303 pacientes e 13 atributos (clínicos e demográficos), além do target indicando presença de doença cardíaca.</p>
Análise exploratória de dados (EDA)
<p style="text-align: justify;">São analisadas as distribuições dos atributos numéricos e categóricos, o balanceamento das classes do target, as correlações entre atributos numéricos e a presença de outliers, relacionando essas observações às decisões de pré-processamento tomadas nas etapas seguintes.</p>
Divisão treino/teste e pré-processamento
<p style="text-align: justify;">Os dados são divididos em treino e teste de forma estratificada, preservando a proporção de classes. Em seguida, são testadas diferentes estratégias de normalização dos atributos numéricos (sem normalizar, MinMaxScaler e StandardScaler) e de codificação dos atributos categóricos (one-hot encoding e ordinal encoding), sempre ajustando as transformações apenas nos dados de treino para evitar vazamento de dados.</p>
Modelo baseline
<p style="text-align: justify;">Um modelo de referência simples é treinado para servir como piso mínimo de comparação, permitindo avaliar se o k-NN está de fato aprendendo padrões úteis a partir dos atributos.</p>
Treinamento e comparação de hiperparâmetros do k-NN
<p style="text-align: justify;">O k-NN é treinado variando o número de vizinhos, a função de distância, a estratégia de normalização e a estratégia de codificação categórica, comparando o desempenho de cada combinação com o baseline e entre si.</p>
Conclusões e principais aprendizados
<p style="text-align: justify;">A última seção do notebook discute qual combinação de pré-processamento e hiperparâmetros obteve o melhor desempenho, relacionando os resultados às características observadas na análise exploratória.</p>
Bibliotecas utilizadas e versão do Python
pandas
<p style="text-align: justify;">Usada para carregamento, manipulação e organização dos dados em DataFrames.</p>
numpy
<p style="text-align: justify;">Usada para operações numéricas auxiliares ao longo da análise.</p>
matplotlib e seaborn
<p style="text-align: justify;">Usadas para a geração de todos os gráficos do projeto (distribuições, correlações, matrizes de confusão e comparações de desempenho).</p>
scikit-learn
<p style="text-align: justify;">Usada para divisão treino/teste, normalização (StandardScaler, MinMaxScaler), codificação categórica (OneHotEncoder, OrdinalEncoder), treinamento dos modelos (KNeighborsClassifier, modelo baseline) e cálculo das métricas de desempenho.</p>
Versão do Python usada

Python 3.x [preencher com a versão exata utilizada]

Pré-requisitos e como rodar o projeto
<p style="text-align: justify;">Para executar o notebook, instale as bibliotecas necessárias rodando o comando abaixo:</p>
pip install pandas numpy matplotlib seaborn scikit-learn
<p style="text-align: justify;">e após isso clone o projeto usando o seguinte comando:</p>
git clone [link do seu repositório aqui]
Descrição do uso de IA neste trabalho
<p style="text-align: justify;">[Preencher com o detalhamento real de como ferramentas de IA foram utilizadas na construção dos textos e códigos deste trabalho — esta seção é obrigatória segundo o enunciado da disciplina.]</p>
Melhorias futuras
<p style="text-align: justify;">Como possíveis melhorias futuras, seria interessante testar outras funções de distância além das já avaliadas, aplicar validação cruzada em vez de uma única divisão treino/teste, e comparar o k-NN com outros algoritmos de classificação.</p>
<img width="1664" height="215" alt="Rodape 3" src="https://github.com/user-attachments/assets/2f033fd0-b1f5-4720-9625-f158f5e865c6" />
