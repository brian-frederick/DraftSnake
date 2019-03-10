<template>
  <div>
    <div v-if="onTheClock">
      <input v-model="draftPick"/>
      <button v-on:click="submitPick">Make your pick</button>
    </div>
    <ul>
      <li v-for="item in draftPicks" :key="item.Id">{{ item.Id }} {{item.User}} {{item.Pick}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'DraftPickForm',
  methods: {
    submitPick: function(){
      this.draftPicks.push({
        User: 'user', 
        Id: this.rank,
        Pick: this.draftPick
      });
      this.draftPick = '';
      this.rank++;
      this.onTheClock = false;
    }
  },
  data: function() {
    return {
      onTheClock: true,
      rank: 1,
      draftPick: '',
      draftPicks: []
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
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
