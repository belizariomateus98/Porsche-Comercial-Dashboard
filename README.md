Dashboard de Performance Comercial Porsche

Um dashboard interativo de performance comercial, desenvolvido em uma única página HTML, utilizando a aba Sanitized da planilha de vendas Porsche fornecida.

Dashboard

Após a ativação do GitHub Pages, o dashboard estará disponível no endereço:

https://<usuario-github>.github.io/<nome-repositorio>/

Status da publicação: ainda não publicado. É necessário conectar a conta do GitHub e aprovar a exposição dos dados antes de disponibilizar uma versão pública.

Questões de negócio selecionadas — e justificativas

O dashboard foi desenvolvido para responder a questões relevantes para a gestão de performance comercial:

Quem gera o maior faturamento e quem possui o maior ticket médio?
Essa análise diferencia o desempenho em volume de vendas do valor financeiro das transações, permitindo identificar vendedores que se destacam pela quantidade de vendas ou pela comercialização de produtos de maior valor.

Qual estado lidera em faturamento e qual possui o maior ticket médio?
A base de dados contém informações de estados e cidades, mas não apresenta uma classificação explícita por região. Por isso, o estado foi utilizado como dimensão geográfica de comparação, evitando agrupamentos não fundamentados.

Qual modelo Porsche vende mais unidades e qual gera o maior faturamento?
A quantidade de unidades vendidas e o faturamento respondem a questões diferentes sobre o portfólio de produtos: popularidade e contribuição financeira.

Como as vendas evoluem mensalmente e quais cidades mais contribuem para o faturamento?
A evolução mensal permite acompanhar tendências e possíveis sazonalidades. Já o faturamento por cidade ajuda a identificar a concentração geográfica das vendas.

O ranking dos vendedores apresenta os dez melhores desempenhos em faturamento, com destaque visual para os três primeiros colocados. A análise de ticket médio considera, sempre que possível, vendedores com pelo menos duas transações, reduzindo a influência de uma única venda de valor excepcional.

Histórico dos prompts e evolução até a versão final

O dashboard foi desenvolvido de forma iterativa, a partir de quatro solicitações principais:

Prompt 1 — Solicitação inicial

Desenvolva um dashboard profissional de performance comercial em HTML, utilizando a planilha anexada e a aba Sanitized como principal fonte de dados, com a aba de tabela dinâmica como referência complementar. Inclua filtros por mês e ano de venda, estado, forma de pagamento e status de entrega; indicadores de faturamento total em USD, quantidade de vendas e ticket médio; respostas às questões de negócio sobre melhor vendedor, desempenho geográfico e desempenho dos modelos Porsche; ranking dos dez melhores vendedores, com destaque para os três primeiros; gráfico de evolução anual das vendas e gráfico de Pareto 80/20 por cidade. Utilize o site internacional da Porsche como inspiração visual, com uma identidade elegante, premium, minimalista e sofisticada. Todo o conteúdo do dashboard deve estar em inglês.

Prompt 2 — Refinamento visual e evolução mensal

O design foi aprimorado com imagens da Porsche, maior presença da paleta dourada, tipografia ampliada e remoção de legendas e subtítulos desnecessários.

O filtro de data foi simplificado para somente o ano. O gráfico de evolução anual foi transformado em um gráfico de evolução mensal das vendas, exibindo os meses do ano selecionado. O gráfico de Pareto por cidade foi substituído por um gráfico de colunas mais simples.

Prompt 3 — Indicador financeiro por cidade e filtros múltiplos

O gráfico de cidades deixou de apresentar a quantidade de transações e passou a exibir o valor financeiro das vendas por cidade.

Todos os filtros foram transformados em seleções múltiplas (multi-select). Os textos das opções e dos filtros passaram a utilizar a cor dourada sobre um fundo cinza-claro.

A identidade visual também foi ajustada para uma combinação de cinza-claro, preto e dourado.

Prompt 4 — Identificação dos meses com o respectivo ano

Os rótulos do gráfico de evolução mensal foram atualizados para incluir o ano, por exemplo, Jan/24, permitindo identificar corretamente os períodos e diferenciar meses pertencentes a anos distintos.

Preparação dos dados antes da utilização da IA

A planilha original contém duas abas: Tabela_Dinamica e Sanitized.

A aba Sanitized foi selecionada como fonte principal de dados, contendo 100 registros e 12 colunas.

A aba Tabela_Dinamica apresenta uma estrutura pré-agregada, semelhante a uma tabela dinâmica, com células em branco e particularidades de formatação. Por esse motivo, não foi utilizada como fonte principal para a análise dos registros individuais.

Não foram identificados valores ausentes nos 100 registros analisados da aba Sanitized.

A coluna SaleDateSanitized foi interpretada como data, considerando o formato original YYYY-MM-DD. O dashboard agrupa as informações por ano e mês, sem utilizar os dias como filtro.

Os nomes dos vendedores foram padronizados para o formato de iniciais maiúsculas, garantindo consistência na consolidação dos dados (por exemplo, variações como kevin e KEVIN passam a ser exibidas de maneira uniforme).

O conjunto de dados utilizado no dashboard contém somente os campos necessários para os indicadores e gráficos: identificador da venda, data, modelo Porsche, ano do modelo, preço de venda, forma de pagamento, cidade, estado, vendedor e status de entrega. Os nomes dos clientes e a quilometragem dos veículos foram excluídos, pois não eram necessários para as análises solicitadas.

Os valores de venda são apresentados em USD porque a solicitação inicial determinou essa moeda. Entretanto, a planilha não possui um campo específico que confirme a moeda original. Portanto, trata-se de uma premissa de apresentação, e não de uma conversão cambial comprovada.

Nenhum valor de venda foi convertido ou recalculado. O ticket médio é calculado dividindo o faturamento total pela quantidade de transações.

Ferramentas e abordagem de implementação

O dashboard foi desenvolvido por meio de um fluxo conversacional de programação com o ChatGPT, resultando em uma página HTML independente, utilizando JavaScript e a biblioteca Chart.js.

ChatGPT Canvas: não utilizado.

Agente com skill: não utilizado.

Ambos: não. O projeto não foi desenvolvido por meio do Canva nem de um fluxo baseado em agente com habilidades específicas. Foi uma implementação direta em HTML, CSS e JavaScript, aprimorada iterativamente a partir dos quatro prompts apresentados.

O arquivo HTML contém os dados utilizados pelo dashboard e utiliza a biblioteca Chart.js por meio de uma CDN. Portanto, é necessária uma conexão com a internet para o carregamento dos gráficos.
