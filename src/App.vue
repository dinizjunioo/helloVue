<template>
  <div id="app">
    <TabNav :tabs="['Home', 'Settings','Comentario']" :selected="selected" @selected="setSelected">
      <Tab :isSelected="selected === 'Home'">
        <h3> TEXTO 1 TEXTO 1</h3>
      </Tab>

      <Tab :isSelected="selected === 'Settings'">
        <item>
          <li> Lista 1 </li>
          <li> Lista 2 </li>
          <li> Lista 3 </li>
          <li> Lista 4 </li>
        </item>
      </Tab>

      <Tab :isSelected="selected === 'Comentario'">
         <Comments/> 
      </Tab>
    </TabNav> 
    <!-- <Comments/> -->
  </div>
</template>

<script>
 import TabNav from './components/TabNav';
 import Tab from './components/Tab';
import Comments from './components/Comments'

export default {
  name: 'App',
  components: {TabNav, Tab,Comments},

   data() {
     return {
       selected: 'Home'
     }
   },

   methods: {
     setSelected(tab){
      this.selected = tab;
     }
   }
}
</script>

<style>

#app{
  font-family: Avenir, Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: aquamarine;
  color:cadetblue;
  margin-top: 60px;
  display: flex; 
  flex-direction: row; 
 
  justify-content: center; 
  /* justify-content-center; */
}
</style>
