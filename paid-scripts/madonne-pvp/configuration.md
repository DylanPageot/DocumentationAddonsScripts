# Configuration



<details>

<summary><em><strong>Content of the configuration file by default</strong></em></summary>

```lua
----------------------------------------------------------------------------------------------------
--                           Madonne Studio © 2023 - All rights reserved                          --
--                                                                                                --
--                                    "MADONNE PVP - v.1.0.0"                                --
--                                                                                                --
--               For any issue with this ressource, please contact us on Discord :                --
--                                                                                                --
--                                  https://discord.gg/nmBAJrFhQB                                 --
--                                                                                                --
--                                    https://madonnestudio.com                                   --
--                                    contact@madonnestudio.com                                   --
--                                                                                                --
----------------------------------------------------------------------------------------------------

CONFIG_MADONNE_PVP = {

    -- Amount of time a player must wait if they fail all three tries. In days.
    ResetOfTestsEvery = 1,

    PeacetimeStateByDefault = false,

    PeacetimeEnabled = "ATTENTION : Le mode passif a été activé. Vous êtes donc à l'abri de tous dégâts.",
    PeacetimeDisabled = "ATTENTION : Le mode passif a été désactivé. Retour à la normale de la situation.",
    QuizUiIsLoading = "Chargement de l'interface d'accès au PVP...",
    AlreadyHavePvp = "Vous disposez déjà des accès PVP.",
    
    NoTryRemaining = "Il ne t'en reste plus.",
    OneTryRemaining = "Il t'en reste 1.",
    TwoTryRemaining = "Il t'en reste 2.",
    ThreeTryRemaining = "Il t'en reste 3.",

    NOTIFICATION_TYPE = "notification",
    notifChatColor = {255,255,255},
    globalPrefixBis = "MadonneStudio",

}

```

</details>

<details>

<summary><em><strong>Main Madonne PVP configuration</strong></em></summary>

Number of days required for the test counter to reset.

```lua
    ResetOfTestsEvery = 1,
```



Default state of passive mode.

```lua
    PeacetimeStateByDefault = false,
```



Translations of the various phrases used in the script.

```lua
    PeacetimeEnabled = "ATTENTION : Le mode passif a été activé. Vous êtes donc à l'abri de tous dégâts.",
    PeacetimeDisabled = "ATTENTION : Le mode passif a été désactivé. Retour à la normale de la situation.",
    QuizUiIsLoading = "Chargement de l'interface d'accès au PVP...",
    AlreadyHavePvp = "Vous disposez déjà des accès PVP.",
    
    NoTryRemaining = "Il ne t'en reste plus.",
    OneTryRemaining = "Il t'en reste 1.",
    TwoTryRemaining = "Il t'en reste 2.",
    ThreeTryRemaining = "Il t'en reste 3.",
```



Changing notification preferences.

```lua
    NOTIFICATION_TYPE = "notification",
    notifChatColor = {255,255,255},
    globalPrefixBis = "MadonneStudio",
```



</details>

<details>

<summary><em>Questions configuration</em></summary>

In the questions.lua, you can edit each questions you want to ask to your players in the quiz. He is pretty simple to edit.

```lua
QuestionsFromCFG = {
    {
        question = "Un joueur roule tranquillement, en voiture civil. Je me décide de l'arrêter pour le contrôler. Ce dernier m'indique qu'il ne veut pas particier à l'action.",
        answerA = "Je comprends sa décision et repart patrouiller. ",
        answerB = "J'insiste en disant que s'il coopère pas, il sera envoyé en garde à vue.",
        answerC = "J'ignore ce qu'il dit et continue mon contrôle.",
        answerD = "Je contacte un membre du staff avec la commande /report.",
        goodAnswer = "A",
    },
    {
        question = "Pendant un braquage de banque, je me fais tuer alors que j'effectuais un assaut pour appréhender les ravisseurs.",
        answerA = "Je reviens en me téléportant pour continuer la scène avec mes collègues.",
        answerB = "Je reviens sur la scène, en voiture, afin de la continuer avec mes collègues.",
        answerC = "J'attends que l'action soit terminée avant de retourner sur place.",
        answerD = "Je crie au freekill et insulte la personne qui m'a tué.",
        goodAnswer = "C",
    },
    {
        question = "Dans le chat HRP, vous pouvez lire qu'un joueur à dit qu'il avait tué quelqu'un.",
        answerA = "Je cherche le joueur sur la map pour l'interpeller, il a quand même tuer quelqu'un !",
        answerB = "Je venge la personne qu'il a tué.",
        answerC = "Je ne prends pas compte de ce message dans mon roleplay.",
        answerD = "Je vais voir d'autres policiers pour leur faire passer l'information.",
        goodAnswer = "C",
    },
    {
        question = "Etant actuellement un civil, je croise un policier en voiture.",
        answerA = "Je fais demi-tour, m'arrête à son niveau et klaxonne pour le provoquer.",
        answerB = "Je lui tire dessus pour qu'il se mette à me poursuivre.",
        answerC = "Je lui propose une course-poursuite pour tester mes compétences de conduite.",
        answerD = "Je continue ma route comme tout bon citoyen lambda.",
        goodAnswer = "D",
    },
    {
        question = "En tant que civil, je souhaite réaliser une attaque terroriste sur le serveur.",
        answerA = "Je me lance directement et tire sur le premier joueur qui passe.",
        answerB = "Je demande à un staff si c'est possible de le faire et la réalise où je le souhaite.",
        answerC = "Je demande à un staff si c'est possible de le faire et la réalise à l'endroit qu'il m'indique.",
        answerD = "Je fais juste un /ano pour prévenir et me met à tirer sur tout le monde.",
        goodAnswer = "C",
    },
    {
        question = "Lequel de ces quatre pseudos est interdit sur le serveur ?",
        answerA = "Jean Neymar",
        answerB = "Jean Culetamer",
        answerC = "François Hollande",
        answerD = "Xx-KillerDu33-xX",
        goodAnswer = "B",
    },
}

-- DON'T TOUCHE BELOW THIS LINE --

function GetQuestionsFromCfg()
   return questionsFromCFG
end

```

</details>

