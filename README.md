# QA-Automation-Challenge

# Desafio 

A primeira parte do desafio entendimento da documentação e fazer as chamadas nos metodos GET e POST para o endpoint /post.

Dentro da collection tem comentarios das validações que foi feita em cada cenario de teste

## Levantado os cenarios:

## Metodo GET
Consulta dos 100 posts  
Consulta e validação por filtro de range  
Consulta e validação por filtro paginação  
Consulta e validação por filtro ordenação  

## Metodo POST
• Criação de um objeto  
• Criação de dois objetos

Levantado mais um cenario para o metodo PUT:  
Teste negativo alteração passando o Body incorrento  

# Configuração do projeto de API Postman
------------

• Postman 8.3.0 (Dowload https://www.postman.com/downloads/ )  
• Import da Collection a mesma se encontra na raiz do projeto com o nome do arquivo /JSONPlaceholderAPI.postman_collection.json (https://learning.postman.com/docs/getting-started/importing-and-exporting-data/)

# Execução dos testes de API via Postman
  
• Documentação da execução da collection (https://learning.postman.com/docs/running-collections/intro-to-collection-runs/)


# Execução dos testes de via git Action na esteira

Configuração do arquivo .yml

## Usage
```yaml
  name: Run Postman Collection

on:
  push:
    branches:
      - main

jobs:
  newman:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v2

    - name: Install Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '16'

    - name: Install Newman
      run: npm install -g newman

    - name: Install Newman report 
      run: npm install -g newman-reporter-html
    
    - name: Run Newman
      run: newman run JSONPlaceholderAPI.postman_collection.json || true

    - name: Upload Report as Artifact
      uses: actions/upload-artifact@v2
      with:
        name: newman-report
        path: newman-report.html

```






