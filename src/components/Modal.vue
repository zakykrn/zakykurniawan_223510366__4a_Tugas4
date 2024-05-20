<template>
    <div>
      <div class="modal-overlay" @click="closeModal"></div>
      <div class="modal-content">
        <div class="modal-header">
          <h2>Detail Pembelian</h2>
          <span class="close" @click="closeModal">&times;</span>
        </div>
        <div class="modal-body">
          <div class="diamond-details">
            <p>Pilihan: {{ selectedDiamond.name }}</p>
            <p>Harga:  {{ formatCurrency(selectedDiamond.price) }}</p>
            <p>Jumlah: {{ selectedDiamond.quantity }}</p>
            <p>Total Harga:  {{ formatCurrency(selectedDiamond.totalPrice) }}</p>
          </div>
          <div class="user-details">
            <p>User ID: {{ userId }}</p>
            <p>Nama Pengguna: {{ username }}</p>
          </div>
          <div class="payment-method">
            <h3>Metode Pembayaran:</h3>
            <label>
              <img src="https://i.pinimg.com/564x/04/02/1b/04021bde951b5aad0aa0bebfb9d8ee01.jpg" class="payment-logo" />
              <input type="radio" v-model="selectedPayment" value="DANA" /> DANA
            </label>
            <label>
              <img src="https://i.pinimg.com/564x/fe/ce/b2/feceb2ca508603b06c2f7ba18a5d018d.jpg" class="payment-logo" />
              <input type="radio" v-model="selectedPayment" value="GoPay" /> GoPay
            </label>
            <label>
              <img src="https://i.pinimg.com/564x/3e/b1/15/3eb1151e7df8559a417f904ebb5ddb0c.jpg" class="payment-logo" />
              <input type="radio" v-model="selectedPayment" value="Telkomsel" /> Telkomsel
            </label>
            <label>
              <img src="https://i.pinimg.com/564x/98/88/27/988827ba70ba45ec5fb9c36423d8d09e.jpg" class="payment-logo" />
              <input type="radio" v-model="selectedPayment" value="QRIS" /> QRIS
            </label>
          </div>
          <div class="payment-summary">
            <p>Metode Pembayaran Terpilih: {{ selectedPayment }}</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      userId: String,
      username: String,
      selectedDiamond: Object
    },
    data() {
      return {
        selectedPayment: ''
      };
    },
    methods: {
      closeModal() {
        this.$emit('close');
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
    max-height: 80%; 
    overflow-y: auto; 
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
  
  .diamond-details {
    border-bottom: 1px solid #ccc;
    padding-bottom: 10px;
    margin-bottom: 10px;
  }
  
  .user-details {
    margin-bottom: 10px;
  }
  
  .payment-method {
    margin-top: 20px;
  }
  
  .payment-method label {
    display: flex; 
    align-items: center; 
    margin-bottom: 10px;
  }
  
  .payment-logo {
    width: 50px;
    height: 40px;
    margin-right: 10px;
  }
  
  .payment-summary {
    margin-top: 10px;
    padding: 10px;
    background-color: #f9f9f9;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  </style>
  