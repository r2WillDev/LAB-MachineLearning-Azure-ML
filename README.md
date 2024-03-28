# LAB-MachineLearning-Azure-ML
Neste exercício, você usará o recurso de machine learning automatizado no Azure Machine Learning para treinar e avaliar um modelo de machine learning. Em seguida, você implantará e testará o modelo treinado.

## Criando um Azure Machine Learning Workspace
Para usar o Azure Machine Learning, crie um espaço de trabalho no Azure e acesse o Azure Machine Learning Studio para gerenciar recursos.

> [!TIP]
> Se você já tiver um espaço de trabalho do Azure Machine Learning, poderá usá-lo e pular para a próxima tarefa.

1. Entre no portal do [Azure]( https://portal.azure.com) e usando suas credenciais da Microsoft, Caso não tenha uma conta Microsoft, crie uma e continue o passo a passo.
2. Selecione "**+ Create a resource**" ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/bf711bd3-ca8f-430f-8c11-2ffe4f9f6c3b)
  - Procure por _Machine Learning_ ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/24932236-f06e-4937-913e-38b49c4f15eb)
  - Crie um novo recurso **Azure Machine Learning** ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/0f39fa37-1193-486d-afe8-f5b414f8b601)
  - Coloque as Seguintes configurações:
    - **Subscription:** Sua assinatura do Azure.
    - **Resource Group:** Crie ou selecione um Resouce Group.
    - **Name:** Insira um nome exclusivo para seu espaço de trabalho.
    - **Region:** Selecione a região geográfica mais próxima.
    - **Storage account:** Observe a nova conta de armazenamento padrão que será criada para seu workspace.
    - **Key vault:** Observe o novo cofre de chaves padrão que será criado para seu workspace.
    - **Application insights:** Observe o novo recurso padrão de insights de aplicativo que será criado para seu workspace.
    - **Container registry:** Nenhum (um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner).
  - Observe o Exemplo abaixo: ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/e2b134db-c301-40c5-bcca-e23a721e077a)
3. Selecione **Review + create** e selecione **Create**. Aguarde a criação do seu espaço de trabalho (pode demorar alguns minutos) e, em seguida, vá para o recurso implantado. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/535c31d4-e955-4f46-9763-34086aefeac3)
4. Selecione **Launch Studio** (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no Azure Machine Learning Studio usando sua conta da Microsoft). Feche todas as mensagens exibidas.![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/7db2daa6-34db-4d5c-b874-43a3ad959f22)
5. No estúdio Azure Machine Learning, você deverá ver seu espaço de trabalho recém-criado. Caso contrário, selecione **All workspaces** no menu à esquerda e selecione o espaço de trabalho que você acabou de criar. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/811625b8-9d16-4c35-9c2d-b76b8021e053)

## Use Automated Machine learning para treinar um modelo
O aprendizado de máquina automatizado permite que você experimente vários algoritmos e parâmetros para treinar vários modelos e identificar o melhor para seus dados. Neste exercício, você usará um conjunto de dados de detalhes históricos de aluguel de bicicletas para treinar um modelo que prevê o número de aluguel de bicicletas esperado em um determinado dia,
com base em características sazonais e meteorológicas.

> [!NOTE]
> Os dados utilizados neste exercício são derivados da [Capital Bikeshare](https://capitalbikeshare.com/system-data) e são utilizados de acordo com o [contrato de licença de dados](https://ride.capitalbikeshare.com/data-license-agreement) publicado.

1. No [Azure Machine Learning studio](https://ml.azure.com/home), veja a página **Automated ML** (em **Criação**). ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/878b4301-8c45-4b3b-8411-043219b5d3df)
2. Crie um novo trabalho de ML automatizado com as seguintes configurações:
  - **Basic Settings**
     - **Job name:** mslearn-bike-automl
     - **New experiment name:** mslearn-bike-rental
     - **Description:** Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
     - **Tags:** None
     - **Exemplo:** ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/b3a7e52d-ea9e-43bb-b83a-43a02808ab1e)
  - **Task type & data**
    - **Select task type:** Regression ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/5f4c08fa-1f4e-4637-a4cf-efe2716f5a7a)

    - **Select dataset:** Crie um novo dataset com as seguintes configurações:
      - **Data type:**
        - **Name:** bike-rentals
        - **Description:** Dados históricos de aluguel de bicicletas
        - **Type:** Tabular ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/255a2042-40cf-4fb9-b7ea-59c52ac894a4)
      - **Data Source:**
        - Selecione **From web files** ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/2d2b4cb0-da8f-499d-83a6-ae31a272ae62)
      - **Web URL:**
         - **Web URL:** https://aka.ms/bike-rentals
         - Skip data validation: _Não Selecione_ ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/fd3642a4-748d-4001-9aff-dafd184490a9)
      - **Settings:**
        - **File format:** Delimited
        - **Delimiter:** Comma
        - **Encoding:** UTF-8
        - **Column headers:** Only first file has headers
        - **Skip rows:** None
        - **Dataset contains multi-line data:** _Não Selecione_ ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/d32712a2-beb3-4140-ae72-c5cab3999c5b)
      - **Schema:**
        - Incluir todas as colunas exceto **Path** ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/aa195c57-cb48-4ddf-bfc2-b2afb21774f8)
        - Revise os tipos detectados automaticamente ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/962ddffb-9b40-4143-94f8-d18ac4f69c21)
Selecione **Create**. Após a criação do conjunto de dados, selecione o conjunto de dados de **bike-rentals** para continuar a enviar o trabalho de ML automatizado. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/f87d3ce2-28b9-4fc0-833a-caf320b4acde)
  - **Task settings:**
    - **Task type:** Regression
    - **Dataset:** bike-rentals
    - **Target column:** Rentals (integer) ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/e3d74d77-21df-47d1-8457-648fe8b3eaa1)

    - **Additional configuration settings:**
      - **Primary metric:** Normalized root mean squared error
      - **Explain best model:** _Não selecionado_
      - **Use all supported models:** _Não selecionado_. Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
      - **Allowed models:** Selecione apenas **RandomForest** e **LightGBM** — _normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho._ ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/c9a08f34-d25b-42f8-905f-2dcd2e1ce356)
    - **Limits:** Expanda esta seção
       - Max trials: 3
       - Max concurrent trials: 3
       - Max nodes: 3
       - Metric score threshold: 0.085 (_de modo que, se um modelo atingir uma pontuação métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho será encerrado._)
       - Timeout: 15
       - Iteration timeout: 15
       - Enable early termination: _Selecionado_ ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/78cd1705-c11c-4f7c-be25-fb7ac717151c)

    - **Validation and test:**
      - **Validation type:** Train-validation split
      - **Percentage of validation data:** 10
      - **Test dataset:** None ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/cd2c365e-a94e-4a40-8b92-0ada23480867)

- **Compute:**
  - **Select compute type:** Serverless
  - **Virtual machine type:** CPU
  - **Virtual machine tier:** Dedicated
  - **Virtual machine size:** Standard_DS3_V2*
  - **Number of instances:** 1 ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/36f523d0-94b7-4337-894f-efd9e55b0bb9)

_Se a sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível._

3. Envie o trabalho de treinamento. Ele inicia automaticamente. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/cacf2ee1-9603-4d7d-a54d-bc4ae243e2ec)
4. Espere o trabalho terminar. Pode demorar um pouco. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/3d9693b2-a450-4ca6-be8f-332c4f3b3319)

## Avalie o melhor modelo
Quando o trabalho automatizado de aprendizado de máquina for concluído, você poderá revisar o melhor modelo treinado.

1. Na guia **Overview** do trabalho automatizado de aprendizado de máquina, observe o melhor resumo do modelo. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/0b19f36f-11a5-4563-bfe2-8273e7e9c8a3)

> [!NOTE]
> Você pode ver uma mensagem com o status “Aviso: pontuação de saída especificada pelo usuário alcançada…”. Esta é uma mensagem esperada. Continue para a próxima etapa

2. Selecione o texto abaixo de **Algorithm name** do melhor modelo para visualizar seus detalhes. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/f9ebc3e0-9646-4564-8675-e1b58891480c)
3. Selecione a guia **Metrics** e selecione os gráficos **residuals** e **predicted_true** se eles ainda não estiverem selecionados.
Revise os gráficos que mostram o desempenho do modelo. O gráfico **residuals** mostra os _resíduos_ (as diferenças entre os valores previstos e reais) como um histograma. O gráfico predicted_true compara os valores previstos com os valores verdadeiros.![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/d35078c1-92d2-401b-9118-69adab40f647)

## Implantar e testar o modelo
1. Na guia** Model** do melhor modelo treinado pelo seu trabalho automatizado de machine learning, selecione **Deploy** e use a opção de **Web Service** para implantar o modelo. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/ce04bea4-6571-47c6-884c-1ef9cc30f477)
- **Deploy a Model**
  - **Name:** predict-rentals
  - **Description:** Prever aluguel de bicicletas
  - **Compute type:** Azure Container Instance
  - **Enable authentication:** _Selecionado_
  
  ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/6205df18-c74f-463e-ab03-bc64369145f3)

2. Aguarde o início da implantação – isso pode levar alguns segundos. O **Deploy status** do endpoint de **predict-rentals** será indicado na parte principal da página como _Running_. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/1a0a17c3-08f7-4d2f-a0ac-ffeae925c378)
3. Aguarde até que o **Deploy Status** mude para _Succeeded_. Isso pode levar de 5 a 10 minutos.

## Testar o serviço implantado
Agora você pode testar seu serviço implantado.

1. No estúdio Azure Machine Learning, no menu esquerdo, selecione **Endpoints** e abra o endpoint em tempo real de **predict-rentals**. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/66e667da-63dd-4645-be83-fbc7584ff37a)
2. Na página do endpoint em tempo real de **predict-rentals**, visualize a guia **Test**. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/c5c55586-c646-405e-8ccb-0b871abd51bb)
3. No painel **Input data to test endpoint**, substitua o modelo JSON pelos seguintes dados de entrada:
``` {
   "Inputs": { 
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
```

4. Clique no botão **Test**.

5. Revise os resultados do teste, que incluem um número previsto de aluguéis com base nos recursos de entrada - semelhante a este:
```
{
   "Results": [
     444.27799000000000
   ]
 }
```

O painel de teste pegou os dados de entrada e usou o modelo treinado para retornar o número previsto de aluguéis.

Vamos revisar o que nós fizemos. nós usamos um conjunto de dados históricos de aluguel de bicicletas para treinar um modelo. O modelo prevê o número de alugueres de bicicletas esperados num determinado dia, com base em características sazonais e meteorológicas.

## Apagar
O serviço web que você criou está hospedado em uma _instância de contêiner do Azure_. Se você não pretende fazer mais experiências com ele, exclua o ponto de extremidade para evitar o acúmulo desnecessário de uso do Azure.

1. No [Azure Machine Learning studio](https://ml.azure.com/home), na guia **Endpoints**, selecione o endpoint de **predict-rentals**. Em seguida, selecione **Delete** e confirme que deseja excluir o endpoint. ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/eec1a575-a1ae-4c51-8fba-8b0ee7e6c2ed)


   Excluir sua computação garante que sua assinatura não será cobrada por recursos de computação. No entanto, será cobrada uma pequena quantia pelo armazenamento de dados, desde que o espaço de trabalho do Azure Machine Learning exista na sua assinatura. Se você terminou de explorar o Azure Machine Learning, você pode excluir o espaço de trabalho do Azure Machine Learning e os recursos associados.

   Para excluir seu **Workspace**:

   1. No [portal Azure](https://portal.azure.com), na página **Resource groups**, abra o grupo de recursos especificado ao criar o seu workspace Azure Machine Learning.![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/e2278e12-85a4-4971-b061-52ebfa101157)
 ![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/344958e1-4512-4b6a-b28d-b42542a534e9)


  
   2. Clique em **Delete resource group**, digite o nome do grupo de recursos para confirmar que deseja excluí-lo e selecione **Delete**.![image](https://github.com/r2WillDev/LAB-MachineLearning-Azure-ML/assets/106842143/215a5840-c8ff-45e6-8324-0bf0bd093e35)
  

> [!IMPORTANT]
> Todo esse passo a passo está no [site oficial da microsoft](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html#create-an-azure-machine-learning-workspace).

























    



