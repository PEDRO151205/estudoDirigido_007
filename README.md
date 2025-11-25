# PATRI-TECH — Etapas 0 e 1 (Do Problema à Modelagem e Escolha de Framework)

## 📌 Objetivo

Documento referente às etapas 0 e 1 do projeto PATRI-TECH, abordando:

* Interpretação do problema
* Identificação de requisitos
* Priorização (MoSCoW)
* Atores e fluxos
* Casos de uso
* Justificativa técnica (Django x FastAPI)
* Síntese final e mini-diagrama de casos de uso

---

## 🚩 PARTE 1 — Leitura e Interpretação Crítica

### **1. Problema Central**

O sistema PATRI-TECH deve resolver a falta de controle atualizado, confiável e eficiente dos bens patrimoniais da Secretaria Municipal de Educação. Os inventários manuais são lentos, sujeitos a erros e incapazes de fornecer rastreamento em tempo real.

### **2. Consequências se o problema não for resolvido**

* Perda ou extravio de bens públicos.
* Informações inconsistentes para auditorias e prestação de contas.
* Retrabalho intenso em inventários manuais.

### **3. Verbos e Adjetivos Identificados**

**Verbos (requisitos funcionais):** identificar, contabilizar, classificar.
**Adjetivos (requisitos não funcionais):** ágil, preciso, adequado ao contexto patrimonial.

### **4. Restrições Reais**

* Infraestrutura limitada em escolas.
* Equipe reduzida.
* Tempo e orçamento restritos.
* Dependência de equipamentos RFID.

---

## 🚩 PARTE 2 — Requisitos, Atores e Fluxos

### **5. Priorização MoSCoW**

**Must Have:** cadastrar bens, ler etiquetas RFID, atualizar status, login seguro.
**Should Have:** gerar relatórios.
**Could Have:** exportar PDF, dashboards, auditoria.
**Would Have:** integrações externas, app mobile.

### **6. Requisitos Funcionais vs Não Funcionais**

* **Funcionais:** descrevem o que o sistema deve fazer.
* **Não funcionais:** descrevem como o sistema deve se comportar (desempenho, segurança etc.).

### **7. Atores do Sistema**

* **Servidor Inventariante:** realiza inventários e leituras RFID.
* **Administrador:** gerencia usuários, auditorias e relatórios.
* **Leitor RFID / Middleware:** envia códigos lidos ao sistema.

### **8. Fluxo Típico de Inventário**

1. Servidor faz login.
2. Inicia inventário em uma unidade.
3. Leitor RFID captura etiquetas.
4. Sistema identifica bens e atualiza status.
5. Servidor registra ocorrências.
6. Sistema gera relatório parcial ou final.

---

## 🚩 PARTE 3 — Casos de Uso e Decisão Técnica

### **9. Casos de Uso (textuais)**

1. Servidor lê uma etiqueta RFID e o sistema registra a presença do bem.
2. Servidor atualiza manualmente o status de um bem.
3. Administrador solicita relatório de inventário.

### **10. Detalhamento de Caso de Uso**

**Caso:** leitura RFID e registro de presença.
**Entrada:** código RFID + usuário + local.
**Processamento:** localizar bem, validar contexto, registrar timestamp e presença.
**Saída:** confirmação visual + atualização no banco.

### **11. Framework escolhido: FastAPI**

**Motivos:**

* Sistema orientado a integração RFID → API-first.
* Alto desempenho e suporte a assincronismo.
* Curva de aprendizado mais curta.
* Independência para frontends diversos.

**Django seria ideal quando:** foco é painel web robusto (admin pronto).

### **12. Riscos da escolha errada**

* Reescrita do projeto.
* Problemas de integração.
* Baixa performance em leituras intensivas.
* Arquitetura inadequada para o escopo.

---

## 🚩 PARTE 4 — Síntese e Diagrama

### **13. Frase de Visão do Produto**

**"O PATRI-TECH agiliza e torna confiável o controle patrimonial municipal usando RFID e inventários inteligentes."**

### **14. Mini-Diagrama de Casos de Uso (Texto)**

```
Servidor → Sistema PATRI-TECH → Registrar leitura RFID
Servidor → Sistema PATRI-TECH → Atualizar status do bem
Administrador → Sistema PATRI-TECH → Gerar relatório
Leitor RFID → Sistema PATRI-TECH → Enviar código RFID
```

### **15. Importância do Alinhamento de Requisitos e Arquitetura**

Sem alinhamento inicial, o time corre o risco de implementar funcionalidades incorretas, escolher tecnologias inadequadas e gerar retrabalho. Boa arquitetura é um mapa — codar sem ela é trabalhar no escuro.

---

