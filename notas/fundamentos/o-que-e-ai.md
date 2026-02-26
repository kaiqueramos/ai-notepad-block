---
title: "O que é AI"
layout: default
---

[← Voltar]({{ '/notas/fundamentos' | relative_url }})

## O que é AI

Já parou pra fazer essa pergunta pra si mesmo? Mas assim, respondendo de forma inteligente, afinal você deve ser uma pessoa que já possui certa instrução sobre o tema. Já vi diversos workshops onde tem aqueles momentos de interação do público, e as pessoas respondem "Inteligencia artificial", "Claude", "GPT", "Vibe coding", até já vi alguém falando "AGI".

Vamos definir isso de uma vez? Que tal?

A resposta pra essa pergunta tem camadas, mas ligando aquilo que temos hoje com o aquilo que foi previamente definido, AI é na essência seria "Um software de reconhecimento de padrões estatísticos em escala massiva que simula comportamento inteligente sem compreensão real". O termo AI foi cunhado por John McCarthy em uma conferência em Dartmouth, em 1956. Em termos simples, essa conferencia tinha a proposta de mapear o significado da inteligência. Nesse aspecto, AI significa "Máquina ou software que raciocina como um ser humano". Sobre o significado de inteligência, não temos uma resposta até hoje.

Não existe um consenso do que é inteligência. Cada área trata de uma forma, ou várias formas, como a filosofia por exemplo. Apesar da discussão que essa pergunta pode gerar, não quero entrar no mérito aqui de definir nada ou dar minha opinião, não é esse o intuito. Acredito que estamos longe dessa definição, como humanidade.

## Pra que serve a AI

Mais uma pergunta subjetiva aqui, sim. Se remontarmos a definição dos anos 50, a AI serviria para beneficiar a humanidade, afinal, poder programar máquinas para agirem como seres humanos é incrível! Teria também algum bilionário com complexo de deus que iria pensar que é dono do mundo e geraria o caos (especulação aqui). Mas brincadeiras a parte, a nossa AI atualmente tem algumas funções muito bem definidas.

Primeiro, podemos classificar nossa AI como um "gerador de texto de luxo superestimado". Não me entenda mal, eu adoro inteligência artificial, adoro usá-las para automatizar meu dia a dia, para tirar dúvidas pontuais, executar códigos, mas ela não passa disso. Já dizia o saudoso Fábio Akita, "Sua empolgação com IA é inversamente proporcional ao seu conhecimento do tema". AIs são incríveis de fato, foi usada uma matemática absurda para possibilitar a existência delas, mas só isso mesmo.

Indo mais a fundo no tema, gosto de dizer que a AI "possibilita automações e interações em fluxos computacionais onde não era possível realizar de forma determinística, ao custo de um pouco de entropia". Gosto dessa afirmação pois, pra mim, a AI brilha justamente em automações complexas que simples if/elses não resolvem, por exemplo, redigir textos resposta para emails corporativos.

A AI também é excelente para realizar tarefas onde a definição do resultado correto é consenso. Os grandes modelos de LLM são treinados com uma grande massa de dados, muitos disponíveis na internet, e existe muita coisa boa e ruim na internet. Coisas certas e erradas. É consenso que 1+1 = 2, mas não é consenso que o homem já foi a lua, por mais louca que seja a ideia de questionar isso. Para desenvolvimento de software, um input gera um ou mais outputs, e isso é totalmente observável e metrificável.

### Para que não serve a AI

Isso é algo que vejo pouca gente falando. Sim, para a surpresa de muitas pessoas, tem coisas que a nossa AI nunca vai fazer. Não digo com relação a escala de tempo, pode ser que um dia futuro possamos definir e metrificar com exatidão a inteligência, ter um consenso de todas as areas, e construir uma máquina que aprenda de fato, mas até lá, não vamos ter a tal da AGI.

AI é péssima quando se trata de devolver resultados determinísticos e exatos. Você pode rodar um prompt 10000 vezes no ChatGPT que você vai obter respostas 10000 vezes diferentes. Atualmente é possível instruir o modelo a cuspir o resultado em um formato, mas ele pode ignorar o comando, nada o impede de fazer isso.

Em um projeto de code review com AI que estou tocando, tenho exatamente esse problema. A AI sempre gera issues quando passa em um código, e sempre que reexecuto o fluxo de revisão, ela altera o resultado, as vezes pra mais, as vezes pra menos. Apesar disso, não posso deixar um comando explícito no prompt para que a AI não gere nenhuma issue caso não seja necessário, pois isso é brincar com a entropia. Pode ser que a AI só ache um problema crítico, mas não ache relevante deixar um comentário sobre, e aprove o MR. São essas as pequenas nuances que a AI atual nunca vai resolver.

A AI nunca vai substituir os empregos que lidam com tomada de decisões considerando vários cenários. Isso requeriria uma pessoa gerando contexto para a AI tomar a decisão, e uma janela de contexto enorme. Um exemplo é quanto a programação, é possível que a AI hoje construa sim servidores que lidam com muitas requisições, mas as nuances do negócio o qual esse servidor irá rodar muitas vezes é tão profunda e complexa que nem um sistema 100% documentado teria essa possibilidade.

Em tomada de decisões que envolve risco, a AI nunca se arriscaria pelo 1% de esperança. A AI não sabe o que é esperança. Se ela tivesse que decidir em um tratamento para uma pessoa com uma doença terminal, entre um tratamento simples que melhora a qualidade de vida, sem risco, ou uma cirurgia arriscada com baixa probabilidade de sucesso, mas que possibilitaria a pessoa ficar viva, a AI sempre escolheria a opção mais segura, mesmo que isso signifique a morte de qualquer forma.

> **Disclaimer:** Este é um exemplo simplificado para ilustrar uma limitação conceitual da AI. Na prática, modelos de AI já são utilizados na medicina para auxiliar em diagnósticos e sugestões de tratamento, inclusive em cenários de risco. O comportamento real de um modelo depende diretamente de como ele foi treinado e instruído. O ponto aqui não é que a AI sempre erra nessas situações, mas que ela não possui a capacidade de ponderar fatores subjetivos como esperança, valores pessoais do paciente ou contexto emocional da forma como um ser humano faria.