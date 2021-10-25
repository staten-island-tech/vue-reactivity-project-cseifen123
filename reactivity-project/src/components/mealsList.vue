<template>
  <div class="item">
    <figure> 
      
        <img :src="mealSelected.itemImg"   @click="$emit(prefList || mealSelected.added ? 'removeMeal':'addMeal',mealSelected.itemID)" 
      :title="description"  :class="{green:!mealSelected.added, red :mealSelected.added }">
      <figcaption :class="{actionGreen:!mealSelected.added, actionRed :mealSelected.added }">{{ mealSelected.itemTitle }} <br> {{description}}</figcaption>
    </figure>
          
  </div>
</template>

<script>
export default {
  props: {
    mealSelected: {
      type: Object,
      required: true
    },
    prefList:{
      type:Boolean,
      required:true
    },
  },
  computed:
  {
    description()
    {
      return( this.prefList || this.mealSelected.added ? 'Click image to Remove from Personal List':'Click image to Add to Personal List');
    }
  }
  
}
</script>
<style  scoped> 
img
{
  max-width:90%;
  min-width:90%;
}

.red 
{
  border: 5px solid red;

}
.green 
{
  border: 5px solid green;

}
.item {
  
  display: flex;
  flex-direction: column;
  flex-basis: 30%;
  
   }
  .actionRed {
    position:static;
    background:red;
    color:white;
    bottom:0;
    margin:auto;
    

  }
  .actionGreen
  {position:static;
  background:green;
  color:yellow;
  bottom:0;
  margin:auto;}
   

</style>