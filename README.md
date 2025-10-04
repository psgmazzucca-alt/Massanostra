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
                <label for="obs" class="block font-semibold text-gray-700 border-t pt-4">6. Observações (Ex: Queijo a parte, Sem cebolinha)</label>
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

        <section id="dessert-section" class="space-y-4 p-4 border border-purple-100 rounded-xl bg-purple-50">
            <h2 class="section-title text-purple-800 border-purple-200">🍰 Adicionar Sobremesa</h2>
            <div id="sobremesa-options" class="space-y-3">
                </div>
            <p id="sobremesa-count" class="text-sm font-medium text-gray-600 pt-2 border-t border-purple-200">
                Total de Unidades: <span id="sobremesa-unidades-display">0</span> | Total: <span id="sobremesa-total-display">R$ 0,00</span>
            </p>
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
        massas: ["Penne", "Spaguetti", "Parafuso", "Fetutini-ESGOTOU "],
        molhos: ["Bolonhesa", "Branco", "Rosé", "Sugo"],
        acompanhamentos: [
            "Alho", "Alho Frito", "Azeitona", "Bacon", "Brócolis",
            "Calabresa", "Catupiry", "Cebola", "Cheddar", "Champignon",
            "Ervilha", "Frango", "Milho", "Palmito", "Pimentão",
            "Presunto", "Salsicha", "Tomate", "Tomate Seco",
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
        bebidas: {
            opcoes: ["Coca-Cola", "Coca-Cola Zero", "Fanta", "Guaraná Antárctica", "Sprite", "Sprite Zero"],
            precoUnitario: 6.00, 
            volume: "350ml"
        },
        // Sobremesa
        sobremesa: {
            nome: "Palha Italiana Ninho com Nutella",
            precoUnitario: 12.00,
        },
        whatsappNumber: "5517997381858",
        // DADOS DO PIX
        pixData: { 
            name: "SUÉLEM CRISTINA MAESTRE MAZZUCCA",
            key: "41756000867 (CPF)" 
        }
    };

    // --- ESTADO GLOBAL ---
    let cart = []; 
    let bebidas = []; 
    let sobremesas = []; 
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
    const sobremesaOptionsDiv = document.getElementById('sobremesa-options');
    const sobremesaTotalDisplay = document.getElementById('sobremesa-total-display');
    const sobremesaUnidadesDisplay = document.getElementById('sobremesa-unidades-display');
    
    // FIELDSET AGORA FOCADO APENAS EM BEBIDAS
    const bebidasFieldset = document.getElementById('bebidas-fieldset'); 

    // Referência para o campo de troco
    const trocoInputContainer = document.getElementById('troco-input-container'); 
    const paymentMethodSelect = document.getElementById('payment-method');

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
            const id = `qtd-${bebida.toLowerCase().replace(/\s/g, '-')}`;
            return `
                <div class="flex justify-between items-center p-3 bg-white rounded-lg shadow-md">
                    <label for="${id}" class="font-medium text-gray-700 flex-1">
                        ${bebida} ${MENU.bebidas.volume} (R$ ${MENU.bebidas.precoUnitario.toFixed(2).replace('.', ',')})
                    </label>
                    <input type="number" id="${id}" name="bebida-qty" data-name="${bebida}"
                            min="0" value="0" class="drink-input" 
                            onchange="updateBebidasTotal(); renderCart();">
                </div>
            `;
        }).join('');
    }

    // Renderizar Sobremesa
    function renderSobremesas() {
        const sobremesa = MENU.sobremesa;
        const id = `qtd-${sobremesa.nome.toLowerCase().replace(/\s/g, '-')}`;

        sobremesaOptionsDiv.innerHTML = `
            <div class="flex justify-between items-center p-3 bg-white rounded-lg shadow-md">
                <label for="${id}" class="font-bold text-purple-700 flex-1">
                    ${sobremesa.nome} (R$ ${sobremesa.precoUnitario.toFixed(2).replace('.', ',')})
                </label>
                <input type="number" id="${id}" name="sobremesa-qty" data-name="${sobremesa.nome}"
                        min="0" value="0" class="drink-input" 
                        onchange="updateSobremesasTotal(); renderCart();">
            </div>
        `;
    }

    function setupUI() {
        // Renderiza as seções do Prato
        renderOptions(sizeOptionsDiv, 'size', MENU.tamanhos, 'radio', 'P', true);
        renderOptions(massaOptionsDiv, 'massa', MENU.massas, 'radio');
        renderOptions(molhoOptionsDiv, 'molho', MENU.molhos, 'radio');
        renderAcompanhamentos();
        renderQueijo(); 

        // Renderiza as sobremesas
        renderSobremesas();
        
        // Renderiza as bebidas com campo de quantidade
        renderBebidas();

        // Adiciona Listeners
        sizeOptionsDiv.addEventListener('change', updateLimitAndPrice);
        acompOptionsDiv.addEventListener('change', updateAcompCount);
        document.querySelector('input[name="acompPremium"]').addEventListener('change', updateItemPrice);
        deliveryFeeRadios.forEach(radio => radio.addEventListener('change', updateFinalSummary));

        // Inicializa
        updateLimitAndPrice();
        updateBebidasTotal();
        updateSobremesasTotal();
        renderCart(); 
        
        // Inicializa a regra de bloqueio (se não houver prato, bloqueia APENAS bebidas)
        toggleDrinksAvailability(); 
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
        // Apenas macarrão no carrinho conta para liberar os adicionais
        const hasPasta = cart.length > 0; 
        
        bebidasFieldset.disabled = !hasPasta; 

        // Se desabilitou e o usuário tinha algo selecionado, zera a quantidade
        if (!hasPasta) {
            // Zera Bebidas
            document.querySelectorAll('input[name="bebida-qty"]').forEach(input => input.value = 0);
            updateBebidasTotal();
            
            // Só mostra a mensagem se tinha bebida selecionada antes
            if (bebidas.length > 0) {
               showModal('Adicione um *Prato de Macarrão* primeiro para selecionar Bebidas.', 'bg-yellow-600');
            }
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
        const inputs = document.querySelectorAll('input[name="bebida-qty"]');
        let totalUnidades = 0;
        
        bebidas = []; 

        inputs.forEach(input => {
            let qtd = parseInt(input.value) || 0;
            
            if (qtd < 0) {
                qtd = 0;
                input.value = 0;
            }
            
            if (qtd > 0) {
                totalUnidades += qtd;
                bebidas.push({
                    nome: input.getAttribute('data-name'),
                    qtd: qtd
                });
            }
        });
        
        const totalBebidas = totalUnidades * MENU.bebidas.precoUnitario;

        bebidasUnidadesDisplay.textContent = totalUnidades;
        bebidasTotalDisplay.textContent = `R$ ${totalBebidas.toFixed(2).replace('.', ',')}`;
        
        updateFinalSummary(); 
    }
    
    // Função para atualizar o total de sobremesas
    function updateSobremesasTotal() {
        const input = document.querySelector('input[name="sobremesa-qty"]');
        let qtd = parseInt(input.value) || 0;
        
        sobremesas = [];
        let totalUnidades = 0;

        if (qtd < 0) {
            qtd = 0;
            input.value = 0;
        }
        
        if (qtd > 0) {
            totalUnidades = qtd;
            sobremesas.push({
                nome: input.getAttribute('data-name'),
                qtd: qtd
            });
        }
        
        const totalSobremesas = totalUnidades * MENU.sobremesa.precoUnitario;

        sobremesaUnidadesDisplay.textContent = totalUnidades;
        sobremesaTotalDisplay.textContent = `R$ ${totalSobremesas.toFixed(2).replace('.', ',')}`;
        
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
            showModal('Por favor, selecione o **Tamanho**, a **Massa**, o **Molho** e o **Queijo**.', 'bg-red-500');
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
        addToCartBtn.disabled = true; 
        addToCartBtn.textContent = 'Adicionando...';
        
        const item = getFormData();
        if (item) {
            cart.push(item);
            showModal('Prato adicionado ao carrinho! Você pode montar outro.', 'bg-green-500');
            renderCart();
            resetForm();
            
            // Chama a função para garantir que as bebidas estão liberadas
            toggleDrinksAvailability(); 

            // NOVO E CORRIGIDO: Scroll para a seção da Sobremesa
            document.getElementById('dessert-section').scrollIntoView({ behavior: 'smooth', block: 'start' });
        }

        setTimeout(() => {
            addToCartBtn.disabled = false;
            addToCartBtn.textContent = 'ADICIONAR PRATO AO CARRINHO E MONTAR OUTRO';
        } , 300); 
    }
    
    function resetForm() {
        // Reset do Prato
        document.querySelectorAll('input[name="massa"]').forEach(r => r.checked = false);
        document.querySelectorAll('input[name="molho"]').forEach(r => r.checked = false);
        document.querySelectorAll('input[name="queijo"]').forEach((r, index) => {
             // Força a seleção da primeira opção de queijo ao resetar, pois é obrigatório
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
        let totalUnidadesBebidas = 0;
        let totalUnidadesSobremesas = sobremesas.reduce((sum, item) => sum + item.qtd, 0);

        if (cart.length === 0 && bebidas.length === 0 && sobremesas.length === 0) {
            cartList.innerHTML = `<li id="empty-cart-message" class="text-gray-500 italic text-center">Nenhum item no carrinho.</li>`;
        } else {
            // 1. Renderiza os Pratos
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
                    <p class="text-sm font-bold text-red-500">Queijo: ${item.queijo}</p> <p class="text-sm text-gray-600">Acompanhamentos Comuns: ${acompList}</p>
                    ${camarãoText} <p class="text-sm text-gray-600 italic">Obs: ${item.obs || 'Nenhuma'}</p>
                    <p class="text-lg font-extrabold text-green-700 text-right">R$ ${item.price.toFixed(2).replace('.', ',')}</p>
                `;
                cartList.appendChild(li);
            });
            
            // 2. Adiciona as Sobremesas
            if (sobremesas.length > 0) {
                const totalSobremesas = totalUnidadesSobremesas * MENU.sobremesa.precoUnitario;
                subtotalPratos += totalSobremesas;
                
                const listaSobremesas = sobremesas.map(s => `${s.qtd}x ${s.nome}`).join(' | ');

                const sobremesaItem = document.createElement('li');
                sobremesaItem.className = 'p-3 border border-purple-200 bg-purple-50 rounded-lg shadow-sm mt-4';
                sobremesaItem.innerHTML = `
                    <h3 class="font-bold text-purple-800">🍰 Sobremesas (${totalUnidadesSobremesas} Unidade(s))</h3>
                    <p class="text-sm text-gray-700">Palha Italiana: ${listaSobremesas}</p>
                    <p class="text-lg font-extrabold text-purple-700 text-right">R$ ${totalSobremesas.toFixed(2).replace('.', ',')}</p>
                `;
                cartList.appendChild(sobremesaItem);
            }
            
            // 3. Adiciona as Bebidas
            if (bebidas.length > 0) {
                const totalBebidas = bebidas.reduce((sum, item) => sum + (item.qtd * MENU.bebidas.precoUnitario), 0);
                totalUnidadesBebidas = bebidas.reduce((sum, item) => sum + item.qtd, 0);
                subtotalPratos += totalBebidas;
                
                const listaBebidas = bebidas.map(b => `${b.qtd}x ${b.nome}`).join(' | ');

                const bebidasItem = document.createElement('li');
                bebidasItem.className = 'p-3 border border-blue-200 bg-blue-50 rounded-lg shadow-sm mt-4';
                bebidasItem.innerHTML = `
                    <h3 class="font-bold text-blue-800">🥤 Bebidas (${totalUnidadesBebidas} Unidade(s))</h3>
                    <p class="text-sm text-gray-700">Latas ${MENU.bebidas.volume}: ${listaBebidas}</p>
                    <p class="text-lg font-extrabold text-blue-700 text-right">R$ ${totalBebidas.toFixed(2).replace('.', ',')}</p>
                `;
                cartList.appendChild(bebidasItem);
            }
        }

        checkoutSection.style.display = (cart.length > 0 || bebidas.length > 0 || sobremesas.length > 0) ? 'block' : 'none';

        document.getElementById('cart-count').textContent = cart.length;
        document.getElementById('subtotal-display').textContent = `R$ ${subtotalPratos.toFixed(2).replace('.', ',')}`;
        updateFinalSummary();
    }

    function removeItem(index) {
        cart.splice(index, 1);
        renderCart();
        
        // Chama a função para bloquear as bebidas se o carrinho de pratos esvaziar
        toggleDrinksAvailability(); 
    }

    function updateFinalSummary() {
        const subtotalPratos = cart.reduce((sum, item) => sum + item.price, 0);
        const subtotalBebidas = bebidas.reduce((sum, item) => sum + (item.qtd * MENU.bebidas.precoUnitario), 0);
        const subtotalSobremesas = sobremesas.reduce((sum, item) => sum + (item.qtd * MENU.sobremesa.precoUnitario), 0);
        
        const subtotalGeral = subtotalPratos + subtotalBebidas + subtotalSobremesas;

        const feeRadio = document.querySelector('input[name="deliveryFee"]:checked');
        const deliveryFee = feeRadio ? parseFloat(feeRadio.value) : 2.00;
        const finalTotalValue = subtotalGeral + deliveryFee;

        document.getElementById('final-subtotal').textContent = `R$ ${subtotalGeral.toFixed(2).replace('.', ',')}`;
        document.getElementById('final-fee').textContent = `R$ ${deliveryFee.toFixed(2).replace('.', ',')}`;
        document.getElementById('final-total').textContent = `R$ ${finalTotalValue.toFixed(2).replace('.', ',')}`;
    }

    // --- FUNÇÕES DE CHECKOUT E WHATSAPP ---
    
    function validateCheckoutForm() {
        const requiredIds = ['nome', 'telefone', 'endereco'];
        let isValid = true;
        
        document.querySelectorAll('.input-style').forEach(input => {
            input.classList.remove('border-red-500', 'ring-2', 'ring-red-500');
        });

        requiredIds.forEach(id => {
            const input = document.getElementById(id);
            if (!input.value.trim()) {
                isValid = false;
                input.classList.add('border-red-500', 'ring-2', 'ring-red-500');
            }
        });

        if (!isValid) {
            showModal('Por favor, preencha todos os campos obrigatórios (*).', 'bg-red-500');
        }

        return isValid;
    }
    
    // Função para formatar o valor (retirar R$ e ,) e retornar float
    function formatCurrencyToFloat(currencyString) {
        if (!currencyString) return 0;
        // Remove "R$", espaços, e troca vírgula por ponto
        return parseFloat(currencyString.replace('R$', '').trim().replace(',', '.')) || 0;
    }

    function generateWhatsAppLink() {
        checkoutBtn.disabled = true;
        checkoutBtn.textContent = 'Montando mensagem...';

        if (cart.length === 0 && bebidas.length === 0 && sobremesas.length === 0) {
            showModal('Seu carrinho, bebidas e sobremesas estão vazios. Adicione um item antes de enviar.', 'bg-yellow-500');
            checkoutBtn.disabled = false;
            checkoutBtn.textContent = 'ENVIAR PEDIDO VIA WHATSAPP';
            return;
        }

        if (!validateCheckoutForm()) {
            checkoutBtn.disabled = false;
            checkoutBtn.textContent = 'ENVIAR PEDIDO VIA WHATSAPP';
            return;
        }

        const nome = document.getElementById('nome').value.trim();
        const telefone = document.getElementById('telefone').value.trim();
        const endereco = document.getElementById('endereco').value.trim();
        const referencia = document.getElementById('referencia').value.trim();
        const paymentMethod = document.getElementById('payment-method').value;
        const trocoString = document.getElementById('troco').value.trim(); // Pega valor do troco
        
        const subtotalPratos = cart.reduce((sum, item) => sum + item.price, 0);
        const subtotalBebidas = bebidas.reduce((sum, item) => sum + (item.qtd * MENU.bebidas.precoUnitario), 0);
        const subtotalSobremesas = sobremesas.reduce((sum, item) => sum + (item.qtd * MENU.sobremesa.precoUnitario), 0);
        
        const totalUnidadesBebidas = bebidas.reduce((sum, item) => sum + item.qtd, 0);
        const totalUnidadesSobremesas = sobremesas.reduce((sum, item) => sum + item.qtd, 0);

        const subtotalGeral = subtotalPratos + subtotalBebidas + subtotalSobremesas;

        const feeRadio = document.querySelector('input[name="deliveryFee"]:checked');
        const deliveryFee = feeRadio ? parseFloat(feeRadio.value) : 2.00;
        const finalTotalValue = subtotalGeral + deliveryFee;
        const feeLabel = feeRadio.nextElementSibling.textContent.trim();

        // Lógica do Troco
        let trocoText = "";
        if (paymentMethod === 'Dinheiro') {
            if (trocoString) {
                const trocoValue = formatCurrencyToFloat(trocoString.replace('R$', ''));
                if (trocoValue > finalTotalValue) {
                    trocoText = `*Troco para:* R$ ${trocoValue.toFixed(2).replace('.', ',')}`;
                } else {
                    trocoText = `*Troco:* Vou pagar o valor exato (R$ ${finalTotalValue.toFixed(2).replace('.', ',')})`;
                }
            } else {
                trocoText = `*Troco:* Vou pagar o valor exato (R$ ${finalTotalValue.toFixed(2).replace('.', ',')})`;
            }
        }

        // Montagem da Mensagem do Pedido
        let message = `🍝 Olá, Massa Nostra! Meu pedido de *${nome}* é o seguinte:\n\n`;
        
        // Adiciona Pratos
        message += `--- ITENS (🍝 ${cart.length} prato(s)) ---\n`;
        if (cart.length === 0) {
            message += `_Nenhum prato montado._\n`;
        }
        cart.forEach((item, index) => {
            // Acompanhamentos Comuns em MAIÚSCULO e NEGITO
            const acompText = item.acompanhamentos.length > 0 
                ? item.acompanhamentos.join(', ').toUpperCase() 
                : 'Nenhum';
            
            // Acompanhamento Premium em MAIÚSCULO e NEGITO
            const camarãoText = item.premium ? 
                `\n  Premium: *${item.premium.name.toUpperCase()}* (+ R$ ${item.premium.cost.toFixed(2).replace('.', ',')})` 
                : '';

            message += `\n*PRATO #${index + 1} (${item.size}):*\n`;
            // Massa em MAIÚSCULO e NEGITO
            message += `  Massa: *${item.massa.toUpperCase()}*\n`;
            // Molho em MAIÚSCULO e NEGITO
            message += `  Molho: *${item.molho.toUpperCase()}*\n`;
            message += `  Queijo: *${item.queijo}* (Incluso)\n`; 
            // Acompanhamentos Comuns: em MAIÚSCULO e em NEGITO
            message += `  Acompanhamentos Comuns: *${acompText}*`;
            message += `${camarãoText}\n`;
            // Observação em NEGITO
            message += `  Obs: *${item.obs || 'Nenhuma'}*\n`;
            message += `  Valor: R$ ${item.price.toFixed(2).replace('.', ',')}\n`;
        });
        
        // Adiciona Sobremesas
        message += `\n--- SOBREMESAS (🍰 ${totalUnidadesSobremesas} unidade(s)) ---\n`;
        if (sobremesas.length > 0) {
            message += `*Valor: R$ ${MENU.sobremesa.precoUnitario.toFixed(2).replace('.', ',')}/cada:*\n`;
            sobremesas.forEach(s => {
                // SOBREMESA EM MAIÚSCULO E NEGITO
                message += `  - ${s.qtd}x *${s.nome.toUpperCase()}*\n`; 
            });
            message += `  _Total Sobremesas: R$ ${subtotalSobremesas.toFixed(2).replace('.', ',')}_\n`;
        } else {
            message += `_Nenhuma sobremesa adicionada._\n`;
        }

        // Adiciona Bebidas com Quantidade
        message += `\n--- BEBIDAS (🥤 ${totalUnidadesBebidas} lata(s)) ---\n`;
        if (bebidas.length > 0) {
            message += `*Latas ${MENU.bebidas.volume} (R$ ${MENU.bebidas.precoUnitario.toFixed(2).replace('.', ',')}/cada):*\n`;
            bebidas.forEach(b => {
                message += `  - ${b.qtd}x ${b.nome}\n`;
            });
            message += `  _Total Bebidas: R$ ${subtotalBebidas.toFixed(2).replace('.', ',')}_\n`;
        } else {
            message += `_Nenhuma bebida adicionada._\n`;
        }


        message += `\n--- RESUMO DA COMPRA ---\n`;
        message += `*SUBTOTAL DOS ITENS:* R$ ${subtotalGeral.toFixed(2).replace('.', ',')}\n`;
        message += `*TAXA DE ENTREGA:* ${feeLabel} (R$ ${deliveryFee.toFixed(2).replace('.', ',')})\n`;
        message += `*TOTAL FINAL:* R$ ${finalTotalValue.toFixed(2).replace('.', ',')}\n\n`;
        
        message += `--- DADOS DO CLIENTE ---\n`;
        message += `Nome: ${nome}\n`;
        message += `Telefone: ${telefone}\n`;
        message += `Endereço: ${endereco}\n`;
        message += `Referência: ${referencia || 'Sem referência'}\n`;
        
        // Adiciona Dados de Pagamento e Pix/Troco
        message += `Forma de Pagamento: *${paymentMethod}*\n`;
        if (paymentMethod === 'Dinheiro') {
            message += `${trocoText}\n\n`;
        }

        // Adiciona as informações do PIX se o método for selecionado
        if (paymentMethod === 'Pix') {
            message += `\n🚨 *PAGAMENTO VIA PIX SELECIONADO:*\n`;
            message += `  *Nome:* ${MENU.pixData.name}\n`;
            message += `  *Chave:* ${MENU.pixData.key}\n\n`;
        }

        message += `Aguardamos a confirmação! Obrigado!`;
        
        const encodedMessage = encodeURIComponent(message);
        const whatsappLink = `https://wa.me/${MENU.whatsappNumber}?text=${encodedMessage}`;

        try {
            const newWindow = window.open(whatsappLink, '_blank');
            if (!newWindow || newWindow.closed || typeof newWindow.closed=='undefined') {
                // Caso o navegador bloqueie a abertura
                showModal('O bloqueador de pop-ups impediu a abertura do WhatsApp. Por favor, desabilite-o.', 'bg-yellow-500');
            }
        } catch (error) {
            console.error("Erro ao tentar abrir o WhatsApp:", error);
        } finally {
            // Re-habilita o botão após a tentativa
            checkoutBtn.disabled = false;
            checkoutBtn.textContent = 'ENVIAR PEDIDO VIA WHATSAPP';
        }
    }

    // Função de Modal Simples (Para fins de teste e feedback ao usuário)
    function showModal(message, bgColor) {
        if (!document.getElementById('simple-modal')) {
            const modal = document.createElement('div');
            modal.id = 'simple-modal';
            modal.className = 'fixed top-0 left-0 right-0 p-4 text-center text-white font-bold transition-all duration-300 transform translate-y-[-100%] z-50';
            document.body.appendChild(modal);
        }
        
        const modal = document.getElementById('simple-modal');
        modal.className = `fixed top-0 left-0 right-0 p-4 text-center text-white font-bold transition-all duration-300 ${bgColor} z-50`;
        modal.textContent = message;
        modal.style.transform = 'translateY(0)';
        
        setTimeout(() => {
            modal.style.transform = 'translateY(-100%)';
        }, 3000);
    }
    
    // Inicia a aplicação
    document.addEventListener('DOMContentLoaded', setupUI);
</script>

</body>
</html>
