<template>    
<v-app id="inspire">
    <v-card class="mx-auto" max-width="344" outlined >
      <v-list-item >
        <v-avatar tile size="80"> <v-img height="100%" :src="data.avatar"></v-img></v-avatar>
        <v-list-item-content>
          <v-list-item-title class="headline mb-1">{{data.first_name}}</v-list-item-title>
          <v-list-item-subtitle>{{data.last_name}}</v-list-item-subtitle>
          <v-list-item-subtitle>{{data.email}}</v-list-item-subtitle>
          <v-list-item-subtitle>{{ads.company}}</v-list-item-subtitle>
          <v-list-item-subtitle>{{ads.url}}</v-list-item-subtitle>
          <v-list-item-subtitle>{{ads.text}}</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
    </v-card>
  </v-app>
</template>
<script>
import axios from 'axios';
export default {
  data:function() { 
      return {
        data: {},
        ads:{}
      }
  },
  mounted() {
    this.asyncData();
  },
  
  methods: {
    async asyncData () {
    let { data} = await axios.get('https://reqres.in/api/users/' + this.$route.params.id)
    this.data = data.data;
    this.ads = data.ad;
   }
  
 } 
}

</script>