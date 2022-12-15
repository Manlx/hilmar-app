<template>
  <div class="backBlock">
    <item-display class="titles" v-for="(item,index) in [this.TitleObj]" :key="index" :InData="item" />
    <item-display class="info" v-for="(item,index) in this.DisplayData" :key="index" :InData="item" />
    <!-- <ItemDisplay v-for="(item,index) in this.DisplayData" :key="index" :InData="this.DisplayData" /> -->
    <!-- {{this.DisplayData}} -->
  </div>
</template>

<script>
import ItemDisplay from './ItemDisplay.vue'
// import ItemDisplay from './components/ItemDisplay.vue';
export default {
  components: { ItemDisplay },
    data:function(){
        return {

        }
    },
    props:["DisplayData","TitleObj"],
    mounted:function(){
        // console.log(this.DisplayData)
    }
}
</script>

<style scoped>
    .backBlock{
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        /* align-items: ; */
        /* height: 40vh; */
        width: 90vw;
        background-color: #000055;
        margin: auto;
        padding: 6vh;
        border-radius: 20px;
    }
    .titles{
      font-size: 1.5rem;
    }
    .info{
      font-size: 1.2rem;
    }
</style>
