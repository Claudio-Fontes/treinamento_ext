# Roteiro de narração — Modelos, Agentes e Multiagentes

Locução em português (Brasil), um único locutor, slide a slide. Voz sintetizada offline (MBROLA br1).

## Slide 1 — Título

Slide 1. Modelos, agentes e multiagentes. Este é um guia de workshop sobre três conceitos que costumam ser confundidos: os modelos, os agentes e os sistemas multiagentes. Ao longo da apresentação, vamos ver o que cada um é, quanto custa usar cada um, e quais são as diferenças e a relação entre eles. Os preços citados são uma referência de setembro de 2026, e mudam com frequência.

## Slide 2 — Agenda

Slide 2. Agenda. Vamos percorrer três blocos. Primeiro, os modelos: o tijolo básico. Ou seja, o que é um modelo de linguagem, como ele processa tokens e como é cobrado. Depois, os agentes: um modelo dentro de um loop, com ferramentas e um objetivo, que traz autonomia, mas com custo variável. E, por fim, os multiagentes: vários agentes coordenados, com mais poder, porém muito mais custo e complexidade. No final, fechamos com uma tabela comparativa, a relação entre os três e boas práticas de custo.

## Slide 3 — Divisor: Modelos

Slide 3. Parte um: modelos. O modelo é o bloco fundamental. Tudo o mais, agentes e multiagentes, é construído em cima dele.

## Slide 4 — O que é um modelo

Slide 4. O que é um modelo. Um modelo de linguagem é uma função treinada: ele recebe um texto, o chamado prompt, e prevê o texto mais provável em resposta, um pedaço de cada vez. Três características importantes. Ele não tem memória própria; cada chamada é isolada. Ele não executa ações no mundo; apenas produz texto. E todo o conhecimento vem do treino, mais o que você coloca no prompt. É a peça que raciocina, mas, sozinho, não faz nada além de responder. A unidade de trabalho, e também de cobrança, é o token, que equivale a cerca de três quartos de uma palavra.

## Slide 5 — Três ideias

Slide 5. Três ideias que explicam quase tudo. Primeira: o token. O texto é quebrado em tokens, e tanto a entrada quanto a saída são medidas e cobradas em tokens; não em palavras, nem em requisições. Segunda: a janela de contexto. O modelo só enxerga o que cabe nessa janela, por exemplo duzentos mil tokens; instruções, histórico e documentos disputam esse espaço. Terceira: ele é stateless, ou seja, não lembra da conversa anterior. Qualquer memória precisa ser reenviada no prompt a cada chamada, o que aumenta os tokens de entrada.

## Slide 6 — Tamanhos de modelo

Slide 6. Não existe um único modelo; existem tamanhos. Os modelos grandes, de fronteira, são mais capazes, e lidam com raciocínio complexo e código difícil; mas são mais caros e mais lentos. Os modelos médios equilibram custo e qualidade, e servem para a maioria das tarefas de produção. E os modelos pequenos são muito baratos e rápidos, ideais para classificação, extração e respostas simples em alto volume, embora com menos profundidade. A regra de ouro: use o menor modelo que resolve a tarefa com qualidade aceitável.

## Slide 7 — Como se cobra

Slide 7. Como se cobra por um modelo. A conta da API tem dois preços diferentes, medidos por milhão de tokens. Os tokens de entrada são tudo o que você envia: instruções, histórico, documentos e resultados de ferramentas; costumam ser mais baratos. Os tokens de saída são o texto que o modelo gera, e custam, tipicamente, de três a cinco vezes mais que a entrada; então respostas longas pesam. Três alavancas ajudam a baixar a conta. O cache de contexto, que reaproveita a entrada repetida por cerca de dez por cento do preço. O modo em lote, com até cinquenta por cento de desconto em tarefas não urgentes. E, simplesmente, usar um modelo menor.

## Slide 8 — Preços de referência

Slide 8. Preços de referência, por milhão de tokens. Nos modelos de fronteira, a entrada custa de cinco a dez dólares, e a saída de vinte e cinco a cinquenta. Nos modelos médios, a entrada fica entre dois e quatro dólares, e a saída entre dez e vinte. Nos pequenos, a entrada custa de cinquenta centavos a um dólar, e a saída de três a cinco. E nos modelos mini, a entrada pode custar de cinco a vinte centavos, com a saída abaixo de um dólar e vinte e cinco. A mensagem central: uma mesma resposta pode custar até cem vezes mais em um modelo de fronteira do que em um modelo mini. A diferença entre caro e barato está, principalmente, na escolha do modelo.

## Slide 9 — Divisor: Agentes

Slide 9. Parte dois: agentes. Um agente é um modelo que ganha ferramentas, um loop e um objetivo.

## Slide 10 — O que é um agente

Slide 10. O que é um agente. Um agente é um modelo colocado dentro de um loop, com autonomia para chamar ferramentas, observar o resultado e decidir o próximo passo, até atingir um objetivo. Ou seja, um agente é a soma de quatro coisas: o modelo, que raciocina; as ferramentas, que agem no mundo; o loop, que repete até concluir; e o objetivo, que define o que resolver. A diferença essencial é esta: o modelo responde uma vez; o agente age em várias etapas para chegar a um fim.

## Slide 11 — A anatomia do loop

Slide 11. A anatomia do loop. O loop de um agente tem quatro passos que se repetem. Primeiro, pensar: o modelo decide o próximo passo, a partir do objetivo e do que já sabe. Segundo, agir: ele chama uma ferramenta, como buscar, ler um arquivo, rodar código ou consultar uma interface de programação. Terceiro, observar: recebe o resultado da ferramenta de volta, como novo contexto. E quarto, repetir: reavalia, e continua o ciclo até concluir a tarefa ou desistir. Um ponto importante: cada volta do loop é uma nova chamada ao modelo, reenviando todo o contexto acumulado.

## Slide 12 — O que dá poder a um agente

Slide 12. O que dá poder a um agente. Três elementos. As ferramentas são funções que o agente pode chamar: buscar na web, ler e escrever arquivos, rodar código, acionar sistemas e serviços externos. O contexto, e a técnica de recuperação de informação, trazem documentos e dados relevantes para dentro do prompt, permitindo que o modelo responda sobre informação que não estava no treino. E a memória guarda e reintroduz fatos entre etapas ou sessões, o que dá continuidade, mas também soma tokens de entrada.

## Slide 13 — Modelo versus agente

Slide 13. Modelo, versus agente. O modelo funciona assim: uma pergunta gera uma resposta; ele não usa ferramentas nem age; é stateless, não lembra nada; tem custo previsível, de uma chamada; e é bom para gerar, resumir, classificar e traduzir. Já o agente parte de um objetivo, e o resolve em várias etapas; usa ferramentas e observa resultados; mantém estado ao longo do loop; tem custo variável, de várias chamadas, difícil de prever; e é bom para pesquisar, automatizar e resolver tarefas com passos.

## Slide 14 — Por que um agente custa mais

Slide 14. Por que um agente custa muito mais. O preço por token é o mesmo do modelo. O que muda é quantas vezes o modelo é chamado, e quanto contexto viaja a cada volta. Uma chamada vira dezenas, porque cada passo do loop é uma nova requisição. O contexto cresce, porque o histórico e os resultados de ferramentas se acumulam no prompt. Na prática, um agente costuma custar cerca de dez vezes mais do que uma única resposta. Para controlar o custo: limite o número de passos, use um modelo menor nas sub-tarefas, ative o cache do contexto repetido, e corte o histórico desnecessário.

## Slide 15 — Divisor: Multiagentes

Slide 15. Parte três: multiagentes. Vários agentes coordenados: mais capacidade, e muito mais custo.

## Slide 16 — O que é um sistema multiagente

Slide 16. O que é um sistema multiagente. São vários agentes especializados trabalhando juntos, normalmente coordenados por um orquestrador que divide a tarefa e junta os resultados. Cada agente tem um papel, como pesquisar, escrever, revisar ou calcular. Eles podem rodar em paralelo, acelerando tarefas amplas, e trocam mensagens entre si; sendo que cada troca consome tokens. Há ganho em qualidade e escopo, mas o custo e a complexidade sobem junto. E vale lembrar: cada caixa, por dentro, é um agente com o seu próprio loop.

## Slide 17 — Padrões de arquitetura

Slide 17. Padrões comuns de arquitetura. Existem quatro arranjos frequentes. No orquestrador com executores, um coordenador divide a tarefa entre agentes e consolida as respostas. No pipeline, ou sequencial, a saída de um agente é a entrada do próximo, como uma linha de montagem. No hierárquico, agentes gerentes delegam a sub-agentes, em vários níveis. E no padrão de debate, ou crítico, um agente produz, e outro critica e revisa, elevando a qualidade. A seguir, vamos detalhar os três arranjos principais: paralelo, sequencial e hierárquico.

## Slide 18 — Paralelo

Slide 18. Arranjo um: paralelo. Dispara, e junta. Aqui o orquestrador dispara vários agentes ao mesmo tempo, cada um em uma subtarefa independente, e junta as respostas no final. É o arranjo ideal quando as subtarefas não dependem umas das outras; por exemplo, pesquisar fontes distintas, processar itens de uma lista, ou gerar variações. Sobre custo e latência: a latência é baixa, porque tudo roda junto; mas o custo soma todos os agentes. É rápido, e é caro. O principal cuidado é ao juntar respostas que podem se contradizer.

## Slide 19 — Sequencial

Slide 19. Arranjo dois: sequencial. A linha de montagem. Neste arranjo, a saída de cada agente é a entrada do seguinte, e cada etapa refina o trabalho da anterior; por exemplo, pesquisar, depois rascunhar, depois revisar, e depois formatar. Ele faz sentido quando há uma ordem natural entre as etapas, e cada passo depende do resultado do anterior. Sobre custo e latência: a latência é alta, porque as etapas acontecem em série; e o custo é previsível e linear. O ponto de atenção é que um elo que falha derruba toda a cadeia.

## Slide 20 — Hierárquico

Slide 20. Arranjo três: hierárquico. Delega em níveis. Aqui um agente gerente decompõe o objetivo e delega a líderes, que, por sua vez, delegam a executores; e os resultados sobem de volta pela árvore. É indicado para tarefas grandes e ramificadas, com subprojetos que também precisam ser coordenados, e escala para muitos agentes. Sobre custo e latência: é o arranjo com o maior custo e a maior complexidade, por causa da coordenação em vários níveis. É muito poderoso, porém difícil de depurar.

## Slide 21 — Comparação das topologias

Slide 21. Paralelo, sequencial e hierárquico, lado a lado. Quanto ao fluxo: o paralelo é um leque, que dispara e junta; o sequencial é uma linha, um após o outro; e o hierárquico é uma árvore, que delega em níveis. Quanto à dependência: no paralelo, as etapas são independentes; no sequencial, cada etapa depende da anterior; no hierárquico, são subtarefas coordenadas. A latência é baixa no paralelo, e alta nos outros dois. O custo soma os agentes no paralelo, é linear no sequencial, e é alto no hierárquico. E os riscos principais são, respectivamente: juntar respostas conflitantes; um elo quebrar a cadeia; e a dificuldade de depurar. Na prática, muitos sistemas reais combinam os três.

## Slide 22 — Quando vale a pena

Slide 22. Quando vale a pena, e quando não. Faz sentido usar multiagentes quando a tarefa é ampla e se divide em partes distintas; quando papéis especializados elevam a qualidade; quando dá para paralelizar e ganhar tempo; ou quando um crítico separado reduz erros. Por outro lado, evite quando um único agente já resolve bem; quando a tarefa é simples ou exige baixa latência; quando o custo importa mais que o ganho marginal; ou quando a coordenação adiciona mais erro do que valor.

## Slide 23 — Onde o custo explode

Slide 23. Onde o custo explode. Se um agente já multiplica as chamadas, um sistema multiagente multiplica os agentes; os custos se somam, e, às vezes, se multiplicam. Com vários agentes, você tem vários loops, porque cada agente roda o seu próprio ciclo. Somam-se, ainda, os tokens de coordenação, ou seja, as mensagens trocadas entre os agentes. Na prática, um sistema multiagente costuma custar cerca de quinze vezes mais do que um único agente. Por isso, antes de escalar: comece com um agente, meça o custo real, e só adicione agentes onde o ganho de qualidade paga a conta. E use modelos pequenos nos executores.

## Slide 24 — Síntese comparativa

Slide 24. Modelo, agente e multiagente, em síntese. O modelo responde uma vez; sem ferramentas, sem memória, sem autonomia; tem baixa complexidade, custo relativo de uma vez, e baixa latência; e é melhor para tarefas únicas. O agente resolve em etapas; usa ferramentas; mantém estado durante o loop; tem autonomia média e complexidade média; custa cerca de dez vezes mais, com latência média a alta; e é melhor para tarefas com passos. O multiagente coordena vários agentes; com estado compartilhado, alta autonomia e alta complexidade; custa quinze vezes ou mais, com alta latência; e é melhor para tarefas amplas e divisíveis.

## Slide 25 — Como os três se encaixam

Slide 25. Como os três se encaixam. Eles não são alternativas; são camadas. O modelo é o núcleo que raciocina. O agente é um modelo embrulhado em um loop com ferramentas. E o multiagente é um time de agentes com um coordenador. Cada camada adiciona capacidade, e também custo, sobre a camada de dentro.

## Slide 26 — Como escolher

Slide 26. Como escolher, do mais barato ao mais caro. Comece com uma pergunta: uma única chamada resolve? Se a tarefa é única, como gerar, resumir ou classificar, use apenas o modelo. Se não, pergunte: a tarefa precisa de passos e ferramentas? Se ela exige buscar, agir e iterar até um objetivo, use um agente. E, por fim: a tarefa é ampla e divisível? Se há papéis distintos, e o paralelismo compensa, aí sim use multiagentes. A regra é subir de camada só quando a de baixo não resolve, porque cada degrau multiplica o custo.

## Slide 27 — Seis alavancas de custo

Slide 27. Seis alavancas para gastar menos. Primeira: escolher o modelo certo; o menor que entrega qualidade aceitável. Segunda: usar cache de contexto, reaproveitando entradas repetidas por uma fração do preço. Terceira: usar o modo em lote, com desconto em tarefas que não são urgentes. Quarta: limitar o loop, com um teto de passos, para evitar agentes rodando à toa. Quinta: manter o prompt enxuto, com menos tokens de entrada e de saída por chamada. E sexta: medir sempre, acompanhando o custo real por tarefa antes de escalar.

## Slide 28 — Resumo

Slide 28. Resumo, em uma frase: o modelo pensa; o agente age; e o multiagente organiza um time. Três ideias para levar. Primeira: cada camada é a de baixo mais autonomia; do modelo para o agente, e do agente para o multiagente. Segunda: o custo sobe rápido a cada camada; aproximadamente uma vez, dez vezes, e quinze vezes ou mais. E terceira: use a camada mais simples que resolve o problema, e meça o custo antes de escalar. Lembrando que os preços citados são uma referência de setembro de 2026, e devem sempre ser confirmados na tabela oficial de cada fornecedor. Obrigado.

