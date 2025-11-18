# A3-montanha-filmes
📽️ API de Recomendação de Filmes
FastAPI + Machine Learning (Collaborative & Content-Based Filtering)

Este projeto implementa uma API de recomendação de filmes utilizando FastAPI e dois métodos principais:

Filtragem Colaborativa (com base nas avaliações dos usuários)

Content-Based (com base em gêneros, elenco, descrição e tags)

A API carrega os dados, treina os modelos e disponibiliza rotas para recomendação.

📁 Estrutura do Projeto
A3-montanha-filmes/
│── main.py
│── requeriments.txt
│── README.md
│
└── data/
     ├── Filmes.csv
     ├── Ratings.csv
     ├── Dados.csv
     └── Tags.csv


Certifique-se de que a pasta data/ está no mesmo nível do arquivo main.py.

🚀 Como Rodar o Projeto Localmente

Abaixo está o passo a passo completo para rodar a API:

1️⃣ Crie o ambiente virtual
Windows (PowerShell):
python -m venv .venv


Ative o ambiente:

& .\.venv\Scripts\Activate.ps1

2️⃣ Instale as dependências

Certifique-se de que o arquivo requeriments.txt está na raiz do projeto:

pip install -r requeriments.txt

3️⃣ Execute a API com Uvicorn

No terminal ativado com o ambiente virtual:

uvicorn main:app --reload


A API estará acessível em:

👉 http://127.0.0.1:8000

👉 Documentação automática (Swagger): http://127.0.0.1:8000/docs

👉 Documentação alternativa (Redoc): http://127.0.0.1:8000/redoc

🔧 Funcionamento Interno

Ao iniciar, a API:

Carrega os CSVs da pasta /data

Prepara os dados para:

Filtragem colaborativa (matriz usuário × filme)

Filtragem por conteúdo (TF-IDF)

Calcula as matrizes de similaridade via cosine_similarity

Armazena tudo em memória para respostas rápidas

🔌 Endpoints Disponíveis
✔️ GET /

Retorna mensagem inicial da API.

Exemplo:
GET http://127.0.0.1:8000/

🎞️ GET /recomendacao/colaborativa/{nome_filme}

Recomenda filmes usando ratings de usuários.

Exemplo:
GET http://127.0.0.1:8000/recomendacao/colaborativa/Toy Story


Retorno:

{
  "filme_origem": "Toy Story",
  "metodo": "Colaborativo (User Ratings)",
  "recomendacoes": {
      "Toy Story 2": 0.92,
      "A Bug's Life": 0.87,
      ...
  }
}

🎬 GET /recomendacao/conteudo/{nome_filme}

Recomenda filmes com base em gênero, elenco, sinopse e tags.

Exemplo:
GET http://127.0.0.1:8000/recomendacao/conteudo/Avatar

🔄 Requisitos dos Arquivos CSV

A API espera arquivos com nomes exatamente iguais aos abaixo:

Filmes.csv

Ratings.csv

Dados.csv

Tags.csv

Eles devem estar na pasta:

data/

🛠️ Tecnologias Utilizadas

FastAPI

Uvicorn

Pandas

NumPy

Scikit-Learn

TfidfVectorizer

cosine_similarity

CORS Middleware

📌 Observações Importantes
✔️ A API carrega tudo ao iniciar

O processamento inicial pode levar alguns segundos.

✔️ O CORS está liberado para Live Server

Portas permitidas:

http://127.0.0.1:5500

http://localhost:5500

http://127.0.0.1:8000

🧪 Testando a API
