# Um agente de IA que não decide permissão

## O problema
O V é o agente de IA dentro do VENDRA. A equipe pergunta em linguagem natural ("quais negócios esfriaram esta semana?") e ele consulta o sistema. O risco é o óbvio: alguém pedir "mostre tudo" e o modelo obedecer, ou um texto de fora (um arquivo, uma página) dar ordens ao agente.

## Como funciona
- **Function calling** pela API Chat Completions da OpenAI. Um modelo leve responde no dia a dia; um modelo mais forte entra só para estratégia, com teto diário de gasto em dólares. Quando o teto é batido, volta sozinho ao modelo leve e avisa.
- **Permissão no servidor, nunca no modelo.** Cada nível de acesso só recebe as ferramentas que pode usar; as outras nem chegam ao modelo. Cada ferramenta filtra pela pessoa e esconde valores de quem não deve vê-los. Pedir "mostre tudo" só traz o que a pessoa já poderia ver.
- **Propor, não executar.** O agente monta um cartão com a ação. Nada muda até a pessoa clicar em Confirmar; aí a permissão é conferida de novo e a ação roda pelas mesmas funções das telas, com registro na auditoria. Cada tipo de ação declara como se desfaz e o que não volta.
- **Texto de fora é dado, não instrução.** Arquivo anexado ou página lida marca a conversa; com essa marca, propor ações fica bloqueado. Se o sistema não consegue conferir a marca, falha fechado.
- **Dados pessoais mascarados.** Telefone e e-mail são mascarados antes de chegar ao modelo.
- **Pesquisa com fonte.** Dados de mercado vêm da Responses API com a ferramenta web_search, sempre com as fontes e com limite diário por pessoa.
- **Voz.** Transcrição e fala com os modelos de áudio da OpenAI.

## O que eu levo
Instrução no prompt ajuda, mas não é controle de acesso. O que o agente pode ver e fazer precisa ser decidido no código, antes de o pedido chegar ao modelo.
