# 2 . Validação de Hipótese ColdWheel

![image](https://github.com/user-attachments/assets/9b4350c0-f842-4046-bdff-c6e01848bcfe)

R-squared:  0.922

Log-Likelihood: 30 .68

Ferramentas e Frameworks: 

| Pyhton | Correlation matrix
**Stepwise →**  identificar o conjunto de variáveis que melhor explica a variável dependente
**Regressão Linear + Box-Cox**
Shapiro_francia **→** Teste de verificação da aderência dos resíduos à normalidade |
| --- | --- |
| Coleta de Dados | ElasticSearch API pyhton - Dados Equipamento
WebScraping - GOP dados posicionamento de trem |

### **Descrição para o Stakeholder:**

Na ferrovia, utilizamos um equipamento chamado ColdWheel, responsável por identificar se os vagões estão freando corretamente. Em determinado período, esse equipamento começou a apresentar um alarme denominado *Low Limit*, indicando que a temperatura mínima esperada não estava sendo atingida.

Junto aos especialistas de campo, levantamos a hipótese de que esse comportamento estava relacionado à combinação entre o peso do trem, a aplicação dos freios e a quantidade de locomotivas. Para validar essa hipótese, aplicamos métodos estatísticos e matemáticos, que confirmaram nossa teoria com base nos dados coletados. Esse estudo trouxe maior confiança na interpretação dos alarmes do equipamento, aprimorando a precisão das análises operacionais.

### **Descrição Técnica:**

### **Coleta de Dados**

- Os dados do **ColdWheel** foram extraídos da **API do Elasticsearch** na **AWS**.
- Foi realizado um tratamento dos JSONs presentes nos pacotes de leitura do equipamento.
- **Web Scraping** foi utilizado para coletar dados de operação do trem, incluindo:
    - Aplicação de freio
    - Condução
    - Peso do trem
    - Quantidade de vagões
    - Outros fatores relevantes
- Os dados das duas fontes foram integrados para dar início ao estudo.

### **Análise e Validações**

- Inicialmente, toda a base foi tratada e limpa para utilizar apenas dados válidos, relacionados ao alarme em análise.
- Aplicamos uma matriz de correlação para identificar as variáveis que apresentam relação com a variável de interesse (*Y*).
- Para validar essas variáveis, utilizamos o método **Stepwise**, desenvolvido pela **USP**, com o objetivo de remover variáveis que:
    1. Sejam insignificantes (*p-valor alto*).
    2. Apresentem multicolinearidade.
    3. Tenham baixo poder explicativo (*coeficiente de regressão padronizado baixo*).
    4. Sejam redundantes (*informação duplicada no modelo*).
    5. Apresentem alta variância (*instáveis ao longo do tempo*).
- Aplicamos um modelo de **regressão linear**, associado a uma **transformação Box-Cox**, para melhorar a distribuição dos dados e validar a hipótese estatística com *p-value e r²*.
- Por fim, realizamos o **teste de Shapiro-Francia** para verificar a aderência dos resíduos à normalidade.
- Com esses testes estatísticos, comprovamos a relação entre as variáveis e a temperatura média dos vagões.

### **Visualização**

- Comparação entre valores ajustados (*fitted values*) e valores reais.

> Mais informações disponíveis no repositório do Git.
> 

### **Resultados e Ganhos:**

- Validamos matematicamente a hipótese levantada pelos especialistas, concluindo que há uma relação direta entre a **pressão de aplicação dos freios (PSI), temperatura e número de locomotivas**. Esses fatores impactam a temperatura média dos rodeiros do trem, influenciando o acionamento do alarme *low limit* do equipamento.
- Confirmamos que as medições do equipamento estavam corretas e que determinados tipos de trem apresentavam esse alarme devido às características operacionais identificadas no estudo.
