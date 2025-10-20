
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <base target="_self">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Conhecimento Geral - Teste Seu Saber</title>
    <meta name="description" content="Teste seu conhecimento com 32 questões de conhecimento geral. Cadastre-se e participe!">
    <meta name="keywords" content="quiz, conhecimento geral, perguntas e respostas, teste, educação">
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: "#3B82F6",
                        secondary: "#1E40AF",
                        accent: "#10B981",
                        danger: "#EF4444",
                        warning: "#F59E0B"
                    },
                    fontFamily: {
                        'sans': ['Inter', 'system-ui', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
</head>
<body class="min-h-screen bg-gray-50 font-sans">
    <!-- Header Global -->
    <header class="bg-white shadow-sm border-b border-gray-200 sticky top-0 z-50">
        <div class="container mx-auto px-4 py-3">
            <div class="flex justify-between items-center">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 bg-gradient-to-r from-primary to-secondary rounded-lg flex items-center justify-center">
                        <i class="fas fa-brain text-white text-lg"></i>
                    </div>
                    <div>
                        <h1 class="text-xl font-bold text-gray-800">Quiz Saber</h1>
                        <p class="text-xs text-gray-500">Teste seu conhecimento</p>
                    </div>
                </div>
                <div class="flex items-center space-x-4">
                    <span id="user-info" class="text-sm text-gray-600 hidden">
                        <i class="fas fa-user mr-1"></i>
                        <span id="user-email"></span>
                    </span>
                    <button id="logout-btn" class="text-gray-500 hover:text-gray-700 hidden">
                        <i class="fas fa-sign-out-alt"></i>
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Tela de Boas-vindas -->
    <div id="welcome-screen" class="min-h-screen flex items-center justify-center bg-gradient-to-br from-blue-500 via-purple-500 to-pink-500 p-4">
        <div class="bg-white rounded-2xl shadow-2xl p-8 w-full max-w-2xl">
            <div class="text-center mb-8">
                <div class="w-20 h-20 bg-gradient-to-r from-primary to-secondary rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fas fa-graduation-cap text-white text-3xl"></i>
                </div>
                <h1 class="text-4xl font-bold text-gray-800 mb-4">Quiz Conhecimento Geral</h1>
                <p class="text-lg text-gray-600 mb-2">Desafie seu cérebro com 32 questões fascinantes</p>
                <div class="flex justify-center items-center space-x-6 mt-6 text-sm text-gray-500">
                    <div class="flex items-center">
                        <i class="fas fa-clock text-primary mr-2"></i>
                        <span>15-20 min</span>
                    </div>
                    <div class="flex items-center">
                        <i class="fas fa-question-circle text-primary mr-2"></i>
                        <span>32 questões</span>
                    </div>
                    <div class="flex items-center">
                        <i class="fas fa-trophy text-primary mr-2"></i>
                        <span>Certificado</span>
                    </div>
                </div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
                <div class="bg-blue-50 rounded-lg p-4">
                    <h3 class="font-semibold text-blue-800 mb-2"><i class="fas fa-star mr-2"></i>Como funciona</h3>
                    <ul class="text-sm text-blue-700 space-y-1">
                        <li>• Cadastro rápido</li>
                        <li>• 32 questões variadas</li>
                        <li>• Resultado imediato</li>
                        <li>• Exportação automática</li>
                    </ul>
                </div>
                <div class="bg-green-50 rounded-lg p-4">
                    <h3 class="font-semibold text-green-800 mb-2"><i class="fas fa-shield-alt mr-2"></i>Privacidade</h3>
                    <ul class="text-sm text-green-700 space-y-1">
                        <li>• Dados protegidos</li>
                        <li>• Uso educacional</li>
                        <li>• Sem spam</li>
                        <li>• Exportação segura</li>
                    </ul>
                </div>
            </div>
            
            <button 
                id="start-btn"
                class="w-full bg-primary hover:bg-secondary text-white font-semibold py-4 px-6 rounded-lg transition-all duration-200 transform hover:scale-105 shadow-lg"
            >
                <i class="fas fa-play mr-2"></i>Começar Agora
            </button>
        </div>
    </div>

    <!-- Tela de Cadastro -->
    <div id="registration-screen" class="min-h-screen flex items-center justify-center bg-gray-50 p-4 hidden">
        <div class="bg-white rounded-2xl shadow-xl p-8 w-full max-w-md">
            <div class="text-center mb-8">
                <button id="back-to-welcome" class="absolute left-4 top-4 text-gray-500 hover:text-gray-700">
                    <i class="fas fa-arrow-left text-xl"></i>
                </button>
                <h2 class="text-2xl font-bold text-gray-800 mb-2">Cadastre-se</h2>
                <p class="text-gray-600">Informe seus dados para começar</p>
            </div>
            
            <form id="registration-form" class="space-y-6">
                <div>
                    <label for="phone" class="block text-sm font-medium text-gray-700 mb-2">
                        <i class="fas fa-phone mr-2 text-primary"></i>Número de Telefone
                    </label>
                    <input 
                        type="tel" 
                        id="phone" 
                        name="phone"
                        required
                        class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent transition-all"
                        placeholder="(11) 99999-9999"
                    >
                    <p class="text-xs text-gray-500 mt-1">Usaremos apenas para contato importante</p>
                </div>
                
                <div>
                    <label for="email" class="block text-sm font-medium text-gray-700 mb-2">
                        <i class="fas fa-envelope mr-2 text-primary"></i>E-mail
                    </label>
                    <input 
                        type="email" 
                        id="email" 
                        name="email"
                        required
                        class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent transition-all"
                        placeholder="seu@email.com"
                    >
                    <p class="text-xs text-gray-500 mt-1">Enviaremos seu resultado por e-mail</p>
                </div>

                <div class="flex items-center">
                    <input 
                        type="checkbox" 
                        id="terms"
                        required
                        class="w-4 h-4 text-primary border-gray-300 rounded focus:ring-primary"
                    >
                    <label for="terms" class="ml-2 text-sm text-gray-600">
                        Concordo com os <a href="#" class="text-primary hover:underline">termos de uso</a> e 
                        <a href="#" class="text-primary hover:underline">política de privacidade</a>
                    </label>
                </div>
                
                <button 
                    type="submit"
                    class="w-full bg-primary hover:bg-secondary text-white font-semibold py-3 px-4 rounded-lg transition-colors duration-200 transform hover:scale-105"
                >
                    <i class="fas fa-rocket mr-2"></i>Iniciar Quiz
                </button>
            </form>
        </div>
    </div>

    <!-- Tela do Quiz -->
    <div id="quiz-screen" class="min-h-screen bg-gray-50 hidden">
        <div class="container mx-auto px-4 py-6">
            <!-- Barra de Progresso Superior -->
            <div class="bg-white rounded-xl shadow-sm p-4 mb-6">
                <div class="flex flex-col md:flex-row md:items-center md:justify-between space-y-4 md:space-y-0">
                    <div class="flex-1">
                        <div class="flex justify-between items-center mb-2">
                            <span id="progress-text" class="text-sm font-medium text-gray-700">Questão 1 de 32</span>
                            <span id="timer" class="text-sm font-medium text-gray-700">
                                <i class="fas fa-clock mr-1"></i><span id="time-display">00:00</span>
                            </span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-3">
                            <div id="progress-bar" class="bg-gradient-to-r from-primary to-secondary h-3 rounded-full transition-all duration-300" style="width: 3%"></div>
                        </div>
                    </div>
                    <div class="flex space-x-2">
                        <button id="pause-btn" class="px-4 py-2 bg-gray-100 hover:bg-gray-200 text-gray-700 rounded-lg transition-colors">
                            <i class="fas fa-pause mr-2"></i>Pausar
                        </button>
                        <button id="hint-btn" class="px-4 py-2 bg-blue-100 hover:bg-blue-200 text-blue-700 rounded-lg transition-colors">
                            <i class="fas fa-lightbulb mr-2"></i>Dica
                        </button>
                    </div>
                </div>
            </div>

            <!-- Área da Questão -->
            <div class="max-w-4xl mx-auto">
                <div id="question-container" class="bg-white rounded-xl shadow-lg p-6 mb-6">
                    <div class="flex items-center justify-between mb-4">
                        <span class="text-sm font-medium text-primary bg-blue-50 px-3 py-1 rounded-full">
                            Questão #<span id="question-number">1</span>
                        </span>
                        <span class="text-sm text-gray-500">
                            <i class="fas fa-bookmark mr-1"></i>Conhecimento Geral
                        </span>
                    </div>
                    
                    <h2 id="question-text" class="text-2xl font-semibold text-gray-800 mb-6 leading-relaxed"></h2>
                    
                    <div id="options-container" class="space-y-3">
                        <!-- Opções serão geradas dinamicamente -->
                    </div>

                    <div id="hint-container" class="mt-4 p-4 bg-yellow-50 border border-yellow-200 rounded-lg hidden">
                        <div class="flex items-start">
                            <i class="fas fa-lightbulb text-yellow-500 mt-1 mr-3"></i>
                            <div>
                                <h4 class="font-semibold text-yellow-800 mb-1">Dica</h4>
                                <p id="hint-text" class="text-yellow-700 text-sm"></p>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Navegação -->
                <div class="flex justify-between items-center bg-white rounded-xl shadow-sm p-4">
                    <button 
                        id="prev-btn"
                        class="bg-gray-500 hover:bg-gray-600 text-white px-6 py-3 rounded-lg transition-colors flex items-center hidden"
                    >
                        <i class="fas fa-arrow-left mr-2"></i>Voltar
                    </button>
                    
                    <div class="flex space-x-3 ml-auto">
                        <button 
                            id="skip-btn"
                            class="border border-gray-300 hover:bg-gray-50 text-gray-700 px-6 py-3 rounded-lg transition-colors flex items-center"
                        >
                            <i class="fas fa-forward mr-2"></i>Pular
                        </button>
                        <button 
                            id="next-btn"
                            class="bg-primary hover:bg-secondary text-white px-6 py-3 rounded-lg transition-colors flex items-center"
                        >
                            Próxima<i class="fas fa-arrow-right ml-2"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal de Confirmação -->
    <div id="confirmation-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50 hidden">
        <div class="bg-white rounded-xl shadow-2xl p-6 w-full max-w-md">
            <div class="text-center mb-4">
                <i class="fas fa-exclamation-triangle text-3xl text-yellow-500 mb-3"></i>
                <h3 class="text-xl font-bold text-gray-800 mb-2">Tem certeza?</h3>
                <p class="text-gray-600" id="modal-message">Você tem respostas pendentes.</p>
            </div>
            <div class="flex space-x-3">
                <button id="modal-cancel" class="flex-1 bg-gray-500 hover:bg-gray-600 text-white py-3 rounded-lg transition-colors">
                    Cancelar
                </button>
                <button id="modal-confirm" class="flex-1 bg-primary hover:bg-secondary text-white py-3 rounded-lg transition-colors">
                    Confirmar
                </button>
            </div>
        </div>
    </div>

    <!-- Tela de Resultados -->
    <div id="results-screen" class="min-h-screen bg-gray-50 hidden">
        <div class="container mx-auto px-4 py-8">
            <div class="max-w-4xl mx-auto">
                <div class="bg-white rounded-xl shadow-lg p-8 mb-6">
                    <div class="text-center mb-8">
                        <div class="w-24 h-24 bg-gradient-to-r from-green-400 to-blue-500 rounded-full flex items-center justify-center mx-auto mb-6">
                            <i class="fas fa-trophy text-white text-4xl"></i>
                        </div>
                        
                        <h1 class="text-4xl font-bold text-gray-800 mb-4">Parabéns!</h1>
                        <p class="text-lg text-gray-600 mb-6">Você completou o quiz de conhecimento geral</p>
                        
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
                            <div class="text-center p-4 bg-blue-50 rounded-lg">
                                <div id="score" class="text-3xl font-bold text-primary mb-2">0/32</div>
                                <p class="text-sm text-gray-600">Pontuação Final</p>
                            </div>
                            <div class="text-center p-4 bg-green-50 rounded-lg">
                                <div id="percentage" class="text-3xl font-bold text-green-600 mb-2">0%</div>
                                <p class="text-sm text-gray-600">Desempenho</p>
                            </div>
                            <div class="text-center p-4 bg-purple-50 rounded-lg">
                                <div id="time-taken" class="text-3xl font-bold text-purple-600 mb-2">00:00</div>
                                <p class="text-sm text-gray-600">Tempo Total</p>
                            </div>
                        </div>
                    </div>

                    <!-- Dados para Exportação -->
                    <div class="bg-gray-50 rounded-lg p-6 mb-6">
                        <h3 class="text-lg font-semibold text-gray-800 mb-4 flex items-center">
                            <i class="fas fa-download mr-2 text-primary"></i>Dados para Exportação
                        </h3>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                            <div class="space-y-2">
                                <p><strong class="text-gray-700">Telefone:</strong> <span id="export-phone" class="text-gray-600"></span></p>
                                <p><strong class="text-gray-700">E-mail:</strong> <span id="export-email" class="text-gray-600"></span></p>
                                <p><strong class="text-gray-700">Data:</strong> <span id="export-date" class="text-gray-600"></span></p>
                            </div>
                            <div class="space-y-2">
                                <p><strong class="text-gray-700">Pontuação:</strong> <span id="export-score" class="text-gray-600"></span></p>
                                <p><strong class="text-gray-700">Porcentagem:</strong> <span id="export-percentage" class="text-gray-600"></span></p>
                                <p
