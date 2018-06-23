- ¿Qué comando utilizaste en el paso 11? ¿Por qué?

git reset --hard HEAD~1. Es necesario añadir la opción --hard para que se elimine el contenido del working copy ya que al no hacerlo quedaría
el fichero git-nuestro.md en el working copy con el contenido que tenía en el commit anterior.

- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

git reset --hard 9ab9b9c, donde 9ab9b9c es el ID del commit anterior. Con esto, la rama actual queda reseteada a ese commit en concreto donde
habíamos modificado el fichero git-nuestro.md. Para obtener el ID he tenido que usar previamente el comando git reflog y ver cual fue el último commit.

- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?

No causa ningún conflicto, se muestra el mensaje "Already up-to-date" porque el padre del último commit de la rama styled es el último commit de master. 
Es decir, master no ha sufrido cambio alguno desde que se creó la rama styled y se hicieron cambios en esta rama por lo que al hacer un merge desde master 
no se absorbe ni se obtiene ningún código adicional. Si se utiliza el comando git graph (donde graph es un alias para visualizar el grafo bien decorado),
se puede visualizar mejor lo que estoy tratando de explicar.

- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?

Tal como contaba en la anterior pregunta. ahora se ha creado una nueva rama y se han modificado las mismas lineas de un fichero que intentamos mergear.
Internamente, lo que está pasando es que la rama styled está tratando de absorber los hunks que se han creado en el commit del paso 18 en la rama htmlify.
Al hacer esta operación, esos hunks entran en conflicto con las lineas de código que ya existen en el fichero y de ahí el conflicto. 

- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?

No hay conflictos porque es un merge fast-forward. La rama styled proviene directamente del último commit de master, es decir, al intentar absorber los hunks
de styled, git lo único que tiene que hacer es seguir el grafo, mover el puntero HEAD (que apuntaba al primer commit, dónde se quedó master) y moverlo al último commit que se hizo en
la rama styled. Si se vuelve a utilizar el comando git graph se ve bastante más claro todo esto XD.

- ¿Qué comando o comandos utilizaste en el paso 25?

Durante el curso creé un alias para que saliera el grafo decorado con la instrucción git config --global alias.graph "log --graph --decorate --pretty=oneline" que es
la instrucción que he ido usando en pasos anteriores para ver la evolución de los commits.

- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?

Si podría ser fast forward, ya que git sólo tendría que mover el puntero HEAD de master al último commit de la rama title para absorber sus cambios.

- ¿Qué comando o comandos utilizaste en el paso 27?

git reset HEAD~1

- ¿Qué comando o comandos utilizaste en el paso 28?

git checkout -- git-nuestro.md

- ¿Qué comando o comandos utilizaste en el paso 29?

git branch -D title

- ¿Qué comando o comandos utilizaste en el paso 30?

1) git reflog para visualizar el ID del commit no fast forward que se hizo para mergear title sobre master.
2) git reset --hard 80a345a. Donde 80a345a es el ID del commit localizado en el paso anterior.

- ¿Qué comando o comandos usaste en el paso 32?

1) git reflog para visualizar el ID del primer commit.
2) git reset --hard 802b667. Donde 802b667 es el ID del commit localizado en el paso anterior.

- ¿Qué comando o comandos usaste en el punto 33?

1) git reflog para visualizar el ID del merge de title sobre master.
2) git reset --hard 80a345a. Donde 80a345a es el ID del commit localizado en el paso anterior.

