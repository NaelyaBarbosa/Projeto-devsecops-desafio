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

3. **Build da Aplicação**  

   Verifica a estrutura e prepara o código para análise.

5. 🔑 **Secrets Scanning (Gitleaks)**  
    
   👉 **Descrição da vulnerabilidade identificada**  
   Vazamento de segredos e credenciais sensíveis no código (chaves de API, tokens, senhas hardcoded). Relaciona-se ao OWASP A05: Security Misconfiguration e A07: Identification and Authentication Failures.

   👉 **Objetivo da implantação da ferramenta**  
   Detectar automaticamente segredos expostos no repositório antes que cheguem ao ambiente de produção.

   👉 **Motivo da escolha da ferramenta**  
   Gitleaks é leve, rápido e altamente eficaz para identificar padrões de credenciais. É amplamente usado em pipelines CI/CD e tem boa integração com GitHub Actions, GitLab CI e outros.   

   👉 Bloqueia o pipeline se encontrar secrets.

6. 🛡️ **SAST (Semgrep)**
   
   👉 **Descrição da vulnerabilidade identificada**
     
   Código inseguro e más práticas de programação, como SQL Injection, XSS, uso inseguro de bibliotecas. Relaciona-se diretamente ao OWASP A01: Broken Access Control, A03: Injection e A06: Vulnerable and Outdated Components.

   👉 **Objetivo da implantação da ferramenta**  
Realizar análise estática de código (SAST) para detectar padrões inseguros e violações de boas práticas de segurança.

   👉 **Motivo da escolha da ferramenta**  
Semgrep é altamente customizável, suporta múltiplas linguagens e possui regras prontas baseadas no OWASP Top 10. Além disso, permite criar regras específicas para o contexto da aplicação.Analisa o código fonte em busca de padrões inseguros.

   👉 Bloqueia o pipeline se houver linhas vulneráveis.

7. **SCA (Grype)**  
   Examina dependências externas em busca de vulnerabilidades.  
   👉 Bloqueia o pipeline se encontrar falhas médias ou maiores.

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
| Deploy | GitHub Pages | Publica aplicação segura | Só se tudo passar ✅ |

---

## URL de Produção

👉 **[https://naelyabarbosa.github.io/Projeto-DevSecOps-desafio/](https://naelyabarbosa.github.io/Projeto-DevSecOps-desafio/)**  
