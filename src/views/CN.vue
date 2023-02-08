<template>
  <div>
    <h1>TVshow</h1>
    <button @click="TVshow()">TVshow</button>
    
  
    <table>
      <thead>
        <th>index</th>
        <th>id</th>
        <th>language</th>
        <th>name</th>
        <th>type</th>
        <th>genres</th>
        <th>runtime</th>
        <th>averageRuntime</th>
        <th>premiered</th>
      </thead>
      <tbody>
        <tr v-for="(value, index) in NNK" :key="index">
            <td>{{ index }}</td>
            <td>{{ value.show.id }}</td>
            <td>{{ value.show.language }}</td>
            <td>{{ value.show.name }}</td>
            <td>{{ value.show.type }}</td>
            <td>{{ value.show.genres }}</td>
            <td>{{ value.show.runtime }}</td>
            <td>{{ value.show.averageRuntime }}</td>
            <td>{{ value.show.premiered }}</td>
            

        </tr>
      </tbody>
    </table>
    </div>
</template>

<script setup >
import axios from"axios";
import { ref } from"vue";

const NNK = ref([]);
const url = ref("http://api.tvmaze.com/search/shows?q=golden%20girls");

function TVshow() {
  axios
    .get(url.value)
    .then((response) => {
      NNK.value = response.data;
    })
    .catch((err) => {
      console.log(err);
    });
}
</script>
<style scope>
    table,thead,tr,{
        text-align: center;
        border: 2px solid black;
    }
    th{
        text-align: center;
        border: 2px solid red; 
        background-color:beige;
    }
    td{
        text-align: center;
        border: 2px solid black;
        background-color:beige;
    }
    h1{
        text-align: center;
        color: hsla(160, 100%, 37%, 1);
        font-weight: bold;
    }
</style>>

