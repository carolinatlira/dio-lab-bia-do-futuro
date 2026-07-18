# Base de Conhecimento

## Dados Utilizados

Os arquivos usados se encontram na pasta data:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `base_referencia_designer_grafico.json` | JSON | Serve como benchmark de mercado |
| `conceitos_financeiros.json` | JSON | Fornece o embasamento financeiro das análises |
| `dados_usuario.json` | JSON | Serve como fonte de dados personalizada |
| `tributacao.json` | JSON | Orienta o agente sobre os principais regimes tributários e seus impactos na precificação |


---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Deletei os arquivos: historico_atendimento.csv, perfil_investidor.json, produtos_financeiros.json e transacoes.csv.
Adicionei os arquivos: base_referencia_designer_grafico.json, conceitos_financeiros.json, dados_usuario.json e tributacao.json.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Os dados serão armazenados em arquivos JSON e carregados pelo sistema no início da execução. O agente acessará essas bases sempre que precisar consultar informações do usuário, conceitos financeiros, tributação e benchmarks de mercado para gerar análises e recomendações.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

O system prompt conterá apenas as instruções de comportamento do agente, definindo seu papel como consultor estratégico de precificação e suas regras de atuação. As bases de conhecimento (base_referencia_designer_grafico, conceitos_financeiros e tributacao) serão consultadas dinamicamente pelo sistema sempre que necessário. Os dados relevantes recuperados serão inseridos no contexto da requisição enviada ao modelo, juntamente com as informações fornecidas pelo usuário (dados_usuario), permitindo que o agente gere respostas personalizadas e fundamentadas.

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
System Prompt:
Você é um agente especialista em precificação para designers gráficos freelancers. Sua função é analisar os dados do usuário, utilizar as informações da base de conhecimento e fornecer recomendações estratégicas, profissionais e fundamentadas. Não substitua um contador nem forneça aconselhamento jurídico.

Dados do Usuário:
- Profissão: Designer Gráfico Freelancer
- Experiência: Pleno
- Regime tributário: Simples Nacional
- Custos mensais: R$ 5.500
- Horas faturáveis: 120 horas/mês
- Valor cobrado atualmente: R$ 75/hora
- Meta de lucro: 30%

Base de Conhecimento (trecho):
- Valor médio por hora para Designer Pleno: R$ 100/hora
- Faixa de mercado: R$ 80 a R$ 130/hora
- Margem de lucro recomendada: 30%
- Regra: Alertar quando o valor cobrado estiver mais de 15% abaixo da média do mercado.

Solicitação do usuário:
"Estou cobrando um valor justo pelos meus serviços?"
```
