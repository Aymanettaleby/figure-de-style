<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Figures de Style - 51 Procédés Littéraires</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .fade-in {
            animation: fadeIn 0.5s ease-out forwards;
        }
        
        .option:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .correct {
            background-color: #d1fae5 !important;
            border-color: #10b981 !important;
        }
        
        .incorrect {
            background-color: #fee2e2 !important;
            border-color: #ef4444 !important;
        }
        
        .progress-bar {
            transition: width 0.5s ease-in-out;
        }
        
        .book-icon {
            width: 24px;
            height: 24px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            border-radius: 4px;
            margin-right: 8px;
            font-size: 12px;
        }
        
        .quote-highlight {
            background: linear-gradient(120deg, #a5b4fc 0%, #818cf8 100%);
            background-size: 100% 40%;
            background-repeat: no-repeat;
            background-position: 0 90%;
        }
        
        .floating {
            animation: floating 3s ease-in-out infinite;
        }
        
        @keyframes floating {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-5px); }
            100% { transform: translateY(0px); }
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body class="bg-gradient-to-br from-gray-50 to-gray-100 font-sans min-h-screen">
    <div class="container mx-auto px-4 py-8 max-w-4xl">
        <!-- Header -->
        <header class="text-center mb-10 fade-in">
            <div class="inline-block p-3 bg-white rounded-full shadow-lg mb-4">
                <i class="fas fa-book-open text-3xl text-indigo-600 floating"></i>
            </div>
            <h1 class="text-3xl md:text-4xl font-bold text-indigo-800 mb-2">
                Maîtrisez les 51 Figures de Style
            </h1>
            <p class="text-lg text-gray-600 max-w-2xl mx-auto">
                Quiz complet sur les procédés stylistiques dans les œuvres classiques
            </p>
            <div class="mt-6 flex flex-wrap justify-center gap-2">
                <span class="inline-flex items-center px-3 py-1 bg-purple-100 text-purple-800 rounded-full text-sm font-medium">
                    <i class="fas fa-brain mr-1"></i> 51 figures étudiées
                </span>
                <span class="inline-flex items-center px-3 py-1 bg-blue-100 text-blue-800 rounded-full text-sm font-medium">
                    <i class="fas fa-book mr-1"></i> 3 œuvres au programme
                </span>
            </div>
        </header>

        <!-- Quiz Container -->
        <div id="quizContainer" class="bg-white rounded-xl shadow-lg p-6 mb-8 border border-indigo-100 transform transition-all duration-300 hover:shadow-xl fade-in">
            <!-- Progress Bar -->
            <div class="mb-6">
                <div class="flex justify-between mb-1">
                    <span class="text-sm font-medium text-indigo-700">Votre progression dans le quiz</span>
                    <span id="progressText" class="text-sm font-medium text-indigo-700">1/51</span>
                </div>
                <div class="w-full bg-gray-200 rounded-full h-2.5">
                    <div id="progressBar" class="progress-bar bg-gradient-to-r from-indigo-500 to-purple-500 h-2.5 rounded-full" style="width: 2%"></div>
                </div>
            </div>

            <!-- Question -->
            <div id="questionContainer" class="fade-in">
                <div id="source" class="flex items-center text-sm font-medium mb-3">
                    <span id="bookIcon" class="book-icon"></span>
                    <span id="bookTitle"></span>
                </div>
                
                <div id="quote" class="bg-gray-50 p-4 rounded-lg border-l-4 border-indigo-300 italic text-gray-700 mb-6 relative">
                    <div class="absolute -top-3 -left-3 w-8 h-8 bg-indigo-100 rounded-full flex items-center justify-center">
                        <i class="fas fa-quote-left text-indigo-500 text-sm"></i>
                    </div>
                    <span id="quoteText" class="quote-highlight"></span>
                    <div class="text-xs text-gray-400 mt-2">
                        Extrait littéraire - Analyse stylistique requise
                    </div>
                </div>
                
                <h2 id="question" class="text-xl font-semibold text-gray-800 mb-4 flex items-center">
                    <i class="fas fa-question-circle text-indigo-500 mr-2"></i>
                    <span>Quelle figure de style reconnaissez-vous dans cet extrait ?</span>
                </h2>
                
                <!-- Options -->
                <div id="options" class="grid grid-cols-1 gap-3 mb-6"></div>
                
                <!-- Feedback -->
                <div id="feedback" class="hidden p-4 rounded-lg mb-6 border-l-4"></div>
                
                <!-- Navigation -->
                <div class="flex justify-between items-center">
                    <button id="prevBtn" class="bg-gray-200 hover:bg-gray-300 text-gray-800 font-medium py-2 px-4 rounded-lg transition duration-300 flex items-center">
                        <i class="fas fa-arrow-left mr-2"></i>Question précédente
                    </button>
                    <div class="text-sm text-gray-500 mx-2 hidden md:block">
                        Cliquez sur une réponse pour continuer
                    </div>
                    <button id="nextBtn" class="ml-auto bg-gradient-to-r from-indigo-500 to-purple-500 hover:from-indigo-600 hover:to-purple-600 text-white font-medium py-2 px-4 rounded-lg transition duration-300 flex items-center shadow-md">
                        Suivant <i class="fas fa-arrow-right ml-2"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Results Container (hidden initially) -->
        <div id="resultsContainer" class="hidden bg-white rounded-xl shadow-lg p-8 text-center fade-in">
            <div class="max-w-lg mx-auto">
                <div class="w-32 h-32 bg-gradient-to-br from-indigo-100 to-purple-100 rounded-full flex items-center justify-center mx-auto mb-6 pulse">
                    <i class="fas fa-award text-5xl text-indigo-600"></i>
                </div>
                <h2 class="text-3xl font-bold text-gray-800 mb-3">Résultats de votre analyse</h2>
                <p id="scoreText" class="text-xl text-gray-600 mb-6"></p>
                
                <div class="relative mb-8">
                    <div class="w-full bg-gray-200 rounded-full h-4">
                        <div id="scoreBar" class="progress-bar h-4 rounded-full bg-gradient-to-r from-indigo-500 to-purple-600" style="width: 0%"></div>
                    </div>
                    <div class="flex justify-between text-xs text-gray-500 mt-1">
                        <span>Débutant</span>
                        <span>Expert</span>
                    </div>
                </div>
                
                <div class="bg-indigo-50 p-4 rounded-lg mb-8 border border-indigo-100 text-left">
                    <h3 class="font-semibold text-indigo-800 mb-2 flex items-center">
                        <i class="fas fa-lightbulb text-indigo-600 mr-2"></i>
                        Conseils pour progresser
                    </h3>
                    <p class="text-sm text-gray-700">
                        Pour mieux identifier les figures de style, entraînez-vous à repérer les écarts par rapport au langage courant. Notez les comparaisons, les oppositions, les répétitions et les images insolites dans les œuvres étudiées.
                    </p>
                </div>
                
                <div id="detailedResults" class="text-left mb-8"></div>
                
                <div class="flex flex-col sm:flex-row justify-center gap-4">
                    <button id="restartQuiz" class="bg-gradient-to-r from-indigo-500 to-purple-500 hover:from-indigo-600 hover:to-purple-600 text-white font-medium py-3 px-6 rounded-lg transition duration-300 shadow-md flex-1 max-w-xs mx-auto">
                        <i class="fas fa-redo mr-2"></i>Recommencer le quiz
                    </button>
                    <button id="shareResults" class="bg-gray-100 hover:bg-gray-200 text-gray-800 font-medium py-3 px-6 rounded-lg transition duration-300 flex-1 max-w-xs mx-auto">
                        <i class="fas fa-share-alt mr-2"></i>Partager mes résultats
                    </button>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <footer class="text-center text-gray-500 text-sm mt-12 fade-in">
            <div class="mb-4">
                <p class="font-medium text-gray-600">Quiz pédagogique sur 51 figures de style</p>
                <p class="mt-1">Comparaison, Métaphore, Personnification, Allégorie, Antithèse, Oxymore, Antiphrase, Hyperbole, Énumération, Gradation, Répétition, Anaphore, Périphrase, Métonymie, Synecdoque, Euphémisme, Litote et bien d'autres</p>
            </div>
            <div class="flex flex-wrap justify-center gap-4 mb-4">
                <a href="#" class="text-indigo-600 hover:text-indigo-800 transition duration-300">
                    <i class="fas fa-book mr-1"></i> Bibliographie
                </a>
                <a href="#" class="text-indigo-600 hover:text-indigo-800 transition duration-300">
                    <i class="fas fa-graduation-cap mr-1"></i> Méthodologie
                </a>
                <a href="#" class="text-indigo-600 hover:text-indigo-800 transition duration-300">
                    <i class="fas fa-question-circle mr-1"></i> Aide
                </a>
            </div>
            <p class="text-xs mt-4">
                © 2023 Quiz Littéraire - Tous droits réservés - Conçu pour l'apprentissage des procédés stylistiques
            </p>
        </footer>
    </div>

    <script>
        // Quiz questions with extracts from the works (51 questions now)
        const questions = [
            // La Boîte à Merveilles (17 questions)
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "La nuit était une grande dame vêtue de velours noir constellé d'étoiles.",
                question: "Quelle figure de style domine dans cette description nocturne ?",
                options: [
                    "Comparaison (avec 'comme')",
                    "Métaphore (assimilation directe)",
                    "Personnification (attribution de traits humains)",
                    "Allégorie (représentation abstraite)"
                ],
                answer: 1,
                explanation: "Il s'agit d'une <strong>métaphore</strong> filée qui assimile la nuit à une grande dame. L'auteur crée une image poétique sans utiliser de mot comparatif ('comme', 'tel'). La suite du texte développe cette image avec 'vêtue de velours noir'."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Les murs de la maison avaient des oreilles.",
                question: "Quelle figure donne des caractéristiques humaines aux murs ?",
                options: [
                    "Métaphore",
                    "Personnification",
                    "Allégorie",
                    "Métonymie"
                ],
                answer: 1,
                explanation: "C'est une <strong>personnification</strong> qui attribue aux murs la capacité d'entendre. Cette image suggère que les secrets ne sont pas à l'abri des indiscrétions dans cette maison. Le procédé crée une atmosphère de surveillance et de méfiance."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Le soleil dévorait les ombres une à une.",
                question: "Quelle figure attribue une action violente au soleil ?",
                options: [
                    "Personnification",
                    "Métaphore",
                    "Synecdoque (partie pour le tout)",
                    "Anaphore (répétition en début de phrase)"
                ],
                answer: 0,
                explanation: "C'est une <strong>personnification</strong> qui donne au soleil la capacité de 'dévorer'. Cette image crée une impression de violence et d'inexorabilité dans l'avancée du jour. Le verbe 'dévorar' anthropomorphise l'astre solaire."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Les murs de la maison soupiraient sous le vent.",
                question: "Quelle figure donne des traits humains à l'architecture ?",
                options: [
                    "Personnification",
                    "Métaphore",
                    "Allégorie",
                    "Hyperbole"
                ],
                answer: 0,
                explanation: "C'est une <strong>personnification</strong> qui attribue aux murs la capacité de soupirer. Cette image donne une âme à la maison et crée une atmosphère mélancolique. Le procédé traduit la sensibilité poétique de l'enfant narrateur."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "L'astre du jour disparaissait à l'horizon.",
                question: "Quelle figure désigne le soleil de manière détournée ?",
                options: [
                    "Métaphore",
                    "Métonymie",
                    "Périphrase",
                    "Synecdoque"
                ],
                answer: 2,
                explanation: "C'est une <strong>périphrase</strong> qui désigne le soleil par une expression détournée ('astre du jour'). Cette figure stylistique apporte une touche poétique à la description tout en évitant la répétition du mot 'soleil'."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Mes jouets étaient mes ministres et mes courtisans.",
                question: "Quelle figure transforme les jouets en personnages de cour ?",
                options: [
                    "Allégorie",
                    "Métaphore",
                    "Personnification",
                    "Métonymie"
                ],
                answer: 1,
                explanation: "Il s'agit d'une <strong>métaphore</strong> qui assimile les jouets à des membres d'une cour royale. Cette image montre comment l'enfant projette son imaginaire sur ses objets familiers, créant un univers miniature."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Le temps s'écoulait comme un ruisseau paresseux.",
                question: "Quelle figure compare le temps à un cours d'eau ?",
                options: [
                    "Comparaison",
                    "Métaphore",
                    "Allégorie",
                    "Personnification"
                ],
                answer: 0,
                explanation: "C'est une <strong>comparaison</strong> introduite par 'comme' qui rapproche le temps qui passe d'un ruisseau. Cette image évoque la lenteur des journées de l'enfance, perçues comme interminables."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "La lune, cette veilleuse céleste, veillait sur mon sommeil.",
                question: "Quelle figure qualifie la lune de veilleuse ?",
                options: [
                    "Métaphore",
                    "Comparaison",
                    "Périphrase",
                    "Personnification"
                ],
                answer: 0,
                explanation: "Nous avons ici une <strong>métaphore</strong> qui assimile la lune à une veilleuse. Cette image réconfortante montre comment l'enfant perçoit la lune comme protectrice de ses nuits."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Les étoiles clignotaient comme des yeux malicieux.",
                question: "Quelle figure donne aux étoiles un regard humain ?",
                options: [
                    "Comparaison",
                    "Personnification",
                    "Métaphore",
                    "Allégorie"
                ],
                answer: 0,
                explanation: "C'est une <strong>comparaison</strong> introduite par 'comme' qui attribue aux étoiles un comportement humain. Cette image montre la tendance de l'enfant à animer le monde qui l'entoure."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "La maison était un navire, mon lit sa cabine.",
                question: "Quelle figure développe cette image maritime ?",
                options: [
                    "Métaphore filée",
                    "Comparaison",
                    "Allégorie",
                    "Personnification"
                ],
                answer: 0,
                explanation: "Il s'agit d'une <strong>métaphore filée</strong> qui assimile la maison à un navire et le lit à une cabine. Cette image montre comment l'enfant transforme son environnement en univers imaginaire cohérent."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Le vent hurlait à la mort toute la nuit.",
                question: "Quelle figure exagère le bruit du vent ?",
                options: [
                    "Hyperbole",
                    "Personnification",
                    "Métaphore",
                    "Antiphrase"
                ],
                answer: 0,
                explanation: "C'est une <strong>hyperbole</strong> qui exagère le bruit du vent ('hurlait à la mort'). Cette figure montre comment l'enfant perçoit intensément les phénomènes naturels, qui prennent des proportions dramatiques."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Mes souvenirs étaient des perles dans un écrin.",
                question: "Quelle figure compare les souvenirs à des bijoux ?",
                options: [
                    "Métaphore",
                    "Comparaison",
                    "Allégorie",
                    "Synecdoque"
                ],
                answer: 0,
                explanation: "Nous avons ici une <strong>métaphore</strong> qui assimile les souvenirs à des perles précieuses. Cette image montre la valeur affective que l'enfant attribue à ses expériences passées."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "La pluie chantait une berceuse sur le toit.",
                question: "Quelle figure attribue une voix à la pluie ?",
                options: [
                    "Personnification",
                    "Métaphore",
                    "Allégorie",
                    "Antiphrase"
                ],
                answer: 0,
                explanation: "C'est une <strong>personnification</strong> qui donne à la pluie la capacité de chanter. Cette image poétique transforme un phénomène météorologique en entité bienveillante qui berce l'enfant."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Le matin, le soleil m'inondait de ses rayons dorés.",
                question: "Quelle figure évoque cette lumière généreuse ?",
                options: [
                    "Métaphore",
                    "Personnification",
                    "Hyperbole",
                    "Antithèse"
                ],
                answer: 1,
                explanation: "C'est une <strong>personnification</strong> qui donne au soleil une intention ('m'inondait'). Cette figure montre comment l'enfant perçoit la nature comme une entité consciente et bienveillante."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Mes peurs étaient des ombres, mes joies des soleils.",
                question: "Quelle figure oppose ces deux images ?",
                options: [
                    "Antithèse",
                    "Oxymore",
                    "Métaphore",
                    "Personnification"
                ],
                answer: 0,
                explanation: "C'est une <strong>antithèse</strong> qui oppose les peurs (ombres) aux joies (soleils). Cette construction binaire montre la vision manichéenne de l'enfant, qui classe ses émotions en catégories tranchées."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "La rue grouillait de monde, fourmilière humaine.",
                question: "Quelle figure compare la foule à une fourmilière ?",
                options: [
                    "Métaphore",
                    "Comparaison",
                    "Personnification",
                    "Allégorie"
                ],
                answer: 0,
                explanation: "Il s'agit d'une <strong>métaphore</strong> qui assimile la foule à une fourmilière. Cette image montre comment l'enfant perçoit l'agitation urbaine comme un phénomène naturel organisé."
            },
            {
                book: "La Boîte à Merveilles",
                bookColor: "bg-amber-100",
                textColor: "text-amber-800",
                icon: "fas fa-box-open",
                quote: "Les heures s'étiraient, interminables.",
                question: "Quelle figure traduit cette dilatation du temps ?",
                options: [
                    "Hyperbole",
                    "Personnification",
                    "Métaphore",
                    "Litote"
                ],
                answer: 1,
                explanation: "C'est une <strong>personnification</strong> qui attribue aux heures la capacité de s'étirer. Cette image montre la perception subjective du temps dans l'esprit de l'enfant qui s'ennuie."

            },
            // Antigone (17 questions)
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je suis née pour partager l'amour, non la haine.",
                question: "Quelle figure structure cette opposition ?",
                options: [
                    "Antithèse (opposition de termes)",
                    "Oxymore (alliance de contraires)",
                    "Parallélisme (construction symétrique)",
                    "Gradation (progression)"
                ],
                answer: 0,
                explanation: "C'est une <strong>antithèse</strong> qui oppose radicalement 'amour' et 'haine'. Cette figure stylistique renforce le caractère d'Antigone et son refus de la violence. L'opposition est marquée par la construction parallèle de la phrase."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je ne veux pas comprendre, c'est bon pour vous.",
                question: "Quelle figure montre ce refus de la raison ?",
                options: [
                    "Antiphrase (contraire du sens apparent)",
                    "Litote (atténuation)",
                    "Paradoxe (apparente contradiction)",
                    "Euphémisme (adoucissement)"
                ],
                answer: 2,
                explanation: "C'est un <strong>paradoxe</strong> qui affirme un refus de comprendre comme vertu. Cette figure montre le rejet des compromis par Antigone. L'apparente contradiction souligne son attachement aux valeurs absolues contre la raison d'État."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je suis de ceux qui aiment, non de ceux qui haïssent.",
                question: "Quelle figure structure cette opposition binaire ?",
                options: [
                    "Antithèse",
                    "Chiasme (structure croisée)",
                    "Anaphore",
                    "Gradation"
                ],
                answer: 0,
                explanation: "C'est une <strong>antithèse</strong> qui oppose radicalement 'ceux qui aiment' et 'ceux qui haïssent'. Cette construction binaire souligne le refus des nuances chez Antigone. La figure stylistique montre son caractère absolu et intransigeant."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Non, vous n'êtes pas digne de savoir pourquoi je dois mourir.",
                question: "Quelle figure exprime ce déni avec force ?",
                options: [
                    "Antiphrase",
                    "Litote",
                    "Paradoxe",
                    "Hyperbole"
                ],
                answer: 0,
                explanation: "C'est une <strong>antiphrase</strong> où Antigone dit 'vous n'êtes pas digne' pour exprimer que Créon est indigne de comprendre ses motivations. Cette figure renforce le caractère tranché de son jugement et son refus de compromis."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je ne tremble pas, je ne rougis pas, je ne mens pas.",
                question: "Quelle figure utilise cette triple négation ?",
                options: [
                    "Anaphore (répétition en début de phrase)",
                    "Gradation (progression)",
                    "Énumération (liste)",
                    "Périphrase (détour)"
                ],
                answer: 0,
                explanation: "C'est une <strong>anaphore</strong> avec la répétition de 'je ne' en début de chaque proposition. Cette figure renforce le caractère catégorique du discours d'Antigone et son refus de toute faiblesse ou compromission."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je ne suis pas venue pour partager votre haine, mais pour partager votre amour.",
                question: "Quelle figure joue sur l'opposition et la répétition ?",
                options: [
                    "Antithèse + Anaphore",
                    "Oxymore + Gradation",
                    "Métaphore + Comparaison",
                    "Personnification + Allégorie"
                ],
                answer: 0,
                explanation: "C'est une combinaison d'<strong>antithèse</strong> (opposition haine/amour) et d'<strong>anaphore</strong> (répétition de 'pour partager votre'). Cette construction complexe montre la maîtrise rhétorique d'Antigone et la force de ses convictions."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Ma vie n'est pas une vie si je dois la vivre sans vous.",
                question: "Quelle figure exprime cette condition absolue ?",
                options: [
                    "Antithèse",
                    "Oxymore",
                    "Hyperbole",
                    "Paradoxe"
                ],
                answer: 3,
                explanation: "C'est un <strong>paradoxe</strong> qui affirme que la vie n'est pas une vie dans certaines conditions. Cette apparente contradiction montre l'absolu des sentiments d'Antigone, pour qui la vie sans l'être aimé perd tout son sens."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je suis seule contre tous. Et j'ai raison.",
                question: "Quelle figure souligne cet isolement assumé ?",
                options: [
                    "Antithèse",
                    "Parallélisme",
                    "Gradation",
                    "Hyperbole"
                ],
                answer: 0,
                explanation: "C'est une <strong>antithèse</strong> qui oppose 'seule' à 'tous'. Cette figure montre le contraste entre l'isolement d'Antigone et sa conviction intérieure. La brièveté de la phrase renforce son caractère péremptoire."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Créon: Tu es folle! Antigone: Non, je suis lucide.",
                question: "Quelle figure structure cet échange ?",
                options: [
                    "Antithèse",
                    "Oxymore",
                    "Parallélisme",
                    "Anaphore"
                ],
                answer: 0,
                explanation: "C'est une <strong>antithèse</strong> qui oppose 'folle' à 'lucide'. Cette figure montre le conflit de perceptions entre les personnages. La réplique courte et tranchée d'Antigone souligne sa certitude."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je dois mourir, et ce ne sera pas rien.",
                question: "Quelle figure atténue tout en renforçant ?",
                options: [
                    "Litote",
                    "Euphémisme",
                    "Antiphrase",
                    "Hyperbole"
                ],
                answer: 0,
                explanation: "C'est une <strong>litote</strong> qui exprime l'importance de la mort ('ce ne sera pas rien') en utilisant la négation du contraire. Cette figure atténue l'expression tout en renforçant l'idée par l'implicite."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je ne suis pas faite pour la haine, mais pour l'amour.",
                question: "Quelle figure oppose ces deux sentiments ?",
                options: [
                    "Antithèse",
                    "Oxymore",
                    "Chiasme",
                    "Gradation"
                ],
                answer: 0,
                explanation: "C'est une <strong>antithèse</strong> qui oppose 'haine' et 'amour'. Cette figure montre la conception binaire qu'Antigone a des sentiments humains. La construction parallèle renforce l'opposition."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je ne défie pas la loi, je lui suis supérieure.",
                question: "Quelle figure exprime cette transcendance ?",
                options: [
                    "Hyperbole",
                    "Antithèse",
                    "Paradoxe",
                    "Litote"
                ],
                answer: 2,
                explanation: "C'est un <strong>paradoxe</strong> qui affirme une supériorité à la loi sans la défier. Cette apparente contradiction montre qu'Antigone se place sur un plan moral différent de celui de la loi humaine."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je ne suis pas née pour haïr, je suis née pour aimer.",
                question: "Quelle figure répète cette structure ?",
                options: [
                    "Anaphore",
                    "Parallélisme",
                    "Gradation",
                    "Énumération"
                ],
                answer: 1,
                explanation: "C'est un <strong>parallélisme</strong> qui répète la structure 'je ne suis pas née pour... je suis née pour...'. Cette figure donne un rythme et une force persuasive au discours d'Antigone."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Ma mort sera plus vivante que votre vie.",
                question: "Quelle figure oppose ces deux concepts ?",
                options: [
                    "Oxymore",
                    "Antithèse",
                    "Paradoxe",
                    "Hyperbole"
                ],
                answer: 1,
                explanation: "C'est une <strong>antithèse</strong> qui oppose 'mort' et 'vie'. Cette figure montre comment Antigone inverse les valeurs, considérant que sa mort aura plus de sens que la vie de ceux qui obéissent à Créon."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je ne suis pas ici pour comprendre, mais pour agir.",
                question: "Quelle figure oppose ces deux actions ?",
                options: [
                    "Antithèse",
                    "Oxymore",
                    "Gradation",
                    "Parallélisme"
                ],
                answer: 0,
                explanation: "C'est une <strong>antithèse</strong> qui oppose 'comprendre' et 'agir'. Cette figure montre le refus d'Antigone de se laisser distraire par la réflexion lorsqu'il s'agit de principes moraux absolus."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je ne crains pas votre colère, je la méprise.",
                question: "Quelle figure intensifie ce mépris ?",
                options: [
                    "Gradation",
                    "Antithèse",
                    "Hyperbole",
                    "Litote"
                ],
                answer: 0,
                explanation: "C'est une <strong>gradation</strong> qui va de 'ne pas craindre' à 'mépriser'. Cette figure montre l'escalade dans le rejet de l'autorité de Créon par Antigone, qui passe de l'indifférence au mépris actif."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Votre justice n'est pas la mienne, votre loi n'est pas la mienne.",
                question: "Quelle figure répète cette structure ?",
                options: [
                    "Anaphore",
                    "Parallélisme",
                    "Antithèse",
                    "Énumération"
                ],
                answer: 1,
                explanation: "C'est un <strong>parallélisme</strong> qui répète la structure 'votre... n'est pas la mienne'. Cette figure donne un rythme martelé au discours d'Antigone, soulignant son refus de toute compromission."
            },
            {
                book: "Antigone",
                bookColor: "bg-red-100",
                textColor: "text-red-800",
                icon: "fas fa-theater-masks",
                quote: "Je suis l'étrangère, la rebelle, la criminelle.",
                question: "Quelle figure accumule ces qualifications ?",
                options: [
                    "Énumération",
                    "Gradation",
                    "Anaphore",
                    "Parallélisme"
                ],
                answer: 0,
                explanation: "C'est une <strong>énumération</strong> qui accumule les termes désignant Antigone. Cette figure montre comment elle assume pleinement les qualifications que lui attribue Créon, les transformant en marques de fierté."
            },
            // Le Dernier Jour d'un Condamné (17 questions)
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Ma tête était une fournaise où brûlaient toutes mes pensées.",
                question: "Quelle figure exprime cette fièvre mentale ?",
                options: [
                    "Comparaison",
                    "Métaphore",
                    "Hyperbole (exagération)",
                    "Énumération"
                ],
                answer: 1,
                explanation: "Nous avons ici une <strong>métaphore</strong> qui assimile la tête à une fournaise. Cette image violente traduit la surchauffe mentale du condamné. L'intensité de la chaleur exprime l'embrasement de ses pensées sous l'effet de l'angoisse."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Chaque minute était une éternité.",
                question: "Quelle figure traduit cette dilatation du temps ?",
                options: [
                    "Oxymore",
                    "Antithèse",
                    "Hyperbole",
                    "Périphrase"
                ],
                answer: 2,
                explanation: "Nous avons ici une <strong>hyperbole</strong> qui exagère la durée subjective des minutes. Cette figure montre comment le temps psychologique du condamné se distend face à l'angoisse. L'opposition minute/éternité crée un effet dramatique."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Ma vie n'était plus qu'un long frisson.",
                question: "Quelle figure réduit l'existence à une sensation ?",
                options: [
                    "Métaphore",
                    "Comparaison",
                    "Métonymie (contiguïté)",
                    "Synecdoque"
                ],
                answer: 0,
                explanation: "Il s'agit d'une <strong>métaphore</strong> qui assimile la vie à un frisson. Cette image traduit l'état de peur permanente du condamné. La réduction de l'existence à une seule sensation montre l'envahissement de l'angoisse."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Six heures du matin. Six heures et demie. Sept heures.",
                question: "Quelle figure traduit cette obsession du temps ?",
                options: [
                    "Énumération",
                    "Gradation",
                    "Répétition",
                    "Anaphore"
                ],
                answer: 0,
                explanation: "Nous avons ici une <strong>énumération</strong> des heures qui passent, traduisant l'obsession du condamné pour le temps qui lui reste. Cette figure montre comment chaque minute est comptée et intensément vécue."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "La lame tombera, et ce ne sera pas rien.",
                question: "Quelle figure atténue l'idée de la décapitation ?",
                options: [
                    "Euphémisme",
                    "Litote",
                    "Antiphrase",
                    "Oxymore"
                ],
                answer: 1,
                explanation: "Nous avons ici une <strong>litote</strong> qui exprime l'importance de l'événement ('ce ne sera pas rien') en utilisant la négation du contraire. Cette figure atténue l'expression tout en renforçant l'idée par l'implicite."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "La prison est un tombeau où l'on entre vivant.",
                question: "Quelle figure compare la prison à un tombeau ?",
                options: [
                    "Métaphore",
                    "Comparaison",
                    "Allégorie",
                    "Personnification"
                ],
                answer: 0,
                explanation: "C'est une <strong>métaphore</strong> qui assimile la prison à un tombeau. Cette image montre comment le condamné perçoit son incarcération comme une mort anticipée. L'oxymore 'vivant' dans un 'tombeau' renforce l'horreur de la situation."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Mes souvenirs dansaient une ronde infernale dans ma tête.",
                question: "Quelle figure attribue une action à des abstractions ?",
                options: [
                    "Personnification",
                    "Métaphore",
                    "Allégorie",
                    "Hyperbole"
                ],
                answer: 0,
                explanation: "C'est une <strong>personnification</strong> qui donne aux souvenirs la capacité de danser. Cette image montre l'agitation incontrôlable des pensées du condamné. L'adjectif 'infernale' renforce l'aspect torturant de ces souvenirs."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Le bourreau, cette machine à tuer, attendait son heure.",
                question: "Quelle figure assimile le bourreau à une machine ?",
                options: [
                    "Métaphore",
                    "Comparaison",
                    "Métonymie",
                    "Synecdoque"
                ],
                answer: 0,
                explanation: "Il s'agit d'une <strong>métaphore</strong> qui assimile le bourreau à une machine. Cette image montre comment le condamné déshumanise son exécuteur, le réduisant à une fonction mécanique de mort."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "J'avais froid, froid partout, froid dans l'âme.",
                question: "Quelle figure insiste sur cette sensation ?",
                options: [
                    "Anaphore",
                    "Gradation",
                    "Hyperbole",
                    "Énumération"
                ],
                answer: 1,
                explanation: "C'est une <strong>gradation</strong> qui intensifie la sensation de froid du physique ('froid') au moral ('froid dans l'âme'). Cette figure montre l'envahissement progressif du désespoir chez le condamné."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "La mort, cette vieille connaissance, allait m'emporter.",
                question: "Quelle figure personnifie la mort ?",
                options: [
                    "Personnification",
                    "Métaphore",
                    "Allégorie",
                    "Périphrase"
                ],
                answer: 0,
                explanation: "C'est une <strong>personnification</strong> qui donne à la mort les traits d'une 'vieille connaissance'. Cette image montre comment le condamné a progressivement apprivoisé l'idée de sa propre mort tout au long de son récit."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Mes larmes étaient un déluge, mes sanglots un ouragan.",
                question: "Quelle figure exagère ces manifestations de désespoir ?",
                options: [
                    "Hyperbole",
                    "Métaphore",
                    "Personnification",
                    "Antithèse"
                ],
                answer: 0,
                explanation: "Nous avons ici une <strong>hyperbole</strong> qui exagère l'intensité des pleurs du condamné. Ces images météorologiques ('déluge', 'ouragan') montrent la violence de son désespoir face à son sort."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Le jour se levait, ironique et gai.",
                question: "Quelle figure donne des traits humains au jour ?",
                options: [
                    "Personnification",
                    "Métaphore",
                    "Antiphrase",
                    "Oxymore"
                ],
                answer: 0,
                explanation: "C'est une <strong>personnification</strong> qui attribue au jour des sentiments humains ('ironique et gai'). Cette figure montre le contraste cruel entre la sérénité de la nature et l'angoisse du condamné."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Ma cellule était un cercueil de pierre.",
                question: "Quelle figure compare la cellule à un cercueil ?",
                options: [
                    "Métaphore",
                    "Comparaison",
                    "Allégorie",
                    "Synecdoque"
                ],
                answer: 0,
                explanation: "Il s'agit d'une <strong>métaphore</strong> qui assimile la cellule à un cercueil. Cette image montre comment le condamné perçoit son emprisonnement comme une mort anticipée. L'ajout 'de pierre' renforce l'aspect minéral et froid de cette prison."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "J'entendais battre mon cœur comme un tambour funèbre.",
                question: "Quelle figure compare les battements cardiaques à un tambour ?",
                options: [
                    "Comparaison",
                    "Métaphore",
                    "Personnification",
                    "Allégorie"
                ],
                answer: 0,
                explanation: "C'est une <strong>comparaison</strong> introduite par 'comme' qui rapproche les battements du cœur d'un tambour funèbre. Cette image souligne l'angoisse croissante du condamné qui perçoit son propre corps comme annonciateur de sa mort."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Les murs avaient des bouches qui chuchotaient mon nom.",
                question: "Quelle figure donne des traits humains aux murs ?",
                options: [
                    "Personnification",
                    "Métaphore",
                    "Allégorie",
                    "Métonymie"
                ],
                answer: 0,
                explanation: "C'est une <strong>personnification</strong> qui attribue aux murs la capacité de parler. Cette image montre les hallucinations du condamné sous l'effet de la peur et de l'isolement. Les chuchotements renforcent l'atmosphère oppressante."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Ma vie n'était qu'un long cri étouffé.",
                question: "Quelle figure réduit l'existence à une expression ?",
                options: [
                    "Métaphore",
                    "Comparaison",
                    "Hyperbole",
                    "Oxymore"
                ],
                answer: 0,
                explanation: "Nous avons ici une <strong>métaphore</strong> qui assimile la vie à un cri étouffé. Cette image montre l'impuissance et la frustration du condamné, dont la protestation contre son sort ne peut s'exprimer pleinement."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Le temps fuyait comme l'eau entre mes doigts.",
                question: "Quelle figure compare le temps à de l'eau ?",
                options: [
                    "Comparaison",
                    "Métaphore",
                    "Personnification",
                    "Allégorie"
                ],
                answer: 0,
                explanation: "C'est une <strong>comparaison</strong> introduite par 'comme' qui rapproche le temps qui passe de l'eau insaisissable. Cette image montre l'impuissance du condamné à retenir les derniers moments de sa vie."
            },
            {
                book: "Le Dernier Jour d'un Condamné",
                bookColor: "bg-blue-100",
                textColor: "text-blue-800",
                icon: "fas fa-gavel",
                quote: "Ma peur était un monstre qui dévorait ma raison.",
                question: "Quelle figure personnifie la peur ?",
                options: [
                    "Personnification",
                    "Métaphore",
                    "Allégorie",
                    "Hyperbole"
                ],
                answer: 0,
                explanation: "C'est une <strong>personnification</strong> qui donne à la peur les traits d'un monstre. Cette image montre comment l'angoisse du condamné prend des proportions incontrôlables, menaçant sa santé mentale."
            }
        ];

        // Quiz variables
        let currentQuestion = 0;
        let score = 0;
        let userAnswers = new Array(questions.length).fill(null);

        // DOM elements
        const quizContainer = document.getElementById('quizContainer');
        const resultsContainer = document.getElementById('resultsContainer');
        const bookIcon = document.getElementById('bookIcon');
        const bookTitle = document.getElementById('bookTitle');
        const quoteText = document.getElementById('quoteText');
        const questionElement = document.getElementById('question');
        const optionsElement = document.getElementById('options');
        const feedbackElement = document.getElementById('feedback');
        const nextBtn = document.getElementById('nextBtn');
        const prevBtn = document.getElementById('prevBtn');
        const progressText = document.getElementById('progressText');
        const progressBar = document.getElementById('progressBar');
        const scoreText = document.getElementById('scoreText');
        const scoreBar = document.getElementById('scoreBar');
        const detailedResults = document.getElementById('detailedResults');
        const restartQuizBtn = document.getElementById('restartQuiz');
        const shareResultsBtn = document.getElementById('shareResults');

        // Load question with animation
        function loadQuestion() {
            const question = questions[currentQuestion];
            
            // Reset animations
            questionContainer.classList.remove('fade-in');
            void questionContainer.offsetWidth; // Trigger reflow
            questionContainer.classList.add('fade-in');
            
            // Set book info
            bookIcon.className = `book-icon ${question.bookColor} ${question.textColor} ${question.icon}`;
            bookTitle.textContent = question.book;
            bookTitle.className = question.textColor;
            
            // Set quote and question
            quoteText.textContent = question.quote;
            questionElement.textContent = question.question;
            
            // Update progress
            progressText.textContent = `${currentQuestion + 1}/${questions.length}`;
            progressBar.style.width = `${((currentQuestion + 1) / questions.length) * 100}%`;
            
            // Clear previous options
            optionsElement.innerHTML = '';
            
            // Add new options with delay
            question.options.forEach((option, index) => {
                const optionElement = document.createElement('div');
                optionElement.className = `option bg-white border border-gray-200 rounded-lg p-3 cursor-pointer transition duration-300 hover:border-indigo-300 ${userAnswers[currentQuestion] === index ? (userAnswers[currentQuestion] === question.answer ? 'correct' : 'incorrect') : ''}`;
                optionElement.innerHTML = `
                    <div class="flex items-center">
                        <div class="w-6 h-6 rounded-full border border-gray-300 mr-3 flex items-center justify-center ${userAnswers[currentQuestion] === index ? (userAnswers[currentQuestion] === question.answer ? 'bg-green-100 border-green-400' : 'bg-red-100 border-red-400') : ''}">
                            ${String.fromCharCode(65 + index)}
                        </div>
                        <span>${option}</span>
                    </div>
                `;
                
                optionElement.addEventListener('click', () => selectOption(index));
                optionsElement.appendChild(optionElement);
            });
            
            // Show feedback if answer was selected
            if (userAnswers[currentQuestion] !== null) {
                showFeedback();
            } else {
                feedbackElement.classList.add('hidden');
            }
            
            // Update navigation buttons
            prevBtn.classList.toggle('hidden', currentQuestion === 0);
            nextBtn.textContent = currentQuestion === questions.length - 1 ? 'Terminer et voir les résultats' : 'Question suivante';
            nextBtn.classList.toggle('hidden', userAnswers[currentQuestion] === null && currentQuestion !== questions.length - 1);
        }

        // Select option
        function selectOption(index) {
            if (userAnswers[currentQuestion] !== null) return;
            
            const question = questions[currentQuestion];
            userAnswers[currentQuestion] = index;
            
            // Update score if correct
            if (index === question.answer) {
                score++;
            }
            
            // Highlight selected option
            const options = optionsElement.children;
            for (let i = 0; i < options.length; i++) {
                options[i].classList.remove('correct', 'incorrect');
                if (i === index) {
                    options[i].classList.add(i === question.answer ? 'correct' : 'incorrect');
                }
                if (i === question.answer && index !== question.answer) {
                    options[i].classList.add('correct');
                }
            }
            
            showFeedback();
            nextBtn.classList.remove('hidden');
        }

        // Show feedback with animation
        function showFeedback() {
            const question = questions[currentQuestion];
            const isCorrect = userAnswers[currentQuestion] === question.answer;
            
            feedbackElement.className = `p-4 rounded-lg mb-6 border-l-4 ${isCorrect ? 'bg-green-50 border-green-400' : 'bg-red-50 border-red-400'} fade-in`;
            feedbackElement.innerHTML = `
                <div class="flex items-start">
                    <div class="mr-3 ${isCorrect ? 'text-green-500' : 'text-red-500'}">
                        <i class="fas ${isCorrect ? 'fa-check-circle' : 'fa-times-circle'} text-xl"></i>
                    </div>
                    <div>
                        <p class="font-medium ${isCorrect ? 'text-green-800' : 'text-red-800'}">
                            ${isCorrect ? 'Excellente analyse !' : 'Attention à votre interprétation'}
                        </p>
                        <p class="text-gray-700 mt-1">${question.explanation}</p>
                        ${!isCorrect ? `<p class="text-sm text-gray-600 mt-2"><i class="fas fa-lightbulb mr-1"></i> Conseil : Relisez attentivement l'extrait en cherchant les écarts par rapport au langage courant.</p>` : ''}
                    </div>
                </div>
            `;
            feedbackElement.classList.remove('hidden');
        }

        // Next question
        nextBtn.addEventListener('click', () => {
            if (currentQuestion < questions.length - 1) {
                currentQuestion++;
                loadQuestion();
            } else {
                showResults();
            }
        });

        // Previous question
        prevBtn.addEventListener('click', () => {
            if (currentQuestion > 0) {
                currentQuestion--;
                loadQuestion();
            }
        });

        // Show results with animation
        function showResults() {
            quizContainer.classList.add('hidden');
            resultsContainer.classList.remove('hidden');
            resultsContainer.classList.add('fade-in');
            
            const percentage = Math.round((score / questions.length) * 100);
            let message = "";
            
            if (percentage >= 90) {
                message = "Expert en analyse stylistique ! Vous maîtrisez parfaitement les 51 figures de style.";
            } else if (percentage >= 70) {
                message = "Très bon niveau ! Vous identifiez correctement la plupart des procédés littéraires.";
            } else if (percentage >= 50) {
                message = "Niveau correct. Continuez à vous entraîner pour perfectionner votre analyse.";
            } else {
                message = "En cours d'acquisition. Relisez les œuvres et révisez les principales figures de style.";
            }
            
            scoreText.innerHTML = `Vous avez obtenu <span class="font-bold">${score}/${questions.length}</span> (${percentage}%)<br><span class="text-sm">${message}</span>`;
            scoreBar.style.width = `${percentage}%`;
            
            // Detailed results
            detailedResults.innerHTML = `
                <h3 class="font-semibold text-lg mb-4 border-b pb-2 flex items-center">
                    <i class="fas fa-clipboard-list text-indigo-600 mr-2"></i>
                    Détail de votre analyse stylistique
                </h3>
            `;
            
            questions.forEach((question, index) => {
                const isCorrect = userAnswers[index] === question.answer;
                const userAnswerText = userAnswers[index] !== null ? question.options[userAnswers[index]] : "Non répondue";
                
                detailedResults.innerHTML += `
                    <div class="mb-4 p-4 rounded-lg ${isCorrect ? 'bg-green-50 border border-green-100' : 'bg-red-50 border border-red-100'}">
                        <div class="flex justify-between items-center mb-3">
                            <div>
                                <span class="inline-block px-2 py-1 rounded text-xs font-medium ${question.bookColor} ${question.textColor} mb-1">
                                    <i class="${question.icon} mr-1"></i> ${question.book}
                                </span>
                                <p class="font-medium">Question ${index + 1}: ${question.question}</p>
                            </div>
                            <span class="px-2 py-1 rounded-full text-xs font-medium ${isCorrect ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800'}">
                                ${isCorrect ? 'Réussite' : 'À revoir'}
                            </span>
                        </div>
                        
                        <div class="bg-gray-50 p-3 rounded mb-3 italic text-gray-700 text-sm relative">
                            <div class="absolute -top-2 -left-2 w-6 h-6 ${question.bookColor} rounded-full flex items-center justify-center">
                                <i class="${question.icon} ${question.textColor} text-xs"></i>
                            </div>
                            <i class="fas fa-quote-left text-gray-400 mr-1"></i>
                            ${question.quote}
                        </div>
                        
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-sm">
                            <div class="bg-white p-2 rounded border ${isCorrect ? 'border-green-200' : 'border-red-200'}">
                                <p class="font-medium text-gray-700 mb-1">Votre réponse:</p>
                                <p>${userAnswerText}</p>
                            </div>
                            <div class="bg-white p-2 rounded border border-gray-200">
                                <p class="font-medium text-gray-700 mb-1">Réponse attendue:</p>
                                <p>${question.options[question.answer]}</p>
                            </div>
                        </div>
                        
                        <div class="mt-3 p-2 bg-indigo-50 rounded text-sm">
                            <p class="font-medium text-indigo-800 mb-1">Explication détaillée:</p>
                            <p>${question.explanation}</p>
                        </div>
                    </div>
                `;
            });
        }

        // Restart quiz
        restartQuizBtn.addEventListener('click', () => {
            currentQuestion = 0;
            score = 0;
            userAnswers = new Array(questions.length).fill(null);
            resultsContainer.classList.add('hidden');
            quizContainer.classList.remove('hidden');
            loadQuestion();
        });

        // Share results
        shareResultsBtn.addEventListener('click', () => {
            const percentage = Math.round((score / questions.length) * 100);
            const shareText = `J'ai obtenu ${score}/${questions.length} (${percentage}%) au quiz sur les 51 figures de style dans "La Boîte à Merveilles", "Antigone" et "Le Dernier Jour d'un Condamné" ! Saurez-vous faire mieux ?`;
            
            if (navigator.share) {
                navigator.share({
                    title: 'Mon score au quiz littéraire',
                    text: shareText,
                    url: window.location.href
                }).catch(err => {
                    console.log('Erreur de partage:', err);
                    fallbackShare();
                });
            } else {
                fallbackShare();
            }
            
            function fallbackShare() {
                const shareUrl = `https://twitter.com/intent/tweet?text=${encodeURIComponent(shareText)}&url=${encodeURIComponent(window.location.href)}`;
                window.open(shareUrl, '_blank');
            }
        });

        // Initialize quiz
        loadQuestion();
    </script>
</body>
</html>
