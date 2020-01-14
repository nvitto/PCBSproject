# PCBSproject

Nina Vittorelli 
PCBS 2019-2020


## Description du projet 

Mon projet consiste à rédiger des algorithmes en langage Python pour résoudre analytiquement certaines équations différentielles que l'on retrouve fréquemment dans des modèles d'écologie des populations. 

Je commence par des équations à une inconnue (modélisation de l'évolution d'une seule population) issues des modèles de croissance exponentielle puis logistique. Ensuite, je cherche à résoudre les systèmes à deux inconnues modélisant l'interaction d'une population de proies et d'une population de prédateurs  (modèle de Lotka-Volterra). 


## Méthode 

J'applique la méthode d'Euler explicite pour afficher graphiquement l'allure des solutions.

J'utilise un notebook pour pouvoir insérer à la fois des explications sur les modèles, des équations en langage Latex, des programmes Python et des graphiques représentant les solutions. 

Voici le programme que j'ai rédigé pour afficher graphiquement l'allure de la solution de l'équation différentielle

![equation](https://github.com/nvitto/PCBSproject/blob/master/Equation.png)


pour t variant entre 0 et 40.

    import matplotlib.pyplot as plt
    import numpy as np

    # On définit F telle que F(N(t), t) = N'(t)
    def F(N, t):
        return 0.1 * N

    n = 4000             # Le nombre de points pour lesquels on calcule l'image par N
    dt =  0.01           # La taille de l'intervalle entre deux points
    t_0, N_0 = 0, 10     # Les conditions initiales

    # On choisit les valeurs de t pour lesquelles on calcule N
    t = np.array([t_0 + k * dt for k in range(n)])

    # On calcule N pour ces valeurs de t
    N_list = [N_0]
    for i in range(1, n):
        N_list.append(N_list[-1] + dt * F(N_list[-1], t[i-1]))
    N = np.array(N_list)

    # Représentation graphique de la solution
    plt.plot(t, N)
    plt.title("Solution de l'équation différentielle E")
    plt.xlabel("t")
    plt.ylabel ("N(t)")
    plt.grid()
    plt.show()

Dans mon projet, je vais utiliser ce code en le modifiant de différentes manières pour obtenir les résultats suivants : 
- Changer la fonction F.
- Sur le même graphique, afficher plusieurs courbes selon la condition initiale.
- Sur le même graphique, afficher plusieurs courbes selon la valeur des paramètres du modèle.
- Afficher la représentation graphique des solutions d'un système d'équations différentielles avec deux fonctions inconnues.


## Accès au projet

Pour accéder à mon projet, il est possible de lire le [notebook sur Github](https://github.com/nvitto/PCBSproject/blob/master/Notebook.ipynb). Sinon, il faut ouvrir le document Notebook.ipynb de ce répertoire dans [Jupyter](https://jupyter.org/). 


## Bilan 

Avant ce cours, j'avais un petit peu d'expérience en programmation, j'avais surtout appris à faire de l'analyse de données avec le language R. J'avais également rencontré Bash et Python pendant un stage.

Ce cours et ce projet m'ont permis d'être plus à l'aise avec le langage Python et de découvrir la programmation pour la modélisation. J'ai aussi appris à utiliser Jupyter, Markdown et Git, et j'ai trouvé que c'étaient des outils très utiles à connaître.

Je trouve ça vraiment intéressant de pouvoir avancer sur un projet personnel à son rythme en posant des questions sur Slack et en cours. Cependant, j'ai le sentiment que la première partie du cours gagnerait à être dispensée devant des groupes de niveau, pour éviter que les débutants ne se sentent perdus et que les élèves les plus avancés ne s'ennuient. En revanche, les petits exercices proposés entre chaque cours étaient utiles pour chercher par soi-même et à son rythme, ils permettaient vraiment de progresser. Enfin, je pense qu'il pourrait être intéressant d'aborder la programmation pour les statistiques pendant les cours. 
