---
title: "Steering"
layout: default
---

[← Voltar]({{ '/notas/fundamentos' | relative_url }})

## Palavras Chave (Steering)

Como estamos falando de IA, e já sabemos que a IA na essência trabalha com probabilidade para geração de texto, precisamos entender as nuances de como trabalhar com essa geração de texto de forma assertiva. Isso me remete a um assunto que estava em alta entre vendedores uns 5~7 anos antes do boom da IA, apesar de existir desde os anos 70. Nessa época eu era vendedor, trabalhava com pessoas, uma época pré-pandemia.
Nessa época rolava um assunto entre os vendedores, onde usando certas palavras e modo de se falar, era possível influenciar os clientes a comprarem algo, ou até mesmo a comprarem um produto específico. Por exemplo, ao falar com o cliente sobre o produto, de vez em quando balançar a cabeça fazendo um sinal de "Sim" (de cima para baixo) inputava afirmação. Perguntas como "O que te impede de comprar meu produto hoje" fazia o cliente expressar os motivos para não querer comprar, o que é algo bom pois podia rebater e quebrar a negação, caso o problema fosse "está muito caro", bastava eu dizer "te consigo um desconto, pra dividir no cartão em 12x sem juros,". Existem diversas dessas técnicas, chamamos de PNL.

Ok, não precisa aprender sobre PNL para usar IA, mas você precisa entender que dizer certas palavras ou frases para a IA irá fazê-la trabalhar ou pensar de certas formas. É bem parecido com o PNL. Por exemplo, falar para a IA `resolva o bug no meu código que impede de mostrar o elemento no centro da tela` vai ter um resultado diferente e provavelmente inferior ao falar para a IA `Monte um plano de debug para entender o motivo do elemento não estar sendo exibido no centro da tela, e aperfeiçoe o plano para exibi-lo corretamente`. 

Nesse caso, "Monte um plano" é um `steering`. Steering significa "direcionar" ou "direção". Na IA é um termo usado para dar uma direção ao modelo, internamente. Existem diversas frases de steering, modos, níveis... Vamos passar por alguns deles:

### Básico de prompting

Com certeza você já fez algum curso de IA para aprender a "falar com o ChatGPT", esses cursos sempre condensam tudo em 3 "pilares", que são basicamente *Prompt Role-play*, *Few Shot Prompting* e *Chain of Thought*. Honestamente, na minha opinião são formas de steering brutas e com overhead demais.

- Prompt Role-play é quando dizemos para a IA como ela deve agir, por exemplo "Você é um desenvolvedor Senior especialista em ABC, com as soft skills XPTO...". Não que isso seja inútil — o problema é fazer isso manualmente no prompt a cada conversa. Esse tipo de instrução pertence a um rule file ou system prompt persistente, não ao chat.
- Few Shot Prompting é quando se dá algum exemplo de resposta para a IA no prompt apresentado. Dependendo do uso, essa técnica deve estar contida em algum rule file, ou contexto de agente. Essa instrução pode ser facilmente perdida ao se estender demais o chat, exigindo que se reinicie a conversa e se perca o contexto geral.
- Chain of Thought é uma técnica onde o modelo é instruído a raciocinar passo a passo antes de responder. É parecido com o steering que citei antes ("Monte um plano..."), mas não é a mesma coisa — CoT foca em mostrar o raciocínio, enquanto steering foca em direcionar a ação. Na prática, a maioria das IDEs e agentes de IA já aplicam CoT internamente.

Minha sugestão, se você usa alguma dessas técnicas, ta na hora de evoluir e colocar as coisas no lugar certo.

### Natural Language Steering

Aqui temos a premissa de que o ambiente de desenvolvimento ou de uso de IA está configurado corretamente. Você como desenvolvedor, deve aprender a usar o ambiente de desenvolvimento para personalizar e melhorar o uso da IA no dia a dia. Escolha uma ferramenta, e ajuste o que for necessário para tirar o máximo de proveito dela.
Vamos usar o Cursor aqui como exemplo. A primeira coisa, tenha um arquivo cursorrules.md configurado com tudo que você precisa que a IA use. Formas de se responder, boas práticas a se seguir, onde ela deve dar foco... se tiver dificuldades para gerar o rule file, lembre-se da primeira lição. Já tentou pedir para o Cursor gerar o rule file pra você? Felizmente ele consegue.
O segundo passo, use o modelo certo. Em qualquer IDE, a todo custo, evite usar modelos antigos ou com versões inferiores. Eu prefiro sempre usar o melhor modelo disponível, mesmo que tenha um custo superior de créditos. Esteja sempre de olho em benchmarks e noticias, atualmente o melhor modelo para código é o Claude Opus 4.6, sempre no Max e sempre no modo thinking.

O Natural Language Steering é aplicado naturalmente aqui. Abra um projeto no Cursor e peça a IDE para recuperar o contexto do projeto aberto. "Recuperar o contexto" é um steering que vai fazer a IA ler os entrypoints e outpoints da aplicação, para entender o fluxo geral. Vai fazer com que ela leia também qualquer documentação presente, e esteja pronta para realizar qualquer ação. Minha recomendação é sempre fazer isso ao entrar em um projeto, é um uso de credito extra, mas te dá mais segurança para seguir.

Quando for trabalhar com a IA, fazer vibe coding, ou spec driven development, sempre faça tudo no modo "plan" (no caso do Cursor). Lembra do básico de prompting? Está tudo condensado aqui. Basta pedir para a IA montar o plano da forma que você espera, informar qual o resultado esperado, apontar para algum card no Kanbanize/Jira/Issue do Gitlab (via MCP ou API mesmo) e validar o que foi pedido. É um steering mais óbvio e com funcionalidades especiais suportadas pela IDE. Use e abuse!

Algumas outras frases e palavras de steering:

- Vamos tomar como verdade XPTO - Afirmação de fato, ou, a IA toma o que foi dito como fato. É importante tomar cuidado aqui, a IA pode aceitar premissas falsas sem questionar e construir todo o resultado em cima delas — isso se chama sycophancy, e é o real risco de afirmar fatos para o modelo
- Me explique de forma simples - Esse é um clássico, a IA usa palavras mais simples para escrever o resultado pedido. Espere mais bullet points e afirmações diretas aqui, é péssimo para escrita de artigos e textos, fica na cara que é escrito por IA
- Faça um resumo executivo - O resumo executivo é um excelente texto simples e direto, sem tecnicidades. Ótimo para readmes e explicações gerais.
- Me pergunte caso algo não esteja claro - Essa é uma frase de steering mais avançada, fica ótima em modos de plan/spec. A IA irá gerar algumas rodadas de perguntas ao usuário, para direcionar melhor o resultado final

### Conclusão

O steering é uma ótima ferramenta de linguagem a aplicar à IA, e deve ser a base da comunicação. Existem mais inúmeras frases pouco usadas ou ainda nem descobertas. A IA é uma ferramenta com infinitas possibilidades!