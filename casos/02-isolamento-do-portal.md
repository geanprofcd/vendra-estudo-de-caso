# Um cliente não pode ver o outro: 80 rotas testadas

## O problema
O VENDRA tem um portal onde cada empresa cliente acompanha o próprio projeto, com tarefas, documentos e prazos. A equipe interna enxerga todos os clientes; o cliente, só o dele. Um erro aqui expõe o dado de uma empresa para outra.

## O que fiz
- Cada empresa cliente ganha um espaço próprio. Ao criar o espaço, o sistema copia apenas a estrutura (status, etiquetas e campos), nunca dados de outros clientes.
- O papel "cliente" é isolado e decidido no servidor, em cada rota. Pessoas de fora do escopo aparecem só como "Equipe".
- A liberação fica atrás de uma chave de configuração, desligada por padrão, e só é ligada depois do teste.

## Como provei
Criei dois clientes de teste, A e B, e passei por 80 rotas do sistema com um tentando abrir o que é do outro: listas, tarefas, documentos, busca, caixa de entrada. Só liberei quando nenhuma rota deixou passar nada. As contas e os dados de teste foram apagados no fim.

## O que eu levo
Segurança em sistema pequeno costuma ficar para depois. Preferi que ela viesse antes do primeiro cliente entrar.
