<template>
<v-container>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field
      v-model="name"
      :counter="10"
      :rules="nameRules"
      label="Name"
      required
    ></v-text-field>

    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-row>
        <v-col cols="4">
            <v-text-field label="CEP" v-model="cep" @blur="getCEP" :rules="cepRules"></v-text-field>
        </v-col>
        <v-col cols="4">
            <v-text-field label="Cidade" v-model="cidade"></v-text-field>
        </v-col>
        <v-col cols="4">
            <v-text-field label="Estado" v-model="estado"></v-text-field>
        </v-col>
    </v-row>

    <v-select
      v-model="select"
      :items="items"
      :rules="[v => !!v || 'Item is required']"
      label="Item"
      required
    ></v-select>

    <v-checkbox
      v-model="checkbox"
      :rules="[v => !!v || 'You must agree to continue!']"
      label="Do you agree?"
      required
    ></v-checkbox>

    <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4"
      @click="validate"
    >
      Validate
    </v-btn>

    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      Reset Form
    </v-btn>

    <v-btn
      color="warning"
      @click="resetValidation"
    >
      Reset Validation
    </v-btn>
  </v-form>
</v-container>
</template>

<script>
  export default {
    data: () => ({
      cep: "",
      cidade: "",
      estado: "",
      cepRules: [
          v => !!v || 'CEP é obrigatório',
          v => (v && v.lentgh <= 8 ) || "CEP precisa ter 8 caracteres"
      ],
      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4',
      ],
      checkbox: false,
    }), 

    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },

      async getCEP() {
        if (this.cep.lenght == 8) {
          try {
            const response = await fetch(`http://viacep.com.br/ws/${this.cep}/json/`);

            const json = await response.json();
            console.log(json)
            this.cidade = json.localidade
            this.estado = json.uf
          } catch (error) {
              console.log("CEP inválido", error)
          }
        } else {
            console.log('CEP inválido')
        }
      }
    },
  }
</script>