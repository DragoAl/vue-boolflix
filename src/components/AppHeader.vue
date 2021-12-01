<template>
    <header>
        <input type="text" v-model.trim="inputText">
        <button @click="$emit('clickBtn', inputText)">Cerca</button>
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
    height: 80px;
}

</style>