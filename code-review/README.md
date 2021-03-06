# Про "code review"

Здесь мы хотели бы задокументировать некоторую культуру создания
pull-request'ов, которую в дальнейшем было бы очень хорошо не нарушать
в проектах, в которых вы работаете.

Эта нужда возникла с тем, что в последнее время стало слишком сложно, слишком
затратно проверять чьи-либо правки. Попадаясь "проверяющим" на pull-request
в проект, в котором ты, возможно, не особо участвуешь, и, собственно, не
разбираешься даже в сути его работы в целом и, тем более, предложенных правок,
ты (на текущий момент) вряд ли сможешь указать на что-то по "начинке", видя лишь
"оболочку" (нувыпоняли). Изменения большого объема даже банально пропадает
желание смотреть. От части всё это происходит потому что сейчас pull-request'ы
в большинстве случаев создаются без какого-либо дополнительного сопровождения,
и быстро получить хоть какую информацию, которая поможет случайному участнику
разобраться в правках, не получится.

Лирическая часть окончена.

## Ваши действия

Итак, мы поняли проблему, и для её решения потребуются некоторые как
единовременные, так и периодические действия от всех нас.

### Вы - тот, кто создает pull-request

* Прежде всего, если вы хотите отдать ваш код на всеобщее обозрение, просмотрите
  его целиком сами. Лучше сделать это несколько раз. Инфасотка, что в первый
  проход вы найдете что-то неправильное, что-то неуместное, что-то, что можно
  сделать лучше.
* Чувствуйте меру в изменениях, не касающихся вашей задачи. Если их много, то
  вынесите в отдельный коммит. Если их слишком много - скорее всего, стоит их
  оформить в виде отдельного pull-request'а и, собственно, отдельной задачи.
  Подобное разделение поможет людям, которые будут смотреть ваш код, больше
  фокусироваться на действительно значимых правках, не отвлекаясь на всякие
  рефакторинги.
* Создавая pull-request, убедитесь, что ваши коммиты (если их вдруг более
  одного) атомарны, и это разделение действительно имеет место. В наших реалиях,
  на самом деле, всё часто можно уместить в один. Каждый ваш коммит должен, как
  все знают (но не все делают), содержать краткое объяснение содержащихся в нём
  правок. Если вдруг этого объяснения мало, то дополнительно можно задавать
  и тело коммита, где уже можно писать сколько угодно много. Но, понятное дело,
  старайтесь не грани за пределы разумного.
* Сам pull-request постарайтесь сопроводить максимумом информации, которая
  поможет в нём разобраться.
  * Если есть ссылки на какие-нибудь статьи, которые использовались при
    внесении правок, то стоит, конечно же, стоит их прикрепить.
  * Определенно стоит сопроводить всё какой-либо информацией о том, например,
    что, собственно, здесь происходит; почему предприняты конкретные решения;
    причины возникновения проблем, которые потребовали внесения этих правок; что
    было до, и что стало после; и так далее. Хорошо, если с большим объемом
    изменений будет сравнима сопровождающая его информация.
  * Возможно, будет неплохой идеей разделить свои объяснения происходящего на
    несколько комментариев (прямо в pull-reqeust'е), чтобы была возможность
    более удобно обсуждать конкретные моменты.
  * Если изменения касаются пользовательского интерфейса, то не будет лишним
    прикрепить скриншоты. Если уместно, можно даже заскринить то, как было,
    и как стало.
* В интерфейсе bitbucket'а есть удобная функция по созданию "задач"
  к комментариям - не забывайте про нее и, собственно, старайтесь использовать.
* Не сливайте ветку до тех пор, пока не реализуете все моменты, которые
  кого-либо не устраивают. Как-либо реагируйте на **каждый** оставленный к вашим
  правкам комментарий - это может быть ответный комментарий или, например,
  "лайк".
* Старайтесь как можно быстрее решить все возникшие вопросы и не скатывайтесь
  в споры из десятков комментариев. Если вдруг вам кажется, что вы правы
  в каком-то моменте, когда вам говорят обратное, то стоит сразу же привлечь
  к этой дискуссии больше людей и принять вынесенный коллективным судом вердикт.
* В каждом проекте, в который вы вносите изменения, возможно наличие файла
  `CONTRIBUTING.md`, который содержит свои специфические правила и рекомендации
  по внесению правок, так что не будет лишним его прочесть и проверить свой
  pull-request на факт соответствия.
* Короче, как, возможно, уже говорилось выше, старайтесь ставить себя на место
  тех, кто проверяет ваши изменения, и оформляйте свой pull-request так, как вы
  хотели бы видеть его оформленным для просмотра вами.

### Вы - "ревьюер"

Тут, в отличии от пункта выше, особо никаких требований и пожеланий нет.  Почти
все следующие пункты можно обобщить фразой "не будьте говном":

* Не жлобьтесь ставить галочку. На самом деле, определенно стоит ставить галочку
  в тех случаях, если:
  * У вас остались лишь минорные замечания, без которых, в принципе,
    все и так хорошо (типа соответствия какому-либо стайл-гайду, `isNotEmpty`
    вместо `!isEmpty` и так далее).
  * У вас остались лишь какие-то пожелания, которые как бы и необязательно даже
    вносить. Касательно таких штучек, кстати, лучше сразу и говорить, что это
    вовсе не особо обязательно - просто вам кажется, что с ними было бы лучше.
  * Собственно, у вас нет никаких замечаний.
* Не стойте бесконечно на своем и не допускайте длительных обсуждений. Помните,
  что ваше мнение не единственно, и оно не всегда может быть правильным. Если вы
  достаточно долго о чём-либо спорите, и уже даже привлекли третьи стороны, но
  всё равно не можете прийти к одному решению - уступите. В целом, в таких
  ситуациях всегда приоритет должен быть у решения, которое уже реализовано
  человеком, отправившим pull-request.
* Старайтесь не затрагивать код, который не касается данных правок. Если очень
  хочется, то обязательно стоит сообщить, что это просто ваша хотелка,
  и в обязательной реализации она не нуждается.
* Не бойтесь поставить галочку "needs work", если она действительно оправдана,
  но и не злоупотребляйте ей.
* Не стесняйтесь попросить больше информации о правках, если вам что-либо в них
  непонятно.

### Вы - в каком-то смысле ответственный за коллегу, вливающего правки

***Тут подразумевается должность "тимлида", либо "ответственный" за какого-либо,
например, стажера.***

Вам стоит уделить его правкам повышенное внимание и, собственно, самому
соблюдать максимальную (прямо вще! нувыпоняли) политкорректность. Понятное дело,
предыдущий параграф к вам тоже относится. На вас также в большей степени лежит
и ответственность за оформление этого pull-request'а таким образом, чтобы он был
максимально всем доступен, так что следите за своими коллегами и по нужде
немного "пинайте" их, чтобы всё у них было "супер-пупер". Это, конечно же, могут
делать и другие, но выжетимлид!

### Вы - "главный" по проекту

***Имеется в виду человек, который начал этот проект, либо который им сейчас
занимается в наибольшей степени.***

Вам, конечно же, стоит озаботиться исчерпывающим `README.md`, чтобы люди,
которые начинают интересоваться проектом, могли осуществить более быстрый старт.
Что туда вносить - ну, на ваше усмотрение. Это может быть описание структуры,
описание его сути, описание процесса инициализации для начала работы над ним
и всё такое прочее. На вас также лежит ответственность по оформлению
`CONTRIBUTING.md`, если в нём есть нужда.

# Заключение

Коллеги! Такие мысли. Создавайте приятные pull-request'ы, набирайтесь опыта в их
оформлении, просматривайте правки других, не бойтесь задавать вопросы и вступать
в разговор, если что-то непонятно.
