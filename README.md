# 📦 Desafio DevSecOps — Gerenciador de Tarefas

## 📂 Sobre o Projeto
Este repositório faz parte do desafio prático do módulo de DevSecOps da ADA Tech.  
O projeto estava com vulnerabilidades propositais e uma pipeline incompleta.  
O objetivo era implementar a pipeline de segurança e corrigir as vulnerabilidades.

---

## ✨ Estado atual 💡
A pipeline foi **completamente implementada**.  
Agora ela contém steps de segurança que bloqueiam automaticamente o fluxo em caso de falhas.

---

## 📋 A missão era:
- Implementar os steps de segurança no `pipeline.yml`  
- Fazer a pipeline quebrar ao detectar os problemas  
- Corrigir as vulnerabilidades encontradas  
- Fazer a pipeline passar com tudo verde ✅  
- Documentar o funcionamento da pipeline neste README  

---

## 🛠️ O que foi implementado
-✅ **Secrets Scanning** com Gitleaks  
-✅ **SAST** com Semgrep  
-✅ **SCA** com Grype  
-✅ **Deploy** com GitHub Pages  

---

## 🔎 Como a pipeline funciona
A pipeline segue o conceito **shift-left security**, garantindo que falhas sejam detectadas o mais cedo possível:

1. 📌 **Checkout do Código**  

   Baixa o repositório para o ambiente de execução. Todos os arquivos do projeto são copiados para o ambiente da pipeline.

2. 🧩 **Build da Aplicação**  

   Verifica a estrutura e prepara o código para análise.

3. 🔑 **Secrets Scanning (Gitleaks)**  
    
   👉 **Descrição da vulnerabilidade identificada**

   API_KEY e DB_PASSWORD estavam escritos diretamente no script.js.  
   Vazamento de segredos e credenciais sensíveis no código (chaves de API, tokens, senhas hardcoded).  
   Relaciona-se ao OWASP A02: Security Misconfiguration e A07: Identification and Authentication Failures.  

   👉 **Objetivo da implantação da ferramenta**  

   Detectar automaticamente segredos expostos no repositório antes que cheguem ao ambiente de produção.  
   Gitleaks é leve, rápido e altamente eficaz para identificar padrões de credenciais.  
   Bloquear o pipeline se encontrar secrets.  
   
   👉 **Correção da Vulnerabilidade**  
   
   Exclusão das informações de credenciais sensíveis que estavam expostas.    

4. 🛡️ **SAST (Semgrep)**
   
   👉 **Descrição da vulnerabilidade identificada**  

   Código inseguro e más práticas de programação, como SQL Injection, XSS, uso inseguro de bibliotecas.  
   Relaciona-se diretamente ao OWASP A01: Broken Access Control, A03: Injection e A04: Design Inseguro.  

   👉 **Objetivo da implantação da ferramenta**  

   Realizar análise estática de código (SAST) para detectar padrões inseguros e violações de boas práticas de segurança.  
   Bloquear o pipeline se houver linhas vulneráveis.  

   👉 **Correção da Vulnerabilidade**  

   Comando estava ausente e foi configurado.  
   Além disso, permite criar regras específicas para o contexto da aplicação.  

5. 🛑 **SCA (Grype)**  

   👉 **Descrição da vulnerabilidade identificada**
   
   Vulnerabilidades em dependências e imagens Docker (CVEs em pacotes e bibliotecas).  
   Relaciona-se ao OWASP A06: Vulnerable and Outdated Components.  

   👉 **Objetivo da implantação da ferramenta**  

   Fazer análise de segurança em imagens containerizadas e dependências antes do deploy.  
   Verificar pacotes contra bancos de dados de vulnerabilidades (como NVD).  
   Bloquear o pipeline se encontrar falhas médias ou maiores.  
   
   👉 **Correção da Vulnerabilidade**  

   Comando estava ausente e foi configurado.  
   Grype é rápido, open source e se integra bem com pipelines que usam Docker/Kubernetes.  

6. 🚀 **Deploy Seguro (GitHub Pages)**
   
   Só é realizado se todos os passos anteriores forem bem-sucedidos.  

   👉 Garante que apenas código seguro chegue ao ambiente de produção.  

---

## 🧾 Checklist dos Steps 👩‍💻
| Step | Ferramenta | Função | Bloqueia Pipeline |
|------|------------|--------|-------------------|
| Secrets Scanning | Gitleaks | Detecta credenciais expostas | ✔️ |
| SAST | Semgrep | Analisa código fonte | ✔️ |
| SCA | Grype | Verifica dependências vulneráveis | ✔️ |
| Deploy | GitHub Pages | Publica aplicação segura | Só se tudo passar ✅ |

---

## 📚 Conclusão

   Essa pipeline mostra como aplicar o conceito de DevSecOps na prática:  
   - Automatizar segurança dentro do ciclo de vida do software.  
   - Quebrar o build sempre que houver falhas.  
   - Garantir que apenas código seguro chegue à produção.

   Com isso, a startup passa a ter um processo moderno, confiável e seguro.  

---

## 🌐 URL de Produção 🧭

👉 **[https://naelyabarbosa.github.io/Projeto-DevSecOps-desafio/](https://naelyabarbosa.github.io/Projeto-DevSecOps-desafio/)**  
