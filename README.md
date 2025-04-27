# Validador-de-Bandeiras-de-Cart-es
Validador de Bandeiras de Cartões
function identificarBandeira(numeroCartao) {
    // Remove espaços e traços do número do cartão
    numeroCartao = numeroCartao.replace(/[^0-9]/g, '');
    
    // Expressões regulares para cada bandeira
    const bandeiras = {
        "Visa": /^4\d{12,18}$/,
        "MasterCard": /^5[1-5]\d{14}$|^2[2-7]\d{14}$/,
        "Elo": /^4011|^4312|^4389|^50\d{2}|^62\d{2}|^65\d{2}/,
        "American Express": /^3[47]\d{13}$/,
        "Discover": /^6011\d{12}$|^65\d{14}$|^64[4-9]\d{13}$/,
        "Hipercard": /^6062/
    };
    
    // Verifica qual bandeira corresponde ao número do cartão
    for (const bandeira in bandeiras) {
        if (bandeiras[bandeira].test(numeroCartao)) {
            return bandeira;
        }
    }

    return "Bandeira desconhecida ou número inválido";
}

// Exemplo de uso
const numero = '4111111111111111'; // Insira o número do cartão aqui
const bandeira = identificarBandeira(numero);
console.log(`A bandeira do cartão é: ${bandeira}`);
