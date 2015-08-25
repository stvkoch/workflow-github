### Tradução livre do artigo http://hugogiraudel.com/2015/08/13/github-as-a-workflow/

Nota: Há termos que estão propositadamente sem serem traduzidos, penso que o
termo traduzido dificulta o entendimento do significado da expressão.

---


# GitHub como um workflow

Este artigo é o resultado da discussão sobre o fluxo de desenvolvimento com um
dos nossos Scrum Master em Edenspiekermann. É assumido que o leitor tenha noções
básicas sobre desenvolvimento Ágil como
[Agile](https://en.wikipedia.org/wiki/Agile_software_development) e
[Scrum](https://en.wikipedia.org/wiki/Scrum_\(software_development\)). Se não
for o seu caso, ainda assim se benificiará da leitura desde artigo mesmo que
falte alguns pontos chaves para o pleno entendimento. É desejavel que tenha
noções do conceito de [Gitflow](https://www.atlassian.com/git/tutorials/
comparing-workflows/gitflow-workflow/) workflow, embora não dependa dele.

Neste pequeno documento, eu tento descrever oque seria, para mim, um ótimo fluxo
de trabalho usando o [GitHub](https://github.com) como "peça chave" em vez de
ter uma colecção de ferramentas e commandos. É óbvio que este ponto-de-vista é
centrado na ótica do desenvolvedor e pode não se enquadrar em todas as equipas
e projectos.

Dado que o artigo pode ser um pouco longo, abaixo há um indexe de conteúdo para
que consigas ir directo a secção que desejas:

  1. Introdução
  2. Qual o problema que resolve
  3. Qual o problema que isso adiciona
  4. Criando um pull-request
  5. Nomeando um pull-request
  6. Adicionando uma descrição
  7. Usando comentários
  8. Revisando pull-request
  9. Mesclando pull-request
  10. Dica: usando labels
  11. Dica: usando atribuições(assignees)
  12. Dica: usando objectivos (milestones)
  13. Dica: usando problemas (issues)




## Introdução


Segue-se uma pequena e informal metodologia de como se tirar partido do
[GitHub](https://github.com) para ter fluxo de trabalho em projectos de
desenvolvimento usando [pull-
requests](https://help.github.com/articles/using-pull-requests/). Embora a
primeira vista possa parecer um pouco medonho, esta abordagem pode trazer um
monte de benefícios, tal como iremos investigar nas próximas sessões.

Grosseiramente, a ideia é começarmos a
[sprint](http://scrummethodology.com/scrum-sprint/), criado N pull-request
para todas as nossas [user stories](http://scrummethodology.com/scrum-user-
stories/). Na descrição do pull-request, nós escreveremos a lista de tarefas no
formato Markdown [GitHub support for
checkboxes](https://github.com/blog/1375%0A-task-lists-in-gfm-issues-pulls-
comments). Os desenvolvedores irão enviar seus commits para o branch do
pull-request e progressivamente irão concluir as tarefas listadas no
pull-request. Uma vez as tarefas concluidas é hora de revisar e mesclar a branch

![Task list github flavours](https://camo.githubusercontent.com/09cbc14d7458e0e2c52f1a66fb8890152da978c9/68747470733a2f2f662e636c6f75642e6769746875622e636f6d2f6173736574732f3138322f35343631302f66326530656131382d356139612d313165322d383236642d6635663562663033663032652e676966)


[Exemplo de git pull-request](https://github.com/stvkoch/workflow-github/pulls)



## Qual o problema que resolve

  * O código, revisões, 'stories' e as tarefas estão centralizadas em um único lugar, fazendo com que seja fácil pular de um tópico para outro.
  * [ScrumDo](https://app.scrumdo.com) e outras ferramentas nem sempre são os melhores lugares para discussões e cometários, enquanto o Github é actualmente feito para isso.
  * GitHub tem um serviço de notificação por email, que é útil para saber andamento do projecto e onde é preciso envolvimento.
  * GitHub tem diversos recursos adicionais, como por exemplo, labels, suporte a Markdown, user assignments e interações com códigos oque faz com que seja uma otima ferramente para gestão de projecto.
  * Bonus: [Slack](http://slack.com) tem intergração com o GitHub, fazendo com que seus processos seja mais fluídos.




## Qual o problema que isso adiciona

Todos os envolvidos no projecto precisam ter um conta no Github desde o 'Scrum
Master' ao 'Product Owner'. Oque leva a poucos minutos, mas que é imperativo para
o correcto workflow.



## Criando um pull-request

A ideia é que cada 'feature' que envolva algum desenvolvimento tenha seu próprio
pull-request aberto no começo do 'sprint'. As tarefas de cada 'feature' são
listadas na descrição do pull-request. A boa noticia é que o Github é
inteligente suficiente e mostra o progresso/andamento da 'feature' directamente
na listagem de pull-requests.

![The progress is shown directly in the PR view](http://hugogiraudel.com/images/github-
as-a-workflow/01.png) O progresso é mostrado directamente na listagem de PR


Para todas as interações que envolvem desenvolvimento, criar um nome de 'branch'
que represneta uma 'story' e abrir um 'pull-request' desta branch para a principal.
Quando se adere a convesão 
[Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-
workflow/), a 'branch' principal chamamos 'develop', e as 'branches' que
representam uma 'story' devem começar com 'feature/' (am alguns casos 'fix/' ou
'refactor/'). E então geralmente colocamos o numero da 'story' primeiro, seguido
do 'slug' da 'story'. (ex: 'feature/42-basic-teaser').


Abrir um pull-request pode ser feito directamente no GitHub, sem precisar clonar
o projecto localmente ou mesmo ter grande conhecimento do Git. Mas somente
pode ser feito quando se tem algo para comparar entre branch
(quando alguem fez um push).
Isso significa que não é possível abrir um pull-request entre dois branchs
idênticos ou branch que foram mesclados e ambos estão no repositorio remoto.


Para contornar este problema, temos duas opções: Esperar que a 'story' seja
inicialiada por alguem, pelo menos o commit, e então teremos algo para comparar
entre a 'story' branch e a branch principal (develop). Embora não seja o melhor
metodo, a idéia é nós termos todas as 'stores' criadas logo no inicio do
'sprint' e os respectivos pull-request abertos directmente. Para que isso seja
possivel podemos criar commits vazios, tal como:

    
    
    # Criando um branch para a story
    git checkout -b feature/42-basic-teaser
    
    # Adicionando um commit vazio (com um significativo nome) para que seja possivel criar um pull-request
    git commit --allow-empty -m "Feature 42: Basic teaser component"

O objectivo desde 'commit' é inicializar o 'branch' e a respectiva 'feature'
para que possa ser possivel criar o 'pull-request' no GitHub.

A partir desde ponto, indo para a página inicial do repositorio no GitHub, será
listado botões em verdes com alguns branchs condidatas a criação de
pull-request.
Então para criar um 'pull-request' apartir de uma 'branch' relevante para o
branch principal (develop) seria simplesmente clicar no respectivo botão verde.
É tão simples quanto isso. Detalharemos mais na próxima sessão.



## Nomeando um pull-request

Nomeie o pull-request depois da feture name, assim que for assignado para alguem
o pull-request podes prefixar com [WIP] para indicar _Work In Progress_.
Depois podes alterar para `[RFR]` _Ready For Review_  quando as tarefas 
estiverem concluidas (veja revisando os pull-quests). Se o pull-request for
especifico para ser mesclado ou enviado para produção, voce pode alterar com
`[RFM]` (for _Ready For Merging_) adicionando um comentario de aprovação que
indicara a revisão e que é seguro fazer a mesclagem.

_Nota: dependendo como usas os labels do GitHub, podes tambem abandonar a ideia
a cima e usar 'labels' 'WIP', 'RFR' e 'RFM'. Eu prefiro guardar os 'labels' para
outro proposito e colocar o estado no nome do pull-request mas isso é algo que
diz respeito a você._

## Adicionando uma descrição

Na descrição da 'story'(pull-request), crie uma lista de tarefas, onde cada
tarefa tem um checkbox, uma curta descrição que seja importante suficiente, um
ou mais pessoas que estão envolvidas na tarefa. Do lado o Markdown, isso seria
parecido com:

    
    
    * [ ] Criar o componente basico React (@hugogiraudel)
    * [ ] Design os icons (@sharonwalsh)
    * [ ] Integrar componentes na página actual (@mattberridge)
    * [ ] clarificar os tipos de 'teasers' com o cliente (@moritzguth)

![A descrição do pull-request contem as tarefas que devem ser realizadas para concluir a 'feature'](http://hugogiraudel.com/images/github-as-a-workflow/02.png) A descrição do pull-request contêm as tarefas que devem ser realizadas para concluir a 'feature'

Como todos os intervenientes no projecto fazem parte da organização por tras do
projecto no GitHub, qualquer um consegue editar/deletar qualquer comentário,
então qualquer tem a habilidade de adicionar novas tarefas a descrição se assim
achar necessário.

_Note: 'GitHub Flavoured Markdown' converterá automagicamente `[ ]` em um
checkbox desabilitado e `[x]` em um checkbox habilitado. E tambem guardar o
estado do checkbox assim que ele for alterado._

![A descrição do PR contem checkboxes que podem ser habilitados para mostrar o actual progresso](http://hugogiraudel.com/images/github-as-a-workflow/03.png) A descrição do PR contem checkboxes que podem ser habilitados para mostrar o actual progresso.




## Usando comentários


Os comentários em um pull-request podem ser usados para discutir detalhes da
'story' ou informações sobre tarefas específicas. Podemos adicionar
questões, solicitar releventes colaborações prefixisando com '@' os nomes de
utilizadores do GitHub, incluir codigos, citações, imagens e muito mais se
assim desejar. Tudo isso usando Markdown, oque torna super fácil.

![Comentários são usados para discutir algumas preocupações e fazer perguntas](http://hugogiraudel.com/images
/github-as-a-workflow/04.png) Comentários são usados para discutir algumas preocupações e fazer perguntas.


## Revisando pull-request

Depois que todos os checkboxes da descrição estiver concluidos, o nome do
pull-request pode ser actualizado para '[RFR]' (_Ready For Review_).
Idealmente a pessoa que marcou a última tarefa como concluída deve solicitar a
alguem que comece o processo de Revisão de código, esta solicitação pode ser
feita criando um cometario e marcando (prefix @) alguem para o efeito.
O pull-request (DONE) só estara concluído se alguem criar um cometario de
revisão de código.

Para revisar um pull-request, nós adicionamos comentarios directamente nas
linhas de códigos na tab de direfença entre ficheiros (_Files changed_). Nesta
tab podemos comentar qualquer linha adicionando questões e sugerindo
modificações. Adicinar uma linha de comentario notificará o proprietario do
pull-request, assim ele saberá que há trabalho adicional a ser feito e o
comentario aparecerá na tab _Conversation_.

![GitHub inline comments é a maneira ideal de colaboração](http://hugogiraudel.com/images
/github-as-a-workflow/05.png) GitHub inline comments é a maneira ideal de colaboração

Quando for actualizado a linha de código que é objecto do comentario o
comentário desaparecerá pois não é mais relevante. então os comentarios que
precisam de revisão desapareceram tornando o pull-request limpo.

![Quando um comentario na linha de codigo for tratado desaparecera para evitar
desordenar as diferenças entre versões](http://hugogiraudel.com/images/github-as-a-workflow/06.png) Quando um comentario na linha de codigo for tratado desaparecera para evitar desordenar as diferenças entre versões


## Mesclando um pull-request

Uma vez que o code review estiver concluido, o pull-request pode ser mesclado
com o branch principal. Se tudo estiver OK, isso pode ser feito directamente no
GitHub mas esta é uma acção que tem a potencialidade de gerar conflictos entre
versões, noque é preciso fazer um 'rebase' para sincronizar com o branch
principal ou mesclar manualmente. Qualquer um pode fazer isso mas o proprietario
do pull-request pode ser a pessoa mais indicada para isso.


_Note: Para manter um historio de mensagens de commits limpo e relevante é
aconcelhavel ter as messagens de commit escrita de forma clara e significativa.
Apesar desde assunto não ser especifico da metodologia, eu penso que é
importante para reforça-lo aqui_


## Dica: usando labels

Labels podem ser muito úteis para adicionar informações extra em um
pull-request no GitHub. Eles são mostrados em uma lista particularmente util
fazendo com que seja facil e obvio percorrer os pull-request abertos.

Não há limites de quantidade de labels que um projecto pode ter. Tambem é
possivel associar uma cor junto com um pequeno, mas poderoso, sistema de
nomeclatura. Labels podem ter nomes como  _Design_, _Front-end_, _Back-end_, ou
mesmo _Waiting for info_, _Waiting for review_ ou _To be started_. Voce nomeia
isso.

![Labels são usado para criar um sistema de nomeclatura](http://hugogiraudel.com/images/github-
as-a-workflow/07.png) Labels são usado para criar um sistema de nomeclatura

Em projectos que envolvem diferentes tipos de equipa, tal como front-end,
back-end, design, devops. É recomendado ter os nomes das equipas como labels
para que cada equipa consiga cuidar das 'stories' que estão trabalhando.


![Labels are applied to stories to be able to filter them as well as givin
more information from the PR view directly](http://hugogiraudel.com/images/github-
as-a-workflow/08.png) Labels são aplicadas a 'stories' para que seja possivel
filtrar, bem como dar mais informações aos pull-requests


## Dica: usando atribuições (assignees)

Mais frequentemente que se possa  dizer que não, uma 'story' é geralmente para
uma pessoa. Ou mesmo quando mais de uma pessoa é envolvida a uma 'story' isso
ocorre geralmente um depois do outro(o designer faz o mockup, o front-end
desenvolve o componente, o back-end integra em um processo, etc...). Por causa
disso é interessante atribuir o pull-request para que um dos interveniente possa
tornar a story mais próxima da conclusão e depois atribuir a outro quando for
necessario.


![Atribuições são uma boa maneira de conhecer quem trabalha noque](http://hugogiraudel.com/images/github-as-a-workflow/09.png) Atribuições são uma boa maneira de conhecer quem trabalha noque



## Tip: using milestones

Because GitHub is a platform for Git, it is a great tool to conserve a clean
history of a project. One way to achieve this goal (if desired), would be to
use milestones. To put it simply, on GitHub a milestone is a named bucket of
issues/pull-requests, that can optionally have a description and a date.

Applying this to a Scrum project could mean having a milestone per sprint
(named after the number of the sprint), with a due date matching the one from
the end of the sprint and the goals of the sprint in the description. All
pull-requests (stories) would be tagged as part of the milestone.

![In this workflow, a milestone equals a sprint](http://hugogiraudel.com/images/github-
as-a-workflow/10.png) In this workflow, a milestone equals a sprint

While not very helpful for the develop because all open pull-requests are part
of the current sprint anyway, it might be interesting to have this as an
history, where all pull-requests are gathered in milestones corresponding to
sprints.

![From the view, we can know to which sprint a story belongs, in case some of
them are late to be resolved](http://hugogiraudel.com/images/github-as-a-workflow/11.png) From the
view, we can know to which sprint a story belongs, in case some of them are
late to be resolved

## Tip: using issues

The fact that this workflow is heavily focused on pull-requests does not mean
that GitHub issues are irrelevant. _Au contraire_! Issues can still be used
for additional conversations, bug reports, and basically any non-feature-
specific discussion.

Also depending on the relationship with the client (internal or external),
issues might be the good place for them to report problems, bugs and
suggestions. Again, everything is centralized on GitHub: the pull-requests
remain clean and focused on features; issues are kept for all side-
discussions.


### Links uteis

  * [Mastering Markdown](https://guides.github.com/features/mastering-markdown/index.html)


* * *

That is all I have written about it so far. I would love to collect opinions
and have feedback about this way of doing. Has anyone ever tried it? How does
it perform? How does it scale? What are the flaws? What are the positive
effects? Cheers!

Published under: github, workflow, and process.

  * [Google+](https://plus.google.com/u/0/101697878480386449961?rel=author)
  * [GitHub](https://github.com/HugoGiraudel)
  * [Twitter](http://twitter.com/HugoGiraudel)
  * [Search](/search/)
  * [RSS](/rss/)

(C) 2012-2015 Hugo Giraudel.

