# User Stories e Cenários BDD

## RF01 – Alerta Automático de Risco de Evasão

### User Story #01: Identificação Automática de Alunos em Risco

#### CARD

Como Coordenador de Curso,

eu quero visualizar alertas automáticos de alunos com risco de evasão,

para que eu possa realizar intervenções antes que o estudante abandone o curso.

#### CONVERSATION (Notas de Regra de Negócio)

* O risco deve ser identificado quando a frequência for inferior a 75%.
* O risco deve ser identificado quando a média geral for inferior a 6,0.
* Alunos com matrícula trancada ou cancelada não devem gerar alertas.

#### CONFIRMATION (Critérios de Aceite)

* [ ] O sistema deve exibir um alerta visual para alunos classificados como "Em Risco".
* [ ] O painel deve permitir filtrar alertas por curso e semestre.
* [ ] O alerta deve desaparecer automaticamente quando o aluno deixar de atender aos critérios de risco.

### Cenário 01: Identificação de Aluno em Risco (Caminho Feliz)

```gherkin
Cenário: Aluno apresenta baixo desempenho acadêmico

Dado que o aluno "João" está matriculado no curso de Sistemas de Informação
E possui frequência de 72%
E possui média geral de 5,8

Quando o sistema executar a análise de risco acadêmico

Então o aluno deve ser classificado como "Em Risco"
E um alerta deve ser exibido no painel do coordenador
```

### Cenário 02: Matrícula Trancada (Fluxo de Exceção)

```gherkin
Cenário: Aluno com matrícula trancada

Dado que o aluno "Pedro" possui matrícula com status "Trancada"

Quando o sistema executar a análise de risco acadêmico

Então nenhum alerta deve ser gerado
E o aluno não deve aparecer na lista de estudantes em risco
```

---

## RF06 – Predição Inteligente de Evasão

### User Story #02: Predição de Possível Evasão

#### CARD

Como Coordenador de Curso,

eu quero visualizar uma estimativa da probabilidade de evasão dos estudantes,

para que eu possa agir preventivamente antes que ocorram desligamentos acadêmicos.

#### CONVERSATION (Notas de Regra de Negócio)

* A predição deve considerar frequência, desempenho acadêmico e histórico do aluno.
* O cálculo deve ser atualizado automaticamente.
* O resultado deve ser apresentado em percentual.

#### CONFIRMATION (Critérios de Aceite)

* [ ] O sistema deve calcular um percentual de risco para cada estudante.
* [ ] O percentual deve ser exibido no dashboard.
* [ ] O cálculo deve ser atualizado automaticamente ao receber novos dados.

---

## RF08 – Envio Automático de Notificações

### User Story #03: Comunicação Automática com Estudantes em Risco

#### CARD

Como Coordenador de Curso,

eu quero que o sistema envie notificações automáticas aos estudantes em risco,

para que eles sejam informados sobre sua situação acadêmica e possam buscar auxílio.

#### CONVERSATION (Notas de Regra de Negócio)

* Apenas estudantes classificados como "Em Risco" devem receber notificações.
* O envio deve ocorrer por e-mail institucional.
* O sistema deve registrar todos os envios realizados.

#### CONFIRMATION (Critérios de Aceite)

* [ ] O sistema deve enviar automaticamente um e-mail ao estudante em risco.
* [ ] O motivo do alerta deve estar presente na mensagem.
* [ ] A data e hora do envio devem ser registradas no sistema.

### Cenário 01: Envio de Notificação (Caminho Feliz)

```gherkin
Cenário: Estudante recebe notificação de risco acadêmico

Dado que a estudante "Maria" foi classificada como "Em Risco"
E possui e-mail institucional cadastrado

Quando o sistema executar o processo de notificações

Então um e-mail deve ser enviado para "Maria"
E o envio deve ser registrado no histórico do sistema
```

### Cenário 02: E-mail Inválido (Fluxo de Exceção)

```gherkin
Cenário: Falha no envio de notificação

Dado que a estudante "Maria" foi classificada como "Em Risco"
E possui um endereço de e-mail inválido

Quando o sistema tentar enviar a notificação

Então o envio não deve ser realizado
E uma mensagem de erro deve ser registrada no log do sistema
```

---

## RF10 – Acompanhamento Pedagógico Personalizado

### User Story #04: Sugestão de Ações de Apoio Acadêmico

#### CARD

Como Coordenador de Curso,

eu quero receber sugestões de acompanhamento pedagógico para estudantes em risco,

para que eu possa oferecer apoio adequado às necessidades de cada aluno.

#### CONVERSATION (Notas de Regra de Negócio)

* O sistema poderá sugerir monitorias.
* O sistema poderá sugerir orientação pedagógica.
* As recomendações devem considerar o histórico acadêmico do estudante.

#### CONFIRMATION (Critérios de Aceite)

* [ ] O sistema deve sugerir pelo menos uma ação de apoio acadêmico.
* [ ] As sugestões devem ser exibidas no perfil do estudante.
* [ ] As recomendações devem considerar o histórico acadêmico disponível.

---

## RF02 – Dashboard Acadêmico Interativo

### User Story #05: Monitoramento Acadêmico por Dashboard

#### CARD

Como Coordenador de Curso,

eu quero visualizar indicadores acadêmicos em um dashboard interativo,

para que eu possa acompanhar rapidamente a situação das turmas e dos estudantes.

#### CONVERSATION (Notas de Regra de Negócio)

* O dashboard deve apresentar indicadores de frequência.
* O dashboard deve apresentar indicadores de desempenho acadêmico.
* As informações devem ser atualizadas automaticamente.

#### CONFIRMATION (Critérios de Aceite)

* [ ] O dashboard deve exibir gráficos de frequência acadêmica.
* [ ] O dashboard deve exibir gráficos de desempenho acadêmico.
* [ ] Os dados apresentados devem refletir as informações mais recentes do sistema.

### Cenário 01: Visualização de Indicadores (Caminho Feliz)

```gherkin
Cenário: Coordenador acessa dashboard acadêmico

Dado que existem dados acadêmicos cadastrados no sistema

Quando o coordenador acessar o dashboard

Então os gráficos de frequência devem ser exibidos
E os gráficos de desempenho acadêmico devem ser exibidos
```

### Cenário 02: Ausência de Dados (Fluxo de Exceção)

```gherkin
Cenário: Dashboard sem informações disponíveis

Dado que não existem dados acadêmicos cadastrados

Quando o coordenador acessar o dashboard

Então o sistema deve exibir a mensagem "Nenhum dado disponível"
E nenhum gráfico deve ser apresentado
```
