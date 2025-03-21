# 🔍 Azure Cognitive Search - AI Search para Indexação e Consulta de Dados

Este projeto explora a configuração e utilização do **Azure Cognitive Search**, uma ferramenta poderosa para indexação e pesquisa inteligente de dados.

## 📌 Passo a Passo para Configuração  

### 1️⃣ Criar um Serviço no Azure  
1. Acesse o [Portal do Azure](https://portal.azure.com/).  
2. Busque por **"Cognitive Search"** e clique em **Criar**.  
3. Escolha um **nome único**, um **grupo de recursos** e uma **camada de preços** adequada.  
4. Clique em **Revisar + Criar** e aguarde a implantação.  

### 2️⃣ Criar e Configurar um Índice  
1. No portal do Azure, vá até **Cognitive Search > Índices** e clique em **Novo Índice**.  
2. Defina os **campos** e **tipos de dados** para sua indexação.  
3. Configure as **chaves primárias** e os **mecanismos de pesquisa** (full-text search, faceted search, etc.).  
4. Salve o índice e ele estará pronto para receber dados.  

### 3️⃣ Importar e Indexar Dados  
- Você pode usar **Azure Blob Storage, SQL Database, Cosmos DB** ou enviar dados manualmente via API REST.  
- Exemplo de requisição para indexar dados usando Python:  

```python
import requests

url = "https://SEU-SERVICO.search.windows.net/indexes/SEU-INDICE/docs/index?api-version=2023-07-01"
headers = {
    "Content-Type": "application/json",
    "api-key": "SUA-CHAVE-DE-API"
}
data = {
    "value": [
        {
            "@search.action": "upload",
            "id": "1",
            "titulo": "Introdução ao Azure Cognitive Search",
            "conteudo": "Este documento explica como configurar a ferramenta..."
        }
    ]
}

response = requests.post(url, json=data, headers=headers)
print(response.status_code, response.json())
