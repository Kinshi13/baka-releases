# Procedimento de publicação

Somente a conta responsável publica releases. Nenhum binário experimental é publicado como release oficial (use pré-release apenas para betas aprovadas).

## 1. Empacotar (no repositório privado do produto)

1. Gere os arquivos finais a partir de uma tag do código, com build reproduzível.
2. Nomeie conforme a convenção do README.
3. Windows: assine digitalmente, se possível. APK: assine com a chave de release (guardada fora de qualquer repositório).

## 2. Manifesto de aprovação (no repositório da loja)

```powershell
npm run release:manifest -- motion-lab 1.0.0 .\dist-release
```

- Cria `src/data/releases/motion-lab-v1.0.0.json` com `approved: false`, tamanhos e SHA-256.
- Cria `.\dist-release\SHA256SUMS.txt`.
- Preencha título, resumo e mudanças; abra um PR na loja para revisão.

## 3. Publicar a release (neste repositório)

```powershell
gh release create motion-lab-v1.0.0 .\dist-release\* --repo Kinshi13/baka-releases --title "Motion Lab 1.0.0" --notes-file notas.md
```

Para beta, adicione `--prerelease`. Envie **exatamente** os arquivos do manifesto, mais o `SHA256SUMS.txt`, sem extras.

## 4. Aprovar e sincronizar (na loja)

1. Mude `approved` para `true` no manifesto (PR revisado).
2. Rode `npm run sync:releases` (ou o workflow "Sincronizar releases"). O sincronizador baixa cada arquivo, confere tamanho, `digest` da API, `SHA256SUMS.txt` e o SHA-256 calculado com o manifesto.
3. Revise o PR gerado e mescle: o Cloudflare publica a nova versão na loja.

## Notas da versão (modelo)

```markdown
## Novidades
- …

## Correções
- …

## Verificação
Os hashes SHA-256 estão em SHA256SUMS.txt e na página do produto na Baka Studios Store.
```
