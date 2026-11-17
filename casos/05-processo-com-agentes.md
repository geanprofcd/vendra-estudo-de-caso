# Programar com agentes de IA sem perder o controle

## Como o trabalho é dividido
Boa parte do código do VENDRA é escrita com agentes de IA de código (Claude Code), organizados como um time:

- cada agente cuida de uma área: comercial, projetos, conexões com outros sistemas, interface;
- um agente só revisa o que os outros entregam, com critérios fixos;
- outro cuida do repositório Git;
- um coordenador junta tudo e é o único que publica.

Eu decido o que entra, aprovo mudança de banco e respondo pelo que vai ao ar.

## As regras que seguram a qualidade
- **Homologação separada da produção**, com banco e configuração próprios.
- **Pacotes pequenos**, cada um com manifesto, revisão e plano de volta.
- **Migration de banco só com o meu sim**, primeiro na homologação e depois na produção.
- **Backup antes e depois** de cada publicação, com ensaio de restauração.
- **Suíte verde ou nada vai ao ar.** Mais de 1.200 testes, incluindo cliques reais no navegador.

## Um erro que virou regra
Num dia de muitas entregas, uma publicação saiu com dois testes falhando, porque o resultado estava escondido no fim do log. Não quebrou nada em produção (eram testes instáveis, não regressão), mas a regra mudou na mesma hora: agora quem decide é o código de saída da suíte, não o olho de quem lê o log.

## O que eu levo
A IA acelera muito a escrita do código. O que mantém o produto de pé é o processo em volta: revisão, testes, homologação e alguém que responde pelo resultado.
