<template>
  <div class="app">
    <header>
      <h1>Catálogo de Produtos</h1>
      <span class="carrinho">🛒 Itens no carrinho: {{ totalCarrinho }}</span>
    </header>

    <main>
      <input
        v-model="busca"
        type="text"
        placeholder="Buscar produto..."
        class="busca"
      />

      <div v-if="produtosFiltrados.length === 0" class="vazio">
        Nenhum produto encontrado.
      </div>

      <div class="grid">
        <ProductCard
          v-for="produto in produtosFiltrados"
          :key="produto.id"
          :nome="produto.nome"
          :preco="produto.preco"
          :imagem="produto.imagem"
          @adicionar="totalCarrinho++"
        />
      </div>
    </main>
  </div>
</template>

<script>
import ProductCard from './components/ProductCard.vue'

export default {
  name: 'App',
  components: { ProductCard },
  data() {
    return {
      busca: '',
      totalCarrinho: 0,
      produtos: [
        { id: 1, nome: 'Tênis Esportivo', preco: 199.90, imagem: 'https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=400&h=300&fit=crop' },
        { id: 2, nome: 'Mochila Urbana', preco: 149.90, imagem: 'https://images.unsplash.com/photo-1553062407-98eeb64c6a62?w=400&h=300&fit=crop' },
        { id: 3, nome: 'Camiseta Básica', preco: 59.90, imagem: 'https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=400&h=300&fit=crop' },
        { id: 4, nome: 'Óculos de Sol', preco: 89.90, imagem: 'https://images.unsplash.com/photo-1572635196237-14b3f281503f?w=400&h=300&fit=crop' },
        { id: 5, nome: 'Relógio Clássico', preco: 299.90, imagem: 'https://images.unsplash.com/photo-1523275335684-37898b6baf30?w=400&h=300&fit=crop' },
        { id: 6, nome: 'Boné Casual', preco: 49.90, imagem: 'https://images.unsplash.com/photo-1588850561407-ed78c282e89b?w=400&h=300&fit=crop' }
      ]
    }
  },
  computed: {
    produtosFiltrados() {
      return this.produtos.filter(p =>
        p.nome.toLowerCase().includes(this.busca.toLowerCase())
      )
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, sans-serif;
  background: #f0f4f8;
  color: #333;
}

.app {
  max-width: 1100px;
  margin: 0 auto;
  padding: 20px;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #2a7c3f;
  color: #fff;
  padding: 16px 24px;
  border-radius: 10px;
  margin-bottom: 24px;
}

header h1 {
  font-size: 1.5rem;
}

.carrinho {
  font-size: 1rem;
  background: #fff;
  color: #2a7c3f;
  padding: 6px 14px;
  border-radius: 20px;
  font-weight: bold;
}

.busca {
  width: 100%;
  padding: 12px 16px;
  border: 2px solid #ccc;
  border-radius: 8px;
  font-size: 1rem;
  margin-bottom: 24px;
  outline: none;
  transition: border 0.2s;
}

.busca:focus {
  border-color: #2a7c3f;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 20px;
}

.vazio {
  text-align: center;
  color: #888;
  padding: 40px;
  font-size: 1.1rem;
}
</style>
