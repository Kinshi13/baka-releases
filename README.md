# Baka Studios — Releases oficiais

Este repositório contém **somente os arquivos oficiais de distribuição** dos aplicativos, ferramentas e jogos da Baka Studios. O código-fonte é privado e não fica aqui.

- Página oficial dos projetos: https://baka-studios-store.bakastudiosstore.workers.dev
- Baixe preferencialmente pela loja: ela mostra apenas versões revisadas e verificadas.

## Como as versões são organizadas

| Item | Convenção | Exemplo |
| --- | --- | --- |
| Tag | `<id-do-produto>-v<versão>` (SemVer) | `motion-lab-v1.0.0` |
| Pré-release (beta) | sufixo SemVer + marcada como *pre-release* | `motion-lab-v1.1.0-beta.1` |
| Arquivo | `<produto>-<versão>-<plataforma>-<arquitetura>[-setup].<ext>` | `motion-lab-1.0.0-win-x64.zip` |
| Hashes | `SHA256SUMS.txt` em toda release | — |

Plataformas: `win`, `android`, `linux`, `mac`, `chrome`, `firefox`. Arquiteturas: `x64`, `arm64`, `x86`, `universal`, `any`.

> Os exemplos acima ilustram a convenção e **não** representam lançamentos.

## Verificar um download

Compare o SHA-256 do arquivo com o valor publicado na loja e no `SHA256SUMS.txt`:

```powershell
Get-FileHash .\motion-lab-1.0.0-win-x64.zip -Algorithm SHA256
```
```bash
sha256sum motion-lab-1.0.0-win-x64.zip
```

Se não bater, **não use o arquivo** e avise a Baka Studios.

## Histórico

Releases e tags nunca são apagadas nem reescritas. Uma versão com problema recebe uma nova versão corrigida; a anterior permanece, marcada como obsoleta nas notas.
