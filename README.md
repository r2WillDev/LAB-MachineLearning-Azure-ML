# LAB-MachineLearning-Azure-ML
Neste exercício, você usará o recurso de machine learning automatizado no Azure Machine Learning para treinar e avaliar um modelo de machine learning. Em seguida, você implantará e testará o modelo treinado.

## Criando um Azure Machine Learning Workspace
Para usar o Azure Machine Learning, crie um espaço de trabalho no Azure e acesse o Azure Machine Learning Studio para gerenciar recursos.

> [!TIP]
> Se você já tiver um espaço de trabalho do Azure Machine Learning, poderá usá-lo e pular para a próxima tarefa.

1. Entre no portal do [Azure]( https://portal.azure.com) em usando suas credenciais da Microsoft.
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









    



