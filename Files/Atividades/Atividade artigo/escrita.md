# Artigo

## Capa

- Título: Desenvolvimento centrado ao usuário como forma de viabilizar a resolução do problema de grade horária
- Disciplina: Interface Homem-Máquina
- Professor: Luis Antonio Rivera Escriba
- Aluno: João Vítor Fernandes Dias

## Introdução <!-- Deve apresentar o tema, sua importância, problemas relacionados e o objetivo -->

Com o avanço da quarta revolução industrial, têm-se visado cada vez mais a melhoria da eficiência e produtividade dos processos, com isso, processos antes realizados por humanos tendem a ser automatizados. Um dos processos que há décadas busca-se uma automatização é o agendamento de grade horária, também chamado de *timetabling* ou *timetable scheduling*.

No que consiste o *timetabling*? Esta área de pesquisa da pesquisa operacional \cite{} visa buscar formas de se alocar recursos escassos em uma tabela de horários de acordo com algumas restrições \cite{}. Uma das subcategorias dessa área de estudo é o *University Course Timetabling* \cite{} que tem como recursos a serem alocados os estudantes, professores e turmas em salas disponíveis na instituição de ensino ao longo de espações de tempo predeterminados. \cite{}

O *University Course Timetabling* é uma área de estudo que segue sendo estudada pois, dada as especificidades de cada uma das instituições de ensino, a quantidade de variáveis a serem analisadas precisam ser modeladas de acordo com suas regras. \cite{}

Ao considerarmos a alta complexidade envolvida e as possibilidades de solução para o dado conjunto de regras e variáveis, este problema acaba se tornando difícil de gerenciar de forma eficiente manualmente, porém também tem alta complexidade computacional tendo tempo de resolução não-polinomial o que o configura como um problema heurístico NP-Difícil. \cite{}

Embora hajam diversos níveis de dificuldades para este ramo de estudo, ele ainda assim segue tendo soluções práticas em cenários reais. \cite{} Essas soluções tendem a ter duas abordagens principais: uma sendo a resolução automatizada, a outra sendo o uso de uma ferramenta de assistência à decisão. Mas e qual é a diferença?

No primeiro caso, as informações base são definidas e através de um algoritmo, um ou várias soluções possíveis são encontradas. Para isto, diversas alternativas já se encontram na literatura <!-- cite artigo com muita referência -->: algoritmo genético, coloração de grafos, modelo binário, modelo de processamento de rede analítica, etc. Os maiores problemas encontrados nessa abordagem são o tempo de resolução crescer rapidamente de acordo com a quantidade de valores e variáveis; dependendo do método de resolução, pode-se encontrar máximos/mínimos locais que limitam a solução.

No segundo caso, o sistema tende a assistir o usuário a encontrar manualmente, ou fazer ajustes à soluções já encontradas no primeiro método. Esta abordagem tende a ter um contato maior com o usuário, que precisará interagir diretamente com as resoluções. Tendo o conhecimento das complexidades dimensionais, é necessário que a interface seja agradável ao usuário, tarefa crítica e de difícil alcance, dada a multitude de especialidades dos usuários e da dificuldade do problema. Mas esse é o enfoque deste trabalho.

A ideia trazida por este trabalho é a de que o desenvolvimento de um software com foco no usuário pode vir a ser uma abordagem confiável e agradável para a resolução desta problemática ainda em aberto.

<!-- Preciso esclarecer de forma escrita a diferença entre:
Problema: Timetabling/scheduling/desafios da generalização do timetabling (com a referencia do thomas lá)
Solução: solução do timetabling/dos desafios/solução final/etc.
...
-->

## Tema principal <!-- Predominando os conceitos relacionados -->

Antes de maiores aprofundamentos é necessário elucidar melhor alguns conceitos. Referentes à esta área de pesquisa.

### Agendamento de grade horária e seus termos

Nesta tarefa de definições de termos envolvendo grades horárias, Wren \cite{} realiza um bom trabalho ao definir alguns termos relevantes ao tópico e suas definições serão utilizadas como norte dos conceitos abaixo listados.

#### *Scheduling* (agendamento)

Segundo WREN: \cite{}

> O *scheduling* pode ser visto como a organização de objetos em um padrão no tempo ou no espaço, de forma que algumas metas sejam atingidas, ou quase atingidas, e que as restrições sobre a forma como os objetos podem ser organizados sejam satisfeitas, ou quase satisfeitas.
>
> Os objetos podem ser pessoas, veículos, aulas, exames, máquinas, trabalhos em uma fábrica, etc. Muitas vezes, a formação de objetos pode ser vista como parte do processo de programação.

Sendo assim, podemos considerar que o agendamento é um caso geral de organização e alocação de recursos segundo certos limites e objetivos.

#### Restrições (*constraints*)

Também segundo Wren: \cite{}

> As restrições definem relações físicas ou legais entre os objetos ou entre os objetos, outros objetos e o padrão. Elas determinam as maneiras pelas quais os objetos podem ser encaixados uns nos outros ou no padrão. As restrições podem ser vistas como regras que impedem a realização das metas. No entanto, elas também podem ser vistas como parte da especificação do problema, que pode ser usada para orientar o solucionador em direção a uma solução. Algumas restrições podem existir apenas na visão do proprietário do problema, e pode fazer parte do processo de solução indicar até que ponto uma solução pode ser melhorada se uma restrição ou restrições forem relaxadas, de modo que o proprietário possa decidir se a restrição é necessária ou quanto vale a pena gastar para abolir a restrição.

Com isso, podemos entender as restrições como limites impostos pelo sistema à alocação dos recursos. Baseado nelas, os objetivos serão alcançados respeitando ao máximos esses limites, ou então levarão em conta a possibilidade de se flexibilizar alguma delas de acordo com um peso respectivo.

#### *Timetable* (grade horária)

Wren \cite{} também cita que a grade horária em si apenas se refere a quando que determinado evento ocorrerá. Entretanto, também alerta quanto ao frequente uso do termo *timetabling* na literatura como um sinônimo de *scheduling*

#### *Class timetable*

Aqui especificamos um pouco mais quais são os recursos que deverão ser alocados, assim definindo que o contexto escolar como foco. Desse foco surgem algumas subáreas similares entre si, também categorizadas por Wren \cite{}:

- A **grade horária de salas** durante o ensino de crianças, tende a muitas vezes ser um ou poucos professores que alternam entre si em uma mesma sala, assim não havendo maiores problemas na alocação de ambos os recursos. <!-- Tá correto? -->
- A **grade horária de provas** levarão em conta a atribuição de grupos de alunos que a realizarão, bem como possíveis salas especiaias necessárias. Algumas restrições novas são consideradas nesse contexto, onde pode-se levar em conta a quantidade de provas que determinado aluno tem agendado para aquele dia ou semana, ou em períodos consecutivos.
- O foco deste trabalho é na **university class timetable** onde cada professor tem uma listagem de disciplinas que pode ministrar, eles também têm preferências de horários e cada aluno tem um conjunto de classes que pode participar, essas regras e preferências variam de instituição para instituição, podendo ter diferentes pesos a serem considerados para se alcançar o objetivo.

### Interação Humano-Máquina

O maior enfoque na pesquisa literária realizada para este trabalho foi na área da Interação Humano-Máquina, onde alguns conceitos-chave podem ser melhor esclarecidos.

- **Interface**: Segundo Paula <!-- https://doi.org/10.22456/1679-1916.21886 --> "interface de um material é a superfície que possibilita o contato entre usuário e conteúdo, ou entre usuário e usuário (no caso de estarem conectados em rede) e permite o acesso às funções do sistema."
- **Design de Interação** ***(Interaction Design - IxD)***  : Andre <!-- http://dx.doi.org/10.1088/1757-899X/407/1/012174 --> descreve o Design de interação como sendo "o princípio de se desenvolver produtos digitais com uma abordagem centrada no usuário e envolve o usuário em todo o fluxo de trabalho."
- **Análise Visual** ***(Visual Analytics)***: Para Thomas, <!-- https://doi.org/10.1109/CGIV.2009.23 --> "a análise visual é o processo iterativo que envolve a coleta de informações, o pré-processamento de dados, representação do conhecimento, interação e tomada de decisão".

## Contextualização <!-- Apresentação das características dos artigos de referência narrativa do contexto do trabalho -->

Para este trabalho, foram três os artigos lidos:

- udpSkeduler: A Web architecture based decision support system for course and classroom scheduling
- Visualization Techniques on the Examination Timetabling Pre-processing Data
- Interaction Design to Enhance UX of University Timetable Plotting System on Mobile Version

### udpSkeduler DSS

Neste artigo os autores trazem comprovações através de dados experimentais quanto aos benefícios que um Sistema de Suporte à Decisão pode trazer ao Timetabling Problem. Além disso, é desenvolvido um sistema para geração de tabelas ótimas utilizando o modelo de programação inteira, permitindo interação direta dos professores com o sistema para que adicionem suas preferências de horários de aula. Os autores também explicam a importância dos Sistemas de Suporte à Decisão, utilizando da revisão bibliográfica.

O problema encontrado pelos autores era que, na universidade em questão, o processo era gerido por 3 gestores que geravam as grades de horário e um coordenador que trabalhava exclusivamente na designação de salas, sendo então um trabalho manual que usava o cronograma do semestre anterior como um formato base. Com isso, erros eram frequentes, assim causando inúmeros conflitos colocando muitas aulas em um mesmo horário, e sobrecarregando a disponibilidade de salas. Causando então o aluguel de salas externas o que gerava problemas administrativos.

Sua motivação era então automatizar parte desse processo, para assim evitar os conflitos recorrentes e liberar estes funcionários para realizarem outras tarefas. Consequentemente atingindo também maior satisfação quanto à grade horária.

Os objetivos a serem alcançados pelo sistema eram:

1. Minimizar o uso de auditórios
2. Minimizar a alocação de aulas laboratoriais (?) fora do horário preferido
3. Minimizar conflitos de alunos e matérias que precisam
4. Minimizar o número de salas externas
5. Maximizar o uso das preferências de tempo dos professores

### Timetabling pré-processing data

O artigo em questão provê visualizações interativas úteis ao problema de de organização de horários de provas. Porém, apenas tratando dos "dados crus" (raw data), visto que esses dados são os existentes prévios ao organizador que gera novas tabelas.

O artigo foca em usar conceitos de Interface Homem Computador (IHC) para realizar a ponte entre o usuário e o sistema, considerando que o usuário precisará explorar os dados e aprender a ter insights que é o foco da visualização, sendo essa sua parte fundamental. O artigo trabalha bastante com o conceito de Visual Analytics que é descrito como "a ciência do raciocínio analítico, facilitado por interfaces visuais interativas".

Ocorre a busca por viabilizar aos designers e tomadores de decisão da tabela de horários a análise dos dados que são relevantes, mesmo sendo multidimensionais e com muitas restrições, para que por fim possam tomar decisões efetivas. Com a adaptação da análise visual e com classificação de técnicas de interação, é esperado que a ciência de interação expanda com benefícios no núcleo dos designers de timetable. Seu objetivo é expandir o papel em que a interação engaja na Infovis, onde facilita na análise dos problemas de timetable. Também é visada a pesquisa de formas com que a interação é usada em Infovis e os benefícios gerados aos usuários dos sistemas de timetable.

### Interaction Design (IxD)

Este artigo conseguiu confirmar, que a abordagem prática guiada pela metodologia de desenvolvimento chamada Design de Interação tem sucesso em guiar o desenvolvedor ao design de melhores UX e UI

O artigo também cita conceitos como a avaliação de usabilidade e também vários modelos de fluxo de trabalho como Cascata, UX Ágil, Esqueumorfismo, Five Design Sheet e por fim aborda o que escolheu para seu desenvolvimento que é o Design de Interação (Interaction Design - IxD).

O artigo buscou introduzir como a implementação do Design de Interação pode resolver o problema de UI/UX em dispositivos mobile, usando uma abordagem centrada no usuário para entregar engajamento. Aplicando isto no sistema de plotagem no quadro de horários da universidades e fazendo a Análise de usabilidade.

## Discussões <!-- Análise e discussões pertinentes em relação ao objetivo inicial -->

Considerando o objetivo do trabalho como sendo a análise do cenário geral em que se encontra a relação do Timetabling com a Interação Humano-Computador, vemos cada um dos três artigos enfocados como relevantes nessa análise.

O artigo sobre o software udpSkeduler desenvolvido por \cite{} traz à minha pesquisa a segurança na comprovação das benesses de se utilizar um sistema de suporte à decisão. Ele informa também sobre os resultados ótimos obtidos através do uso da programação inteira. Outro ponto deveras característico percebido durante seu desenvolvimento é a utilização de uma aplicação elaborada em diferentes módulos e etapas. Tendo elas tamanha relevância para tratar objetivamente sobre diferentes assuntos.

Enquanto isso, o artigo sobre dados de pré-processamento \cite{} representa a complexidade intrínseca a um problema multidimensional, sendo então difícil conceber visual e mentalmente de que forma os dados relacionados ao problema se estruturam. Dessa forma, a apresentação de diversas formas de visualização deste artigo podem ter forte influência no desenvolvimento de uma aplicação que seja interativa e engaje o usuário. Também contribui ao ilustrar novas funcionalidades que podem auxiliar o usuário a ter insights para a elaboração da grade.

Por fim, o artigo sobre o Desing de Interação \cite{} descreve o fluxo necessário para criação de interfaces de focadas ao usuário, desde o modelo usado até o resultado da satisfação dos possíveis usuários. Também informando outras metodologias possíveis, mesmo que não escolhidas. O artigo ilustra diferentes modelos visuais para a representação das tabelas utilizadas no problema, ressaltando o impacto que a alteração de cores influencia na intuitividade do usuário.

## Conclusão

Tendo em vista o que foi revisado em outras literaturas vê-se necessário que os software desenvolvidos com a finalidade de solucionar o problema de grade horária deve ter enfoque no usuário, visto que dada a complexidade intrínseca à multidimensionalidade do problema, acaba que o software tende a se tornar similarmente complexo, assim se tornando difícil de se manusear, causando então a tendência do usuário de se ater ao método vigente de resolução.

## Referências

ANDRE, A.; DINATA, H. Interaction design to enhance ux of university timetable plotting system on mobile version. IOP Conference Series: Materials Science and Engineering, IOP Publishing, v. 407, n. 1, p. 012174, aug 2018. Disponível em: <https://dx.doi.org/10.1088/1757-899X/407/1/012174>. Citado na página 8.

MIRANDA, J.; REY, P. A.; ROBLES, J. M. udpskeduler: A web architecture based decision support system for course and classroom scheduling. Decision Support Systems, v. 52, n. 2, p. 505–513, 2012. ISSN 0167-9236. Disponível em: <https://www.sciencedirect.com/science/article/pii/S0167923611001746>. Citado 2 vezes nas páginas 6 e 7.

THOMAS, J. J.; KHADER, A. T.; BELATON, B. Visualization techniques on the examination timetabling pre-processing data. In: 2009 Sixth International Conference on Computer Graphics, Imaging and Visualization. [S.l.: s.n.], 2009. p. 454–458. Citado na página 7.
