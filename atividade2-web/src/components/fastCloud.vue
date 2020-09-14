<template>
  <div class="container">
    <img class="cloud" src="../assets/cloud.jpeg" width="120" height="100" />

    <form class="formulario" action>
      <label>
        Name:
        <input name="name" type="text" id="name" v-model="nome" />
      </label>

      <label>
        E-mail:
        <input type="text" id="email" v-model="email" />
      </label>

      <label>
        Date of birth:
        <input type="date" id="date" v-model="data" />
      </label>

      <div class="checkbox">
        <label id="services">Services:</label>

        <div class="input_check">
          <label for="micro">
            <input
              type="checkbox"
              id="micro"
              name="Processing - 1 micro - $ 1,00 per hour"
              value="1"
              v-model="checado"
            />
            Processing - 1 micro - $ 1,00 per hour
          </label>

          <label for="medium">
            <input
              type="checkbox"
              id="medium"
              name="Processing - 1 medium - $ 2,00 per hour"
              value="2"
              v-model="checado"
            />Processing - 1 medium - $ 2,00 per hour
          </label>

          <label for="large">
            <input
              type="checkbox"
              id="large"
              name="Processing - 1 large - $ 10,00 per hour"
              value="10"
              v-model="checado"
            />Processing - 1 large - $ 10,00 per hour
          </label>
        </div>

        <div class="input_check">
          <label for="gb">
            <input
              type="checkbox"
              id="gb"
              v-model="checado"
              name="Storage - 10 GB HD - $ 0.5 per hour"
              value="0.5"
            />Storage -
            10 GB HD - $ 0,5 per hour
          </label>

          <label for="hd">
            <input
              type="checkbox"
              id="hd"
              v-model="checado"
              name="Storage - 1 TB HD - $ 1,00 per hour"
              value="1.0"
            />Storage - 1
            TB HD - $ 1,00 per hour
          </label>

          <label for="gbssd">
            <input
              type="checkbox"
              id="gbssd"
              name="Storage - 100 GB SSD - $ 5,00 per hour"
              value="5"
              v-model="checado"
            />Storage - 100 GB SSD - $ 5,00 per hour
          </label>
        </div>
      </div>

      <div class="botao">
        <input class="botao_clear" id="clear" type="reset" value="CLEAR" />
        <input class="botao_add" id="add" type="button" value="ADD" @click="botao_add()" />
      </div>
    </form>

    <table class="table">
      <thead class="table-dark">
        <tr>
          <th scope="col">Name</th>
          <th scope="col">E-mail</th>
          <th scope="col">Date of Birth</th>
          <th scope="col">Services</th>
          <th scope="col">Total</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="dado in dados" v-bind:key="dado.nome">
          <td>{{dado.nome}}</td>
          <td>{{dado.email}}</td>
          <td>{{dado.data}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<!--> modal -->

<script>
export default {
  name: "fastCloud",
  data() {
    return {
      nome: "",
      email: "",
      data: "",
      dados: [],
      
    };
  },

  methods: {
    botao_add() {
      var name = document.getElementById("name");
      var email = document.getElementById("email");
      var data_nascimento = document.getElementById("date");

      var check = document.querySelectorAll(".input_check > label > input");

      var servicos_selecionados = "";
      var valor_total = 0;
      for (var i = 0; i < check.length; i++) {
        if (check[i].checked === true) {
          servicos_selecionados += check[i].name + "</br>";
          valor_total += Number(check[i].value);
        }
      }
      valor_total = valor_total.toFixed(2);

      document.querySelector("table").innerHTML +=
        "<tr> <td>" +
        name.value +
        "</td> <td> " +
        email.value +
        "</td> <td>" +
        date.value +
        "</td> <td> " +
        servicos_selecionados +
        "</td> <td>  " +
        " $ " +
        valor_total +
        " per hour " +
        " </td> </tr>";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0px;
  padding: 0px;
}

.container {
  display: flex;
  align-items: center;
  flex-direction: column;
  margin-left: 5%;
}

.cloud {
  margin: 0 auto;
}

.checkbox {
  display: flex;
  flex-direction: row;
}

.checkbox > div {
  display: flex;
  flex-direction: column;
}

label {
  margin: 10px;
}

.input_check > label > input {
  margin-right: 5px;
}

#services {
  margin-right: 70px;
}

.formulario {
  margin-bottom: 15px;
  margin-top: 10px;
  display: flex;
  flex-direction: column;
}

.formulario > label > input {
  margin-left: 50px;
  width: 300px;
  height: 20px;
}
.botao > input {
  width: 110px;
  height: 30px;
  margin: 10px;
  font-size: verdana;
  background-color: #d9d9d9;
  color: #595959;
  border-radius: 5px;
}

.botao {
  text-align: center;
}

#name {
  margin-left: 91px;
}

#email {
  margin-left: 88px;
}
</style>
