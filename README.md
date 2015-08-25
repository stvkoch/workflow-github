### Tradu√ß√£o livre do artigo http://hugogiraudel.com/2015/08/13/github-as-a-workflow/

Nota: H√° termos que est√£o propositadamente sem serem traduzidos, penso que o
termo traduzido dificulta o entendimento do significado da express√£o.

---


# GitHub como um workflow

Este artigo √© o resultado da discuss√£o sobre o fluxo de desenvolvimento com um
dos nossos Scrum Master em Edenspiekermann. √â assumido que o leitor tenha no√ß√µes
b√°sicas sobre desenvolvimento √Ågil como
[Agile](https://en.wikipedia.org/wiki/Agile_software_development) e
[Scrum](https://en.wikipedia.org/wiki/Scrum_\(software_development\)). Se n√£o
for o seu caso, ainda assim se benificiar√° da leitura desde artigo mesmo que
falte alguns pontos chaves para o pleno entendimento. √â desejavel que tenha
no√ß√µes do conceito de [Gitflow](https://www.atlassian.com/git/tutorials/
comparing-workflows/gitflow-workflow/) workflow, embora n√£o dependa dele.

Neste pequeno documento, eu tento descrever oque seria, para mim, um √≥timo fluxo
de trabalho usando o [GitHub](https://github.com) como "pe√ßa chave" em vez de
ter uma colec√ß√£o de ferramentas e commandos. √â √≥bvio que este ponto-de-vista √©
centrado na √≥tica do desenvolvedor e pode n√£o se enquadrar em todas as equipas
e projectos.

Dado que o artigo pode ser um pouco longo, abaixo h√° um indexe de conte√∫do para
que consigas ir directo a sec√ß√£o que desejas:

  1. Introdu√ß√£o
  2. Qual o problema que resolve
  3. Qual o problema que isso adiciona
  4. Criando um pull-request
  5. Nomeando um pull-request
  6. Adicionando uma descri√ß√£o
  7. Usando coment√°rios
  8. Revisando pull-request
  9. Mesclando pull-request
  10. Dica: usando labels
  11. Dica: usando atribui√ß√µes(assignees)
  12. Dica: usando objectivos (milestones)
  13. Dica: usando problemas (issues)




## Introdu√ß√£o


Segue-se uma pequena e informal metodologia de como se tirar partido do
[GitHub](https://github.com) para ter fluxo de trabalho em projectos de
desenvolvimento usando [pull-
requests](https://help.github.com/articles/using-pull-requests/). Embora a
primeira vista possa parecer um pouco medonho, esta abordagem pode trazer um
monte de benef√≠cios, tal como iremos investigar nas pr√≥ximas sess√µes.

Grosseiramente, a ideia √© come√ßarmos a
[sprint](http://scrummethodology.com/scrum-sprint/), criado N pull-request
para todas as nossas [user stories](http://scrummethodology.com/scrum-user-
stories/). Na descri√ß√£o do pull-request, n√≥s escreveremos a lista de tarefas no
formato Markdown [GitHub support for
checkboxes](https://github.com/blog/1375%0A-task-lists-in-gfm-issues-pulls-
comments). Os desenvolvedores ir√£o enviar seus commits para o branch do
pull-request e progressivamente ir√£o concluir as tarefas listadas no
pull-request. Uma vez as tarefas concluidas √© hora de revisar e mesclar a branch

![Task list github flavours](https://camo.githubusercontent.com/09cbc14d7458e0e2c52f1a66fb8890152da978c9/68747470733a2f2f662e636c6f75642e6769746875622e636f6d2f6173736574732f3138322f35343631302f66326530656131382d356139612d313165322d383236642d6635663562663033663032652e676966)


[Exemplo de git pull-request](https://github.com/stvkoch/workflow-github/pulls)



## Qual o problema que resolve

  * O c√≥digo, revis√µes, 'stories' e as tarefas est√£o centralizadas em um √∫nico lugar, fazendo com que seja f√°cil pular de um t√≥pico para outro.
  * [ScrumDo](https://app.scrumdo.com) e outras ferramentas nem sempre s√£o os melhores lugares para discuss√µes e comet√°rios, enquanto o Github √© actualmente feito para isso.
  * GitHub tem um servi√ßo de notifica√ß√£o por email, que √© √∫til para saber andamento do projecto e onde √© preciso envolvimento.
  * GitHub tem diversos recursos adicionais, como por exemplo, labels, suporte a Markdown, user assignments e intera√ß√µes com c√≥digos oque faz com que seja uma otima ferramente para gest√£o de projecto.
  * Bonus: [Slack](http://slack.com) tem intergra√ß√£o com o GitHub, fazendo com que seus processos seja mais flu√≠dos.




## Qual o problema que isso adiciona

Todos os envolvidos no projecto precisam ter um conta no Github desde o 'Scrum
Master' ao 'Product Owner'. Oque leva a poucos minutos, mas que √© imperativo para
o correcto workflow.



## Criando um pull-request

A ideia √© que cada 'feature' que envolva algum desenvolvimento tenha seu pr√≥prio
pull-request aberto no come√ßo do 'sprint'. As tarefas de cada 'feature' s√£o
listadas na descri√ß√£o do pull-request. A boa noticia √© que o Github √©
inteligente suficiente e mostra o progresso/andamento da 'feature' directamente
na listagem de pull-requests.

![The progress is shown directly in the PR view](http://hugogiraudel.com/images/github-
as-a-workflow/01.png) O progresso √© mostrado directamente na listagem de PR


Para todas as intera√ß√µes que envolvem desenvolvimento, criar um nome de 'branch'
que represneta uma 'story' e abrir um 'pull-request' desta branch para a principal.
Quando se adere a conves√£o 
[Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-
workflow/), a 'branch' principal chamamos 'develop', e as 'branches' que
representam uma 'story' devem come√ßar com 'feature/' (am alguns casos 'fix/' ou
'refactor/'). E ent√£o geralmente colocamos o numero da 'story' primeiro, seguido
do 'slug' da 'story'. (ex: 'feature/42-basic-teaser').


Abrir um pull-request pode ser feito directamente no GitHub, sem precisar clonar
o projecto localmente ou mesmo ter grande conhecimento do Git. Mas somente
pode ser feito quando se tem algo para comparar entre branch
(quando alguem fez um push).
Isso significa que n√£o √© poss√≠vel abrir um pull-request entre dois branchs
id√™nticos ou branch que foram mesclados e ambos est√£o no repositorio remoto.


Para contornar este problema, temos duas op√ß√µes: Esperar que a 'story' seja
inicialiada por alguem, pelo menos o commit, e ent√£o teremos algo para comparar
entre a 'story' branch e a branch principal (develop). Embora n√£o seja o melhor
metodo, a id√©ia √© n√≥s termos todas as 'stores' criadas logo no inicio do
'sprint' e os respectivos pull-request abertos directmente. Para que isso seja
possivel podemos criar commits vazios, tal como:

    
    
    # Criando um branch para a story
    git checkout -b feature/42-basic-teaser
    
    # Adicionando um commit vazio (com um significativo nome) para que seja possivel criar um pull-request
    git commit --allow-empty -m "Feature 42: Basic teaser component"

O objectivo desde 'commit' √© inicializar o 'branch' e a respectiva 'feature'
para que possa ser possivel criar o 'pull-request' no GitHub.

A partir desde ponto, indo para a p√°gina inicial do repositorio no GitHub, ser√°
listado bot√µes em verdes com alguns branchs condidatas a cria√ß√£o de
pull-request.
Ent√£o para criar um 'pull-request' apartir de uma 'branch' relevante para o
branch principal (develop) seria simplesmente clicar no respectivo bot√£o verde.
√â t√£o simples quanto isso. Detalharemos mais na pr√≥xima sess√£o.



## Nomeando um pull-request

Nomeie o pull-request depois da feture name, assim que for assignado para alguem
o pull-request podes prefixar com [WIP] para indicar _Work In Progress_.
Depois podes alterar para `[RFR]` _Ready For Review_  quando as tarefas 
estiverem concluidas (veja revisando os pull-quests). Se o pull-request for
especifico para ser mesclado ou enviado para produ√ß√£o, voce pode alterar com
`[RFM]` (for _Ready For Merging_) adicionando um comentario de aprova√ß√£o que
indicara a revis√£o e que √© seguro fazer a mesclagem.

_Nota: dependendo como usas os labels do GitHub, podes tambem abandonar a ideia
a cima e usar 'labels' 'WIP', 'RFR' e 'RFM'. Eu prefiro guardar os 'labels' para
outro proposito e colocar o estado no nome do pull-request mas isso √© algo que
diz respeito a voc√™._

## Adicionando uma descri√ß√£o

Na descri√ß√£o da 'story'(pull-request), crie uma lista de tarefas, onde cada
tarefa tem um checkbox, uma curta descri√ß√£o que seja importante suficiente, um
ou mais pessoas que est√£o envolvidas na tarefa. Do lado o Markdown, isso seria
parecido com:

    
    
    * [ ] Criar o componente basico React (@hugogiraudel)
    * [ ] Design os icons (@sharonwalsh)
    * [ ] Integrar componentes na p√°gina actual (@mattberridge)
    * [ ] clarificar os tipos de 'teasers' com o cliente (@moritzguth)

![A descri√ß√£o do pull-request contem as tarefas que devem ser realizadas para concluir a 'feature'](http://hugogiraudel.com/images/github-as-a-workflow/02.png) A descri√ß√£o do pull-request cont√™m as tarefas que devem ser realizadas para concluir a 'feature'

Como todos os intervenientes no projecto fazem parte da organiza√ß√£o por tras do
projecto no GitHub, qualquer um consegue editar/deletar qualquer coment√°rio,
ent√£o qualquer tem a habilidade de adicionar novas tarefas a descri√ß√£o se assim
achar necess√°rio.

_Note: 'GitHub Flavoured Markdown' converter√° automagicamente `[ ]` em um
checkbox desabilitado e `[x]` em um checkbox habilitado. E tambem guardar o
estado do checkbox assim que ele for alterado._

![A descri√ß√£o do PR contem checkboxes que podem ser habilitados para mostrar o actual progresso](http://hugogiraudel.com/images/github-as-a-workflow/03.png) A descri√ß√£o do PR contem checkboxes que podem ser habilitados para mostrar o actual progresso.




## Usando coment√°rios


Os coment√°rios em um pull-request podem ser usados para discutir detalhes da
'story' ou informa√ß√µes sobre tarefas espec√≠ficas. Podemos adicionar
quest√µes, solicitar releventes colabora√ß√µes prefixisando com '@' os nomes de
utilizadores do GitHub, incluir codigos, cita√ß√µes, imagens e muito mais se
assim desejar. Tudo isso usando Markdown, oque torna super f√°cil.

![Coment√°rios s√£o usados para discutir algumas preocupa√ß√µes e fazer perguntas](http://hugogiraudel.com/images
/github-as-a-workflow/04.png) Coment√°rios s√£o usados para discutir algumas preocupa√ß√µes e fazer perguntas.


## Revisando pull-request

Once all checkboxes from the description have been checked, the name of the
pull-request can be updated to `[RFR]` for _Ready For Review_. Ideally, the
person checking the last bullet might want to ping someone to get the
reviewing process started. Doing so avoid having a pull-request done but
unmerged because nobody has reviewed it.

To review a pull-request, we use GitHub inline comments in the _Files changed_
tab. In there, we can comment any line to ask for modification. Adding a line
comment notifies the owner of the pull-request so that he knows he has some
re-working to do, and the comment shows up in the _Conversation_ tab.

![GitHub inline comments are the ideal way for collaborating on code](http://hugogiraudel.com/images
/github-as-a-workflow/05.png) GitHub inline comments are the ideal way for
collaborating on code

When updating a line that is the object of an inline comment, the latter
disappears because it is not relevant anymore. Then, as comments get fixed,
they disappear so the pull-request remains clean.

![When an inline comment has been taken care of, it disappears to avoid
cluttering the diff](http://hugogiraudel.com/images/github-as-a-workflow/06.png) When an inline
comment has been taken care of, it disappears to avoid cluttering the diff

## Merging the pull-request

Once the review has been done, the pull-request can be merged into the main
branch. If everything is fine, it should be mergeable from GitHub directly but
sometimes there are potential conflicts so we need to either rebase the branch
to synchronize it with the main branch or merge it manually. Anybody can do
it, but the pull-request owner is probably the best person to do it.

_Note: in order to keep a relevant and clean commit history, it would be wise
to keep commit messages clear and meaningful. While this is not specific to
this methodology, I think it is important enough to stress it._

## Tip: using labels

Labels can be very helpful to add extra pieces of information to a pull-
request on GitHub. They come in particularly handy as they show up in the list
view, making it visible and obvious for everybody scanning through the open
pull-requests.

There is no limit regarding the amount of labels a project can have. They also
are associated with colors, building a little yet powerful nomenclaturing
system. Labels can be something such as _Design_, _Front-end_, _Back-end_, or
even _Waiting for info_, _Waiting for review_ or _To be started_. You name it.

![Labels are used to create a nomenclature](http://hugogiraudel.com/images/github-
as-a-workflow/07.png) Labels are used to create a nomenclature

On a project involving design, front-end, back-end and devops teams, I would
recommend having these team names as labels so each team is aware of the
stories they have to be working on.

![Labels are applied to stories to be able to filter them as well as givin
more information from the PR view directly](http://hugogiraudel.com/images/github-
as-a-workflow/08.png) Labels are applied to stories to be able to filter them
as well as givin more information from the PR view directly

## Tip: using assignees

More often than not, a story is mostly for one person. Or when several actors
have to get involved in a story, it usually happens one after the other (the
designer does the mockup, then the front-end developer does the component,
then the back-end developer integrates it in the process, etc.). Because of
this, it might be interesting to _assign_ the pull-request to the relevant
actor on GitHub, and change this assignment when needed.

![Assignees are a good way of knowing who works on what from the PR
view](http://hugogiraudel.com/images/github-as-a-workflow/09.png) Assignees are a good way of knowing
who works on what from the PR view

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


