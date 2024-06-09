<template>
    <div>
        <button className="delet" @click="deletUser(index)">Удалить</button>
        <p>
          {{user.user}}</p>
        <p>
          {{user.pass}}</p>
        <p>
          {{user.email}}</p>
      </div>
</template>

<script>
    export default {
        props: {
            user:{
                type: Object,
                required: true
            },
            index:{
                type: Number,
                required: true
            },
            deletUser:{
                type: Function,
                required: true
            }
        }
    }
</script>

<style scoped>
   
    .delet{
        background-color: black;
        color: white;
        font-size: 16px;
        font-weight: 600;
        border-radius: 10px;
        padding: 10px 15px;
        margin-left: auto;
        display: block;
        cursor: pointer;
    }
</style>