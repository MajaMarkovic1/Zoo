<template>
  <div>
        <h1>Animals</h1>
        <table>
            <thead>
                <th>Type</th>
                <th>Name</th>
                <th>Date of Birth</th>
            </thead>
            <tbody>
                <tr v-for="(animal, key) in animals" :key="key">
                    <td>{{ animal.type }}</td>
                    <td>{{ animal.name }}</td>
                    <td>{{ animal.dateOfBirth }}</td>
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
              {type: 'elephant', name: 'Marko', dateOfBirth: '04/02/2009'}
              
          ]
      }
  }

}
</script>

