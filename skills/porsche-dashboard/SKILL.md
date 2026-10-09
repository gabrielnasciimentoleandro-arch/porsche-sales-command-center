---
name: porsche-dashboard
version: 1.0.0
description: Audita uma base de vendas, define perguntas de negócio e entrega um dashboard HTML único, privado por design e verificável.
---

# Skill: dashboard comercial autoral

## Quando usar

Use esta skill quando a tarefa pedir transformar uma planilha de vendas em um dashboard web interativo e publicável sem backend.

## Objetivo

Produzir uma resposta de negócio, não uma coleção de gráficos. O artefato final deve ser auditável, responsivo, acessível e seguro para publicação.

## Fluxo obrigatório

1. **Preserve a fonte**
   - registre URL, tamanho e SHA-256;
   - não altere a planilha original;
   - separe fonte local de artefatos públicos.

2. **Audite antes de desenhar**
   - conte linhas e chaves únicas;
   - identifique colunas cruas e sanitizadas;
   - liste categorias, nulos, inválidos, extremos e inconsistências;
   - recalcule os totais de forma independente.

3. **Proteja pessoas**
   - aplique minimização de dados;
   - remova nomes, IDs, contatos e campos não necessários;
   - não incorpore dados pessoais no HTML público;
   - documente exatamente o que foi removido.

4. **Defina perguntas**
   - escolha pelo menos três perguntas acionáveis;
   - associe cada pergunta a uma métrica e um visual;
   - escreva as definições antes de implementar.

5. **Projete o dashboard**
   - HTML único com CSS e JavaScript incorporados;
   - sem API, CDN, cookie ou backend;
   - filtros, reset e estado vazio;
   - visual coerente com a marca sem copiar layouts existentes;
   - responsividade e navegação por teclado.

6. **Valide**
   - compare todos os registros públicos com as colunas sanitizadas da fonte;
   - confira totais, categorias e perguntas centrais;
   - teste filtros, reset, exportação e mobile em navegador real;
   - verifique erros de console e acessibilidade;
   - rejeite o build se houver identificadores ou dependências externas.

7. **Documente e publique**
   - explique perguntas, prompt, refinamentos, tratamento e modalidade de IA;
   - inclua print geral e print com filtro;
   - publique `index.html` no GitHub Pages;
   - valide o endereço público e entregue o link do repositório.

## Critérios de saída

- perguntas respondidas e justificadas;
- cálculos reproduzíveis;
- fonte rastreável;
- nenhuma informação pessoal no artefato público;
- nenhum erro de console;
- nenhuma violação séria de acessibilidade;
- página pública funcionando sem serviço pago.