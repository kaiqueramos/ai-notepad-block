---
title: "Base de conhecimento"
layout: default
---

[← Voltar]({{ '/notas/fundamentos' | relative_url }})

## Base de conhecimento

Vamos partir da premissa que você tem acesso a IA de algum provedor, seja local ou na nuvem, modelo proprietário ou open-source. Tokens são caros, uns mais que outros, e brincar com tokens é mais caro ainda.
Só que, não vamos aprender nada sem gastar um pouco. Hoje, 2026, a maioria das empresas paga alguma ferramenta de IA para os desenvolvedores e tech leads, seja o ChatGPT, o Grok, o Claude, o Cursor, ou o meu favorito do momento, o Kiro (AWS). Alguns desses oferecem planos acessíveis por uma bagatela de 20~40$ (de 100 a 250 reais). Uma coisa que você irá notar, qualquer limite imposto não é generoso, pode nem ser o suficiente. Chego a consumir os 1000 créditos do cursor em 15 dias corridos.

A Inteligência Artificial aplicada ao desenvolvimento de software é, no fundo, uma geradora de texto — e texto é código, mas também é review, documentação, análise de logs, planos de teste, e qualquer outra coisa que caiba em linguagem natural ou formal. Ela vai vomitar qualquer coisa que você pedir, exatamente da forma que você pedir. Atualmente a IA possui o suficiente de "inteligência" (o que você vai descobrir logo mais que não se trata de inteligência) para ler as nuances das suas palavras, processar os tokens da sua entrada através de camadas de atenção e redes neurais, calculando probabilidades para o próximo token — não é exatamente aleatório, mas também não é determinístico.

*A analogia abaixo é propositalmente incorreta, mas serve pra criar uma intuição inicial. Não leve ao pé da letra — logo abaixo mostro como realmente funciona.*

Imagine a IA como um sistema que possui um banco de dados relacional, onde a tabela tem vários registros e várias colunas, cada coluna sendo um número, e cada registro sendo um outro número. Dentro de cada célula, temos um array de várias outras palavras:


| Registro (Linha) | Coluna 1 (Número) | Coluna 2 (Número) | Coluna 3 (Número) | ... |
|---|---|---|---|---|
| 1 | `["gato", "felino", "animal"]` | `["correr", "pular", "mover"]` | `["azul", "cor", "céu"]` | ... |
| 2 | `["carro", "veículo", "motor"]` | `["rápido", "veloz", "acelerar"]` | `["vermelho", "cor", "quente"]` | ... |
| 3 | `["código", "programa", "software"]` | `["compilar", "executar", "debugar"]` | `["função", "método", "classe"]` | ... |
| ... | ... | ... | ... | ... |

Essa representação é muito simplista, e é o que chamamos de "Embeddings". Entenda embeddings como "representações numéricas para palavras". As palavras parecidas estão, por assim dizer, correlacionadas.

Na realidade, a representação interna de um modelo de linguagem não usa palavras — usa vetores numéricos (embeddings). Cada token (palavra ou pedaço de palavra) é mapeado para um vetor de centenas ou milhares de dimensões. Abaixo, uma representação mais próxima do real, usando apenas 5 dimensões (modelos reais usam 768, 1536, ou até 12288 dimensões):

| Token | Dim 1 | Dim 2 | Dim 3 | Dim 4 | Dim 5 | ... Dim 1536 |
|---|---|---|---|---|---|---|
| "gato" | 0.231 | -0.892 | 0.045 | 0.671 | -0.334 | ... |
| "felino" | 0.228 | -0.887 | 0.051 | 0.665 | -0.329 | ... |
| "carro" | -0.654 | 0.123 | 0.789 | -0.234 | 0.567 | ... |
| "código" | 0.012 | 0.456 | -0.321 | 0.890 | 0.111 | ... |
| "compilar" | 0.018 | 0.461 | -0.315 | 0.884 | 0.105 | ... |

Note como "gato" e "felino" possuem números muito parecidos — isso é a proximidade vetorial. Palavras com significado semelhante ficam próximas nesse espaço numérico. Já "carro" tem valores completamente diferentes, porque está em outra região semântica. É assim que o modelo "sabe" que gato e felino são relacionados, sem nunca ter entendido o que é um gato.

Podemos dizer então que a IA é uma forma de calcular estatísticas. Estatisticamente, gato e felino são palavras parecidas e podem aparecer juntas, ou significarem algo parecido.

### Tokens
Falando de tokens, eles são tudo na IA. Cada frase de entrada, saída, cobrança realizada, medida de complexidade, tudo é token. Falando de formas mais subjetivas, tokens são a forma de se comunicar com a IA. Mais a frente você irá ver que a IA entende tokens diferentes de formas diferentes, e tokens parecidos de forma parecida. Isso nos permite o que chamo de economia mental de tokens, sabe quando erramos um texto e saímos apagando tudo com backspace? Dependendo do erro, não existe a necessidade de correção para a IA, ela consegue correlacionar os tokens da mesma forma.

### Formas de usar IA

Aqui irei ser breve, pretendo escrever um artigo só para isso. Existem algumas formas de usar IA, cada uma com sua vantagem e desvantagem:

- Via chat, o clássico. Sinceramente? Pra dev, é perda de tempo. Você abre o navegador, digita um prompt, copia o código, cola na IDE, vê que não funciona, volta pro chat, cola o erro, espera, copia de novo... Isso não é produtividade, é ser pombo-correio de código. Chat sem contexto de projeto é basicamente um papagaio caro. Agora, se o chat tem acesso aos seus arquivos e ao projeto, aí muda de figura — mas nesse ponto você já está mais perto de uma IDE com IA do que de um chat.

- Embeddado em alguma ferramenta corporativa. Isso é bem útil na verdade, mas atualmente ainda é bem limitado a certas ferramentas. Um exemplo é o Claude tendo acesso e modificando planilhas no Excel, ou gerando PPTs. Não sei porque cargas d'água a Microsoft não faz algo melhor. Mas aí é pedir demais também. Esse modo é muito útil para pessoas que precisam organizar dados em planilhas, ou gerar apresentações, mas hoje ainda está evoluindo. Atualmente já existem ferramentas que conseguem extrair o texto ou imagens de uma apresentação, reorganizar, e exibir em tela, mas ainda é embrionário.

- Via IDE, como o Cursor. É uma boa, conheço muitos devs que só usam o autocomplete ou pedem coisas muito específicas para o chat. Sequer testaram o que essas ferramentas proporcionam, como SDD, bughunt, Steering tools, skills, debug assistido, etc. Atualmente uso o Kiro para esses fins.

- CLI, e esse é o melhor modo na minha opinião. A máxima numero um, quando você roda a IA via CLI, ela consegue acessar todas as ferramentas de CLI. Tudo que diz respeito a um computador hoje, ao uso dele seja para desenvolvimento de software ou qualquer outra coisa, é possível ser feito via CLI. Com isso, abre-se um mundo de oportunidades para trabalhar com IA. Infelizmente isso é negligenciado pela grande maioria das pessoas. Nesse artigo vou tratar o CLI/Terminal a porta de input para se trabalhar com IA.

### IA no CLI

Não precisa ter um plano ultra pro master do Claude, nem pagar 1000 dolares no Gemini. A maioria dos providers de IA disponibilizam cotas gratis e ferramentas de CLI para uso de seus modelos. Apesar disso, recomendo fortemente que você, leitor, tenha acesso a alguma ferramenta paga.

No meu caso, uso o Kiro CLI, da AWS. O Kiro tem um plano mensal de 20$ que dá acesso a 1000 créditos, e esses créditos não são cobrados 1 a cada requisição. Cada requisição tem um peso, de no máximo 1 crédito, e no mínimo 0.01 crédito. Um pedido simples como um `whoami` é bem barato, e um plano para desenvolver um Saas que fatura 1 milhão por dia custa mais, obviamente. O Kiro como um todo disponibiliza acesso aos modelos mais avançados da Anthropic, mas peca quando fala-se de janela de contexto, limitando a janela máxima aos 200k tokens. Podemos falar mais do Kiro em outro momento.

A IA via terminal, pra mim é a grande porta de entrada para o mundo da alta performance com IA. Ela pode fazer tudo que fazemos no dia a dia, por exemplo, revisar um MR no gitlab, desde que você forneça as chaves ou instale o MCP. Ela pode se conectar a um banco de dados e realizar queries de qualquer tipo, diretamente do terminal. Ela pode acessar o google e fazer buscas. Estando no linux, muitas vezes baixamos arquivos em formatos diferentes que precisamos instalar, mas eu nunca me lembro dos comandos. Basta pedir para a IA instalar. Essas pequenas ações me fazem ganhar alguns minutos de pouco a pouco, mas geram horas no acumulado total.

Alguns comandos úteis:

`Entra na pasta de downloads e instala o arquivo XPTO`
`O PC está lento, pode analisar o que está pegando?`
`Busca na internet o changelog da ultima atualização do Kiro CLI e me explica o que mudou`
`Chama a API XPTO pra mim e vê o que retorna`
`Loga na minha AWS via SSO e ve quais instâncias do EMR ainda estão rodando`
`Entra no meu K8s e vê pra mim as especificações do pod do serviço XPTO`


As opções são infinitas. Obviamente você precisa saber o que está fazendo para lidar com a IA, por exemplo, a IA não sabe qual a sua conta AWS. Dependendo do modelo, ele vai te perguntar qual a conta, mas a IA não tem bola de cristal. Então entra a segunda grande lição, para a IA, contexto é tudo!


### Dando contexto a IA

Existem diversas táticas para gerar contexto que irei discorrer nesse bloco de notas. Ao usar IA, lembre-se que ela é um modelo estatístico treinado, provavelmente com toda a internet. Por ser estatístico, em algum embedding pode-se encontrar uma combinação onde a geração de texto te leve a uma conta AWS que por acaso teve seus dados guardados na base do modelo, quando você pedir pra ela logar na sua conta. A cada novo modelo, isso se torna cada vez mais improvável, mas pode acontecer.

Esse ponto se ressalta para tudo, senhas de banco que vazaram, senhas de APIs, secrets, tokens, emails, dados pessoais... Só que isso é assunto para outro momento.

A IA precisa saber o mínimo para seguir com a solicitação. Como disse antes, os modelos mais atuais podem te perguntar algo caso alguma informação falte, e isso é extremamente positivo. Agentes e sistemas AI-Based possuem também o que chamamos de "Base de Conhecimento" ou KB. Entenda isso como mais uma forma de RAG, e é muito útil no dia a dia. Dá pra fazer um teste, conte um pouco da sua vida ao Perplexity ou ao ChatGPT, onde você mora, ou qual o seu carro, sua cor favorita, comida favorita, talvez alguma alergia ou condição clínica. Esses modelos possuem base vetorizadas que servem como KB, e futuramente podem te dizer para não cozinhar frango xadrez com amendoim, pois você é alérgico (se você disse isso para ele), ou pelo menos te lembrar de tirar o amendoim do frango. Ou talvez ela não diga nada, afinal é um modelo estatístico.

Da mesma forma, é uma boa prática manter uma base de conhecimento local quando se fala de IA via CLI. Tente pedir para a IA acessar sua conta AWS, que possui as configurações de perfil criadas no caminho `.aws/credentials` e que ela deve guardar na KB essa forma de conexão. Das proximas vezes pode encurtar o pedido que ela vai ter contexto do que você quer fazer.

