<template>
  <v-app id="list-sample">
    <v-flex sm6 offset-sm3>
      <v-list two-line
              v-for="(listItem, index) in listData"
              :key="index">
        <v-list-tile>
          <v-list-tile-content>
            <v-list-tile-title class="text--primary">
              {{ listItem.subject }}
            </v-list-tile-title>
            <v-list-tile-sub-title>
              {{ listItem.desc }}
            </v-list-tile-sub-title>
          </v-list-tile-content>
 
          <v-list-tile-action>
            <v-icon ripple
                    @click="">
              edit
            </v-icon>
            <v-icon ripple
                    @click="">
              delete
            </v-icon>
          </v-list-tile-action>
        </v-list-tile>
        <v-divider></v-divider>
      </v-list>
  </v-app>
</template>


<script>
  export default {
    data() {
      return {
        listData: []
      }
    },
    created() {
      this.axios.get('http://localhost:8080/server/listTest.json')
        .then((response) => {
          this.listData = response.data;
          console.log(this.listData);
        });
    }
  }
</script>
