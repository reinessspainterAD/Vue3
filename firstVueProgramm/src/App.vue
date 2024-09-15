<template>
  <input type="text" v-model="userName" placeholder="Имя">
  <input type="password" v-model="userPassword" placeholder="Пароль">
  <input type="email" v-model="userEmail" placeholder="Email">
  <p className="error">{{ error }}</p>
  <button @click="sendData()">Отправить</button>

  <!-- Условие на отображение(v-if), если оно выполняется, то блок показывается на странице, в обратном случае - нет -->
  <div v-if="users.length == 0">
    У нас нет пользователей
  </div>
  <!-- Также есть функции else-if и else -->
  <div v-else-if="users.length == 1">
    В массиве один элемент
  </div>

  <div v-else>
    В массиве больше одного элемента
  </div>

  <!-- Перебор массива users через цикл(v-for) -->
  <div v-for="(i, index) in users" :key="index" className="user">
    <h3>{{ i.name }}</h3>
    <p>{{ i.email }} - <b>{{ i.password }}</b></p>
  </div>
</template>

<script>
  export default{
    data(){
      return{
        users: [],
        error: '',
        userName: '',
        userPassword: '',
        userEmail: ''
      }
    },
    methods:{
      sendData(){
        if(this.userName == ''){
          this.error = 'Имя не введено';
          return;
        }else if(this.userPassword == ''){
          this.error = 'Пароль не введён';
          return;
        }else if(this.userEmail == ''){
          this.error = 'Почта не введена';
          return;
        }else{
            this.users.push({
            name: this.userName,
            password: this.userPassword,
            email: this.userEmail
          })
          this.error = ''
        }

        

        
      }
    }

  }
</script>

<style scoped>
 
</style>
