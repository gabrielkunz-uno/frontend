<template>
  <v-container>
    <v-row>
      <v-col>
        <v-text-field
          v-model='descricao'
          outlined
          placeholder='Informe o TODO'
          label='Descrição do TODO'
          @keypress="handleKeyPress"
        ></v-text-field>
      </v-col>
      <v-col>
        <v-btn @click='cadastrar' class='mx-2' fab dark color='indigo'>
          <v-icon dark> mdi-plus </v-icon>
        </v-btn>
      </v-col>
    </v-row>
    <v-container>
      <v-row
        v-for='(todo, i) in todos'
        :key='i'
      >
        <h3>{{ todo }}</h3>
        <v-btn
          @click='excluir(i)'
          x-small
          style='margin-left: 10px; margin-top: 5px;'
        >
          Excluir
        </v-btn>
      </v-row>
    </v-container>
  </v-container>
</template>

<script>
export default {
  name: 'TodosPage',

  data () {
    return {
      todos: [],
      descricao: ''
    }
  },

  methods: {
    cadastrar () {
      this.todos.push(this.descricao)
      this.descricao = ''
    },

    excluir (index) {
      if (confirm('Deseja deletar esse TODO?')) {
        this.todos.splice(index, 1)
      }
    },

    handleKeyPress (evento) {
      console.log(evento)
      if (evento.keyCode === 13) {
        this.cadastrar()
      }
    }
  }
}
</script>
