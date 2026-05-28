# Desafio DevSecOps — Gerenciador de Tarefas

## Sobre o Projeto
Este repositório faz parte do desafio prático do módulo de DevSecOps da ADA Tech.  
Você recebeu este projeto com vulnerabilidades propositais e uma pipeline incompleta.  
O objetivo é implementar a pipeline de segurança e corrigir as vulnerabilidades.

---

## Estado atual
A pipeline foi **completamente implementada**.  
Agora ela contém steps de segurança que bloqueiam automaticamente o fluxo em caso de falhas.

---

## Sua missão
- Implementar os steps de segurança no `pipeline.yml`  
- Fazer a pipeline quebrar ao detectar os problemas  
- Corrigir as vulnerabilidades encontradas  
- Fazer a pipeline passar com tudo verde   
- Documentar o funcionamento da pipeline neste README  

---

## O que foi implementado
- *✅*Secrets Scanning** com Gitleaks  
- **SAST** com Semgrep  
- **SCA** com Grype  
- **Passo Extra 1**: CVE Check com OSV-Scanner  
- **Passo Extra 2**: DAST com OWASP ZAP  
- **Deploy** com GitHub Pages  

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

6. **Passo Extra 1 — CVE Check (OSV-Scanner)**  
   Consulta a base OSV para verificar se as dependências possuem CVEs conhecidos.  
   👉 Bloqueia o pipeline se houver vulnerabilidades altas ou críticas.

7. **Passo Extra 2 — DAST (OWASP ZAP)**  
   Executa testes dinâmicos simulando ataques reais contra a aplicação em execução.  
   👉 Bloqueia o pipeline se detectar falhas críticas.

8. **Deploy Seguro (GitHub Pages)**  
   Só é realizado se todos os passos anteriores forem bem-sucedidos.  
   👉 Garante que apenas código seguro chegue ao ambiente de produção.

---

## Checklist dos Steps
| Step | Ferramenta | Função | Bloqueia Pipeline |
|------|------------|--------|-------------------|
| Secrets Scanning | Gitleaks | Detecta credenciais expostas | ✔️ |
| SAST | Semgrep | Analisa código fonte | ✔️ |
| SCA | Grype | Verifica dependências vulneráveis | ✔️ |
| Passo Extra 1 | OSV-Scanner | Confere CVEs conhecidos | ✔️ |
| Passo Extra 2 | OWASP ZAP | Testes dinâmicos (DAST) | ✔️ |
| Deploy | GitHub Pages | Publica aplicação segura | Só se tudo passar ✅ |

---

## URL de Produção
  
👉 **[https://naelyabarbosa.github.io/gerenciador-de-tarefas](https://naelyabarbosa.github.io/gerenciador-de-tarefas)**  
