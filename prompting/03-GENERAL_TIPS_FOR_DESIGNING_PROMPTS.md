# Dicas Gerais para a Criação de Prompts

Aqui estão algumas dicas importantes a serem consideradas ao projetar seus prompts:

### Comece Simples

Ao começar a projetar prompts, tenha em mente que este é um processo iterativo que exige muita experimentação para obter resultados ideais.

Comece com prompts simples e vá adicionando mais elementos e contexto gradualmente à medida que busca resultados melhores. Iterar no seu prompt ao longo do processo é fundamental por esse motivo. Ao longo deste guia, você verá muitos exemplos onde a especificidade, a simplicidade e a concisão trazem resultados superiores.

Quando você tiver uma tarefa grande que envolve várias subtarefas, tente dividi-la em etapas mais simples e construa a solução gradualmente. Isso evita adicionar complexidade excessiva ao design do prompt logo no início.

### A Instrução

Você pode projetar prompts eficazes para várias tarefas simples usando comandos diretos para instruir o modelo sobre o que deseja alcançar, como "Escreva", "Classifique", "Resuma", "Traduza", "Ordene", etc.

Lembre-se de que é necessário experimentar bastante para ver o que funciona melhor. Tente instruções diferentes com palavras-chave, contextos e dados distintos para identificar o que se adapta melhor ao seu caso de uso. Geralmente, quanto mais específico e relevante for o contexto para a tarefa que você deseja realizar, melhor será o resultado.

Também é recomendável colocar as instruções no início do prompt. Outra boa prática é usar separadores claros, como "###", para dividir a instrução do contexto.

Por exemplo:

*Prompt:*

```text
### Instrução ###
Traduza o texto abaixo para o espanhol:

Texto: "hello!"
```

*Saída:*

```text
¡Hola!
```

### Especificidade

Seja muito específico sobre a instrução e a tarefa que você deseja que o modelo execute. Quanto mais descritivo e detalhado for o prompt, melhores serão os resultados. Isso é particularmente importante quando você busca um resultado ou estilo de geração específico. Não existem palavras-chave mágicas que garantam resultados melhores; é mais importante ter uma boa estrutura e um prompt descritivo. Na verdade, fornecer exemplos dentro do prompt é altamente eficaz para obter respostas no formato desejado.

Ao projetar prompts, considere também o limite de tamanho (tokens) suportado pelo modelo. Avalie quão específico e detalhado você precisa ser. Incluir detalhes desnecessários nem sempre é uma boa abordagem; as informações devem ser relevantes e contribuir para a tarefa em questão.

Como exemplo, vamos testar um prompt simples para extrair informações específicas de um texto:

*Prompt:*

```text
Extraia o nome dos locais no texto a seguir. 

Formato desejado:
Local: <lista_de_locais_separada_por_virgulas>

Entrada: "Embora esses desenvolvimentos sejam animadores para os pesquisadores, muito ainda permanece um mistério. “Muitas vezes temos uma caixa-preta entre o cérebro e o efeito que vemos na periferia”, diz Henrique Veiga-Fernandes, neuroimunologista do Champalimaud Centre for the Unknown em Lisboa. “Se quisermos usá-lo no contexto terapêutico, precisamos realmente entender o mecanismo.”"
```

*Saída:*

```text
Local: Champalimaud Centre for the Unknown, Lisboa
```

### Evite a Imprecisão

Considerando as dicas acima sobre ser detalhado e melhorar a formatação, é fácil cair na armadilha de tentar ser rebuscado demais nos prompts e acabar criando descrições imprecisas. Na maioria das vezes, é melhor ser específico e direto. A analogia aqui é idêntica à comunicação humana eficaz: quanto mais direta for a mensagem, mais eficiente será a compreensão.

Por exemplo, você pode estar interessado em aprender o conceito de engenharia de prompt. Você poderia tentar algo como:

```text
Explique o conceito de engenharia de prompt. Mantenha a explicação curta, apenas algumas frases, e não seja muito descritivo.
```

O prompt acima não deixa claro quantas frases devem ser usadas nem qual estilo adotar. Embora ainda possa gerar uma resposta aceitável, um prompt melhor seria aquele que é altamente específico, conciso e direto ao ponto. Por exemplo:

```text
Use de 2 a 3 frases para explicar o conceito de engenharia de prompt para um estudante do ensino médio.
```

### O que fazer vs. O que não fazer

Outra dica comum ao criar prompts é evitar dizer o que *não* fazer e focar em instruir o que *deve* ser feito. Isso incentiva maior especificidade e direciona a atenção do modelo para os detalhes que conduzem a boas respostas.

Veja um exemplo em que um chatbot de recomendação de filmes falha exatamente no que foi pedido para não fazer, devido à forma como a instrução foi elaborada (focando no "não faça"):

*Prompt:*

```text
A seguir está um agente que recomenda filmes a um cliente. NÃO PEÇA POR INTERESSES. NÃO PEÇA INFORMAÇÕES PESSOAIS.

Cliente: Por favor, me recomende um filme com base nos meus interesses.
Agente:
```

*Saída:*

```text
Claro, posso recomendar um filme com base nos seus interesses. Que tipo de filme você gostaria de assistir? Você prefere ação, comédia, romance ou outro gênero?
```

Aqui está um prompt mais bem estruturado:

*Prompt:*

```text
A seguir está um agente que recomenda filmes a um cliente. O agente é responsável por recomendar um filme a partir da lista dos filmes mais populares do mundo atualmente. Ele deve evitar pedir as preferências do usuário e evitar solicitar informações pessoais. Se o agente não tiver um filme para recomendar, ele deve responder "Desculpe, não consegui encontrar um filme para recomendar hoje.".

Cliente: Por favor, me recomende um filme com base nos meus interesses.
Agente:
```

*Saída:*

```text
Desculpe, não tenho informações sobre seus interesses. No entanto, aqui está uma lista dos filmes mais populares do mundo no momento: [lista de filmes]. Espero que goste de algum!
```
