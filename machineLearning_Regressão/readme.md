🧪 Lab01 - Machine Learning

https://ml.azure.com/
O Azure Machine Learning (Azure ML) é um serviço de nuvem que permite aos desenvolvedores e cientistas de dados construir, treinar e implantar modelos de machine learning de forma escalável e eficiente. Ele oferece uma variedade de recursos, incluindo o provisionamento de infraestrutura, gerenciamento de dados, treinamento de modelos, experimentação, monitoramento e implantação de modelos em produção. Com o Azure ML, os usuários podem explorar e implementar algoritmos de machine learning, realizar análises avançadas e criar soluções personalizadas para uma variedade de cenários de negócios.

Seguindo os passos da documentação é possível facilmente criar o laboratório de Machine Learning Automatizado mostrado no curso "Trabalhando com Machine Learning na Prática no Azure ML"
No Azure Portal, ir em "Create a resource" e buscar por "Machine learning"
Preencher os campos de criação conforme suas preferências de nome
create-ml-resource

Quando a validação acabar, vá em "Create" e assim o resource terá sido criado. Após esses passos, clique no botão "Launch studio" para ir ao Studio de IA do Azure
launch-studio

Dentro do Studio vá até "ML Automatizado" para criar um Novo Trabalho de Machine Learning Automatizado
Nessa etapa deve ser configurado o job, usando as seguintes configurações básicas:
Configurações básicas:
Nome do trabalho: mslearn-bike-automl
Novo nome do experimento: mslearn-bike-rental
Descrição: Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
Tags: nenhuma
Tipo de tarefa e dados:
Tipo de tarefa: Regressão
Conjunto de dados:
Nome: bike-rentals
Descrição: Dados históricos de aluguel de bicicletas
Tipo: Tabular
Fonte de dados: De arquivos da web
URL da web: https://aka.ms/bike-rentals
Pular validação de dados: não
Configurações da tarefa:
Tipo de tarefa: Regressão
Conjunto de dados: bike-rentals
Coluna alvo: Aluguéis (inteiro)
Configurações adicionais:
Métrica primária: Erro médio quadrático normalizado
Explicar o melhor modelo: Não selecionado
Usar todos os modelos suportados: Não selecionado
Modelos permitidos: RandomForest e LightGBM
Limites:
Máximo de tentativas: 3
Máximo de tentativas simultâneas: 3
Máximo de nós: 3
Limiar de pontuação da métrica: 0.085
Tempo limite: 15
Tempo limite da iteração: 15
Ativar término antecipado: Selecionado
Validação e teste:
Tipo de validação: Divisão de treinamento-validação
Porcentagem de dados de validação: 10
Conjunto de dados de teste: Nenhum
Computação:
Tipo de computação: Serverless
Tipo de máquina virtual: CPU
Nível da máquina virtual: Dedicado
Tamanho da máquina virtual: Standard_DS3_V2*
Número de instâncias: 1
Na aba "Modelos" o modelo estará disponível

Criar o ponto de extremidade na aba "Pontos de extremidade" para realizar testes

Clicando em "Create" vai abrir um formulário pra sincronizar com o modelo criado anteriormente, após selecionar, o processo de criação de ponto de extremidade começará. Esse processo pode demorar, basta aguardar.
create-point-tests

Testando o Modelo
Para testar o modelo, vá na aba "Testes"
Substituia o template de json que está no input para o seguinte:
{
  "input_data": { 
    "data": [
      {
        "day": 1,
        "mnth": 1,   
        "year": 2022,
        "season": 2,
        "holiday": 0,
        "weekday": 1,
        "workingday": 1,
        "weathersit": 2, 
        "temp": 0.3, 
        "atemp": 0.3,
        "hum": 0.3,
        "windspeed": 0.3 
      }
    ]    
  },   
  "GlobalParameters": 1.0
}
Ao testar usando o json, é necessário alterar o "Inputs" do template e doc para "input_data", como está no json acima
Após isso, clicando no botão de testar o resultado será mostrado:
