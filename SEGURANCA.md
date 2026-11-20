# Segurança do repositório de releases

## Conta e acesso

- Autenticação em dois fatores (2FA) obrigatória na conta que publica (de preferência com chave de segurança ou app autenticador, não SMS).
- Ninguém além do responsável tem permissão de escrita.
- Tokens: o sincronizador da loja só **lê** a API pública; nenhum token com escrita neste repositório é guardado na loja.

## Proteção de tags e releases

Conforme o plano disponível do GitHub:

1. **Settings → Rules → Rulesets → New tag ruleset**: alvo `*-v*`, bloqueando *deletion* e *non-fast-forward* (atualização da tag).
2. Ative **Settings → General → Releases → "Enable release immutability"**, se disponível na conta: impede alterar assets e tags depois de publicar.
3. Se rulesets não estiverem disponíveis para a conta, siga a regra operacional: tags e releases nunca são apagadas ou editadas depois de publicadas.

## Substituir uma versão problemática (sem reescrever o histórico)

1. **Não** apague a release nem substitua arquivos. Publique uma nova versão (ex.: `1.0.1`) com a correção e um novo manifesto aprovado.
2. Edite apenas o texto das notas da versão com problema, adicionando no topo: "⚠ Versão obsoleta — use 1.0.1 (motivo)".
3. Na loja, registre uma atualização `"type": "manutencao"` explicando o motivo. A versão antiga continua no histórico.
4. Se houver risco de segurança (arquivo comprometido), remova o `approved` do manifesto, publique a correção imediatamente e comunique pelo Diário e pelas notas da release.

## O que o sincronizador bloqueia

- Repositórios fora da lista autorizada, tags fora do padrão, rascunhos.
- Releases sem manifesto aprovado, arquivos extras ou ausentes.
- Divergência de tamanho, `digest`, `SHA256SUMS.txt` ou hash calculado.
- Alterações em releases que já estão no catálogo.
