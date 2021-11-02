<template>
  <div >
    <button @click="getMeals(true)"> My Meals List </button>
    <searchBox 
      v-model="searchKey"
      placeholder="Search Ingredients"
      @keydown.enter="getMeals(false)"
    />
    <div class="list" v-if="meals.length">
			<mealsList
				v-for="meal in meals"
				:key="meal.idMeal"
				:mealSelected="meal"
        :prefList="prefList"
        @removeMeal="removeMeal"
        @addMeal="addMeal"
			/>
		</div>
		<p v-else>
			Nothing left in the list. Add a new ingredient in the input above.
		</p>
  </div>
</template>

<script>

import searchBox from './searchBox.vue'
import mealsList from './mealsList.vue'
class item {
  constructor(itemID, itemTitle, itemImg, added) {
    this.itemID = itemID;
    this.itemTitle = itemTitle;
    this.added=added;
    this.itemImg = itemImg; 

  }
}

export default {
  name: 'MealsSelection',
  components:{searchBox, mealsList},
  data () 
  { 
    return {
      meals: [],  
      searchKey :'',
      favList:[],
      prefList:false    
    }   
  },
  methods:  {
    async getMeals(choice) {
      
     let searchParams=this.searchKey.trim();
      console.log("search key is " + searchParams);
  // GET request using fetch with async/await
  this.prefList =choice;
  if (choice)
     this.meals=this.favList;
  else 
  try {
    const response = await fetch(`https://www.themealdb.com/api/json/v1/1/filter.php?i=${searchParams}`);
   //response = await fetch(`www.themealdb.com/api/json/v1/1/categories.php`);
    const data = await response.json();
    let found;
    this.meals = [];
    data.meals.forEach(meal=>
    {
    found=(this.favList.findIndex(mealID => {
				return mealID.itemID == meal.idMeal
			}) == -1? false:true);

        this.meals.push(new item(meal.idMeal,meal.strMeal,meal.strMealThumb,found)); 
      
    })
         
    } catch (error) {
    console.log(error);
    alert("Sorry! It seems like something went wrong.");
  }
  },
  addMeal(mealToAdd) {
     
      
     let newItemIndex = this.meals.findIndex(mealID => {
				return mealID.itemID == mealToAdd
			});
      this.meals[newItemIndex].added=true;
      let newItem = this.meals[newItemIndex];

         
			this.favList.push(newItem);
      
     
	},
  removeMeal(mealToRemove) {
			this.favList = this.favList.filter(mealID => {
				return mealID.itemID !== mealToRemove
			})
      this.getMeals(this.prefList);
      
     
	}
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
 
a {
  color: #42b983;
}
.list
{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  
}

</style>
