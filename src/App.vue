<template>
  <div class="bigBod">
    <display-list-block :DisplayData="this.Craftsman" :TitleObj="this.TitleObj"/>
    <data-filter @SortFunction="this.SortFunc" />
  </div>
  
</template>

<script>
import $ from 'jquery'
import DisplayListBlock from './components/DisplayListBlock.vue';
import DataFilter from './components/dataFilter.vue';
export default {
  name: 'App',
  components: {
    DisplayListBlock,
    DataFilter
  },
  data:function(){
    return {
      Craftsman:{},
      TitleObj:{Name : `Name`, Jarowa: 'Jarowa', WinCasaPartners: `WinCasaPartners`, WinCasaDiscount: `WinCasaDiscount`}
    }
  },
  methods:{
    getData:function(){
      let self = this;
      $.getJSON("/data.json",
        function (data) {
          // console.log(data)
          self.Craftsman = data.Craftsman
        }
      );
    },
    SortFunc:function(SortMeth,Priorty,Group){
      SortMeth(this.Craftsman,Priorty,Group)
    }
  },
  created:function(){
    this.getData();
  }
}
</script>

<style scoped>
  .bigBod{
    margin: auto;
  }
</style>