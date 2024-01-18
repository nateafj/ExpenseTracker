<template>
  <h3>History</h3>
        <ul id="list" class="list">
          <li v-for="transaction in transactions" v-bind:key="transaction.id" :class="transaction.amount < 0 ? 'minus' : 'plus'"  >
          {{ transaction.text }}
            <span>${{ transaction.amount }}</span>
            <button @click="deleteTransaction(transaction.id)" class="delete-btn">x</button>
          </li>
        </ul>
        </template>
        <script setup>
        import { defineProps } from 'vue';


const emit = defineEmits(['transactionDeleted']);

        const props = defineProps({
          transactions: {
            type: Array,
            required: true,
          },
        });

        const deleteTransaction = (id) => {
          emit('transactionDeleted',id);
        };
      </script>



<!-- OPTIONAL API EXAMPLE -->
<!-- <template>
<h3>History</h3>
      <ul id="list" class="list">
        <li v-for="transaction in transactions" v-bind:key="transaction.id" :class="transaction.amount < 0 ? 'minus' : 'plus'"  >
        {{ transaction.text }}
          <span>${{ transaction.amount }}</span><button class="delete-btn">x</button>
        </li>
      </ul>
      </template>
      <script>
      export default{
        data() {
          return{
            transactions: [
              {id: 1, text: 'iPhone', amount: -1500.99},
              {id: 2, text: 'Airpod Pro 2', amount: -200.99},
              {id: 3, text: 'Sold Macbook Pro', amount: +275.00}

            ]
          }
        }
      }
    </script> -->