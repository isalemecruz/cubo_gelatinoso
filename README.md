<img width="2480" height="254" alt="Cabeçalho" src="https://github.com/user-attachments/assets/14f721de-0601-4f8d-9782-06dc02ec0d44" />

<h1 align="center">Classificação de Doença Cardíaca com k-NN</h1>

<h4 align="center">Isabela Leme Cruz</h4>
<h4 align="center">Turma 26 — 2° Semestre</h4>
<h4 align="center">Ilum Escola de Ciência (CNPEM)</h4>

<p align="justify">
Este projeto corresponde à primeira entrega da disciplina <strong>Aprendizado de Máquina</strong>, denominada "Cubo Gelatinoso", ministrada pelo professor doutor Daniel Roberto Cassar, no 2° semestre de 2026.
</p>

---

<h2>📖 Introdução</h2>

<p align="justify"> As doenças cardiovasculares estão entre as principais causas de mortalidade no mundo, tornando relevante o desenvolvimento de métodos capazes de auxiliar na identificação de possíveis casos a partir de informações clínicas. Nesse contexto, técnicas de <strong>aprendizado de máquina</strong> podem ser utilizadas para identificar padrões nos dados e realizar classificações. </p>

<p align="justify"> Este projeto investiga a aplicação do algoritmo <strong>k-vizinhos mais próximos (k-NN)</strong> na classificação de pacientes quanto à presença ou ausência de doença cardíaca, utilizando o conjunto de dados <strong>Heart Disease (Cleveland)</strong>, disponibilizado pelo UCI Machine Learning Repository. </p>
<h2>📌 Descrição do projeto</h2>

<p align="justify">
O projeto consiste no estudo do desempenho de modelos de <strong>k-vizinhos mais próximos (k-NN)</strong> aplicados à predição de doença cardíaca, utilizando o dataset <strong>Heart Disease (Cleveland)</strong>, com 303 pacientes e 13 atributos clínicos e demográficos, disponibilizado pelo UCI Machine Learning Repository.
</p>

<p align="justify">
O target original, denominado <code>num</code>, possui 5 níveis de gravidade. Para este trabalho, ele foi binarizado em duas classes: <strong>"com doença"</strong> e <strong>"sem doença"</strong>, resultando em uma base relativamente balanceada, com aproximadamente 54% dos pacientes sem doença e 46% com doença.
</p>

<p align="justify">
Foram avaliados quatro fatores que podem influenciar o desempenho do k-NN:
</p>

<ul>
    <li>Normalização dos atributos numéricos;</li>
    <li>Codificação dos atributos categóricos;</li>
    <li>Hiperparâmetros do algoritmo;</li>
    <li>Seleção de atributos por correlação com o target.</li>
</ul>

<p align="justify">
Para a normalização, foram comparadas as estratégias <strong>sem normalização, MinMaxScaler e StandardScaler</strong>. Para os atributos categóricos, foram testados <strong>One-Hot Encoding e Ordinal Encoding</strong>.
</p>

<p align="justify">
Também foram avaliadas diferentes combinações de hiperparâmetros, envolvendo o número de vizinhos, a função de distância e a estratégia de ponderação dos vizinhos. Ao todo, foram testadas <strong>48 combinações</strong>.
</p>

<p align="justify">
Os experimentos foram comparados entre si e com um modelo <strong>baseline</strong>. O desempenho foi avaliado principalmente por meio da <strong>acurácia</strong> e da <strong>matriz de confusão</strong>, considerando a relevância dos falsos negativos em um contexto de classificação de doença.
</p>

---

<h2>📂 Notebooks e arquivos do projeto</h2>

<ul>
    <li>
        <strong>README.md:</strong> descrição geral, metodologia, resultados e conclusões do projeto.
    </li>
    <li>
        <strong>heart_disease_knn.ipynb:</strong> notebook contendo toda a análise, desde o carregamento e exploração dos dados até o treinamento dos modelos e as conclusões, com explicações em células de texto ao longo do código.
    </li>
</ul>

---

<h2>⚙️ Funcionamento</h2>

<h3>1. Carregamento e descrição dos dados</h3>

<p align="justify">
O dataset é carregado a partir do arquivo <code>processed.cleveland.data</code>, disponibilizado pelo <strong>UCI Machine Learning Repository</strong>. A base possui 303 pacientes e 13 atributos clínicos e demográficos.
</p>

<p align="justify">
O target original (<code>num</code>) apresenta cinco níveis de gravidade. Para a classificação binária utilizada neste trabalho, os valores foram agrupados em duas categorias: <strong>presença</strong> ou <strong>ausência de doença cardíaca</strong>.
</p>

<h3>2. Análise Exploratória dos Dados (EDA)</h3>

<p align="justify">
Foi realizada uma análise exploratória para compreender as principais características do conjunto de dados. Foram analisadas as distribuições dos atributos numéricos e categóricos, estatísticas descritivas, o balanceamento das classes do target, as correlações entre os atributos numéricos e a presença de outliers.
</p>

<p align="justify">
Também foi investigada a relação entre os atributos numéricos e o target binarizado. Essas observações foram utilizadas para orientar as decisões de pré-processamento realizadas nas etapas seguintes.
</p>

<h3>3. Divisão treino/teste e pré-processamento</h3>

<p align="justify">
Os dados foram divididos em conjuntos de <strong>treino e teste de forma estratificada</strong>, preservando a proporção das classes do target.
</p>

<p align="justify">
Em seguida, foram testadas diferentes estratégias de normalização dos atributos numéricos:
</p>

<ul>
    <li>Sem normalização;</li>
    <li><code>MinMaxScaler</code>;</li>
    <li><code>StandardScaler</code>.</li>
</ul>

<p align="justify">
Para os atributos categóricos, foram comparadas duas estratégias de codificação:
</p>

<ul>
    <li><code>OneHotEncoder</code>;</li>
    <li><code>OrdinalEncoder</code>.</li>
</ul>

<p align="justify">
As transformações foram ajustadas exclusivamente nos dados de treino, evitando <strong>vazamento de dados (data leakage)</strong>.
</p>

<p align="justify">
A combinação de <strong>One-Hot Encoding + StandardScaler</strong> apresentou o melhor desempenho entre as estratégias de pré-processamento avaliadas e foi utilizada nas etapas seguintes.
</p>

<h3>4. Modelo baseline</h3>

<p align="justify">
Foi utilizado um <code>DummyClassifier</code> com a estratégia <code>most_frequent</code> como modelo baseline. Seu objetivo é estabelecer um <strong>piso mínimo de comparação</strong>, permitindo verificar se o k-NN consegue aprender padrões úteis a partir dos atributos disponíveis.
</p>

<h3>5. Treinamento e comparação de hiperparâmetros do k-NN</h3>

<p align="justify">
O algoritmo <strong>k-vizinhos mais próximos (k-NN)</strong> foi treinado utilizando diferentes combinações de hiperparâmetros.
</p>

<p align="justify">
Foram avaliados:
</p>

<ul>
    <li>Diferentes números de vizinhos (<code>k</code>);</li>
    <li>Distância euclidiana;</li>
    <li>Distância Manhattan;</li>
    <li>Distância Chebyshev;</li>
    <li><code>weights="uniform"</code>;</li>
    <li><code>weights="distance"</code>.</li>
</ul>

<p align="justify">
Ao todo, foram testadas <strong>48 combinações</strong>. O melhor resultado foi obtido utilizando <strong>k = 7, distância euclidiana e <code>weights="uniform"</code></strong>, alcançando uma acurácia de <strong>0,90</strong> no conjunto de teste.
</p>

<h3>6. Seleção de atributos por correlação</h3>

<p align="justify">
Como experimento adicional, foi testado um modelo k-NN utilizando apenas os <strong>8 atributos mais correlacionados, em módulo, com o target</strong>.
</p>

<p align="justify">
O objetivo foi investigar se a redução da dimensionalidade causada pela seleção de atributos poderia melhorar o desempenho do modelo, especialmente considerando a quantidade de variáveis geradas pelo One-Hot Encoding.
</p>

<p align="justify">
Nesse experimento, entretanto, a redução dos atributos resultou em desempenho inferior ao modelo utilizando todos os atributos.
</p>

---

<h2>📊 Resultados</h2>

<table align="center">
    <thead>
        <tr>
            <th>Experimento</th>
            <th>Acurácia</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Baseline</td>
            <td>0,53</td>
        </tr>
        <tr>
            <td>k-NN sem normalização</td>
            <td>0,68</td>
        </tr>
        <tr>
            <td>Encoding ordinal</td>
            <td>0,82</td>
        </tr>
        <tr>
            <td>One-Hot + normalização</td>
            <td>0,87</td>
        </tr>
        <tr>
            <td>k-NN com seleção de 8 atributos</td>
            <td>0,83</td>
        </tr>
        <tr>
            <td><strong>Modelo final — k = 7</strong></td>
            <td><strong>0,90</strong></td>
        </tr>
    </tbody>
</table>

---

<h2>📚 Bibliotecas utilizadas</h2>

<p align="justify">
O projeto foi desenvolvido em <strong>Python</strong>, utilizando principalmente bibliotecas do ecossistema científico e de aprendizado de máquina.
</p>

<ul>
    <li>
        <strong>matplotlib.pyplot (<code>plt</code>):</strong>
        utilizada para criar visualizações, como histogramas, boxplots e gráficos de comparação de acurácia.
    </li>

<li>
    <strong>pandas (<code>pd</code>):</strong>
    utilizada para carregamento, manipulação e organização dos dados em DataFrames.
</li>

<li>
    <strong>seaborn (<code>sns</code>):</strong>
    utilizada em conjunto com o matplotlib para criar visualizações, como histogramas por classe e mapas de calor de correlação.
</li>

<li>
    <strong>train_test_split:</strong>
    utilizada para dividir os dados em conjuntos de treino e teste de forma estratificada.
</li>

<li>
    <strong>StandardScaler e MinMaxScaler:</strong>
    utilizadas para testar diferentes estratégias de normalização dos atributos numéricos.
</li>

<li>
    <strong>OneHotEncoder e OrdinalEncoder:</strong>
    utilizadas para testar diferentes estratégias de codificação dos atributos categóricos.
</li>

<li>
    <strong>DummyClassifier:</strong>
    utilizado para estabelecer o modelo baseline e definir um parâmetro mínimo de comparação.
</li>

<li>
    <strong>accuracy_score, confusion_matrix e ConfusionMatrixDisplay:</strong>
    utilizadas para calcular e visualizar as métricas de desempenho dos modelos.
</li>

<li>
    <strong>KNeighborsClassifier:</strong>
    algoritmo principal do projeto, utilizado para treinar os modelos de k-vizinhos mais próximos.
</li>
```

</ul>



<h2>💻 Pré-requisitos e como executar</h2>

<h3>1. Instalação das bibliotecas</h3>

<p align="justify">
Para executar o notebook, é necessário possuir uma instalação do Python e instalar as bibliotecas utilizadas no projeto:
</p>

```bash
pip install pandas matplotlib seaborn scikit-learn
```

<h3>2. Clonagem do repositório</h3>

<p align="justify">
Após instalar as dependências, clone o repositório utilizando:
</p>

```bash
git clone https://github.com/isalemecruz/cubo_gelatinoso.git
```

<h3>3. Execução</h3>

<p align="justify">
Abra o arquivo <code>heart_disease_knn.ipynb</code> em um ambiente compatível com Jupyter Notebook ou JupyterLab e execute as células sequencialmente.
</p>

---

<h2>🧠 Conclusões e principais aprendizados</h2>

<p align="justify">
Neste trabalho, foram treinados e avaliados modelos de <strong>k-NN</strong> para prever a presença de doença cardíaca utilizando o dataset <strong>Heart Disease (Cleveland)</strong>. Os principais resultados e aprendizados foram:
</p>

<ul>

<li>
<p align="justify">
<strong>A normalização é essencial para o k-NN:</strong>
normalizar os atributos numéricos elevou a acurácia de <strong>0,68 para até 0,87</strong>, evidenciando a sensibilidade do algoritmo às diferenças de escala entre os atributos numéricos.
</p>
</li>

<li>
<p align="justify">
<strong>One-Hot Encoding apresentou melhor desempenho que o Ordinal Encoding:</strong>
a codificação One-Hot alcançou aproximadamente <strong>0,87</strong> de acurácia, enquanto a codificação ordinal alcançou <strong>0,82</strong>. Uma possível explicação é que o One-Hot Encoding evita a criação de relações de ordem artificiais entre categorias que não possuem uma ordem natural.
</p>
</li>

<li>
<p align="justify">
<strong>A escolha dos hiperparâmetros teve impacto significativo:</strong>
entre as 48 combinações testadas, a configuração <strong>k = 7, distância euclidiana e <code>weights="uniform"</code></strong> apresentou o melhor desempenho, com <strong>0,90 de acurácia</strong> e apenas <strong>3 falsos negativos</strong>.
</p>
</li>

<li>
<p align="justify">
<strong>A redução dos atributos por correlação não melhorou o desempenho:</strong>
a utilização dos 8 atributos mais correlacionados resultou em uma acurácia de <strong>0,83</strong>, inferior à obtida pelo modelo utilizando todos os atributos. Isso indica que atributos com correlação individual mais baixa ainda podem contribuir para a classificação quando considerados em conjunto.
</p>
</li>

<li>
<p align="justify">
<strong>O k-NN apresentou desempenho superior ao baseline:</strong>
o modelo baseline apresentou acurácia de <strong>0,53</strong> e, por utilizar a classe mais frequente, não identificou pacientes pertencentes à classe minoritária. Em um contexto de classificação de doença, esse comportamento é particularmente relevante, pois erros de classificação do tipo falso negativo podem representar a não identificação de pacientes que possuem a condição investigada.
</p>
</li>

</ul>

<p align="justify">
De forma geral, o trabalho mostrou que, para o k-NN, as decisões de <strong>pré-processamento, especialmente normalização e codificação dos atributos categóricos</strong>, tiveram impacto significativo no desempenho. Além disso, a busca sistemática por hiperparâmetros mostrou-se importante, uma vez que houve uma diferença superior a <strong>20 pontos percentuais de acurácia</strong> entre as configurações avaliadas.
</p>

---
<h3>🤖 Descrição do uso de Inteligência Artificial</h3>

<p align="justify"> Durante o desenvolvimento do projeto, utilizei o <strong>Claude</strong> como apoio no planejamento das etapas, na definição do target, no tratamento dos dados e na organização dos experimentos de k-NN. A ferramenta também auxiliou na interpretação dos resultados e na revisão das conclusões. </p>

<p align="justify"> O <strong>ChatGPT</strong> foi utilizado principalmente para revisar e organizar a documentação do projeto, incluindo este README. As sugestões das ferramentas foram analisadas e adaptadas por mim, sendo os códigos executados, os experimentos realizados e os resultados analisados por mim. </p>

<p align="justify"> O registro da conversa está no documento word anexado, já que não consegui compartilhar o lnk da conversa com o claude </p>

<p align="justify"> O <strong>ChatGPT</strong> foi utilizado principalmente para revisar e organizar a documentação do projeto, incluindo o README. As sugestões das ferramentas foram analisadas e adaptadas pelo autor. </p>

<p align="justify"> <a href="https://chatgpt.com/share/6aaf0256-cb2c-83e9-9643-f947fd71bbf2">Registro da conversa utilizada com o Chat gpt</a> </p>

---

<h2>🚀 Melhorias futuras</h2>

<p align="justify">
Como possíveis melhorias futuras, seria interessante testar outras funções de distância, utilizar <strong>validação cruzada</strong> em vez de depender de uma única divisão entre treino e teste e comparar o desempenho do k-NN com outros algoritmos de classificação.
</p>

<p align="justify">
Também poderiam ser exploradas métricas adicionais, como <strong>precisão, recall, F1-score e ROC-AUC</strong>, permitindo uma análise mais completa do comportamento do modelo, especialmente em relação aos falsos negativos.
</p>

---

<h2>📎 Repositório</h2>

<p align="center">
    <a href="https://github.com/isalemecruz/cubo_gelatinoso">
        <strong>🔗 Acessar o repositório no GitHub</strong>
    </a>
</p>

<br>

<img width="1664" height="215" alt="Rodapé" src="https://github.com/user-attachments/assets/2f033fd0-b1f5-4720-9625-f158f5e865c6" />
