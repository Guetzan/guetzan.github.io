# Exemplos de Prompts

A seção anterior introduziu um exemplo básico de como enviar prompts para LLMs.

Esta seção fornecerá mais exemplos de como usar prompts para realizar diferentes tarefas e introduzirá conceitos-chave ao longo do caminho. Frequentemente, a melhor maneira de aprender conceitos é analisando exemplos. Os exemplos a seguir ilustram como você pode usar prompts bem elaborados para executar diferentes tipos de tarefas.

Tópicos:

- Extração de Informações
- Respostas a Perguntas (QA)
- Classificação de Texto
- Conversação
- Geração de Código
- Raciocínio

## Extração de Informações

Embora os modelos de linguagem sejam treinados para realizar a geração de linguagem natural e tarefas correlatas, eles também são altamente capazes de executar tarefas de classificação e uma variedade de outros processamentos de linguagem natural (PLN).

Aqui está um exemplo de prompt para extrair informações de um determinado parágrafo:

*Prompt:*

```text
As declarações de contribuição dos autores e os agradecimentos em artigos de pesquisa devem declarar de forma clara e específica se, e em que medida, os autores utilizaram tecnologias de IA, como o ChatGPT, na preparação do manuscrito e na análise. Eles também devem indicar quais LLMs foram utilizadas. Isso alertará editores e revisores para examinarem os manuscritos com mais cuidado quanto a potenciais vieses, imprecisões e creditação inadequada de fontes. Da mesma forma, as revistas científicas devem ser transparentes sobre o uso de LLMs, por exemplo, ao selecionar manuscritos submetidos.

Mencione o produto baseado em modelo de linguagem de grande porte citado no parágrafo acima:
```

*Saída:*

```text
O produto baseado em modelo de linguagem de grande porte mencionado no parágrafo acima é o ChatGPT.
```

## Respostas a Perguntas (*Question Answering*)

Uma das melhores maneiras de fazer com que o modelo responda com precisão é estruturar adequadamente o prompt. Conforme abordado anteriormente, um prompt pode combinar instruções, contexto, dados de entrada e indicadores de saída para obter melhores resultados. Abaixo está um exemplo de como isso se parece em um prompt estruturado:

*Prompt:*

```text
Responda à pergunta com base no contexto abaixo. Mantenha a resposta curta e concisa. Responda "Incerteza sobre a resposta" caso não tenha certeza da resposta.

Contexto: O teplizumabe tem suas raízes em uma empresa farmacêutica de Nova Jersey chamada Ortho Pharmaceutical. Lá, os cientistas geraram uma versão inicial do anticorpo, apelidada de OKT3. Originada originalmente de camundongos, a molécula era capaz de se ligar à superfície das células T e limitar seu potencial de destruição celular. Em 1986, foi aprovado para ajudar a prevenir a rejeição de órgãos após transplantes de rim, tornando-se o primeiro anticorpo terapêutico permitido para uso humano.

Pergunta: De onde o OKT3 foi originalmente obtido?

Resposta:
```

*Saída:*

```text
Camundongos.
```

## Classificação de Texto

Até agora, usamos instruções simples para realizar tarefas. Para casos de uso mais difíceis, apenas fornecer instruções pode não ser suficiente. É aqui que entra o uso de `dados de entrada` ou `exemplos` adicionais.

Vamos demonstrar isso com um exemplo de classificação de texto:

*Prompt:*

```text
Classifique o texto em neutro, negativo ou positivo. 

Texto: Eu achei a comida razoável. 
Sentimento:
```

*Saída:*

```text
Neutro
```

O modelo respondeu com `'Neutro'`, o que está correto. No entanto, suponha que você precise que o rótulo seja retornado exatamente em letras minúsculas (`neutro`). Fornecer exemplos especifica o comportamento correto:

*Prompt:*

```text
Classifique o texto em neutro, negativo ou positivo. 

Texto: Achei as férias razoáveis.
Sentimento: neutro 

Texto: Eu achei a comida razoável. 
Sentimento:
```

*Saída:*

```text
neutro
```

O exemplo fornecido no prompt ajudou o modelo a ser específico na formatação da sua saída.

## Conversação

Você também pode instruir o sistema de LLM sobre como ele deve se comportar, qual é sua intenção e sua identidade. Isso é particularmente útil ao construir sistemas conversacionais, como chatbots de atendimento ao cliente.

Esta técnica é frequentemente chamada de **prompting de papel** (*role prompting*).

*Prompt:*

```text
A seguir está uma conversa com um assistente de pesquisa em IA. O tom do assistente é técnico e científico.

Humano: Olá, quem é você?
IA: Saudações! Sou um assistente de pesquisa em IA. Como posso ajudá-lo hoje?
Humano: Você pode me falar sobre a criação de buracos negros?
IA:
```

*Saída:*

```text
Certamente! Buracos negros são regiões do espaço-tempo onde a força gravitacional é tão intensa que nada, nem mesmo a luz, consegue escapar. Eles são criados quando uma estrela muito massiva morre e seu núcleo colapsa sobre si mesmo, formando uma singularidade de densidade infinita. A intensa gravidade da singularidade atrai toda a matéria e radiação ao seu redor, criando o buraco negro.
```

Podemos alterar o papel para ajustar a resposta para outro público:

*Prompt:*

```text
A seguir está uma conversa com um assistente de pesquisa em IA. As respostas do assistente devem ser fáceis de entender, mesmo para alunos do ensino fundamental.

Humano: Olá, quem é você?
IA: Saudações! Sou um assistente de pesquisa em IA. Como posso ajudá-lo hoje?
Humano: Você pode me falar sobre a criação de buracos negros?
IA:
```

*Saída:*

```text
Claro! Buracos negros são criados quando uma estrela muito grande fica sem combustível e encolhe até desmontar sobre si mesma. A gravidade dessa estrela fica tão forte que puxa tudo para perto dela, e nem mesmo a luz consegue fugir. Isso cria um ponto no espaço com uma força gigante chamada buraco negro.
```

## Geração de Código

LLMs também são bastante eficazes na geração de código. Veja dois exemplos:

*Prompt:*

```text
Peça o nome do usuário e diga "Olá"
```

*Saída:*

```javascript
let name = prompt("Qual é o seu nome?");
console.log(`Olá, ${name}!`);
```

Podemos também fornecer esquemas de dados:

*Prompt:*

```text
"""
Tabela departamentos, colunas = [DepartmentId, DepartmentName]
Tabela estudantes, colunas = [DepartmentId, StudentId, StudentName]
Crie uma consulta MySQL para todos os estudantes do Departamento de Ciência da Computação
"""
```

*Saída:*

```sql
SELECT StudentId, StudentName 
FROM estudantes 
WHERE DepartmentId IN (SELECT DepartmentId FROM departamentos WHERE DepartmentName = 'Ciência da Computação');
```

## Raciocínio

Tarefas que exigem raciocínio estão entre as mais desafiadoras para uma LLM.

Veja um exemplo de como a estruturação da instrução altera o resultado:

*Prompt:*

```text
Os números ímpares neste grupo somam um número par: 15, 32, 5, 13, 82, 7, 1. 

R:
```

*Saída:*

```text
Não, os números ímpares neste grupo somam um número ímpar: 119.
```

A resposta está incorreta. Vamos orientar o modelo a resolver a tarefa passo a passo:

*Prompt:*

```text
Os números ímpares neste grupo somam um número par: 15, 32, 5, 13, 82, 7, 1. 

Resolva dividindo o problema em etapas. Primeiro, identifique os números ímpares, some-os e indique se o resultado é ímpar ou par.
```

*Saída:*

```text
Números ímpares: 15, 5, 13, 7, 1
Soma: 41 
41 é um número ímpar.
```

Instruir o modelo a pensar em etapas melhora significativamente a capacidade de raciocínio e a precisão do resultado.

## Créditos da Fonte Original

Este material foi traduzido e adaptado a partir do conteúdo original fornecido pelo **Prompt Engineering Guide**.

- **Fonte Original:** https://www.promptingguide.ai/
- **Projeto de Origem:** DAIR AI (Democratizing AI Research and Education)
