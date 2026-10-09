# Relatório de validação

## Resultado

**VALIDAÇÃO APROVADA**

## Dados e cálculos

| Verificação | Resultado |
|---|---:|
| Linhas processadas | 100 |
| IDs únicos na fonte | 100 |
| Valor bruto | US$ 12.827.800,50 |
| Negócios ativos | 93 |
| Valor ativo | US$ 12.202.550,50 |
| Ticket médio ativo | US$ 131.210,22 |
| Entregues | 41 |
| Em andamento | 52 |
| Cancelados | 7 |
| Valor cancelado | US$ 625.250,00 |
| Taxa de entrega | 44,1% |

## Respostas verificadas

- família líder em valor ativo: **911 — US$ 4.168.100,00**;
- estado líder em valor ativo: **TX — US$ 2.023.400,50**;
- método líder em valor ativo: **Wire Transfer — US$ 3.979.450,00**;
- composição ativa: **68 combustão, 20 elétricos e 5 híbridos**.

## Testes estruturais

- HTML único com CSS, JavaScript e 100 registros incorporados;
- cinco seletores de filtro;
- reset, exportação CSV e tema claro/escuro;
- quatro perguntas de negócio;
- gráficos clicáveis;
- tabela agregada de modelos;
- layout responsivo;
- Content Security Policy;
- nenhuma biblioteca ou stylesheet externo;
- nenhuma chamada `fetch`, XHR ou WebSocket;
- sintaxe JavaScript verificada com Node quando disponível.

## Testes em navegador real

O Chromium headless carregou o dashboard e confirmou:

- zero erros de console;
- 100 registros na visualização inicial;
- 93 negócios ativos;
- filtro da família 911 com 23 registros e 22 negócios ativos;
- filtro de cancelados com 7 registros;
- reset dos filtros;
- alternância entre temas;
- abertura do diálogo de metodologia;
- download do CSV filtrado;
- largura móvel de 390 px sem overflow horizontal.

## Acessibilidade

O dashboard foi auditado com axe-core nos temas escuro e claro:

- violações críticas: 0;
- violações sérias: 0;
- navegação por teclado preservada;
- rótulos nos controles;
- regiões atualizadas com `aria-live`;
- opção `prefers-reduced-motion` respeitada.

## Privacidade

O validador compara o resultado com a fonte e confirma que nenhum valor de `customer_name` ou `salesperson` foi incorporado ao dataset público. Também são excluídos IDs, campos crus e datas individualizadas.

## Integridade da fonte

```text
f874650657ca4e1a99fd4462b297bfc5fd9915e8e693956d9cec47eda2cb2e2d
```

## Como repetir

```bash
python scripts/gerar_dashboard.py
python scripts/verificar_dashboard.py
```

Saída esperada:

```text
VALIDAÇÃO APROVADA
```