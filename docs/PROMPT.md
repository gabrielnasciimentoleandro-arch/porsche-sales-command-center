# Prompt e refinamento

## Prompt orientador usado com o agente

> Atue como analista de dados, designer de dashboards e desenvolvedor front-end. Use a planilha sanitizada da Porsche disponibilizada no desafio DIO, sem copiar o dashboard do professor ou de outros participantes.
>
> Primeiro, audite as 100 linhas e compare as colunas cruas com as versões sanitizadas. Para a versão pública, remova identificadores, nomes de clientes, vendedores, valores crus e qualquer campo que não seja necessário à análise.
>
> Crie um dashboard autoral chamado **Porsche Velocity — Sales Command Center** em um único arquivo `index.html`, compatível com GitHub Pages e funcional também ao abrir localmente. Não use API, backend, biblioteca externa, CDN, cookie ou armazenamento persistente.
>
> O painel deve responder a quatro perguntas:
>
> 1. Em quais famílias Porsche o valor comercial se concentra?
> 2. Quais estados lideram em valor?
> 3. Quais métodos de pagamento movimentam mais valor e qual é seu ticket médio?
> 4. Como os registros se distribuem entre entregues, em andamento e cancelados?
>
> Adote como métricas centrais: valor ativo, negócios ativos, ticket médio ativo, taxa de entrega e valor cancelado. Não trate cancelamentos como receita ativa.
>
> Inclua filtros por família, estado, ano-modelo, pagamento e etapa; filtros por clique nos gráficos; botão para limpar; exportação CSV da seleção; tema claro/escuro; ranking de modelos; seção de qualidade de dados; layout responsivo; navegação por teclado; textos visíveis e rótulos acessíveis.
>
> Use uma identidade visual própria, premium e sóbria, inspirada no universo automotivo: preto, marfim, vermelho e dourado. Não use logotipo oficial ou fotografias protegidas.
>
> Como a data sanitizada contém `INVALID` e datas futuras, não use série temporal nos indicadores. Mostre essa limitação na metodologia.
>
> Gere também scripts reproduzíveis de preparação e validação, documentação do processo, capturas da tela padrão e de um filtro aplicado e instruções para publicação no GitHub Pages.

## O que mudou até a versão final

A ideia inicial era um painel genérico de vendas com total, quantidade e gráficos convencionais. O refinamento mudou decisões importantes:

1. **Perguntas antes dos gráficos:** cada visual recebeu uma pergunta explícita de negócio.
2. **Valor ativo separado do bruto:** sete cancelamentos deixaram de inflar a métrica principal.
3. **Datas removidas dos KPIs:** 24 valores estão marcados como `INVALID`, e a faixa válida avança até 2027.
4. **Privacidade por design:** IDs, clientes, vendedores e colunas cruas foram excluídos do HTML e do CSV público.
5. **Famílias derivadas:** 40 versões de modelo foram consolidadas em seis famílias úteis à gestão.
6. **Etapas consolidadas:** dez situações operacionais foram organizadas em Entregue, Em andamento e Cancelado.
7. **Sem dependências externas:** os gráficos foram implementados com HTML e CSS em vez de biblioteca via CDN.
8. **Interação reforçada:** além dos cinco seletores, barras e legenda também funcionam como filtros.
9. **Acessibilidade e celular:** contraste, teclado e responsividade foram testados em navegador real.
10. **Reprodução automatizada:** a fonte é conferida por SHA-256, e scripts geram e validam a entrega.

## Modalidade de IA utilizada

Foi usado **um agente com ferramentas e skill de análise, desenvolvimento e validação**, no Arena.ai Agent Mode. O fluxo não utilizou ChatGPT Canvas. A skill versionada está em [`skills/porsche-dashboard/SKILL.md`](../skills/porsche-dashboard/SKILL.md).

A IA foi usada como parceira de execução e revisão; as perguntas, regras de negócio, escolhas de privacidade e critérios de aceite permaneceram explícitos e verificáveis no repositório.