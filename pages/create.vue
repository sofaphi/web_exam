<template>
    <div>
        <form 
            accept-charset="UTF-8"
            v-on:submit.prevent="onSubmit()"
            method="POST"
        >
            <div class="form-line" v-for="(field, propertyName, index) in orderForm.fields" :key="index">
                <label> {{field.title}}
                    <input v-model="departure_address" v-if="propertyName === 'departure_address'" placeholder="Введите значение">
                    <input v-model="destination_address" v-if="propertyName === 'destination_address'" placeholder="Введите значение">
                    <input v-model="weight" v-if="propertyName === 'weight'" placeholder="Введите значение">
                    <input v-model="volume" v-if="propertyName === 'volume'" placeholder="Введите значение">
                    <select v-model="type" v-if="propertyName === 'type'">
                        <option v-for="(value, valueKey) in field.values" :key="valueKey">{{value}}</option>
                    </select>
                    <select v-model="departure_city" v-if="propertyName === 'departure_city'">
                        <option v-for="(value, valueKey) in field.values" :key="valueKey">{{value}}</option>
                    </select>
                    <select v-model="destination_city" v-if="propertyName === 'destination_city'">
                        <option v-for="(value, valueKey) in field.values" :key="valueKey">{{value}}</option>
                    </select>
                </label>
            </div>
            <button class="submit-btn" type="submit">Отправить</button>
        </form>
    </div>
</template>

<style scoped>
    .submit-btn {
        background: #fefefe;
        padding: 10px;
        color: #000;
        border-radius: 10px;
    }

    select {
        background: #fff;
        padding: 5px;
        width: 100%;
        border-radius: 10px;
    }

    .form-line {
        margin-bottom: 15px
    }

    input {
        background: #fff;
        color: #000;
        width: 100%;
        padding: 10px;
        border-radius: 10px;
    }

    form {
        max-width: 500px;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: stretch;
    }
</style>

<script>
export default {
  async fetch({store}) {
    await store.dispatch('orderForm/fetch')
  },
  computed: {
    orderForm() {
      return this.$store.getters['orderForm/orderForm']
    }
  },
  data() {
      return {
        type: '',
        departure_city: '',
        departure_address: '',
        destination_city: '',
        destination_address: '',
        weight: '',
        volume: ''
    }
  },
  methods: {
      async onSubmit() {
        const data = {
            type: this.type,
            departure_city: this.departure_city,
            departure_address: this.departure_address,
            destination_city: this.destination_city,
            destination_address: this.destination_address,
            weight: this.weight,
            volume: this.volume
        }  
        if (
            data.type === '' ||
            data.departure_city === '' ||
            data.departure_address === '' ||
            data.destination_city === '' ||
            data.destination_address === '' ||
            data.weight === '' ||
            data.volume === '' 
        ) {
            alert('Заполните все поля формы')
        } else {
            await this.$store.dispatch('orderForm/postForm', data)
            await this.$store.dispatch('refresh')
        }
      }
  }
}
</script>