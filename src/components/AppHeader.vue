<template>
    <header>
        <h1>BOOLFLIX</h1>
        <div>
            <input type="text" v-model.trim="inputText">
            <button @click="$emit('clickBtn', inputText)">Cerca</button>
        </div>
        
    </header>
</template>

<script>

export default {
    name:'AppHeader',

    data() {
        return {
            inputText: '' 
        }
    }
}
</script>

<style scoped lang="scss">
header {
    display: flex;
    height: 80px;
    background-color: #000000;
    justify-content: space-between;
    align-items: center;
    
    h1 {
        color: red;
        margin: 0 20px;
    }

    div {
        margin: 0 20px;
        
        input {
            margin-right: 10px;
        }
        
        button {
            background-color: red;
            border: 1px solid red;
            height: 20px;
            width: 80px;
            color: black;
            font-weight: bold;
            
        }
    }
}

</style>