<template>
  <div>
        <h1>Animals</h1>
        <table>
            <thead>
                <th>Type</th>
                <th>Name</th>
                <th>Date of Birth</th>
                <th></th>
                <th></th>                
            </thead>
            <tbody>
                <tr v-for="(animal, key) in animals" :key="key">
                    <td>{{ animal.type }}</td>
                    <td>{{ animal.name }}</td>
                    <td>{{ animal.dateOfBirth ? animal.dateOfBirth : "Unknown"  }}</td>
                    <button @click="removeAnimal(animal)">Remove</button>
                    <button @click="moveToTop(animal)">Move to top</button>
                </tr>
            </tbody>
        </table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data(){
      return {
          animals: [
              {type: 'monkey', name: 'Mihajlo', dateOfBirth: '01/01/2010'},
              {type: 'lion', name: 'Milan', dateOfBirth: '01/02/2011'},
              {type: 'snake', name: 'Damir', dateOfBirth: '02/01/2012'},
              {type: 'tiger', name: 'Maja', dateOfBirth: '03/02/2013'},
              {type: 'elephant', name: 'Marko', dateOfBirth: ''}
              
          ],

      }
  },
  methods: {
      removeAnimal(animal){
          let indexOfAnimal = this.animals.indexOf(animal);
          this.animals.splice(indexOfAnimal, 1);
      },
    moveToTop(animal){
        let indexOfAnimal = this.animals.indexOf(animal);
        this.animals.splice(indexOfAnimal, 1);
        this.animals.unshift(animal); 
        
        
    }
     
  }

}
</script>


