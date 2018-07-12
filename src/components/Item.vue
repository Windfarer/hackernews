<template>
    <section>
        <a :href="story.url"><h2>{{story.title}}</h2></a>
        <p>time: {{story.time}}</p>
        <p>{{story.text}}</p>
    </section>
</template>
<script>
import { axios } from "axios";
export default {
  name: "Item",
  props: ["story"],
  data: function () {
      return {}
  }
}
</script>
<style scoped>

</style>
