<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Massa Nostra - Monte Seu Macarrão</title>
<script src="https://cdn.tailwindcss.com"></script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
body {
    font-family: 'Inter', sans-serif;
    background-color: #f4f7f9;
}
.section-title {
    @apply text-xl font-bold border-b-2 pb-2 mb-4 text-red-700 border-red-200;
}
.input-style {
    @apply w-full p-3 border border-gray-300 rounded-lg focus:ring-red-500 focus:border-red-500 transition duration-150;
}
/* Estilo para item desabilitado visualmente */
.acomp-option input:disabled + span,
.input-style:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    background-color: #f3f4f6;
    text-decoration: line-through;
}
/* Estilo para fieldset desabilitado (opcional, para reforçar) */
fieldset:disabled {
    pointer-events: none; /* Impede cliques */
    opacity: 0.7; /* Suaviza a cor */
}

/* Adicionando sombra ao texto para que fique legível sobre a bandeira */
.flag-text-shadow {
    text-shadow: 1px 1px 4px rgba(0,0,0,0.9);
}
/* Cores vibrantes da bandeira italiana aplicadas ao fundo do cabeçalho */
.italian-flag-gradient {
    /* Cores: Verde (#008C45), Branco (#FFFFFF), Vermelho (#CD212A) */
    background: linear-gradient(to right, #008C45 33.3%, #FFFFFF 33.3%, #FFFFFF 66.6%, #CD212A 66.6%);
}
/* Estilo para o input de quantidade de bebida */
.drink-input {
    @apply w-16 p-2 text-center border border-gray-300 rounded-lg;
}
/* Estilo para a nova seção de Queijo */
.cheese-option {
    @apply p-3 bg-red-100 border border-red-300 rounded-lg shadow-inner;
}
/* Estilo para o botão de checkout desativado */
#checkout-btn.closed-state {
    @apply bg-gray-400 cursor-not-allowed transform-none shadow-none;
}
</style>
</head>
<body class="min-h-screen p-4 flex justify-center">

<div id="app" class="w-full max-w-xl bg-white shadow-2xl rounded-xl space-y-6 md:p-0">
    <header class="text-center relative italian-flag-gradient rounded-t-xl py-6 shadow-2xl">
        <img src="https://i.postimg.cc/prk8G3cV/Imagem-do-Whats-App-de-2025-10-01-s-01-45-52-b1184834.jpg" 
             alt="Logo Massa Nostra" 
             class="w-40 h-40 object-cover mx-auto rounded-full mb-3 shadow-2xl border-4 border-white z-10 relative">
        <div class="px-2">
            <h1 class="text-4xl font-extrabold text-white sm:text-5xl flag-text-shadow leading-tight">MASSA NOSTRA POTY</h1>
            <p class="text-base text-white font-medium mt-1 flag-text-shadow">@massanostra_poty | Monte sua massa!</p>
        </div>
    </header>

    <div class="p-6 space-y-6 md:p-8 pt-0">
        
        <section id="custom-order-section" class="space-y-6 p-4 border border-red-100 rounded-xl bg-red-50">
            <h2 class="section-title text-red-800">🍝 Monte Sua Massa</h2>

            <div class="space-y-2">
                <label class="block font-semibold text-gray-700">📏 1. Escolha o Tamanho</label>
                <div id="size-options" class="flex space-x-4">
                    </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="space-y-2">
                    <label class="block font-semibold text-gray-700">🍝 2. Escolha a Massa (Obrigatório)</label>
                    <div id="massa-options" class="space-y-1"></div>
                </div>

                <div class="space-y-2">
                    <label class="block font-semibold text-gray-700">🥣 3. Escolha o Molho (Obrigatório)</label>
                    <div id="molho-options" class="space-y-1"></div>
                </div>
            </div>

            <div class="space-y-2">
                <label class="block font-semibold text-gray-700">🥓 4. Acompanhamentos Comuns</label>
                
                <div id="acomp-premium-options" class="mb-3 p-3 bg-yellow-50 rounded-lg border border-yellow-200">
                    </div>
                
                <p id="acomp-counter" class="text-sm font-medium text-red-600">Selecionados: 0/6 (Tamanho P)</p>
                
                <div id="acomp-options" class="grid grid-cols-2 sm:grid-cols-3 gap-2"></div>
            </div>

            <div class="space-y-2">
                <label class="block font-bold text-gray-800 border-t pt-4">🧀 5. Escolha o Queijo (Obrigatório)</label>
                <div id="queijo-options" class="flex space-x-4 cheese-option">
                    </div>
            </div>


            <div class="space-y-2">
                <label for="obs" class="block font-semibold text-gray-700 border-t pt-4">6. Observações (Ex: Sem cebolinha)</label>
                <input type="text" id="obs" class="input-style" placeholder="Digite aqui...">
                <p class="text-2xl font-extrabold text-green-700 mt-4 text-right">
                    Preço do Item: <span id="item-price-display">R$ 24,90</span>
                </p>
            </div>
            
            <button id="add-to-cart-btn" onclick="addToCart()" 
                class="w-full bg-green-600 hover:bg-green-700 text-white font-bold py-3 rounded-lg shadow-md transition duration-300 transform hover:scale-[1.01] active:scale-[0.98]">
                ADICIONAR PRATO AO CARRINHO E MONTAR OUTRO
            </button>
        </section>
        
        <section id="fixed-plates-section" class="space-y-4 p-4 border border-green-100 rounded-xl bg-green-50">
            <h2 class="section-title text-green-800 border-green-200">🍽️ Pratos da Casa</h2>
            <div id="pratos-fixos-options" class="space-y-3"></div>
        </section>
        <section id="drinks-section" class="space-y-4 p-4 border border-blue-100 rounded-xl bg-blue-50">
            <fieldset id="bebidas-fieldset" disabled> <h2 class="section-title text-blue-800 border-blue-200">🥤 Adicionar Bebidas Geladas (R$ 6,00/cada)</h2>
                <div id="bebidas-options" class="space-y-3">
                    </div>
            </fieldset>
            <p id="bebidas-count" class="text-sm font-medium text-gray-600 pt-2 border-t border-blue-200">
                Total de Unidades: <span id="bebidas-unidades-display">0</span> | Total: <span id="bebidas-total-display">R$ 0,00</span>
            </p>
        </section>
        

        <section class="space-y-4 p-4 border border-gray-200 rounded-xl bg-gray-50">
            <h2 class="section-title text-gray-700 border-gray-200">🛒 Seu Pedido (<span id="cart-count">0</span> Pratos)</h2>
            <ul id="cart-list" class="space-y-3">
                <li id="empty-cart-message" class="text-gray-500 italic text-center">Nenhum item no carrinho.</li>
            </ul>
            <p class="text-3xl font-extrabold text-red-700 pt-3 border-t border-gray-300 text-right">
                SUBTOTAL: <span id="subtotal-display">R$ 0,00</span>
            </p>
        </section>

        <section id="checkout-section" class="space-y-6" style="display: none;">
            <h2 class="section-title">Dados de Entrega e Pagamento</h2>

            <div class="space-y-3">
                <label class="block font-semibold text-gray-700">Seus Dados:</label>
                <input type="text" id="nome" class="input-style" placeholder="Nome Completo *" required>
                <input type="tel" id="telefone" class="input-style" placeholder="Telefone (WhatsApp) *" required>
                <input type="text" id="endereco" class="input-style" placeholder="Endereço (Rua, Número, Bairro) *" required>
                <input type="text" id="referencia" class="input-style" placeholder="Ponto de Referência (Ex: Casa verde, ao lado da praça)">
            </div>

            <div class="space-y-2">
                <label class="block font-semibold text-gray-700">Taxa de Entrega</label>
                <div id="delivery-fee-options" class="flex flex-col space-y-2">
                    <label class="flex items-center p-2 bg-white rounded-lg shadow-sm cursor-pointer">
                        <input type="radio" name="deliveryFee" value="2.00" class="form-radio text-red-600" checked>
                        <span class="ml-2">Entrega na Cidade (R$ 2,00)</span>
                    </label>
                    <label class="flex items-center p-2 bg-white rounded-lg shadow-sm cursor-pointer">
                        <input type="radio" name="deliveryFee" value="5.00" class="form-radio text-red-600">
                        <span class="ml-2">Entrega até 5km (R$ 5,00)</span>
                    </label>
                </div>
            </div>
            
            <div class="space-y-2">
                <label class="block font-semibold text-gray-700">Forma de Pagamento</label>
                <select id="payment-method" class="input-style" onchange="toggleTrocoField()"> <option value="Pix">Pix (Informar na mensagem)</option>
                    <option value="Dinheiro">Dinheiro (Precisa de troco?)</option>
                    <option value="Cartao-Debito">Cartão de Débito</option>
                    <option value="Cartao-Credito">Cartão de Crédito</option>
                </select>
            </div>
            
            <div id="troco-input-container" class="space-y-2" style="display: none;">
                <label for="troco" class="block font-semibold text-gray-700">Precisa de Troco?</label>
                <input type="text" id="troco" class="input-style" placeholder="Troco para (Ex: R$ 50,00)">
                <p class="text-sm text-gray-500">Deixe em branco se for pagar o valor exato.</p>
            </div>


            <div class="mt-6 p-4 bg-red-100 rounded-lg shadow-inner">
                <p class="text-lg font-bold text-red-800">Subtotal: <span id="final-subtotal">R$ 0,00</span></p>
                <p class="text-lg font-bold text-red-800">Taxa: <span id="final-fee">R$ 2,00</span></p>
                <p class="text-4xl font-extrabold text-red-900 mt-2">TOTAL FINAL: <span id="final-total">R$ 0,00</span></p>
            </div>

            <button id="checkout-btn" onclick="generateWhatsAppLink()" 
                class="w-full flex items-center justify-center bg-green-500 hover:bg-green-600 text-white font-extrabold py-4 rounded-lg shadow-xl transition duration-300 transform hover:scale-[1.01] active:scale-[0.98]">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor" class="mr-2">
                    <path d="M12.001 2c-5.522 0-9.999 4.477-9.999 9.999 0 3.864 2.193 7.224 5.434 8.937l-.547 1.884c-.053.183.018.384.183.454.16.07.362.003.415-.177l.568-1.859c.772.196 1.583.298 2.404.298 5.522 0 9.999-4.477 9.999-9.999s-4.477-9.999-9.999-9.999zm4.646 12.339l-.025.048c-.627 1.127-1.428 1.176-2.923 1.025-1.579-.164-3.56-1.077-5.118-2.635-1.558-1.558-2.471-3.539-2.635-5.118-.151-1.495-.102-2.296 1.025-2.923l.048-.025.109-.052c.245-.118.528-.108.763.027l1.559.866c.216.12.339.362.31.597l-.078.618c-.035.267-.168.513-.377.674l-.234.186c-.198.158-.178.431.042.616l2.365 2.365c.184.22.457.24.616.042l.186-.234c.161-.209.407-.342.674-.377l.618-.078c.235-.029.477.094.597.31l.866 1.559c.135.235.145.518.027.763l-.052.109z"/>
                </svg>
                ENVIAR PEDIDO VIA WHATSAPP
            </button>
        </section>
    </div>

</div>

<script>
    // --- DADOS DO CARDÁPIO (FONTE ÚNICA DE VERDADE) ---
    const MENU = {
        massas: ["Penne", "Spaguetti", "Parafuso", "Fetutini"],
        molhos: ["Bolonhesa", "Branco", "Rosé", "Sugo"],
        acompanhamentos: [
            "Alho Frito", "Azeitona", "Bacon", "Brócolis",
            "Calabresa", "Catupiry Original", "Cebola", "Cheddar", "Champignon",
            "Ervilha", "Frango", "Milho", "Palmito", "Pimentão",
            "Presunto", "Salsicha", "Tomate Seco",
            "Uva Passa"
        ],
        // Opções de Queijo
        queijos: ["Parmesão Ralado", "Muçarela Ralada"],
        acompanhamentosPremium: {
            'Camarão': 10.00
        },
        tamanhos: [
            { id: 'P', nome: 'Pequeno', preco: 24.90, limite: 6 },
            { id: 'G', nome: 'Grande', preco: 32.90, limite: 8 }
        ],
        // ✨ NOVO PRATO FIXO ADICIONADO ✨
        pratosFixos: [
            {
                nome: "Lasanha à Bolonhesa",
                descricao: "Deliciosas camadas de massa fresca, recheadas com um molho bolonhesa artesanal preparado com carne moída, presunto, muçarela e temperos selecionados.",
                preco: 26.90
            }
        ],
        // SOBREMESA FOI REMOVIDA DESTE OBJETO
        bebidas: {
            opcoes: ["Coca-Cola", "Coca-Cola Zero", "Fanta", "Guaraná Antárctica", "Sprite", "Sprite Zero"],
            precoUnitario: 6.00,
            volume: "350ml"
        },
        // 👇 TROQUE AQUI PELO SEU NÚMERO REAL 👇
        whatsappNumber: "5517997381858",
        pixData: {
            name: "SUÉLEM CRISTINA MAESTRE MAZZUCCA",
            key: "41756000867 (CPF)"
        }
    };

    // --- ESTADO GLOBAL ---
    let cart = []; // Para pratos customizáveis
    let pratosFixosQuantities = {}; // Para pratos fixos (Lasanha)
    let bebidasQuantities = {}; // ✨ NOVO: Para quantidades de bebidas
    let currentItemPrice = MENU.tamanhos[0].preco;
    let premiumPrice = 0;
    let selectedAcompanhamentos = 0;
    let maxAcompanhamentos = MENU.tamanhos[0].limite;

    // --- REFERÊNCIAS DOM ---
    const sizeOptionsDiv = document.getElementById('size-options');
    const massaOptionsDiv = document.getElementById('massa-options');
    const molhoOptionsDiv = document.getElementById('molho-options');
    const acompOptionsDiv = document.getElementById('acomp-options');
    const queijoOptionsDiv = document.getElementById('queijo-options');
    const pratosFixosOptionsDiv = document.getElementById('pratos-fixos-options'); 
    const acompCounter = document.getElementById('acomp-counter');
    const itemPriceDisplay = document.getElementById('item-price-display');
    const cartList = document.getElementById('cart-list');
    const checkoutSection = document.getElementById('checkout-section');
    const deliveryFeeRadios = document.querySelectorAll('input[name="deliveryFee"]');
    const addToCartBtn = document.getElementById('add-to-cart-btn');
    const checkoutBtn = document.getElementById('checkout-btn');
    const bebidasOptionsDiv = document.getElementById('bebidas-options');
    const bebidasTotalDisplay = document.getElementById('bebidas-total-display');
    const bebidasUnidadesDisplay = document.getElementById('bebidas-unidades-display');
    
    const bebidasFieldset = document.getElementById('bebidas-fieldset');
    
    const trocoInputContainer = document.getElementById('troco-input-container');
    const paymentMethodSelect = document.getElementById('payment-method');

    // --- NOVO: LÓGICA DE VERIFICAÇÃO DE HORÁRIO ---

    /**
     * Verifica se o estabelecimento está fechado.
     * FECHADO: Domingo (0) depois das 14h, até Quarta (3) às 12h.
     */
    function isClosed() {
        const now = new Date();
        const day = now.getDay(); // 0 = Domingo, 1 = Segunda, ..., 6 = Sábado
        const hour = now.getHours();

        // 1. Está fechado a qualquer hora na Segunda (1) ou Terça (2)
        if (day >= 1 && day <= 2) {
            return true;
        }

        // 2. Está fechado no Domingo (0) após as 14h
        if (day === 0 && hour >= 14) {
            return true;
        }

        // 3. Está fechado na Quarta (3) antes das 12h
        if (day === 3 && hour < 12) {
            return true;
        }

        return false;
    }

    /**
     * Aplica o estado de "fechado" ao botão do WhatsApp (checkout).
     */
    function applyClosedState() {
        if (isClosed()) {
            checkoutBtn.disabled = true;
            // Remove classes de ativo e adiciona as de inativo
            checkoutBtn.classList.remove('bg-green-500', 'hover:bg-green-600', 'transform', 'hover:scale-[1.01]', 'active:scale-[0.98]');
            checkoutBtn.classList.add('closed-state');
            checkoutBtn.textContent = '❌ FECHADO - Pedidos de Quarta (12h) a Domingo (14h)';
            // Desativa o botão do carrinho se estiver no modo checkout
            addToCartBtn.disabled = true;
            addToCartBtn.textContent = 'ESTABELECIMENTO FECHADO';
        } else {
            // Estado de Aberto
            checkoutBtn.disabled = false;
            checkoutBtn.classList.remove('closed-state');
            checkoutBtn.classList.add('bg-green-500', 'hover:bg-green-600', 'transform', 'hover:scale-[1.01]', 'active:scale-[0.98]');
            checkoutBtn.textContent = 'ENVIAR PEDIDO VIA WHATSAPP';
            // Restaura o botão do carrinho
            addToCartBtn.disabled = false;
            addToCartBtn.textContent = 'ADICIONAR PRATO AO CARRINHO E MONTAR OUTRO';
        }
    }

    // --- FUNÇÕES DE LÓGICA E RENDERIZAÇÃO INICIAL ---

    function renderOptions(container, name, options, type = 'radio', checkedValue = null, isSizeOption = false) {
        container.innerHTML = options.map((option, index) => {
            const value = isSizeOption ? option.id : option;
            let labelText = isSizeOption 
                ? `${option.id} (${option.nome}) (R$ ${option.preco.toFixed(2).replace('.', ',')}, Máx. ${option.limite} Acomp.)`
                : option;
            
            const isQueijoOption = name === 'queijo';
            const isChecked = checkedValue ? (value === checkedValue) : (index === 0 && (!isSizeOption || isQueijoOption));
            
            return `
                <label class="flex items-center p-3 bg-white rounded-lg shadow-md hover:bg-red-50 transition duration-150 flex-1 cursor-pointer acomp-option">
                    <input type="${type}" name="${name}" value="${value}" 
                        class="${type === 'radio' ? 'form-radio text-red-600' : 'form-checkbox text-red-600'}"
                        ${isChecked ? 'checked' : ''}>
                    <span class="ml-2 font-medium">${labelText}</span>
                </label>
            `;
        }).join('');
    }
    
    function renderAcompanhamentos() {
        MENU.acompanhamentos.sort((a, b) => a.localeCompare(b));
        renderOptions(acompOptionsDiv, 'acomp', MENU.acompanhamentos, 'checkbox');
        
        const premiumOptionsDiv = document.getElementById('acomp-premium-options');
        premiumOptionsDiv.innerHTML = Object.entries(MENU.acompanhamentosPremium).map(([nome, preco]) => `
            <label class="flex items-center cursor-pointer font-bold text-gray-800">
                <input type="checkbox" name="acompPremium" value="${nome}" class="form-checkbox text-red-600">
                <span class="ml-2">${nome} Premium (+ R$ ${preco.toFixed(2).replace('.', ',')})</span>
            </label>
        `).join('');
    }

    function renderQueijo() {
        renderOptions(queijoOptionsDiv, 'queijo', MENU.queijos, 'radio', MENU.queijos[0]);
    }
    
    function renderBebidas() {
        bebidasOptionsDiv.innerHTML = MENU.bebidas.opcoes.map(bebida => {
            const id = `qty-bebida-${bebida.toLowerCase().replace(/\s/g, '-')}`;
            const qty = bebidasQuantities[bebida] || 0; 
            
            return `
                <div class="flex justify-between items-center p-3 bg-white rounded-lg shadow-md">
                    <label class="font-medium text-gray-700 flex-1">
                        ${bebida} ${MENU.bebidas.volume} (R$ ${MENU.bebidas.precoUnitario.toFixed(2).replace('.', ',')})
                    </label>
                    <div class="flex items-center space-x-2">
                        <button onclick="changeDrinkQuantity('${bebida}', -1)" class="bg-red-500 hover:bg-red-600 text-white font-bold py-1 px-3 rounded-lg transition duration-150 active:scale-95 text-xl">-</button>
                        <span id="${id}" class="font-bold text-lg w-8 text-center">${qty}</span>
                        <button onclick="changeDrinkQuantity('${bebida}', 1)" class="bg-green-500 hover:bg-green-600 text-white font-bold py-1 px-3 rounded-lg transition duration-150 active:scale-95 text-xl">+</button>
                    </div>
                </div>
            `;
        }).join('');
    }
    
    // ✨ NOVA FUNÇÃO: GERENCIAR QUANTIDADE DE BEBIDA
    function changeDrinkQuantity(name, change) {
        bebidasQuantities[name] = bebidasQuantities[name] || 0;

        let newQty = bebidasQuantities[name] + change;
        if (newQty < 0) newQty = 0;
        
        bebidasQuantities[name] = newQty;
        
        const id = `qty-bebida-${name.toLowerCase().replace(/\s/g, '-')}`;
        document.getElementById(id).textContent = newQty;

        updateBebidasTotal();
        renderCart();
    }


    // ✨ FUNÇÃO: RENDERIZAR PRATOS FIXOS (LASANHA)
    function renderPratosFixos() {
        pratosFixosOptionsDiv.innerHTML = MENU.pratosFixos.map(prato => {
            const id = `fixed-${prato.nome.toLowerCase().replace(/\s/g, '-')}`;
            const qty = pratosFixosQuantities[prato.nome] || 0;
            return `
                <div class="p-3 bg-white rounded-lg shadow-md border border-green-200">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-green-700">${prato.nome}</h3>
                        <p class="font-extrabold text-lg text-red-600">R$ ${prato.preco.toFixed(2).replace('.', ',')}</p>
                    </div>
                    <p class="text-sm text-gray-600 mb-2">${prato.descricao}</p>
                    <div class="flex items-center justify-end space-x-2 border-t pt-2 mt-2">
                        <button onclick="changeFixedItemQuantity('${prato.nome}', -1)" class="bg-red-500 hover:bg-red-600 text-white font-bold py-1 px-3 rounded-lg transition duration-150 active:scale-95 text-xl">-</button>
                        <span id="${id}-qty" class="font-bold text-lg w-8 text-center">${qty}</span>
                        <button onclick="changeFixedItemQuantity('${prato.nome}', 1)" class="bg-green-500 hover:bg-green-600 text-white font-bold py-1 px-3 rounded-lg transition duration-150 active:scale-95 text-xl">+</button>
                    </div>
                </div>
            `;
        }).join('');
    }

    // ✨ FUNÇÃO: ALTERAR QUANTIDADE DO PRATO FIXO
    function changeFixedItemQuantity(name, change) {
        pratosFixosQuantities[name] = pratosFixosQuantities[name] || 0;

        let newQty = pratosFixosQuantities[name] + change;
        if (newQty < 0) newQty = 0;
        
        pratosFixosQuantities[name] = newQty;
        
        const id = `fixed-${name.toLowerCase().replace(/\s/g, '-')}-qty`;
        document.getElementById(id).textContent = newQty;

        renderCart();
    }
    // FIM NOVAS FUNÇÕES


    function setupUI() {
        // Renderiza as seções do Prato
        renderOptions(sizeOptionsDiv, 'size', MENU.tamanhos, 'radio', 'P', true);
        renderOptions(massaOptionsDiv, 'massa', MENU.massas, 'radio');
        renderOptions(molhoOptionsDiv, 'molho', MENU.molhos, 'radio');
        renderAcompanhamentos();
        renderQueijo(); 

        // Renderiza os pratos fixos (Lasanha)
        renderPratosFixos();
        
        // Renderiza as bebidas com botões +/-
        renderBebidas();

        // Adiciona Listeners
        sizeOptionsDiv.addEventListener('change', updateLimitAndPrice);
        acompOptionsDiv.addEventListener('change', updateAcompCount);
        document.querySelector('input[name="acompPremium"]').addEventListener('change', updateItemPrice);
        deliveryFeeRadios.forEach(radio => radio.addEventListener('change', updateFinalSummary));

        // Inicializa
        updateLimitAndPrice();
        updateBebidasTotal();
        renderCart(); 
        
        // Inicializa a regra de bloqueio (se não houver prato, bloqueia APENAS bebidas)
        toggleDrinksAvailability(); 
        
        // NOVO: Aplica o estado de fechamento ao carregar
        applyClosedState();
    }
    
    // Função para alternar visibilidade do campo de troco
    function toggleTrocoField() {
        const isMoney = paymentMethodSelect.value === 'Dinheiro';
        trocoInputContainer.style.display = isMoney ? 'block' : 'none';
        // Limpa o campo se ele for escondido
        if (!isMoney) {
            document.getElementById('troco').value = '';
        }
    }

    // Função para habilitar/desabilitar SOMENTE Bebidas
    function toggleDrinksAvailability() {
        // Apenas itens no carrinho (customizados ou fixos) liberam os adicionais
        const hasItems = cart.length > 0 || Object.values(pratosFixosQuantities).some(qty => qty > 0);
        
        bebidasFieldset.disabled = !hasItems; 

        // Se desabilitou e o usuário tinha algo selecionado, zera a quantidade
        if (!hasItems) {
            // Zera Bebidas
            bebidasQuantities = {};
            renderBebidas(); // Atualiza o DOM para mostrar 0
            updateBebidasTotal();
        }
    }


    // Lógicas de atualização 
    function updateLimitAndPrice() {
        const selectedSizeId = document.querySelector('input[name="size"]:checked').value;
        const selectedSize = MENU.tamanhos.find(t => t.id === selectedSizeId);
        
        if (selectedSize) {
            maxAcompanhamentos = selectedSize.limite;
        }
        
        updateItemPrice();
        updateAcompCount();
    }

    function updateItemPrice() {
        const selectedSizeId = document.querySelector('input[name="size"]:checked').value;
        const basePrice = MENU.tamanhos.find(t => t.id === selectedSizeId)?.preco || 0;
        
        const camarãoCheckbox = document.querySelector('input[name="acompPremium"][value="Camarão"]');
        premiumPrice = camarãoCheckbox && camarãoCheckbox.checked ? MENU.acompanhamentosPremium['Camarão'] : 0;
        
        currentItemPrice = basePrice + premiumPrice;
        itemPriceDisplay.textContent = `R$ ${currentItemPrice.toFixed(2).replace('.', ',')}`;
    }

    function updateAcompCount() {
        const checkboxes = document.querySelectorAll('input[name="acomp"]:checked');
        selectedAcompanhamentos = checkboxes.length;
        const selectedSizeId = document.querySelector('input[name="size"]:checked').value;

        acompCounter.textContent = `Selecionados: ${selectedAcompanhamentos}/${maxAcompanhamentos} (Tamanho ${selectedSizeId})`;
        acompCounter.classList.toggle('font-bold', selectedAcompanhamentos === maxAcompanhamentos);

        document.querySelectorAll('input[name="acomp"]').forEach(cb => {
            if (selectedAcompanhamentos >= maxAcompanhamentos && !cb.checked) {
                cb.disabled = true;
                cb.closest('label').classList.add('opacity-50');
            } else {
                cb.disabled = false;
                cb.closest('label').classList.remove('opacity-50');
            }
        });
    }

    function updateBebidasTotal() {
        let totalUnidades = 0;
        let totalBebidas = 0;
        
        // Calcula o total e o número de unidades a partir do objeto bebidasQuantities
        Object.entries(bebidasQuantities).forEach(([nome, qtd]) => {
            if (qtd > 0) {
                totalUnidades += qtd;
                totalBebidas += qtd * MENU.bebidas.precoUnitario;
            }
        });

        bebidasUnidadesDisplay.textContent = totalUnidades;
        bebidasTotalDisplay.textContent = `R$ ${totalBebidas.toFixed(2).replace('.', ',')}`;
        
        updateFinalSummary(); 
    }
    
    function getFormData() {
        const sizeRadio = document.querySelector('input[name="size"]:checked');
        const massaRadio = document.querySelector('input[name="massa"]:checked');
        const molhoRadio = document.querySelector('input[name="molho"]:checked');
        const queijoRadio = document.querySelector('input[name="queijo"]:checked'); 
        const acompCheckboxes = document.querySelectorAll('input[name="acomp"]:checked');
        const camarãoCheckbox = document.querySelector('input[name="acompPremium"][value="Camarão"]');
        
        if (!sizeRadio || !massaRadio || !molhoRadio || !queijoRadio) {
            alert('Por favor, selecione o Tamanho, a Massa, o Molho e o Queijo.');
            return null;
        }

        const camarão = camarãoCheckbox && camarãoCheckbox.checked ? {
            name: camarãoCheckbox.value,
            cost: premiumPrice
        } : null;
        
        const customItem = {
            size: sizeRadio.value,
            price: currentItemPrice,
            massa: massaRadio.value,
            molho: molhoRadio.value,
            queijo: queijoRadio.value, 
            acompanhamentos: Array.from(acompCheckboxes).map(cb => cb.value),
            premium: camarão,
            obs: document.getElementById('obs').value.trim()
        };

        return customItem;
    }

    function addToCart() {
        // Bloqueia o botão do carrinho se a loja estiver fechada
        if (isClosed()) {
            alert('🚨 O estabelecimento está FECHADO. Não é possível adicionar itens ao carrinho neste momento. Pedidos de Quarta-feira (12:00) até Domingo (14:00).');
            return;
        }
        
        addToCartBtn.disabled = true; 
        addToCartBtn.textContent = 'Adicionando...';
        
        const item = getFormData();
        if (item) {
            cart.push(item);
            alert('Prato adicionado ao carrinho! Você pode montar outro.');
            renderCart();
            resetForm();
            
            toggleDrinksAvailability(); 

            document.getElementById('fixed-plates-section').scrollIntoView({ behavior: 'smooth', block: 'start' });
        }

        setTimeout(() => {
            // Verifica o estado de fechamento antes de reabilitar
            if (!isClosed()) {
                 addToCartBtn.disabled = false;
                 addToCartBtn.textContent = 'ADICIONAR PRATO AO CARRINHO E MONTAR OUTRO';
            }
        } , 300); 
    }
    
    function resetForm() {
        // Reset do Prato
        document.querySelectorAll('input[name="massa"]').forEach(r => r.checked = false);
        document.querySelectorAll('input[name="molho"]').forEach(r => r.checked = false);
        document.querySelectorAll('input[name="queijo"]').forEach((r, index) => {
             r.checked = index === 0; 
        });
        document.querySelectorAll('input[name="acomp"]').forEach(cb => cb.checked = false);
        document.querySelectorAll('input[name="acompPremium"]').forEach(cb => cb.checked = false); 
        document.getElementById('obs').value = '';

        document.querySelector('input[name="size"][value="P"]').checked = true;
        updateLimitAndPrice(); 
    }

    // --- FUNÇÕES DE CARRINHO E TOTALIZAÇÃO ---

    function renderCart() {
        cartList.innerHTML = '';
        let subtotalPratos = 0;
        let totalUnidadesFixos = 0;
        let totalUnidadesBebidas = 0;
        
        // Verifica se há itens customizados, fixos ou bebidas
        const hasCustomItems = cart.length > 0;
        const hasFixedItems = Object.values(pratosFixosQuantities).some(qty => qty > 0);
        const hasDrinks = Object.values(bebidasQuantities).some(qty => qty > 0);
        const hasItems = hasCustomItems || hasFixedItems || hasDrinks;


        if (!hasItems) {
            cartList.innerHTML = `<li id="empty-cart-message" class="text-gray-500 italic text-center">Nenhum item no carrinho.</li>`;
            document.getElementById('cart-count').textContent = '0';
            checkoutSection.style.display = 'none';
        } else {
            document.getElementById('cart-count').textContent = cart.length + Object.values(pratosFixosQuantities).reduce((sum, qty) => sum + qty, 0); 
            checkoutSection.style.display = 'block';

            // 1. Renderiza os Pratos Customizados
            cart.forEach((item, index) => {
                subtotalPratos += item.price;
                const li = document.createElement('li');
                li.className = 'p-3 border border-gray-100 bg-white rounded-lg shadow-sm space-y-1';
                
                const camarãoText = item.premium ? `<p class="text-sm font-semibold text-green-700">Premium: ${item.premium.name} (+ R$ ${item.premium.cost.toFixed(2).replace('.', ',')})</p>` : '';
                const acompList = item.acompanhamentos.length > 0 ? item.acompanhamentos.join(', ') : 'Nenhum';
                
                li.innerHTML = `
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-800">#${index + 1} - Massa ${item.size} (${item.massa})</h3>
                        <button onclick="removeItem(${index})" class="text-red-500 hover:text-red-700 text-sm font-semibold transition duration-150">
                            Remover
                        </button>
                    </div>
                    <p class="text-sm text-gray-600">Molho: ${item.molho}</p>
                    <p class="text-sm font-bold text-red-500">Queijo: ${item.queijo}</p>
                    <p class="text-sm text-gray-600">Acompanhamentos Comuns: ${acompList}</p>
                    ${camarãoText}
                    ${item.obs ? `<p class="text-sm font-italic text-blue-600">Obs: ${item.obs}</p>` : ''}
                    <p class="text-lg font-extrabold text-red-700 text-right">R$ ${item.price.toFixed(2).replace('.', ',')}</p>
                `;
                cartList.appendChild(li);
            });
            
            // 2. Renderiza os Pratos Fixos (Lasanha)
            Object.entries(pratosFixosQuantities).forEach(([name, qty]) => {
                if (qty > 0) {
                    const pratoFixo = MENU.pratosFixos.find(p => p.nome === name);
                    if (pratoFixo) {
                        const precoTotal = qty * pratoFixo.preco;
                        subtotalPratos += precoTotal;
                        totalUnidadesFixos += qty;

                        const li = document.createElement('li');
                        li.className = 'p-3 border border-green-300 bg-white rounded-lg shadow-sm space-y-1';
                        
                        li.innerHTML = `
                            <div class="flex justify-between items-center">
                                <h3 class="font-bold text-green-800">🍝 Prato Fixo: ${name} (x${qty})</h3>
                                <p class="text-lg font-extrabold text-red-600">R$ ${precoTotal.toFixed(2).replace('.', ',')}</p>
                            </div>
                            <p class="text-sm text-gray-600">${pratoFixo.descricao.substring(0, 100)}...</p>
                            <button onclick="changeFixedItemQuantity('${name}', -${qty})" class="text-red-500 hover:text-red-700 text-sm font-semibold transition duration-150">
                                Remover Todos
                            </button>
                        `;
                        cartList.appendChild(li);
                    }
                }
            });


            // 3. Renderiza as Bebidas
            Object.entries(bebidasQuantities).forEach(([name, qtd]) => {
                if (qtd > 0) {
                    totalUnidadesBebidas += qtd;
                    const total = qtd * MENU.bebidas.precoUnitario;
                    subtotalPratos += total;
                    
                    const li = document.createElement('li');
                    li.className = 'p-3 border border-blue-200 bg-white rounded-lg shadow-sm flex justify-between items-center';
                    li.innerHTML = `
                        <h3 class="font-bold text-blue-800">🥤 Bebida: ${name} (x${qtd})</h3>
                        <p class="text-lg font-extrabold text-blue-600">R$ ${total.toFixed(2).replace('.', ',')}</p>
                    `;
                    cartList.appendChild(li);
                }
            });
        }
        
        document.getElementById('subtotal-display').textContent = `R$ ${subtotalPratos.toFixed(2).replace('.', ',')}`;
        updateFinalSummary();
        
        // Atualiza a disponibilidade das bebidas
        toggleDrinksAvailability(); 
    }

    function removeItem(index) {
        cart.splice(index, 1);
        renderCart();
    }

    function updateFinalSummary() {
        const subtotalString = document.getElementById('subtotal-display').textContent.replace('R$', '').replace(',', '.').trim();
        const subtotal = parseFloat(subtotalString) || 0;

        const selectedFeeRadio = document.querySelector('input[name="deliveryFee"]:checked');
        const fee = parseFloat(selectedFeeRadio?.value || 0);

        const total = subtotal + fee;

        document.getElementById('final-subtotal').textContent = `R$ ${subtotal.toFixed(2).replace('.', ',')}`;
        document.getElementById('final-fee').textContent = `R$ ${fee.toFixed(2).replace('.', ',')}`;
        document.getElementById('final-total').textContent = `R$ ${total.toFixed(2).replace('.', ',')}`;
    }


    // --- FUNÇÃO DE CHECKOUT ---

    function generateWhatsAppLink() {
        if (isClosed()) {
            alert('🚨 O estabelecimento está FECHADO. Pedidos de Quarta-feira (12:00) até Domingo (14:00).');
            return;
        }
        
        const hasFixedItems = Object.values(pratosFixosQuantities).some(qty => qty > 0);
        const hasDrinks = Object.values(bebidasQuantities).some(qty => qty > 0);
        
        if (cart.length === 0 && !hasFixedItems && !hasDrinks) {
            alert('Seu carrinho está vazio. Adicione itens antes de enviar o pedido.');
            return;
        }
        
        // Validação de dados pessoais
        const nome = document.getElementById('nome').value.trim();
        const telefone = document.getElementById('telefone').value.trim();
        const endereco = document.getElementById('endereco').value.trim();
        const referencia = document.getElementById('referencia').value.trim();
        const troco = document.getElementById('troco').value.trim();
        const paymentMethod = document.getElementById('payment-method').value;
        const total = document.getElementById('final-total').textContent.trim();
        const subtotal = document.getElementById('final-subtotal').textContent.trim();
        const fee = document.getElementById('final-fee').textContent.trim();

        if (!nome || !telefone || !endereco) {
            alert('Por favor, preencha seu Nome, Telefone e Endereço para a entrega.');
            return;
        }

        let message = `*🍕 NOVO PEDIDO - MASSA NOSTRA POTY 🍝*\n\n`;
        message += `*Cliente:* ${nome}\n`;
        message += `*Telefone:* ${telefone}\n`;
        message += `*Endereço:* ${endereco}\n`;
        message += `*Ponto de Ref.:* ${referencia || 'Não informado'}\n\n`;
        
        message += `*--- ITENS DO PEDIDO (${cart.length + Object.values(pratosFixosQuantities).reduce((sum, qty) => sum + qty, 0)} Total) ---*\n\n`;

        // 1. Itens Customizados
        cart.forEach((item, index) => {
            // Formatação: Acompanhamentos, Massa, Molho e Queijo em negrito.
            const acompList = item.acompanhamentos.length > 0 ? item.acompanhamentos.map(acomp => `*${acomp}*`).join(', ') : 'Nenhum';
            const premiumText = item.premium ? ` (+ *${item.premium.name} Premium* - R$ ${item.premium.cost.toFixed(2).replace('.', ',')})` : '';
            
            message += `*#${index + 1} - Massa ${item.size} (R$ ${item.price.toFixed(2).replace('.', ',')})*\n`;
            message += `> Massa: *${item.massa}*\n`;
            message += `> Molho: *${item.molho}*\n`;
            message += `> Queijo: *${item.queijo}*\n`;
            message += `> Acompanhamentos: ${acompList}${premiumText}\n`;
            if (item.obs) message += `> Obs: ${item.obs}\n`;
            message += `\n`;
        });
        
        // 2. Pratos Fixos (Lasanha)
        Object.entries(pratosFixosQuantities).forEach(([name, qty]) => {
            if (qty > 0) {
                 const pratoFixo = MENU.pratosFixos.find(p => p.nome === name);
                 const totalPrato = (qty * pratoFixo.preco).toFixed(2).replace('.', ',');
                 message += `*🍽️ Prato Fixo: ${name} (x${qty})*\n`;
                 message += `> Total do Item: R$ ${totalPrato}\n`;
                 message += `\n`;
            }
        });


        // 3. Bebidas
        if (hasDrinks) {
            message += `*🥤 Bebidas:*\n`;
            Object.entries(bebidasQuantities).forEach(([name, qtd]) => {
                if (qtd > 0) {
                    const precoUnitario = MENU.bebidas.precoUnitario.toFixed(2).replace('.', ',');
                    message += `> ${qtd}x ${name} (R$ ${precoUnitario} cada)\n`;
                }
            });
            message += `\n`;
        }

        // 4. Resumo Financeiro
        message += `*--- RESUMO FINANCEIRO ---*\n`;
        message += `*SUBTOTAL (Itens):* ${subtotal}\n`;
        message += `*Taxa de Entrega:* ${fee}\n`;
        message += `*TOTAL FINAL:* ${total}\n\n`;

        // 5. Pagamento e Troco
        message += `*FORMA DE PAGAMENTO:* ${paymentMethod}\n`;
        if (paymentMethod === 'Dinheiro' && troco) {
            message += `*Precisa de TROCO para:* R$ ${troco}\n`;
        } else if (paymentMethod === 'Dinheiro') {
            message += `*Troco:* Não informado (Pagar valor exato)\n`;
        } else if (paymentMethod === 'Pix') {
            message += `*Dados Pix:* ${MENU.pixData.key} (${MENU.pixData.name})\n`;
        }
        
        message += `\n_Aguarde a confirmação da entrega. Obrigado!_`;

        // Gera o link do WhatsApp
        const waLink = `https://api.whatsapp.com/send?phone=${MENU.whatsappNumber}&text=${encodeURIComponent(message)}`;
        
        window.open(waLink, '_blank');
    }

    // Inicializa a aplicação
    setupUI();
</script>
</body>
</html>
