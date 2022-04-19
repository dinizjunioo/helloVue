<template>
    <div class="main">
    <h1>TABELA COM VUE </h1>
        <div class="container">
            <ul class="nav nav-tabs">
                <li v-for="tab in tabs" :key="tab" class="nav-item" >
                    <button type = "button" class="btn btn-outline-primary"  :class="{active: tab === selected}" @click="setTab(tab)">
                        {{ tab }}
                    </button>
                </li>
                
            </ul>
            
            <slot></slot>
        </div>
    </div>
</template>


<script>
export default {
     props:{
      tabs: {
          Type: Array,
          required: true,
      },
      selected:{
          type: String,
          required: true,
      }
    },
     methods:{
        setTab(tab){
            this.$emit('selected', tab);
        }
  }
}
</script>
<style scoped>
.nav-item{
    margin: 10px 10px 10px 10px;
}
.container{
    background-color: aquamarine;
}
.main{
    /* background-color: antiquewhite; */
}
</style>