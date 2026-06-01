# Cenários BDD

## US01 - Alerta Automático de Risco de Evasão

### Cenário 1 - Caminho Feliz

```gherkin
Cenário: Aluno identificado com risco de evasão

Dado que o aluno "João" possui frequência de 70%
E média geral de 5,5

Quando o sistema executar a análise de risco

Então o aluno deverá ser classificado como "Em Risco"
E um alerta deverá ser exibido no painel do coordenador
```

### Cenário 2 - Fluxo Alternativo

```gherkin
Cenário: Aluno com matrícula trancada

Dado que o aluno "Pedro" possui matrícula com status "Trancada"

Quando o sistema executar a análise de risco

Então nenhum alerta deverá ser gerado
E o aluno não deverá aparecer na lista de risco
```

---

## US03 - Envio Automático de Notificações

### Cenário 1 - Caminho Feliz

```gherkin
Cenário: Envio automático de notificação

Dado que o aluno "Maria" foi classificado como "Em Risco"

Quando o sistema processar os alertas

Então um e-mail deverá ser enviado para "Maria"
E o envio deverá ser registrado no histórico
```

### Cenário 2 - Fluxo Alternativo

```gherkin
Cenário: E-mail inválido

Dado que o aluno "Maria" está classificado como "Em Risco"
E possui endereço de e-mail inválido

Quando o sistema tentar enviar a notificação

Então o envio não deverá ser realizado
E uma mensagem de erro deverá ser registrada no log
```

---

## US05 - Dashboard Acadêmico Interativo

### Cenário 1 - Caminho Feliz

```gherkin
Cenário: Visualização do dashboard

Dado que existem dados acadêmicos cadastrados

Quando o coordenador acessar o dashboard

Então os gráficos de frequência deverão ser exibidos
E os gráficos de desempenho deverão ser exibidos
```

### Cenário 2 - Fluxo Alternativo

```gherkin
Cenário: Ausência de dados acadêmicos

Dado que não existem dados acadêmicos cadastrados

Quando o coordenador acessar o dashboard

Então o sistema deverá informar que não há dados disponíveis
E nenhum gráfico deverá ser exibido
```

