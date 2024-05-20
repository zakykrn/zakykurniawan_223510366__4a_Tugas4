<template>
  <div class="diamond-item-horizontal">
    <img :src="diamond.imageUrl" alt="Diamond Image" @click="toggleEnlarge" />
    <div class="diamond-info">
      <p>{{ diamond.name }} <br> {{ formatCurrency(diamond.price) }}</p>
      <p>Masukkan Jumlah Pembelian</p>
      <input type="number" v-model.number="quantity" min="1" />
      <button @click="selectDiamond">Pilih</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    diamond: {
      type: Object,
      required: true
    },
    userId: String,
    username: String
  },
  data() {
    return {
      quantity: 1,
      isModalVisible: false,
      selectedDiamond: null
    };
  },
  methods: {
    selectDiamond() {
      const quantity = parseInt(this.quantity);
      if (isNaN(quantity) || quantity <= 0) {
        alert('Silakan masukkan jumlah pembelian yang valid.');
        return;
      }
      const totalPrice = parseFloat(this.diamond.price) * quantity;

      this.selectedDiamond = {
        ...this.diamond,
        userId: this.userId,
        username: this.username,
        quantity: quantity,
        totalPrice: totalPrice // simpan sebagai number untuk perhitungan lebih lanjut
      };

      this.$emit('diamondSelected', this.selectedDiamond);
    },
    toggleEnlarge() {
      // Implementasi untuk toggleEnlarge jika diperlukan
    },
    closeModal() {
      this.isModalVisible = false;
    },
    formatCurrency(value) {
      return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR' }).format(value);
    }
  }
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 999;
}

.modal-content {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  padding: 20px;
  border-radius: 5px;
  z-index: 1000;
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.modal-header h2 {
  margin: 0;
}

.close {
  cursor: pointer;
}

.modal-body {
  padding-top: 20px;
}

.diamond-item-horizontal {
  display: inline-block;
  align-items: center;
  border: 1px solid #ddd;
  border-radius: 4px;
  background-color: #fff;
  margin: 10px;
  padding: 10px;
}

.diamond-item-horizontal img {
  width: 100px;
  height: 100px;
  cursor: pointer;
}

.diamond-info {
  margin-left: 10px;
  margin-top: 50px;
  flex-grow: 1;
}

button {
  background-color: #007bff; 
  color: white;
  border: none;
  padding: 5px 10px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  cursor: pointer;
  border-radius: 4px;
}

button:hover {
  background-color: #0056b3; 
}
</style>
