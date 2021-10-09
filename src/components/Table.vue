<template>
  <div class="league-table">
    <h1>Premier League Table</h1>
      <table>
        <thead>
          <tr>
            <th>Position</th>
            <th>Club</th>
            <th>Played</th>
            <th>Won</th>
            <th>Draw</th>
            <th>Lost</th>
            <th>GF</th>
            <th>GA</th>
            <th>GD</th>
            <th>Points</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="club in table" v-bind:key="club.team.id">
            <td>{{ club.position }}</td>
            <td>{{ club.team.name }}</td>
            <td>{{ club.playedGames }}</td>
            <td>{{ club.won }}</td>
            <td>{{ club.draw }}</td>
            <td>{{ club.lost }}</td>
            <td>{{ club.goalsFor }}</td>
            <td>{{ club.goalsAgainst }}</td>
            <td>{{ club.goalDifference }}</td>
            <td>{{ club.points }}</td>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Table',
  data() {
    return {
      table: [],
    };
  },
  mounted() {
    this.fetchApi();
  },
  methods: {
    fetchApi() {
      axios.get('https://api.football-data.org/v2/competitions/2021/standings', { headers: { 'X-Auth-Token': '8f6b1a6e1caf4aef81cfa24b45d5ddcd' } })
        .then((response) => {
          console.log(response.data.standings[0].table);
          this.table = response.data.standings[0].table;
          console.log(this.table);
          this.table.forEach((element) => {
            console.log(element.team.name);
          });
        });
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Heebo:wght@100;200;300;400;500;600;700;800;900&display=swap');
  h1{
    text-align: center;
    color: #37003c;
    display: block;
    margin-top: 40px;
  }
  table {
    border-collapse: collapse;
    text-align: center;
  }
  table th:nth-child(1), th:nth-child(3), th:nth-child(4), th:nth-child(5), th:nth-child(6){
    width: 5%;
  }
  table th:nth-child(2){
    width: 35%;
  }
  table th:nth-child(7), th:nth-child(8), th:nth-child(9), th:nth-child(10){
    width: 10%;
  }
  thead {
    height: 5vh;
    font-size: 15px;
  }
  thead tr th {
    padding: 6px 20px;
  }
  tbody tr td{
    font-size: 14px;
     padding: 6px 20px;
    border-bottom: 1px solid #444444;
  }
  tbody tr:nth-child(1) td:nth-child(1), tr:nth-child(2) td:nth-child(1),
   tr:nth-child(3) td:nth-child(1), tr:nth-child(4) td:nth-child(1){
    background-color: #77D970;
  }
  tbody tr:nth-child(5) td:nth-child(1){
    background-color: #38A3A5;
  }
  tbody tr:nth-child(18) td:nth-child(1), tr:nth-child(19) td:nth-child(1),
  tr:nth-child(20) td:nth-child(1){
    background-color: #D57E7E;
  }
  tbody tr td:nth-child(2){
    text-align: start;
  }
  tbody tr td:nth-child(10){
    font-weight: 900;
  }
  thead tr th:nth-child(2){
    text-align: start;
  }
  @media (max-width: 480px) {
    h1{
      font-size: 22px;
    }
    thead {
      font-size: 9px;
    }
    thead tr th {
      padding: 2px 2px;
    }
    tbody tr td{
      font-size: 8px;
      padding: 2px 2px;
    }
    @media (max-width: 930px){
      h1{
        font-size: 25px;
      }
      .league-table{
        width: 100%;
      }
    }
}
</style>
