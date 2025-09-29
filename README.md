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
.acomp-option input:disabled + span {
    opacity: 0.6;
    cursor: not-allowed;
    background-color: #f3f4f6;
    text-decoration: line-through;
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
/* Novo estilo para grid de massas/molhos */
#massa-options, #molho-options {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 8px;
}
/* Novo estilo para grid de acompanhamentos */
#acomp-options {
    grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
    gap: 8px;
}
/* Ajuste de layout para opções com imagem (macarrão/molho/acompanhamento) */
.acomp-option {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 8px !important; /* Ajuste para caber melhor */
}
.acomp-option input {
    order: 3; /* Move o checkbox para baixo */
    margin-top: 5px;
}
.acomp-option .font-medium {
    order: 2; /* Move a label para o meio */
    margin-left: 0 !important;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
}
.acomp-option img {
    order: 1; /* Move a imagem para cima */
    margin-right: 0 !important;
    margin-bottom: 4px;
    width: 60px !important;
    height: 60px !important;
    border-radius: 9999px !important; /* Circular */
}

/* Reverte o layout para Tamanhos e Queijos, que não usam imagem assim */
#size-options .acomp-option, #queijo-options .acomp-option {
    flex-direction: row;
    align-items: center;
    text-align: left;
    padding: 12px !important;
}
#size-options .acomp-option input, #queijo-options .acomp-option input {
    order: 1;
    margin-top: 0;
}
#size-options .acomp-option .font-medium, #queijo-options .acomp-option .font-medium {
    order: 2;
    margin-left: 8px !important;
    flex-direction: row;
}
</style>
</head>
<body class="min-h-screen p-4 flex justify-center">

<div id="app" class="w-full max-w-xl bg-white shadow-2xl rounded-xl space-y-6 md:p-0">
    <header class="text-center relative italian-flag-gradient rounded-t-xl py-6 shadow-2xl">
        <img src="https://drive.google.com/uc?id=1cGwwqA1h1z9G_s5l8DM9qkV9XkdYF--6" 
             alt="Logo Massa Nostra" 
             class="w-40 h-40 object-cover mx-auto rounded-full mb-3 shadow-2xl border-4 border-white z-10 relative">
        <div class="px-2">
            <h1 class="text-4xl font-extrabold text-white sm:text-5xl flag-text-shadow leading-tight">MASSA NOSTRA POTY</h1>
            <p class="text-base text-white font-medium mt-1 flag-text-shadow">@massanostra_poty | Monte seu prato e faça seu pedido!</p>
        </div>
    </header>

    <div class="p-6 space-y-6 md:p-8 pt-0">
        
        <section id="custom-order-section" class="space-y-6 p-4 border border-red-100 rounded-xl bg-red-50">
            <h2 class="section-title text-red-800">Monte Seu Prato</h2>

            <div class="space-y-2">
                <label class="block font-semibold text-gray-700">1. Escolha o Tamanho</label>
                <div id="size-options" class="flex space-x-4">
                    </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="space-y-2">
                    <label class="block font-semibold text-gray-700">2. Escolha a Massa (Obrigatório)</label>
                    <div id="massa-options" class="space-y-1"></div>
                </div>

                <div class="space-y-2">
                    <label class="block font-semibold text-gray-700">3. Escolha o Molho (Obrigatório)</label>
                    <div id="molho-options" class="space-y-1"></div>
                </div>
            </div>

            <div class="space-y-2">
                <label class="block font-semibold text-gray-700">4. Acompanhamentos Comuns</label>
                
                <div id="acomp-premium-options" class="mb-3 p-3 bg-yellow-50 rounded-lg border border-yellow-200">
                    </div>
                
                <p id="acomp-counter" class="text-sm font-medium text-red-600">Selecionados: 0/6 (Tamanho P)</p>
                
                <div id="acomp-options" class="grid grid-cols-2 sm:grid-cols-3 gap-2"></div>
            </div>

            <div class="space-y-2">
                <label class="block font-bold text-gray-800 border-t pt-4">5. Escolha o Queijo (Obrigatório)</label>
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

        <section id="drinks-section" class="space-y-4 p-4 border border-blue-100 rounded-xl bg-blue-50">
            <h2 class="section-title text-blue-800 border-blue-200">Adicionar Bebidas Geladas (R$ 6,00/cada)</h2>
            <div id="bebidas-options" class="space-y-3">
                </div>
            <p id="bebidas-count" class="text-sm font-medium text-gray-600 pt-2 border-t border-blue-200">
                Total de Unidades: <span id="bebidas-unidades-display">0</span> | Total: <span id="bebidas-total-display">R$ 0,00</span>
            </p>
        </section>

        <section class="space-y-4 p-4 border border-gray-200 rounded-xl bg-gray-50">
            <h2 class="section-title text-gray-700 border-gray-200">Seu Pedido (<span id="cart-count">0</span> Pratos)</h2>
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
                <select id="payment-method" class="input-style">
                    <option value="Pix">Pix (Informar na mensagem)</option>
                    <option value="Dinheiro">Dinheiro (Precisa de troco?)</option>
                    <option value="Cartao-Debito">Cartão de Débito</option>
                    <option value="Cartao-Credito">Cartão de Crédito</option>
                </select>
            </div>
            
            <div id="pix-info" class="p-3 bg-green-100 border border-green-300 rounded-lg shadow-md hidden">
                <p class="font-bold text-green-800">PIX Selecionado!</p>
                <p class="text-sm text-gray-700">Titular: <span id="pix-name" class="font-extrabold text-green-900"></span></p>
                <p class="text-sm text-gray-700">Chave PIX (CPF): <span id="pix-number" class="font-extrabold text-green-900"></span></p>
                <p class="text-xs text-gray-500 mt-1">Lembre-se: O pagamento via PIX deve ser confirmado no WhatsApp.</p>
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

<div id="custom-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 hidden" onclick="hideModal()">
    <div id="modal-content" class="bg-white rounded-lg shadow-xl p-6 max-w-sm w-full transform transition-all duration-300 scale-95" onclick="event.stopPropagation()">
        <div id="modal-header" class="flex justify-between items-center pb-3 border-b border-gray-200">
            <h3 class="text-xl font-bold text-gray-800">Aviso</h3>
            <button onclick="hideModal()" class="text-gray-400 hover:text-gray-600 transition duration-150">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
            </button>
        </div>
        <div class="py-4">
            <p id="modal-text" class="text-gray-700"></p>
        </div>
        <div class="pt-3 border-t border-gray-200 text-right">
            <button onclick="hideModal()" class="px-4 py-2 bg-red-600 text-white font-semibold rounded-lg hover:bg-red-700 transition duration-150">
                Fechar
            </button>
        </div>
    </div>
</div>
<script>
    // --- DADOS DO CARDÁPIO (FONTE ÚNICA DE VERDADE) ---
    const MENU = {
        // ATUALIZADO COM IMAGENS (PLACEHOLDERS)
        massas: [
            { nome: "Penne", img: "https://via.placeholder.com/60/FFD500/000000?text=Penne" },
            { nome: "Spaguetti", img: "https://via.placeholder.com/60/FFD500/000000?text=Spag" },
            { nome: "Parafuso", img: "https://via.placeholder.com/60/FFD500/000000?text=Par" },
            { nome: "Fetutini", img: "https://via.placeholder.com/60/FFD500/000000?text=Fetu" }
        ],
        molhos: [
            { nome: "Bolonhesa", img: "https://via.placeholder.com/60/8B0000/FFFFFF?text=Bolo" },
            { nome: "Branco", img: "https://via.placeholder.com/60/FFFFFF/333333?text=Bco" },
            { nome: "Rosé", img: "https://via.placeholder.com/60/FFB6C1/000000?text=Rosé" },
            { nome: "Sugo", img: "https://via.placeholder.com/60/FF4500/FFFFFF?text=Sugo" }
        ],
        acompanhamentos: [
            { nome: "Alho", img: "https://via.placeholder.com/60/D3D3D3/000000?text=Alho" },
            { nome: "Alho Frito", img: "https://via.placeholder.com/60/D2B48C/000000?text=AF" },
            { nome: "Azeitona", img: "https://via.placeholder.com/60/006400/FFFFFF?text=Azei" },
            { nome: "Bacon", img: "https://via.placeholder.com/60/A0522D/FFFFFF?text=Bacon" },
            { nome: "Brócolis", img: "https://via.placeholder.com/60/008000/FFFFFF?text=Broc" },
            { nome: "Calabresa", img: "https://via.placeholder.com/60/8B0000/FFFFFF?text=Cala" },
            { nome: "Catupiry", img: "https://via.placeholder.com/60/F0F8FF/000000?text=Catu" },
            { nome: "Cebola", img: "https://via.placeholder.com/60/C0C0C0/000000?text=Ceb" },
            { nome: "Cheddar", img: "https://via.placeholder.com/60/FF8C00/000000?text=Ched" },
            { nome: "Champignon", img: "https://via.placeholder.com/60/D2B48C/000000?text=Cham" },
            { nome: "Ervilha", img: "https://via.placeholder.com/60/3CB371/FFFFFF?text=Erv" },
            { nome: "Frango", img: "https://via.placeholder.com/60/FFD700/000000?text=Fran" },
            { nome: "Milho", img: "https://via.placeholder.com/60/FFFF00/000000?text=Milh" },
            { nome: "Palmito", img: "https://via.placeholder.com/60/F5F5DC/000000?text=Palm" },
            { nome: "Pimentão", img: "https://via.placeholder.com/60/FF0000/FFFFFF?text=Pime" },
            { nome: "Presunto", img: "https://via.placeholder.com/60/FA8072/000000?text=Pres" },
            { nome: "Salsicha", img: "https://via.placeholder.com/60/FF6347/FFFFFF?text=Sals" },
            { nome: "Tomate", img: "https://via.placeholder.com/60/DC143C/FFFFFF?text=Tom" },
            { nome: "Tomate Seco", img: "https://via.placeholder.com/60/8B0000/FFFFFF?text=TS" },
            { nome: "Uva Passa", img: "https://via.placeholder.com/60/800080/FFFFFF?text=Uva" }
        ],
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
        whatsappNumber: "5517997381858",
        pixKey: "41756000867",
        pixName: "SUÉLEM CRISTINA MAESTRE MAZZUCCA"
    };

    // --- ESTADO GLOBAL ---
    let cart = []; 
    let bebidas = []; 
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
    
    const paymentMethodSelect = document.getElementById('payment-method');
    const pixInfoDiv = document.getElementById('pix-info');
    const pixNumberDisplay = document.getElementById('pix-number');
    const pixNameDisplay = document.getElementById('pix-name');

    // --- FUNÇÕES DE MODAL (INALTERADAS) ---
    function showModal(message, colorClass = 'bg-gray-500') {
        const modal = document.getElementById('custom-modal');
        const modalContent = document.getElementById('modal-content');
        const modalHeader = document.getElementById('modal-header');
        const modalText = document.getElementById('modal-text');

        modalHeader.className = modalHeader.className.replace(/bg-\w+-\d+/g, '').trim();

        modalContent.classList.remove('scale-95');
        modalContent.classList.add('scale-100');
        
        const headerTitle = modalHeader.querySelector('h3');
        headerTitle.classList.remove('text-green-800', 'text-red-800', 'text-yellow-800', 'text-gray-800');

        if (colorClass.includes('green')) {
            headerTitle.textContent = 'Sucesso! 🎉';
            headerTitle.classList.add('text-green-800');
        } else if (colorClass.includes('red')) {
            headerTitle.textContent = 'Erro';
            headerTitle.classList.add('text-red-800');
        } else if (colorClass.includes('yellow')) {
            headerTitle.textContent = 'Atenção';
            headerTitle.classList.add('text-yellow-800');
        } else {
            headerTitle.textContent = 'Aviso';
            headerTitle.classList.add('text-gray-800');
        }

        modalText.innerHTML = message.replace(/\n/g, '<br>');

        modal.classList.remove('hidden');
    }

    function hideModal() {
        const modal = document.getElementById('custom-modal');
        modal.classList.add('hidden');
        document.getElementById('modal-content').classList.remove('scale-100');
        document.getElementById('modal-content').classList.add('scale-95');
    }

    // --- FUNÇÕES DE LÓGICA E RENDERIZAÇÃO INICIAL (ATUALIZADA) ---

    function renderOptions(container, name, options, type = 'radio', checkedValue = null, isSizeOption = false) {
        // Verifica se a opção é um objeto (com nome e img)
        const isObjectOption = !isSizeOption && Array.isArray(options) && options.length > 0 && typeof options[0] === 'object';

        container.innerHTML = options.map((option, index) => {
            const value = isObjectOption ? option.nome : (isSizeOption ? option.id : option);
            const labelText = isObjectOption ? option.nome : (isSizeOption 
                ? `${option.id} (${option.nome}) (R$ ${option.preco.toFixed(2).replace('.', ',')}, Máx. ${option.limite} Acomp.)`
                : option);
            const imageUrl = isObjectOption ? option.img : null;
            
            const isQueijoOption = name === 'queijo';
            const isChecked = checkedValue ? (value === checkedValue) : (index === 0 && (!isSizeOption || isQueijoOption));
            
            // Adiciona a imagem e ajusta o layout se for uma opção com imagem
            const imageHtml = imageUrl ? `<img src="${imageUrl}" alt="${labelText}" class="w-10 h-10 object-cover rounded mr-2 border border-gray-200">` : '';
            const layoutClasses = isObjectOption ? 'flex items-center p-3' : 'flex items-center p-3'; // Mantém o estilo base
            // Se for um item com imagem, usamos uma estrutura de coluna no CSS (veja a tag <style>)
            const innerContentClasses = isObjectOption ? '' : ''; // O estilo de coluna é aplicado no CSS

            return `
                <label class="${layoutClasses} bg-white rounded-lg shadow-md hover:bg-red-50 transition duration-150 flex-1 cursor-pointer acomp-option">
                    <input type="${type}" name="${name}" value="${value}" 
                        class="${type === 'radio' ? 'form-radio text-red-600' : 'form-checkbox text-red-600'}"
                        ${isChecked ? 'checked' : ''}>
                    
                    <span class="ml-2 font-medium ${innerContentClasses}">
                        ${imageHtml}
                        ${labelText}
                    </span>
                </label>
            `;
        }).join('');
    }
    
    function renderAcompanhamentos() {
        // Agora, MENU.acompanhamentos já é um array de objetos
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

    function handlePaymentChange() {
        if (paymentMethodSelect.value === 'Pix') {
            pixNameDisplay.textContent = MENU.pixName; 
            pixNumberDisplay.textContent = MENU.pixKey;
            pixInfoDiv.classList.remove('hidden');
        } else {
            pixInfoDiv.classList.add('hidden');
        }
    }

    function setupUI() {
        renderOptions(sizeOptionsDiv, 'size', MENU.tamanhos, 'radio', 'P', true);
        renderOptions(massaOptionsDiv, 'massa', MENU.massas, 'radio');
        renderOptions(molhoOptionsDiv, 'molho', MENU.molhos, 'radio');
        renderAcompanhamentos();
        renderQueijo();
        renderBebidas();

        sizeOptionsDiv.addEventListener('change', updateLimitAndPrice);
        acompOptionsDiv.addEventListener('change', updateAcompCount);
        document.querySelector('input[name="acompPremium"]').addEventListener('change', updateItemPrice);
        deliveryFeeRadios.forEach(radio => radio.addEventListener('change', updateFinalSummary));
        
        paymentMethodSelect.addEventListener('change', handlePaymentChange);

        updateLimitAndPrice();
        updateBebidasTotal();
        renderCart();
        
        handlePaymentChange();
    }
    // ... (O restante das funções de update, getFormData, addToCart, renderCart, etc. permanecem inalteradas) ...
    
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

        if (selectedAcompanhamentos > maxAcompanhamentos) {
             showModal(`Você selecionou ${selectedAcompanhamentos} acompanhamentos, mas o máximo para o tamanho é ${maxAcompanhamentos}. Por favor, ajuste sua seleção.`, 'bg-red-500');
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
        }

        setTimeout(() => {
            addToCartBtn.disabled = false;
            addToCartBtn.textContent = 'ADICIONAR PRATO AO CARRINHO E MONTAR OUTRO';
        }, 300); 
    }
    
    function resetForm() {
        // Reset Massa, Molho e Queijo para a primeira opção (ou desmarcar)
        document.querySelectorAll('input[name="massa"]').forEach((r, index) => { r.checked = index === 0; });
        document.querySelectorAll('input[name="molho"]').forEach((r, index) => { r.checked = index === 0; });
        document.querySelectorAll('input[name="queijo"]').forEach((r, index) => { r.checked = index === 0; });

        // Desmarcar Acompanhamentos
        document.querySelectorAll('input[name="acomp"]').forEach(cb => cb.checked = false);
        document.querySelectorAll('input[name="acompPremium"]').forEach(cb => cb.checked = false); 
        document.getElementById('obs').value = '';

        // Reset Tamanho e limites
        document.querySelector('input[name="size"][value="P"]').checked = true;
        updateLimitAndPrice(); 
    }

    function renderCart() {
        cartList.innerHTML = '';
        let subtotalPratos = 0;
        let totalUnidadesBebidas = 0;

        if (cart.length === 0 && bebidas.length === 0) {
            cartList.innerHTML = `<li id="empty-cart-message" class="text-gray-500 italic text-center">Nenhum item no carrinho.</li>`;
        } else {
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
            
            if (bebidas.length > 0) {
                const totalBebidas = bebidas.reduce((sum, item) => sum + (item.qtd * MENU.bebidas.precoUnitario), 0);
                totalUnidadesBebidas = bebidas.reduce((sum, item) => sum + item.qtd, 0);
                subtotalPratos += totalBebidas;
                
                const listaBebidas = bebidas.map(b => `${b.qtd}x ${b.nome}`).join(' | ');

                const bebidasItem = document.createElement('li');
                bebidasItem.className = 'p-3 border border-blue-200 bg-blue-50 rounded-lg shadow-sm space-y-1 mt-4';
                bebidasItem.innerHTML = `
                    <h3 class="font-bold text-blue-800">Bebidas (${totalUnidadesBebidas} Unidade(s))</h3>
                    <p class="text-sm text-gray-700">Latas ${MENU.bebidas.volume}: ${listaBebidas}</p>
                    <p class="text-lg font-extrabold text-blue-700 text-right">R$ ${totalBebidas.toFixed(2).replace('.', ',')}</p>
                `;
                cartList.appendChild(bebidasItem);
            }
        }

        checkoutSection.style.display = (cart.length > 0 || bebidas.length > 0) ? 'block' : 'none';

        document.getElementById('cart-count').textContent = cart.length;
        document.getElementById('subtotal-display').textContent = `R$ ${subtotalPratos.toFixed(2).replace('.', ',')}`;
        updateFinalSummary();
    }

    function removeItem(index) {
        cart.splice(index, 1);
        renderCart();
    }

    function updateFinalSummary() {
        const subtotalPratos = cart.reduce((sum, item) => sum + item.price, 0);
        const subtotalBebidas = bebidas.reduce((sum, item) => sum + (item.qtd * MENU.bebidas.precoUnitario), 0);
        
        const subtotalGeral = subtotalPratos + subtotalBebidas;

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

    function generateWhatsAppLink() {
        checkoutBtn.disabled = true;
        checkoutBtn.textContent = 'Montando mensagem...';

        if (cart.length === 0 && bebidas.length === 0) {
            showModal('Seu carrinho e sua lista de bebidas estão vazios. Adicione um item antes de enviar.', 'bg-yellow-500');
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
        
        const subtotalPratos = cart.reduce((sum, item) => sum + item.price, 0);
        const subtotalBebidas = bebidas.reduce((sum, item) => sum + (item.qtd * MENU.bebidas.precoUnitario), 0);
        const totalUnidadesBebidas = bebidas.reduce((sum, item) => sum + item.qtd, 0);

        const subtotalGeral = subtotalPratos + subtotalBebidas;

        const feeRadio = document.querySelector('input[name="deliveryFee"]:checked');
        const deliveryFee = feeRadio ? parseFloat(feeRadio.value) : 2.00;
        const finalTotalValue = subtotalGeral + deliveryFee;
        const feeLabel = feeRadio.nextElementSibling.textContent.trim();

        // Montagem da Mensagem do Pedido
        let message = `🍝 Olá, Massa Nostra! Meu pedido é o seguinte:\n\n`;
        
        // Adiciona Pratos
        message += `--- ITENS (${cart.length} prato(s)) ---\n`;
        if (cart.length === 0) {
            message += `_Nenhum prato montado._\n`;
        }
        cart.forEach((item, index) => {
            const acompText = item.acompanhamentos.length > 0 ? item.acompanhamentos.join(', ') : 'Nenhum';
            const camarãoText = item.premium ? `\n  Premium: ${item.premium.name} (+ R$ ${item.premium.cost.toFixed(2).replace('.', ',')})` : '';

            message += `\n*PRATO #${index + 1} (${item.size}):*\n`;
            message += `  Massa: ${item.massa}\n`;
            message += `  Molho: ${item.molho}\n`;
            message += `  Queijo: *${item.queijo}* (Incluso)\n`; 
            message += `  Acompanhamentos Comuns: ${acompText}`;
            message += `${camarãoText}\n`;
            message += `  Obs: ${item.obs || 'Nenhuma'}\n`;
            message += `  Valor: R$ ${item.price.toFixed(2).replace('.', ',')}\n`;
        });
        
        // Adiciona Bebidas com Quantidade
        message += `\n--- BEBIDAS (${totalUnidadesBebidas} lata(s)) ---\n`;
        if (bebidas.length > 0) {
            message += `*Latas ${MENU.bebidas.volume} (R$ ${MENU.bebidas.precoUnitario.toFixed(2).replace('.', ',')}/cada):*\n`;
            bebidas.forEach(b => {
                message += `  - ${b.qtd}x ${b.nome}\n`;
            });
            message += `  _Total Bebidas: R$ ${subtotalBebidas.toFixed(2).replace('.', ',')}_\n`;
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
        message += `Pagamento: ${paymentMethod}\n`;
        
        // Adiciona PIX à mensagem se for o método selecionado 
        if (paymentMethod === 'Pix') {
             message += `*Titular PIX:* ${MENU.pixName}\n`; 
             message += `*CHAVE PIX (CPF):* ${MENU.pixKey}\n`;
        }
        
        message += `\nAguardamos a confirmação! Obrigado!`;
        
        const encodedMessage = encodeURIComponent(message);
        const whatsappLink = `https://wa.me/${MENU.whatsappNumber}?text=${encodedMessage}`;

        try {
            window.open(whatsappLink, '_blank');
            showModal('Seu pedido foi enviado com sucesso para o WhatsApp! Clique para confirmar e envie a mensagem.', 'bg-green-500');
            checkoutBtn.disabled = false;
            checkoutBtn.textContent = 'ENVIAR PEDIDO VIA WHATSAPP';
        } catch (error) {
            console.error('Erro ao tentar abrir o WhatsApp:', error);
            showModal('Houve um erro ao tentar abrir o WhatsApp. Verifique sua conexão e tente novamente.', 'bg-red-500');
            checkoutBtn.disabled = false;
            checkoutBtn.textContent = 'ENVIAR PEDIDO VIA WHATSAPP';
        }
    }

    // Inicializa a aplicação
    document.addEventListener('DOMContentLoaded', setupUI);
</script>

</body>
</html>
