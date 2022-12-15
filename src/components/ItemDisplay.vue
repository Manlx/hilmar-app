<template>
  <div class="ListItem">
    <p>{{InData.Name}}</p>
    <p>{{InData.Jarowa}}</p>
    <p>{{InData.WinCasaPartners}}</p>
    <p>{{InData.WinCasaDiscount}}</p>
  </div>
</template>

<script>
export default {
    props:["InData"],
    mounted:function(){
        // console.log("Gaming"+this.InData)
    }
}
</script>

<style scoped>
.ListItem{
  display: flex;
  /* justify-content: space-between; */
}

p{
  width: 15%;
  margin: 0.1% 2.5%;
  padding: 0% 2.5%;
  border-radius: 20px;
}
p:nth-child(even){
  background-color: #898989;
}
p:nth-child(odd){
  background-color: #565656;
}
</style>