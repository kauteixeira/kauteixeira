const axios = require('axios');

// 1. Buscar um produto
const buscarProduto = async (produto) => {
    try {
        const response = await axios.get(`https://www.advantageonlineshopping.com/catalog/api/v1/products/search`, {
            params: { search: produto }
        });
        console.log('Status Code:', response.status);
        console.log('Produtos encontrados:', response.data);
    } catch (error) {
        console.error('Erro ao buscar produto:', error.response.status);
    }
};

// 2. Atualizar a imagem de um produto
const atualizarImagemProduto = async (userId, imageSource, color) => {
    try {
        const response = await axios.put(`https://www.advantageonlineshopping.com/catalog/api/v1/product/image/${userId}/${imageSource}/${color}`);
        console.log('Status Code:', response.status);
        console.log('Produto atualizado com a nova imagem:', response.data);
    } catch (error) {
        console.error('Erro ao atualizar imagem do produto:', error.response.status);
    }
};

// Exemplo de uso
buscarProduto('Speakers');
atualizarImagemProduto('12345', 'new-image-url.png', 'red');
