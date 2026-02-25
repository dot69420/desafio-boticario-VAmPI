# Desafio técnico grupo boticário

Este repositório é uma demonstração de implementação de ferramentas de segurança (SAST e DAST) em um pipeline de CI/CD utilizando Github Actions.

## Impementação

A pipeline foi configurada para ser executada em cada push ou pull request nas principais branches.

### SAST (Static Application Security Testing)
Ferramenta escolhida: Bandit https://github.com/PyCQA/bandit
Finalidade: Analisar o código fonte estático em busca de vulnerabilidades comuns de segurança em Python

##### Processo de implementação 
- Configuração do Job no Github Actions ('sast').
- Varre todo diretório recursivamente.
- Gera um artefato json (bandit-results.json) com os achados.


### DAST (Dynamic Application Security Testing)
Ferramenta escolhida: OWASP ZAP https://www.zaproxy.org/
Finalidade: Testar a aplicação em tempo de execução no modo caixa-preta.

##### Processo de implementação 
- Configuração do Job no Github Actions ('dast').
- A aplicação sobe em um container Docker dentro do runner do github.
- O passo "zaproxy/action-full-scan" é executado contra a URL local da API no container (http://localhost:5000)


### Consultando os resultados
1. Acesse a aba Actions no topo do repositório da aplicação no Github
2. Clique na execução mais recente do workflow "Processo Seletivo Boticário"
3. No job de SAST, você pode baixar o arquivo de resultados em "Artifacts"
4. No job de DAST, o relatório detalhado do OWASP ZAP aparecerá no log da execução.