# 63 mensagens repetidas e o portão de envio

## O problema
O VENDRA dispara mensagens de WhatsApp em lote, e quem faz o envio são cenários no Make. Numa conferência de outubro, 63 contatos tinham recebido a mesma mensagem duas vezes.

O envio passa por vários cenários: disparo inicial, follow-ups e resposta da IA. Por isso a proteção precisava valer para todos, e não só para o ponto onde o erro apareceu.

## O que fiz
Três barreiras, cada uma num ponto por onde todos os caminhos passam:

1. **Trava por telefone no banco.** Uma regra no PostgreSQL recusa o segundo envio para o mesmo telefone. Ela vale mesmo que a aplicação erre, porque está no banco.
2. **Freio de envio.** Quando algo foge do normal (por exemplo, uma lista com muitos números que a Meta recusa), a fila para e espera, em vez de seguir disparando.
3. **Portão.** Antes de enviar, o cenário do Make pergunta ao VENDRA se pode. Se não pode (por exemplo, o contato recusou ou a conversa foi desligada), a resposta é não, com o motivo.

Junto veio um auditor que roda a cada 15 minutos em dias úteis e avisa por e-mail se aparecer envio repetido.

## Resultado
Zero envios repetidos nas conferências depois da correção. O portão foi homologado em produção com uma mensagem real.

## O que eu levo
Quando várias peças podem disparar a mesma ação, a regra precisa morar no lugar por onde todas passam. No nosso caso, o banco e o portão.
