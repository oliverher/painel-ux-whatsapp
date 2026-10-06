# Painel UX · Canal WhatsApp do Estado de Goiás

Painel de gestão da Pesquisa de Experiência do Usuário do WhatsApp do Estado de Goiás, (62) 3201-8700. GEEU / SCTP / SEAD-GO.

Endereço: https://oliverher.github.io/painel-ux-whatsapp/

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | O painel (página única, sem servidor) |
| `data.json` | Base em uso, gerada a partir da planilha "Base e Painel - Pesquisa UX WhatsApp" |
| `historico.json` | Registro das atualizações feitas pelo botão "Atualizar base" |
| `config.json` | Token do GitHub cifrado com a senha da equipe. Criado na primeira configuração |

## Como atualizar a base

1. Abra o painel e clique em **Atualizar base**.
2. Digite a senha da equipe.
3. Envie a planilha `.xlsx` com as abas QUANTI_JORNADA, TRIAGEM e QUALI_ENTREVISTAS.
4. Confira o resumo e clique em **Publicar no GitHub**. O endereço público mostra a nova versão em 1 a 2 minutos.

## Configuração inicial (uma única vez)

Enquanto o repositório não tem `config.json`, o primeiro envio pede um token do GitHub:

1. Em GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens**, gere um token com:
   - Repository access: **Only select repositories** → `painel-ux-whatsapp`
   - Permissions → Repository → **Contents: Read and write**
   - Validade de sua escolha (quando vencer, gere outro e apague o `config.json`)
2. No painel, clique em **Atualizar base**, digite a senha da equipe e cole o token.

O painel guarda o token cifrado (AES-GCM, chave derivada da senha por PBKDF2 com 310 mil iterações). Depois disso, a equipe só precisa da senha.

## Limites de segurança

- O repositório é público: `data.json` pode ser lido por qualquer pessoa que tenha o link.
- A proteção do envio depende da força da senha. Senha curta ou previsível pode ser descoberta por força bruta a partir do `config.json`. Use uma senha longa e troque-a quando alguém sair da equipe (apague o `config.json` e refaça a configuração).
- O token deve ter acesso apenas a este repositório.
