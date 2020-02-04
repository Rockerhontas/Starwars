<template>
  <div class="container">

   <div>
      <button v-for="(entry, index) in filterList"
        :item="entry"
        :key="index"
        @click="filter = entry; active = index;"
        :class="{ active: entry == filter }">
        {{ entry }}
      </button>
    </div>

    <ul class="namelist">
     <li v-for="(entry, index) in people"
        v-if="entry[fkey] === filter || filter === 'All'"
        :item="entry"
        :key="index"
        class="namen">

        <h5>{{ entry.name }}</h5>
     
        Gender: <strong>{{ entry.gender }}</strong> |
        Birth year: <strong>{{ entry.birth_year }}</strong>
     </li>
    </ul>

  </div>
  
</template>

<script>
  export default {
    name: "Charas",
   data: function() {
      return {
           fkey: "gender",
    filterList: ["male", "female", "n\/a", "All"],
    filter: "All",
        people: []
      }
    },
  created: function() {
    axios
      .get("https://swapi.co/api/people/?format=json")
      .then(res => {
        this.people = res.data.results;
      });
  },
}

</script>

<style scoped>

button {
  font-family: Montserrat;
  font-size: 1.0em;
  background: #8b7e51;
  color: #0c0c0c;
  border: 0px solid #ccc;
  padding: 10px 15px 10px 15px;
  margin: 5px;
  margin-bottom: 15px;
}

button.active {
  background: #0c0c0c;
  color: #ccc;
  border: 2px solid #8b7e51;
}

.namelist {
  list-style-type: none;
  flex-wrap: wrap;
  justify-content: center;
  flex-direction: row;
  padding: 0;
  margin: 0;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
}

.namen {
  padding: 10px;
  margin: 10px 10px 10px 10px;
  background: #0c0c0c;
  color: #989898;
  border: 2px solid #8b7e51;
  border-radius: 2px;
  width: 25%;
  text-align: center;
}

h5 {
  color: #ccc;
  font-size: 1.1rem;
  text-align: center;
  letter-spacing: 1px;
  text-transform: uppercase;
  font-weight: bold;
  margin: 0;
}

.gender {
  display: center;
  text-align: center;
  font-size: 0.9rem;
}

</style>