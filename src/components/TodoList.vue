<script setup>
import {ref, onMounted} from 'vue'

    const current_task = ref()
    const todos = ref(["asdasda","asdsadas","asdsadas"])
    


    const addtodo = () =>{
        if(current_task.value.trim() !== ''){
        todos.value.push(current_task.value)
        current_task.value = ''
        }
    }

    const deletetodo = (event) =>{
       todos.value.splice(event,1)
    }


    onMounted(() => {
    console.log(`the component is now mounted.`)
    })

</script>

<template>
    <div class="container">
        <div class="insert">
            <input type="text" @keyup.enter="addtodo()" v-model="current_task">
            <button @click="addtodo">Add</button>   
        </div> 
        <ul>
            <li v-for="(todo, index) in todos" :key="todo"> 
                <p>
                    {{todo}}
                </p>
                
                <button class="btn-action delete" @click="deletetodo(index)">X</button>
            </li>
        </ul>
    </div>
</template>


<style scoped>

.container{
   width: 100%;
    max-width: 480px;
    min-width: 320px;
}
.insert{
    padding: 1.25rem;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
    background-color: rgb(63, 63, 63);
}
ul{ 
    width: 100%;
    list-style-type: none;
    margin: 0;
    padding: 0;
}
li{
    margin: 10px auto;
    display: flex;
    justify-content:space-between;
    align-items: center;
    width: fill;
    padding: 0.8rem 1rem;
    background-color: rgb(63, 63, 63);
    list-style-type: none;
    text-decoration: none;
}
.actions{
    display: flex;
    gap: 10px;

}
.btn-action{
    width: 40px;
    height: 40px;
}
.complete{
    background-color: green;
}
.delete{
    background-color: red;
}
input{
    padding: 0.8rem 1rem;
    background-color: rgb(51, 51, 51);
    border:solid rgb(59, 59, 59) 1px;
}
button {
    height: 40px;
    width: fill;  
    font-size: 1em;
    font-weight: bold;
    color: white;
    border: none;
    text-align: center;
    cursor: pointer;
    background-color: #2f31ac;

}
</style>