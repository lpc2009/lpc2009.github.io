# TypeLab

Plataforma de estudos de TypeScript em português.

## O que está implementado
- Trilha de aulas com explicações e exemplos.
- Exercícios de múltipla escolha com feedback.
- Progresso, XP e conquistas salvos no navegador.
- Laboratório no navegador que transpila TypeScript para JavaScript e aponta problemas de sintaxe.
- Interface do tutor preparada para conversa com IA generativa e revisão de código.
- Backend Cloudflare Worker separado, com chave OpenAI guardada como segredo no servidor.

## Ativar o tutor de IA

O site público não pode guardar a chave da API. O tutor usa um Cloudflare Worker como intermediário seguro.

1. Crie uma chave de API no painel da OpenAI. A API é cobrada separadamente de uma assinatura do ChatGPT. Nunca envie essa chave pelo chat nem a coloque em arquivos públicos.
2. No painel Cloudflare, crie um Worker chamado `typelab-ai` e publique o conteúdo de `worker/index.js`.
3. Nas configurações do Worker, em Variables and Secrets, adicione `OPENAI_API_KEY` como **Secret** (não como variável pública). O arquivo `worker/wrangler.toml` já sugere o modelo `gpt-5.5`; ele pode ser ajustado com a variável `OPENAI_MODEL`.
4. Copie o endereço publicado do Worker. Ele deve terminar com `.workers.dev`.
5. No arquivo `config.js`, defina `window.TYPELAB_AI_URL` com o endereço completo, incluindo `/chat`. Exemplo de formato: `https://typelab-ai.seu-subdominio.workers.dev/chat`.
6. Salve a alteração. O site passa a chamar o tutor real e a ferramenta de correção de código.

O Worker aceita apenas solicitações vindas de `https://lpc2009.github.io`, limita o tamanho das mensagens e aplica um limite básico de solicitações por endereço IP. Esse limite em memória é uma proteção inicial, não substitui controles de produção mais robustos.

## Limitações atuais
O laboratório faz transpilação e verificação rápida de sintaxe, mas não substitui a checagem completa de tipos do compilador (`tsc --noEmit`). A correção generativa de código é feita pelo tutor de IA quando o Worker e a chave estiverem configurados.

## Publicação
Os arquivos ficam em `typelab/` dentro do repositório `lpc2009.github.io`. Se o GitHub Pages estiver publicando a branch principal a partir da raiz, a URL do projeto é:

https://lpc2009.github.io/typelab/
