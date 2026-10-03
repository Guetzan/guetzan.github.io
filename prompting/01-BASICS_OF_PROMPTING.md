# Conceitos Básicos de Prompting

Você pode alcançar excelentes resultados com prompts simples, mas a qualidade das respostas depende de quanta informação você fornece ao modelo e de quão bem estruturado o prompt está. Um prompt pode conter elementos como a *instrução* ou a *pergunta* enviada ao modelo, além de detalhes adicionais como *contexto*, *dados de entrada* (*inputs*) ou *exemplos*. Você pode usar esses elementos para instruir o modelo de maneira mais eficaz e melhorar a qualidade dos resultados.

Vamos começar analisando um exemplo básico de um prompt simples:

*Prompt*

```text
O céu é
```

*Saída:*

```text
azul.
```

Uma observação importante é que, ao utilizar modelos de chat da OpenAI como `gpt-3.5-turbo` ou `gpt-4`, você pode estruturar seu prompt utilizando três papéis (*roles*) diferentes: `system`, `user` e `assistant`. A mensagem do sistema (`system`) não é obrigatória, mas ajuda a definir o comportamento geral do assistente. O exemplo acima inclui apenas a mensagem do usuário (`user`), que você usa para fazer solicitações diretas ao modelo. Por simplicidade, a menos que seja explicitamente mencionado, todos os exemplos usarão apenas a mensagem `user`. A mensagem `assistant` no exemplo corresponde à resposta do modelo. Você também pode definir uma mensagem de assistente para fornecer exemplos do comportamento desejado que deseja obter.

A partir do exemplo de prompt acima, note que o modelo de linguagem responde com uma sequência de tokens que faz sentido dado o contexto `"O céu é"`. A saída pode ser inesperada ou distante da tarefa que você deseja realizar. Na verdade, este exemplo básico destaca a necessidade de fornecer mais contexto ou instruções sobre o que especificamente você deseja alcançar. É exatamente disso que se trata a **engenharia de prompt** (*prompt engineering*).

Vamos tentar melhorar um pouco:

*Prompt:*

```text
Complete a frase: 

O céu é
```

*Saída:*

```text
azul durante o dia e escuro à noite.
```

Ficou melhor? Com o prompt acima, você está instruindo o modelo a completar a frase, então o resultado fica muito melhor, pois segue exatamente o que foi solicitado ("Complete a frase"). Essa abordagem de projetar prompts eficazes para instruir o modelo a executar uma tarefa desejada é o que chamamos de **engenharia de prompt** neste guia.

O exemplo acima é uma ilustração básica do que é possível com LLMs (*Large Language Models*) hoje. As LLMs atuais são capazes de realizar diversos tipos de tarefas avançadas, desde a sumarização de textos e raciocínio matemático até a geração de código.

## Formatação de Prompts

Você experimentou um prompt muito simples acima. Um prompt padrão possui o seguinte formato:

```text
<Pergunta>?
```

ou

```text
<Instrução>
```

Você pode formatá-lo em uma estrutura de Pergunta e Resposta (QA - *Question Answering*), que é padrão em muitos conjuntos de dados de QA, conforme demonstrado abaixo:

```text
P: <Pergunta>?
R: 
```

Quando você envia um prompt como o exemplo acima, ele é chamado de *zero-shot prompting*, ou seja, você está solicitando uma resposta diretamente ao modelo sem fornecer exemplos ou demonstrações prévias da tarefa que deseja que ele execute. Alguns modelos de linguagem têm a capacidade de realizar *zero-shot prompting*, mas isso depende da complexidade da tarefa, do conhecimento necessário e das tarefas para as quais o modelo foi treinado para ter um bom desempenho.

Um exemplo concreto de prompt:

*Prompt*

```text
P: O que é engenharia de prompt?
```

Com modelos mais recentes, você pode omitir o prefixo "P:", pois ele é implicitamente entendido pelo modelo como uma tarefa de pergunta e resposta com base em como a sequência é composta. Em outras palavras, o prompt poderia ser simplificado assim:

*Prompt*

```text
O que é engenharia de prompt?
```

Dada a estrutura padrão acima, uma técnica popular e eficaz de prompting é o *few-shot prompting*, em que você fornece demonstrações (exemplares) da tarefa. Você pode formatar prompts *few-shot* da seguinte maneira:

```text
<Pergunta>?
<Resposta>

<Pergunta>?
<Resposta>

<Pergunta>?
<Resposta>

<Pergunta>?
```

A versão no formato de Pergunta e Resposta (QA) ficaria assim:

```text
P: <Pergunta>?
R: <Resposta>

P: <Pergunta>?
R: <Resposta>

P: <Pergunta>?
R: <Resposta>

P: <Pergunta>?
R:
```

Lembre-se de que não é obrigatório usar o formato QA. O formato do prompt depende da tarefa que precisa ser realizada. Por exemplo, você pode executar uma tarefa simples de classificação fornecendo demonstrações que exemplifiquem o comportamento desejado:

*Prompt:*

```text
Isso é incrível! // Positivo
Isso é ruim! // Negativo
Uau, esse filme foi muito legal! // Positivo
Que show horrível! //
```

*Saída:*

```text
Negativo
```

Prompts *few-shot* habilitam o aprendizado em contexto (*in-context learning*), que é a capacidade dos modelos de linguagem de aprender tarefas a partir de poucas demonstrações.

## Créditos da Fonte Original

Este material foi traduzido e adaptado a partir do conteúdo original fornecido pelo **Prompt Engineering Guide**.

- **Fonte Original:** https://www.promptingguide.ai/
- **Projeto de Origem:** DAIR AI (Democratizing AI Research and Education)