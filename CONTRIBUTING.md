# Contribuindo

Contribuições de código, documentação, acessibilidade e testes são bem-vindas.

## Fluxo

1. Crie um fork e uma branch curta.
2. Não adicione a planilha-fonte ou dados identificáveis ao Git.
3. Execute:

```bash
python scripts/gerar_dashboard.py
python scripts/verificar_dashboard.py
```

4. Confirme `VALIDAÇÃO APROVADA`.
5. Teste o `index.html` em computador e celular.
6. Abra um pull request explicando a motivação e o impacto.

## Regras

- preserve a minimização dos dados;
- não adicione CDN, API ou rastreamento;
- mantenha o dashboard funcional como arquivo único;
- documente qualquer mudança de regra de negócio;
- não use logotipos, fotografias ou entregas de terceiros sem licença compatível;
- mantenha navegação por teclado e contraste WCAG AA.
