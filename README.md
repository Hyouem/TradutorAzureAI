# TradutorAzureAI
TradutorAzureAI
import requests
import uuid

# Configurações do Azure
KEY = "SUA_CHAVE_AZURE"
ENDPOINT = "https://api.cognitive.microsofttranslator.com"
LOCATION = "brazilsouth"

# Endpoint da API
url = ENDPOINT + "/translate"

# Parâmetros
params = {
    "api-version": "3.0",
    "from": "en",
    "to": ["pt"]
}

# Cabeçalhos
headers = {
    "Ocp-Apim-Subscription-Key": KEY,
    "Ocp-Apim-Subscription-Region": LOCATION,
    "Content-type": "application/json",
    "X-ClientTraceId": str(uuid.uuid4())
}

# Texto para tradução
body = [{
    "text": "Machine learning models require high-quality datasets."
}]

# Requisição
response = requests.post(url, params=params, headers=headers, json=body)
result = response.json()

# Resultado
print(result[0]["translations"][0]["text"])
