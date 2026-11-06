<template>
  <div class="card">
    <img :src="imagem" :alt="nome" />
    <div class="card-info">
      <h3>{{ nome }}</h3>
      <p class="preco">R$ {{ preco.toFixed(2) }}</p>
      <button @click="$emit('adicionar')">Adicionar ao Carrinho</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    nome: String,
    preco: Number,
    imagem: String
  },
  emits: ['adicionar']
}
</script>

<style scoped>
.card {
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.card img {
  width: 100%;
  height: 180px;
  object-fit: cover;
}

.card-info {
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.card-info h3 {
  margin: 0;
  font-size: 1rem;
  color: #333;
}

.preco {
  margin: 0;
  font-size: 1.1rem;
  font-weight: bold;
  color: #2a7c3f;
}

button {
  background: #2a7c3f;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 0.9rem;
  transition: background 0.2s;
}

button:hover {
  background: #1f5e30;
}
</style>
