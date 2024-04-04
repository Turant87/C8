<template>
  <div>
    <h1> {{ shopTitle }} </h1>
    <div v-for="(phone, key) in phones" :key="key"
    class="card">
      <h3> {{ phone.title + " - " + phone.price + "руб." }} </h3>

      <div> {{ phone.count }} </div>

      <div>
        <button class="btn" v-on:click="minusCount(phone)">-</button>
        <input v-model="phone.count" type="text" class="input">
        <button class="btn" @click="plusCount(phone)">+</button>
      </div>

      <div> {{ itemPrice(phone) }} </div>
    </div>

    <div> Сумма: {{ totalPrice }}</div>
  </div>
</template>

<script>
export default {
  name: "MyShop.vue",
  props: {
    shopTitle: String
  },
  data (){
    return {
      phones: [
        {
          title: 'iPhone 12',
          price: 10000,
          count: 0
        },
        {
          title: 'iPhone 13',
          price: 25000,
          count: 0
        },
        {
          title: 'iPhone 14',
          price: 35000,
          count: 0
        },
        {
          title: 'iPhone 15',
          price: 66000,
          count: 0
        }
      ]
    }
  },
  computed: {
    totalPrice(){
      let sum = 0;
      this.phones.forEach(item => {
        sum += item.count * item.price
      });
      return sum;
    }
  },
  methods: {
    itemPrice(phone){
      return +phone.count !== 0 ? phone.price * phone.count : phone.price;
    },
    plusCount(phone){
      phone.count = +phone.count + 1;
    },
    minusCount(phone){
      phone.count = +phone.count - 1;
    }
  }
}
</script>

<style scoped lang="scss">

.card {
  box-shadow: 0 2px 4px 0 #333;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  margin-bottom: 10px;
}

.btn {
  box-shadow: none;
  border: 1px solid #ccc;
  background: #ffffff;
  height: 30px;
  width: 30px;
  cursor: pointer;

  &:first-child {
    border-radius: 8px 0 0 8px;

    &:hover {
      background: #666;
      color: #fff;
    }
  }

  &:last-child {
    border-radius: 0 8px 8px 0;

    &:hover {
      background: green;
      color: #fff;
    }
  }
}

.input {
  box-sizing: border-box;
  height: 30px;
  border: 1px solid #ccc;
  border-left: 0;
  border-right: 0;
  width: 30px;
  text-align: center;
}

</style>