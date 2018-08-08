<template>
  <div>
        <h1>Animals</h1>
        <form @submit.prevent>
            <label>Type: </label>
            <input v-model="newAnimal.type" placeholder="Type" type="text"><br>
            <label>Name: </label>
            <input v-model="newAnimal.name" placeholder="Name" type="text"><br>
            <label>Date of Birth: </label>
            <input v-model="newAnimal.dateOfBirth" placeholder="dateOfBirth" type="text"><br>
            <label>Sector: </label>
            <select v-model="newAnimal.sector">
                <option v-for="(sector, key) in sectors" :key="key" v-bind:value='sector'>{{sector.name}}</option><br>
            </select><br>
            <button @click="addAnimal">Add animal</button>
        </form>
        <table>
            <thead>
                <th>Type</th>
                <th>Name</th>
                <th>Date of Birth</th>
                <th>Sector name</th>
                <th>Sector space</th>                
                               
            </thead>
            <tbody>
                <tr v-for="(animal, key) in animals" :key="key" v-bind:class="{ greenRow: animal.background}">
                    <td>{{ animal.type }}</td>
                    <td>{{ animal.name }}</td>
                    <td>{{ animal.dateOfBirth ? animal.dateOfBirth : "Unknown"  }}</td>
                    <td>{{ animal.sector.name }}</td>
                    <td>{{ animal.sector.space }}</td>
                    <td><button @click="removeAnimal(animal)">Remove</button></td>
                    <td><button @click="moveToTop(animal)">Move to top</button></td>
                    <td><button @click="toggleBackground(animal)">Toggle background</button></td>
                </tr>
            </tbody>
        </table>
        
        <table>
            <thead>   
                <th>Sector name</th>              
                <th></th>   
            </thead>
            <tbody>
                <tr v-for="(sector, key) in sectors" :key="key">
                    <td>{{ sector.name }}</td>
                    <button @click="seeAnimalList(sector)">See Animal List</button>    
                </tr>
            </tbody>
        </table>
  </div>
</template>

<script>

const sectors = [
    {name: 'memos', space: 'cage'},
    {name: 'reptiles', space: 'cage'},
    {name: 'fish', space: 'water'}
    
]

export default {
  name: 'AnimalList',
  data(){
      return {
          animals: [
              {type: 'bear', name: 'Mihajlo', dateOfBirth: '01/01/2010', sector: sectors[0], background: true},
              {type: 'lion', name: 'Milan', dateOfBirth: '01/02/2011', sector: sectors[0], background: false},
              {type: 'snake', name: 'Damir', dateOfBirth: '02/01/2012', sector: sectors[1], background: true},
              {type: 'tiger', name: 'Maja', dateOfBirth: '03/02/2013', sector: sectors[0], background: false},
              {type: 'shark', name: 'Marko', dateOfBirth: '', sector: sectors[2]}
              
          ],
          newAnimal: {},
          sectors: sectors

      }
  },
  methods: {
    removeAnimal(animal){
        let indexOfAnimal = this.animals.indexOf(animal);
        this.animals.splice(indexOfAnimal, 1);
    },

    moveToTop(animal){
        this.removeAnimal(animal);
        this.animals.unshift(animal);  
    },

    addAnimal(){
        this.animals.push(this.newAnimal);
        this.newAnimal = {};
    },

    seeAnimalList(sector){
        let animalList = [];
        this.animals.forEach(function(animal){
            if (sector === animal.sector){
                animalList.push(`${animal.type} ${animal.name}`);
            }
            }
        )
        alert(animalList);
    }, 

    toggleBackground(animal){
        if (animal.background){
            animal.background = false;
        } else {
            animal.background = true;
        }
         
    }
  }

}
</script>

<style>
label, input, select {
    margin-top: 0.5rem;
}

table {
    border-collapse: separate;
    margin-top: 1rem; 
}

table, th, td {
    border: 1px solid black;
}
.greenRow {
    background-color: rgb(64, 230, 64);
}
</style>


