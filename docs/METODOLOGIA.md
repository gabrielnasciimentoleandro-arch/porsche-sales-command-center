# Metodologia

## 1. Fonte

A fonte é a planilha sanitizada disponibilizada pela DIO para o desafio “Criando uma Dashboard da Porsche com Agentes de IA”.

- URL: `https://hermes.dio.me/files/assets/8683bed0-cc33-4e06-bca9-04db9c31f9e2.xlsx`
- SHA-256: `f874650657ca4e1a99fd4462b297bfc5fd9915e8e693956d9cec47eda2cb2e2d`
- Aba: `Sanitized`
- Registros: 100
- IDs únicos na fonte: 100

A planilha-fonte é baixada somente para a geração local e fica em `data/source/`, diretório ignorado pelo Git.

## 2. Seleção de campos

A base contém pares de colunas: um valor cru e sua versão sanitizada. O projeto utiliza apenas as versões sanitizadas:

| Campo analítico | Origem |
|---|---|
| Modelo | `PorscheModelSanitized` |
| Ano-modelo | `ModelYearSanitized` |
| Preço | `SalesPriceSanitized` |
| Quilometragem | `VehicleMileageSanitized` |
| Pagamento | `PayMethodSanitized` |
| Cidade | `CitySanitized` |
| Estado | `StateSanitized` |
| Situação | `DeliveryStatusSanitized` |

Foram removidos da versão pública:

- `sale_id`;
- `customer_name`;
- `salesperson`;
- todas as colunas cruas;
- datas individualizadas.

## 3. Dimensões derivadas

### Família

A variedade foi reduzida de 40 modelos para seis famílias: `911`, `718`, `Cayenne`, `Macan`, `Taycan` e `Panamera`.

### Etapa operacional

| Situação sanitizada | Etapa derivada |
|---|---|
| `Delivered` | Entregue |
| `Cancelled` | Cancelado |
| Todas as demais | Em andamento |

### Motorização

- Elétrico: família Taycan e `Macan Electric`;
- Híbrido: modelos contendo `E-Hybrid`;
- Combustão: demais modelos.

## 4. Regras de negócio

```text
valor_bruto = soma do preço de todos os registros selecionados
valor_ativo = soma do preço onde etapa ≠ Cancelado
negócios_ativos = contagem onde etapa ≠ Cancelado
ticket_médio_ativo = valor_ativo ÷ negócios_ativos
taxa_de_entrega = entregues ÷ negócios_ativos
valor_cancelado = soma do preço onde etapa = Cancelado
```

Os gráficos financeiros priorizam negócios ativos. Quando a seleção contém somente cancelados, o painel exibe o valor desses registros para que o filtro continue informativo.

## 5. Tratamento das datas

A coluna `SaleDateSanitized` contém:

- 24 valores `INVALID`;
- 76 datas parseáveis;
- intervalo válido de 14/03/2024 a 01/10/2027;
- 21 datas posteriores a 09/10/2026, data de geração da versão 1.0.0.

A dimensão temporal foi excluída dos indicadores e do HTML. Isso evita transformar inconsistências conhecidas em uma tendência aparentemente precisa.

## 6. Perguntas de negócio

1. **Onde o valor do portfólio se concentra?** Orienta mix de produto e prioridade comercial.
2. **Quais mercados lideram?** Ajuda a localizar concentração geográfica e oportunidades.
3. **Como os clientes pagam?** Apoia estratégia financeira e experiência de compra.
4. **Como está o fluxo de entrega?** Evidencia carteira entregue, em andamento e cancelada.

## 7. Privacidade e segurança

O arquivo público contém somente dimensões necessárias à análise. Não há nome, ID de venda, vendedor ou data individualizada. O HTML:

- não chama APIs;
- não carrega CDN, fonte, script ou imagem externa;
- não usa cookie, localStorage ou sessionStorage;
- não possui formulário de envio;
- aplica uma Content Security Policy que bloqueia conexões de rede.

## 8. Tecnologia

O dashboard é um único `index.html` com CSS, JavaScript e dados incorporados. Gráficos de barras, donut e cartões são componentes nativos, sem framework.

O gerador usa Python e `openpyxl` apenas no processo local. O dashboard publicado não precisa de servidor, banco de dados ou instalação.