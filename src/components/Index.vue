<template>
    <div>
        <item v-for="story in stories" v-bind:key="story.id" v-bind:story="story"></item>
    </div>
</template>
<script>
import axios from "axios";
import Item from "./Item.vue"
export default {
  name: "Index",
  components: {
      Item
  },
  data: function () {   
      return {
          stories: []
      }
  },
  mounted: function() {
      axios.get("https://hacker-news.firebaseio.com/v0/topstories.json?print=pretty").then(res => {
          return res.data
      }).then(story_ids => {  
        story_ids.forEach(story_id => {
            return axios.get("https://hacker-news.firebaseio.com/v0/item/"+ story_id +".json?print=pretty").then(res => {
                this.stories.push(res.data)
            })
        });
      })
  }
}
</script>
<style scoped>

</style>
