<template>
    <div class="container">
        <input @input="onInput" v-model="textSearch" type="text" placeholder="Rechercher">
    </div>
</template>

<script>
    export default {
        name:'SearchBar',
        data(){
            return {
                textSearch: '',
            }
        },
        methods: {
            onInput(e){
                this.textSearch = e.target.value;
                this.$emit('termChange', this.textSearch);
            }
        },
    }
</script>

<style scoped>
    input {
        width:75%;
    }
</style>