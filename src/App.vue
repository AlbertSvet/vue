
<template>
    <input type="text" placeholder="Имя" v-model= "userName">
    <input type="password" placeholder="Пароль" v-model= "userPass">
    <input type="email" placeholder="Емаил" v-model= "userEmail">
    <button type="button" @click="sendData()">Отправить</button>
    <div v-if="users.length === 0">
      Нет пользователей
    </div>
    <div className="block">
      <User v-for="(el, index) in users" 
      :key="index"
      :user="el" 
      :index="index" 
      :deletUser="deletUser" 
      className="user"/>
    </div>
      <p>{{error}}</p>
</template>


<script>
// Импортируем компонент
import User from './components/User.vue'

  export default {
    components: {
      User
    },
    data () {
      return {
        users: [],
        userName: '',
        userPass: '',
        userEmail: '',
        error: ''
      }
    }, 
    methods: {
      sendData(){
        if(this.userName !== '' && this.userPass !== '' && this.userEmail !== ''){
            this.users.push({
              user:'Имя: ' + this.userName ,
              pass:'Пароль: ' + this.userPass,
              email:'Емаил: ' + this.userEmail,
            })
            this.userName = '';
            this.userPass = '';
            this.userEmail = '';
            this.error = ''
        }else{
            this.error = 'Заполните все поля'
        }
       
      },
      deletUser(index){
        this.users.splice(index,1);
      }
    }
  
  }
</script>

<style scoped>
  .block{
    display: grid;
   
    grid-template-columns: repeat(3,1fr);
    grid-gap: 20px;
  }
  .user{
    background-color:aquamarine;
    max-width: 100%;
    margin-top: 30px;
    border-radius: 10px;
    padding: 20px 10px;
    color:cornflowerblue;
    font-size: 20px;
    font-weight: 600;
    border: 1px solid rgb(99, 83, 61);
  }
</style>

/* 
  В Vue.js methods: - это зарезервированное свойство в объекте компонента. Это не просто название свойства объекта, а специальное свойство, используемое для определения методов компонента Vue.js.
  Когда вы определяете методы компонента Vue.js, вы должны помещать их в свойство methods. Это свойство предназначено для хранения определений методов, которые могут быть вызваны из шаблона, других методов компонента или из другого кода вашего приложения.
 */
 /*   
  В методе мы создаем функцию( еще один метод) затем передаем ее в обработчик события который записывается как  
  @click= функция. 
   v-on:click=
  https://v3.ru.vuejs.org/ru/guide/events.html#%D0%BC%D0%BE%D0%B4%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%82%D0%BE%D1%80-exact
  */

  /* 
      Vue также предоставляет директиву v-model, которая реализует двустороннюю привязку между элементом формы и состоянием приложения:
      @input="insertData($event.target.value) 
       methods: {
        insertData(vel){
          this.userName = vel
        }
    }      => v-model = userName - просто надо добавить в тег 

      https://v3.ru.vuejs.org/ru/guide/introduction.html#%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0-%D1%81-%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D1%81%D0%BA%D0%B8%D0%BC-%D0%B2%D0%B2%D0%BE%D0%B4%D0%BE%D0%BC

    ==============================================
     директиву v-for можно использовать для отображения списка элементов, используя данные из массива. Цикл 
   */

   /* 
    v-if
    
     https://v3.ru.vuejs.org/ru/guide/introduction.html#%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0-%D1%81-%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D1%81%D0%BA%D0%B8%D0%BC-%D0%B2%D0%B2%D0%BE%D0%B4%D0%BE%D0%BC
    */