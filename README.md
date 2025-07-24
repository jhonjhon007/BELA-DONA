<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BELA DONA - Produtos de Luxo com Preços Acessíveis</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Poppins:wght@300;400;500;600&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
        }
        
        .header-font {
            font-family: 'Playfair Display', serif;
        }
        
        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
        }
        
        .hero-gradient {
            background: linear-gradient(135deg, #0d1b6b 0%, #1e3a8a 100%);
        }
        
        .btn-primary {
            transition: all 0.3s ease;
        }
        
        .btn-primary:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1);
        }
        
        .gold-text {
            color: #D4AF37;
        }
        
        .gold-bg {
            background-color: #D4AF37;
        }
        
        .gold-hover:hover {
            background-color: #C0A02C;
        }
        
        .royal-blue {
            background-color: #0d1b6b;
        }
        
        .royal-blue-light {
            background-color: #1e3a8a;
        }
        
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
        }
        
        .modal-content {
            background-color: #0d1b6b;
            margin: 5% auto;
            padding: 20px;
            border: 2px solid #D4AF37;
            border-radius: 10px;
            width: 90%;
            max-width: 600px;
            position: relative;
        }
        
        .close {
            color: #D4AF37;
            float: right;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }
        
        .close:hover {
            color: #C0A02C;
        }
        
        .cart-item {
            border-bottom: 1px solid #1e3a8a;
            padding: 15px 0;
        }
        
        /* Animation for "Fale Conosco" */
        .send-animation {
            animation: sendMessage 1s ease-in-out forwards;
        }
        
        @keyframes sendMessage {
            0% { transform: translateX(0); opacity: 1; }
            50% { transform: translateX(20px); opacity: 0.7; }
            100% { transform: translateX(0); opacity: 1; }
        }
        
        .sending-animation {
            position: relative;
            overflow: hidden;
        }
        
        .sending-animation::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            animation: sending 1.5s infinite;
        }
        
        @keyframes sending {
            0% { left: -100%; }
            100% { left: 100%; }
        }
        
        .success-message {
            color: #10B981;
            text-align: center;
            padding: 10px;
            display: none;
        }
        
        .mission-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            border-left: 4px solid #D4AF37;
        }
        
        .value-item {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }
        
        .value-icon {
            background: #D4AF37;
            color: #0d1b6b;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            font-weight: bold;
        }
    </style>
</head>
<body class="royal-blue text-white">

    <!-- Header -->
    <header class="royal-blue-light p-4 md:p-6 flex flex-col md:flex-row justify-between items-center">
        <h1 class="header-font text-3xl md:text-4xl font-bold mb-4 md:mb-0 gold-text">BELA DONA</h1>
        <div class="flex space-x-4">
            <button class="gold-bg gold-hover px-4 py-2 rounded flex items-center text-black font-semibold" onclick="openModal('cart')">
                <i class="fas fa-shopping-cart mr-2"></i>
                Carrinho (<span id="cart-count">0</span>)
            </button>
            <button class="gold-bg gold-hover px-4 py-2 rounded flex items-center text-black font-semibold" onclick="openModal('favorites')">
                <i class="fas fa-heart mr-2"></i>
                Favoritos (<span id="favorites-count">0</span>)
            </button>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="py-16 md:py-24 text-center bg-cover bg-center" style="background-image: url('https://placehold.co/1920x800/0d1b6b/D4AF37?text=Bela+Dona+Essencial');">
        <div class="container mx-auto px-4">
            <h2 class="header-font text-4xl md:text-6xl font-bold mb-6 gold-text">Bela Dona Essencial</h2>
            <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto">
                Produtos de luxo com preços acessíveis para homens e mulheres modernos
            </p>
            <button class="btn-primary gold-bg gold-hover px-8 py-4 rounded-lg text-lg font-semibold text-black" onclick="scrollToProducts()">
                Conheça nossa coleção exclusiva
            </button>
        </div>
    </section>

    <!-- Categories Section -->
    <section class="py-12 royal-blue-light">
        <div class="container mx-auto px-4">
            <h3 class="text-3xl font-bold text-center mb-12 gold-text">Nossas Categorias</h3>
            <div class="grid grid-cols-2 md:grid-cols-5 gap-4">
                <div class="gold-bg p-6 rounded-lg text-center cursor-pointer hover:bg-yellow-600 transition text-black font-semibold" onclick="filterCategory('Perfumes Femininos')">
                    <i class="fas fa-venus text-3xl mb-3"></i>
                    <p>Perfumes Femininos</p>
                </div>
                <div class="gold-bg p-6 rounded-lg text-center cursor-pointer hover:bg-yellow-600 transition text-black font-semibold" onclick="filterCategory('Perfumes Masculinos')">
                    <i class="fas fa-mars text-3xl mb-3"></i>
                    <p>Perfumes Masculinos</p>
                </div>
                <div class="gold-bg p-6 rounded-lg text-center cursor-pointer hover:bg-yellow-600 transition text-black font-semibold" onclick="filterCategory('Maquiagem')">
                    <i class="fas fa-paint-brush text-3xl mb-3"></i>
                    <p>Maquiagem</p>
                </div>
                <div class="gold-bg p-6 rounded-lg text-center cursor-pointer hover:bg-yellow-600 transition text-black font-semibold" onclick="filterCategory('Skincare')">
                    <i class="fas fa-leaf text-3xl mb-3"></i>
                    <p>Skincare</p>
                </div>
                <div class="gold-bg p-6 rounded-lg text-center cursor-pointer hover:bg-yellow-600 transition text-black font-semibold" onclick="filterCategory('Cremes')">
                    <i class="fas fa-spa text-3xl mb-3"></i>
                    <p>Cremes</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Featured Products -->
    <section class="py-16" id="products-section">
        <div class="container mx-auto px-4">
            <h3 class="text-3xl font-bold text-center mb-12 gold-text">Produtos em Destaque</h3>
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Product 1 -->
                <div class="product-card royal-blue-light rounded-xl overflow-hidden shadow-lg transition duration-300 ease-in-out cursor-pointer border-2 border-yellow-500">
                    <img src="https://placehold.co/400x500/0d1b6b/D4AF37?text=Perfume+Feminino" alt="Perfume Feminino" class="w-full h-64 object-cover">
                    <div class="p-6">
                        <span class="gold-text text-sm">Perfumes Femininos</span>
                        <h4 class="text-xl font-bold mt-2 mb-3">Essencial Feminino - 100ml</h4>
                        <div class="flex justify-between items-center">
                            <span class="text-2xl font-bold">R$ 69,99</span>
                            <button class="gold-bg gold-hover px-4 py-2 rounded text-black font-semibold" onclick="addToCart('Essencial Feminino - 100ml', 69.99)">
                                Comprar
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Product 2 -->
                <div class="product-card royal-blue-light rounded-xl overflow-hidden shadow-lg transition duration-300 ease-in-out cursor-pointer border-2 border-yellow-500">
                    <img src="https://placehold.co/400x500/0d1b6b/D4AF37?text=Perfume+Masculino" alt="Perfume Masculino" class="w-full h-64 object-cover">
                    <div class="p-6">
                        <span class="gold-text text-sm">Perfumes Masculinos</span>
                        <h4 class="text-xl font-bold mt-2 mb-3">Essencial Masculino - 100ml</h4>
                        <div class="flex justify-between items-center">
                            <span class="text-2xl font-bold">R$ 59,99</span>
                            <button class="gold-bg gold-hover px-4 py-2 rounded text-black font-semibold" onclick="addToCart('Essencial Masculino - 100ml', 59.99)">
                                Comprar
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Product 3 -->
                <div class="product-card royal-blue-light rounded-xl overflow-hidden shadow-lg transition duration-300 ease-in-out cursor-pointer border-2 border-yellow-500">
                    <img src="https://placehold.co/400x500/0d1b6b/D4AF37?text=Kit+Maquiagem" alt="Maquiagem" class="w-full h-64 object-cover">
                    <div class="p-6">
                        <span class="gold-text text-sm">Maquiagem</span>
                        <h4 class="text-xl font-bold mt-2 mb-3">Kit Maquiagem Completo</h4>
                        <div class="flex justify-between items-center">
                            <span class="text-2xl font-bold">R$ 89,99</span>
                            <button class="gold-bg gold-hover px-4 py-2 rounded text-black font-semibold" onclick="addToCart('Kit Maquiagem Completo', 89.99)">
                                Comprar
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Product 4 -->
                <div class="product-card royal-blue-light rounded-xl overflow-hidden shadow-lg transition duration-300 ease-in-out cursor-pointer border-2 border-yellow-500">
                    <img src="https://placehold.co/400x500/0d1b6b/D4AF37?text=Creme+Facial" alt="Creme Facial" class="w-full h-64 object-cover">
                    <div class="p-6">
                        <span class="gold-text text-sm">Cremes e Skincare</span>
                        <h4 class="text-xl font-bold mt-2 mb-3">Creme Facial Hidratante</h4>
                        <div class="flex justify-between items-center">
                            <span class="text-2xl font-bold">R$ 49,99</span>
                            <button class="gold-bg gold-hover px-4 py-2 rounded text-black font-semibold" onclick="addToCart('Creme Facial Hidratante', 49.99)">
                                Comprar
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Product 5 -->
                <div class="product-card royal-blue-light rounded-xl overflow-hidden shadow-lg transition duration-300 ease-in-out cursor-pointer border-2 border-yellow-500">
                    <img src="https://placehold.co/400x500/0d1b6b/D4AF37?text=Sérum+Facial" alt="Sérum Facial" class="w-full h-64 object-cover">
                    <div class="p-6">
                        <span class="gold-text text-sm">Skincare</span>
                        <h4 class="text-xl font-bold mt-2 mb-3">Sérum Facial Anti-Idade</h4>
                        <div class="flex justify-between items-center">
                            <span class="text-2xl font-bold">R$ 79,99</span>
                            <button class="gold-bg gold-hover px-4 py-2 rounded text-black font-semibold" onclick="addToCart('Sérum Facial Anti-Idade', 79.99)">
                                Comprar
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Product 6 -->
                <div class="product-card royal-blue-light rounded-xl overflow-hidden shadow-lg transition duration-300 ease-in-out cursor-pointer border-2 border-yellow-500">
                    <img src="https://placehold.co/400x500/0d1b6b/D4AF37?text=Kit+Beleza" alt="Kit Completo" class="w-full h-64 object-cover">
                    <div class="p-6">
                        <span class="gold-text text-sm">Kits Especiais</span>
                        <h4 class="text-xl font-bold mt-2 mb-3">Kit Beleza Completo</h4>
                        <div class="flex justify-between items-center">
                            <span class="text-2xl font-bold">R$ 199,99</span>
                            <button class="gold-bg gold-hover px-4 py-2 rounded text-black font-semibold" onclick="addToCart('Kit Beleza Completo', 199.99)">
                                Comprar
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="py-16 hero-gradient">
        <div class="container mx-auto px-4 text-center">
            <h3 class="header-font text-3xl md:text-4xl font-bold mb-6 gold-text">Descubra a Essência da Beleza</h3>
            <p class="text-xl mb-8 max-w-3xl mx-auto">
                Junte-se a milhares de homens e mulheres que já descobriram o luxo acessível com Bela Dona Essencial
            </p>
            <div class="flex flex-col sm:flex-row justify-center gap-4">
                <button class="btn-primary gold-bg gold-hover px-8 py-4 rounded-lg text-lg font-semibold text-black" onclick="scrollToProducts()">
                    <i class="fas fa-shopping-bag mr-2"></i>
                    Comprar Agora
                </button>
                <button class="btn-primary bg-transparent border-2 border-yellow-500 hover:bg-yellow-500 hover:text-black px-8 py-4 rounded-lg text-lg font-semibold" onclick="openModal('contact')">
                    <i class="fas fa-whatsapp mr-2"></i>
                    Fale Conosco
                </button>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 py-12">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div>
                    <h4 class="header-font text-2xl font-bold mb-4 gold-text">BELA DONA</h4>
                    <p class="text-gray-300">
                        Produtos de luxo com preços acessíveis para homens e mulheres modernos.
                    </p>
                </div>
                <div>
                    <h5 class="text-xl font-bold mb-4 gold-text">Links Rápidos</h5>
                    <ul class="space-y-2 text-gray-300">
                        <li><a href="#" class="hover:text-yellow-500" onclick="scrollToProducts(); return false;">Produtos</a></li>
                        <li><a href="#" class="hover:text-yellow-500" onclick="openModal('about'); return false;">Sobre Nós</a></li>
                        <li><a href="#" class="hover:text-yellow-500" onclick="openModal('mission'); return false;">Missão, Visão e Valores</a></li>
                        <li><a href="#" class="hover:text-yellow-500" onclick="openModal('contact'); return false;">Contato</a></li>
                        <li><a href="#" class="hover:text-yellow-500" onclick="openModal('privacy'); return false;">Política de Privacidade</a></li>
                    </ul>
                </div>
                <div>
                    <h5 class="text-xl font-bold mb-4 gold-text">Contato</h5>
                    <ul class="space-y-2 text-gray-300">
                        <li><i class="fas fa-envelope mr-2"></i> contato@beladona.com</li>
                        <li><i class="fas fa-phone mr-2"></i> (11) 99999-9999</li>
                        <li><i class="fas fa-map-marker-alt mr-2"></i> São Paulo, SP</li>
                    </ul>
                    <div class="flex space-x-4 mt-4">
                        <a href="#" class="text-gray-300 hover:text-yellow-500" onclick="openModal('social'); return false;"><i class="fab fa-instagram text-2xl"></i></a>
                        <a href="#" class="text-gray-300 hover:text-yellow-500" onclick="openModal('social'); return false;"><i class="fab fa-facebook text-2xl"></i></a>
                        <a href="#" class="text-gray-300 hover:text-yellow-500" onclick="openModal('contact'); return false;"><i class="fab fa-whatsapp text-2xl"></i></a>
                    </div>
                </div>
            </div>
            <div class="border-t border-gray-700 mt-8 pt-8 text-center text-gray-400">
                <p>&copy; Bela Dona. Todos os direitos reservados.</p>
            </div>
        </div>
    </footer>

    <!-- Cart Modal -->
    <div id="cart-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('cart')">&times;</span>
            <h2 class="text-2xl font-bold gold-text mb-6">Seu Carrinho</h2>
            <div id="cart-items">
                <p class="text-center py-8">Seu carrinho está vazio</p>
            </div>
            <div class="mt-6 pt-4 border-t border-yellow-500">
                <div class="flex justify-between text-xl font-bold mb-4">
                    <span>Total:</span>
                    <span id="cart-total">R$ 0,00</span>
                </div>
                <button class="gold-bg gold-hover w-full py-3 rounded text-black font-semibold">
                    Finalizar Compra
                </button>
            </div>
        </div>
    </div>

    <!-- Favorites Modal -->
    <div id="favorites-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('favorites')">&times;</span>
            <h2 class="text-2xl font-bold gold-text mb-6">Seus Favoritos</h2>
            <div id="favorites-items">
                <p class="text-center py-8">Você ainda não tem favoritos</p>
            </div>
        </div>
    </div>

    <!-- Contact Modal -->
    <div id="contact-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('contact')">&times;</span>
            <h2 class="text-2xl font-bold gold-text mb-6">Fale Conosco</h2>
            <div class="space-y-4">
                <div>
                    <label class="block mb-2">Nome:</label>
                    <input type="text" id="contact-name" class="w-full p-2 rounded bg-blue-900 text-white border border-yellow-500">
                </div>
                <div>
                    <label class="block mb-2">Email:</label>
                    <input type="email" id="contact-email" class="w-full p-2 rounded bg-blue-900 text-white border border-yellow-500">
                </div>
                <div>
                    <label class="block mb-2">Mensagem:</label>
                    <textarea id="contact-message" class="w-full p-2 rounded bg-blue-900 text-white border border-yellow-500 h-32"></textarea>
                </div>
                <div id="success-message" class="success-message">
                    <i class="fas fa-check-circle mr-2"></i>
                    Mensagem enviada com sucesso!
                </div>
                <button id="send-message-btn" class="gold-bg gold-hover w-full py-3 rounded text-black font-semibold" onclick="sendMessage()">
                    Enviar Mensagem
                </button>
            </div>
        </div>
    </div>

    <!-- About Modal -->
    <div id="about-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('about')">&times;</span>
            <h2 class="text-2xl font-bold gold-text mb-6">Sobre a Bela Dona</h2>
            <p class="mb-4">
                A Bela Dona é uma marca que acredita que todos merecem produtos de beleza de qualidade com preços acessíveis.
            </p>
            <p class="mb-4">
                Nossa linha Essencial traz o melhor da beleza para homens e mulheres modernos, sem comprometer a qualidade.
            </p>
            <p>
                Com mais de 30 anos de experiência no mercado, estamos comprometidos em oferecer produtos que realcem a beleza natural de cada pessoa.
            </p>
        </div>
    </div>

    <!-- Mission Modal -->
    <div id="mission-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('mission')">&times;</span>
            <h2 class="text-2xl font-bold gold-text mb-6 text-center">Missão, Visão e Valores</h2>
            
            <div class="mission-card">
                <h3 class="text-xl font-bold gold-text mb-3"><i class="fas fa-bullseye mr-2"></i> MISSÃO</h3>
                <p>
                    Oferecer produtos de higiene e beleza de alta qualidade para o público de diversas classes de São Paulo, com foco no consumidor exigente e na responsabilidade social.
                </p>
            </div>
            
            <div class="mission-card">
                <h3 class="text-xl font-bold gold-text mb-3"><i class="fas fa-eye mr-2"></i> VISÃO</h3>
                <p>
                    Ser referência nacional em qualidade e ética no setor, com forte presença nos bairros de classe baixa média e alta.
                </p>
            </div>
            
            <div class="mission-card">
                <h3 class="text-xl font-bold gold-text mb-3"><i class="fas fa-heart mr-2"></i> VALORES</h3>
                <div class="value-item">
                    <div class="value-icon">1</div>
                    <span>Valorização das pessoas</span>
                </div>
                <div class="value-item">
                    <div class="value-icon">2</div>
                    <span>Responsabilidade social</span>
                </div>
                <div class="value-item">
                    <div class="value-icon">3</div>
                    <span>Qualidade e transparência</span>
                </div>
                <div class="value-item">
                    <div class="value-icon">4</div>
                    <span>Respeito ao cliente</span>
                </div>
                <div class="value-item">
                    <div class="value-icon">5</div>
                    <span>Ética e compromisso social</span>
                </div>
                <div class="value-item">
                    <div class="value-icon">6</div>
                    <span>Valorização da origem dos produtos</span>
                </div>
            </div>
        </div>
    </div>

    <!-- Privacy Modal -->
    <div id="privacy-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('privacy')">&times;</span>
            <h2 class="text-2xl font-bold gold-text mb-6">Política de Privacidade</h2>
            <p class="mb-4">
                Sua privacidade é importante para nós. Esta Política de Privacidade explica como coletamos, usamos e protegemos suas informações pessoais.
            </p>
            <p class="mb-4">
                Ao usar nosso site, você concorda com a coleta e uso de informações de acordo com esta política.
            </p>
            <p>
                Para mais informações, entre em contato conosco através dos canais disponibilizados.
            </p>
        </div>
    </div>

    <!-- Social Modal -->
    <div id="social-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('social')">&times;</span>
            <h2 class="text-2xl font-bold gold-text mb-6">Siga-nos nas Redes Sociais</h2>
            <div class="flex justify-center space-x-8 py-8">
                <a href="#" class="text-4xl text-yellow-500 hover:text-yellow-400"><i class="fab fa-instagram"></i></a>
                <a href="#" class="text-4xl text-yellow-500 hover:text-yellow-400"><i class="fab fa-facebook"></i></a>
                <a href="#" class="text-4xl text-yellow-500 hover:text-yellow-400"><i class="fab fa-whatsapp"></i></a>
            </div>
        </div>
    </div>

    <script>
        // Carrinho e favoritos
        let cart = [];
        let favorites = [];
        let cartCount = 0;
        let favoritesCount = 0;

        // Função para adicionar ao carrinho
        function addToCart(productName, price) {
            cart.push({ name: productName, price: price });
            cartCount++;
            document.getElementById('cart-count').textContent = cartCount;
            updateCartDisplay();
            openModal('cart');
        }

        // Função para atualizar a exibição do carrinho
        function updateCartDisplay() {
            const cartItems = document.getElementById('cart-items');
            const cartTotal = document.getElementById('cart-total');
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<p class="text-center py-8">Seu carrinho está vazio</p>';
                cartTotal.textContent = 'R$ 0,00';
                return;
            }
            
            let itemsHTML = '';
            let total = 0;
            
            cart.forEach((item, index) => {
                itemsHTML += `
                    <div class="cart-item flex justify-between items-center">
                        <div>
                            <h4 class="font-semibold">${item.name}</h4>
                            <p class="text-yellow-500">R$ ${item.price.toFixed(2)}</p>
                        </div>
                        <button onclick="removeFromCart(${index})" class="text-red-500 hover:text-red-300">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                `;
                total += item.price;
            });
            
            cartItems.innerHTML = itemsHTML;
            cartTotal.textContent = `R$ ${total.toFixed(2)}`;
        }

        // Função para remover do carrinho
        function removeFromCart(index) {
            cart.splice(index, 1);
            cartCount--;
            document.getElementById('cart-count').textContent = cartCount;
            updateCartDisplay();
        }

        // Função para abrir modais
        function openModal(modalId) {
            document.getElementById(modalId + '-modal').style.display = 'block';
        }

        // Função para fechar modais
        function closeModal(modalId) {
            document.getElementById(modalId + '-modal').style.display = 'none';
        }

        // Função para filtrar categorias
        function filterCategory(category) {
            alert(`Filtrando produtos da categoria: ${category}`);
            // Aqui você poderia implementar a lógica real de filtragem
        }

        // Função para rolar até os produtos
        function scrollToProducts() {
            document.getElementById('products-section').scrollIntoView({ behavior: 'smooth' });
        }

        // Função para enviar mensagem com animação
        function sendMessage() {
            const name = document.getElementById('contact-name').value;
            const email = document.getElementById('contact-email').value;
            const message = document.getElementById('contact-message').value;
            
            // Verificar se todos os campos estão preenchidos
            if (!name || !email || !message) {
                alert('Por favor, preencha todos os campos.');
                return;
            }
            
            const button = document.getElementById('send-message-btn');
            const successMessage = document.getElementById('success-message');
            
            // Adicionar animação de envio
            button.classList.add('sending-animation');
            button.disabled = true;
            button.textContent = 'Enviando...';
            
            // Simular envio (em um site real, aqui você faria a chamada para o servidor)
            setTimeout(() => {
                button.classList.remove('sending-animation');
                button.disabled = false;
                button.textContent = 'Enviar Mensagem';
                
                // Mostrar mensagem de sucesso
                successMessage.style.display = 'block';
                
                // Limpar campos
                document.getElementById('contact-name').value = '';
                document.getElementById('contact-email').value = '';
                document.getElementById('contact-message').value = '';
                
                // Esconder mensagem de sucesso após 3 segundos
                setTimeout(() => {
                    successMessage.style.display = 'none';
                }, 3000);
            }, 2000);
        }

        // Fechar modais ao clicar fora
        window.onclick = function(event) {
            const modals = document.querySelectorAll('.modal');
            modals.forEach(modal => {
                if (event.target == modal) {
                    modal.style.display = 'none';
                }
            });
        }

        // Fechar modais com ESC
        document.addEventListener('keydown', function(event) {
            if (event.key === 'Escape') {
                const modals = document.querySelectorAll('.modal');
                modals.forEach(modal => {
                    modal.style.display = 'none';
                });
            }
        });
    </script>
</body>
</html>
