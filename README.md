# Desafio DevSecOps — Gerenciador de Tarefas

## Sobre o Projeto
Este repositório faz parte do desafio prático do módulo de DevSecOps da ADA Tech.  
O projeto estava com vulnerabilidades propositais e uma pipeline incompleta.  
O objetivo era implementar a pipeline de segurança e corrigir as vulnerabilidades.

---

## Estado atual
A pipeline foi **completamente implementada**.  
Agora ela contém steps de segurança que bloqueiam automaticamente o fluxo em caso de falhas.

---

## A missão era:
- Implementar os steps de segurança no `pipeline.yml`  
- Fazer a pipeline quebrar ao detectar os problemas  
- Corrigir as vulnerabilidades encontradas  
- Fazer a pipeline passar com tudo verde ✅  
- Documentar o funcionamento da pipeline neste README  

---

## O que foi implementado
-✅ **Secrets Scanning** com Gitleaks  
-✅ **SAST** com Semgrep  
-✅ **SCA** com Grype  
-✅ **Deploy** com GitHub Pages  

---

## Como a pipeline funciona
A pipeline segue o conceito **shift-left security**, garantindo que falhas sejam detectadas o mais cedo possível:

1. **Checkout do Código**  
   Baixa o repositório para o ambiente de execução.

2. **Build da Aplicação**  
   Verifica a estrutura e prepara o código para análise.

3. **Secrets Scanning (Gitleaks)**  
   Detecta credenciais expostas.  
   👉 Bloqueia o pipeline se encontrar secrets.

4. **SAST (Semgrep)**  
   Analisa o código fonte em busca de padrões inseguros.  
   👉 Bloqueia o pipeline se houver linhas vulneráveis.

5. **SCA (Grype)**  
   Examina dependências externas em busca de vulnerabilidades.  
   👉 Bloqueia o pipeline se encontrar falhas médias ou maiores.

6. **Deploy Seguro (GitHub Pages)**  
   Só é realizado se todos os passos anteriores forem bem-sucedidos.  
   👉 Garante que apenas código seguro chegue ao ambiente de produção.

---

## Checklist dos Steps
| Step | Ferramenta | Função | Bloqueia Pipeline |
|------|------------|--------|-------------------|
| Secrets Scanning | Gitleaks | Detecta credenciais expostas | ✔️ |
| SAST | Semgrep | Analisa código fonte | ✔️ |
| SCA | Grype | Verifica dependências vulneráveis | ✔️ |
| Deploy | GitHub Pages | Publica aplicação segura | Só se tudo passar ✅ |

---

## URL de Produção

👉 **[https://naelyabarbosa.github.io/Projeto-DevSecOps-desafio/](https://naelyabarbosa.github.io/Projeto-DevSecOps-desafio/)**  
