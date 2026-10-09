# Segurança e privacidade

## Características do projeto

O dashboard publicado:

- não contém nomes, IDs ou vendedores;
- não carrega recursos externos;
- não chama APIs;
- não usa cookies ou armazenamento persistente;
- não envia dados pela rede;
- possui Content Security Policy com `connect-src 'none'`;
- funciona sem backend.

A planilha-fonte é baixada localmente em `data/source/`, caminho ignorado pelo Git. Somente o CSV minimizado é publicado.

## Relato responsável

Se encontrar uma exposição de dados ou vulnerabilidade, evite abrir uma issue com detalhes exploráveis. Entre em contato pelo perfil do autor no GitHub e informe:

- componente afetado;
- passos para reprodução;
- impacto;
- correção sugerida, se possível.

## Dados reais

Este projeto usa uma base educacional. Não substitua o conteúdo por dados reais sem avaliação de base legal, anonimização, controle de acesso e política de retenção.
