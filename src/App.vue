<template>
  <div>
    <header>
      <img src="https://i.pinimg.com/236x/e9/eb/76/e9eb76e6e14467f488e8204dc257ee8b.jpg" alt="Logo ZRRN" class="logo">
      <h1>ZAKY STORE.ID</h1>
    </header>
    <div id="app">
      <div class="user-info">
        <label for="userId">User ID:</label>
        <input type="text" id="userId" v-model="userId" placeholder="Masukkan User ID (server)">
        <label for="username">Nama Pengguna:</label>
        <input type="text" id="username" v-model="username" placeholder="Masukkan Nama Pengguna">
      </div>
      <DiamondItem
        v-for="diamond in diamonds"
        :key="diamond.id"
        :diamond="diamond"
        :userId="userId"
        :username="username"
        @diamondSelected="displayDiamondDetails"
      />
      <Modal
        v-if="selectedDiamond"
        :userId="userId"
        :username="username"
        :selectedDiamond="selectedDiamond"
        @close="closeModal"
      />
    </div>
  </div>
</template>

<script>
import DiamondItem from './components/DiamondItem.vue';
import Modal from './components/Modal.vue';

export default {
  components: {
    DiamondItem,
    Modal
  },
  data() {
    return {
      userId: '',
      username: '',
      diamonds: [
        { id: 1, name: '5 Diamond', price: '1.427', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 2, name: '12 Diamond', price: '3.323', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 3, name: '19 Diamond', price: '5.223', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 4, name: '28 Diamond', price: '7.600', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 5, name: '44 Diamond', price: '11.400', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 6, name: '59 Diamond', price: '15.200', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 7, name: '85 Diamond', price: '21.850', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 8, name: '170 Diamond', price: '43.700', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 9, name: '240 Diamond', price: '61.750', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 10, name: '296 Diamond', price: '76.000', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 11, name: '408 Diamond', price: '104.500', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 12, name: '568 Diamond', price: '142.500', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 13, name: '875 Diamond', price: '218.500', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 14, name: '2010 Diamond', price: '475.000', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' },
        { id: 15, name: '2199 Diamond', price: '541.300', imageUrl: 'https://i.pinimg.com/564x/f6/de/d7/f6ded79ce5658d6cecc8531c4ca2ed7e.jpg' }
      ],
      selectedDiamond: null
    };
  },
  methods: {
    displayDiamondDetails(diamond) {
      this.selectedDiamond = {
        ...diamond,
        userId: this.userId,
        username: this.username
      };
    },
    closeModal() {
      this.selectedDiamond = null;
    }
  }
};
</script>

<style scoped>
.h1 {
  color:white;
}
.user-info {
  margin-bottom: 20px;
  color:white;
}

.user-info label {
  display: block;
  margin-bottom: 5px;
}

.user-info input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-bottom: 10px;
}

.user-info #userId {
  width: 200px;
}

.user-info #username {
  width: 200px;
}

.user-info input::placeholder {
  color: #aaa;
}

.user-info input:focus {
  border-color: #007bff;
  outline: none;
}

.user-info input.error {
  border-color: #dc3545;
}

.error-message {
  color: #dc3545;
  font-size: 12px;
  margin-top: 5px;
}

header {
  background-color: #007bff;
  color: white;
  padding: 20px;
  text-align: center;
  display: flex;
  margin: 0;
  align-items: center;
}

.logo {
  width: 50px;
  margin-right: 10px;
}

header h1 {
  margin: 0;
}
</style>
