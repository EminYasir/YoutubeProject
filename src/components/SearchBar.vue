<template>
  <div>
    <form class="searchForm" @submit.prevent="submitForm">
        <input class="searchInput" type="text" v-model="searchInput"/>
        <button class="searchBtn" type="submit">Ara</button>
    </form>
  </div>
</template>

<script>
export default {
    name: 'SearchBar',
    emits: ['searchInput'],
    components: {
    
    },
    data(){
        return {
            searchInput: ''
        }
    },
    methods: {
        submitForm(){
            this.$emit('searchInput', this.searchInput)
            this.searchInput = ''
        }
    }
}

</script>

<style scoped>
.searchForm{
    display: flex;
    margin: 20px 0px;
}
.searchInput{
    width: 85%;
    padding: 8px;
    margin-right: 20px;
    border-radius: 20px;
}
.searchBtn{
    width: 15%;
    border-radius: 20px;
    border: none;
    background: green;
    color: white;
    font-size: 18px;
    cursor: pointer;
}
</style>