<template>
    <section class="overlay">
      <div class="modal">
        <p>Criar novo contato</p>
        <hr>
        <p class="subtitle">Nome</p>
        <input type="text" placeholder="23" v-model="this.nameInput" v-on:keyup="enableSubmit()">
        <p class="subtitle">Email</p>
        <input type="text" placeholder="23" v-model="this.emailInput" v-on:keyup="enableSubmit()">
        <p class="subtitle">Telefone</p>
        <input type="text" class="phone_input" placeholder="23" v-model="this.phoneInput" v-on:keyup="enableSubmit()">
        <hr class="last-hr">
        <button class="red-theme" v-bind:class="{ disabled: disabled }" @click="this.addContactEvent">Salvar</button>
        <button class="white-theme" @click="this.closeEvent">Cancelar</button>
        <div class="obj"></div>
      </div>
    </section>
</template>
<script>
const nameInput = '';
const emailInput = '';
const phoneInput = '';
const disabled = true;
export default {
  name: 'ModalContactCreate',
  props: ['index'],
  data: () => {
    return {
      nameInput: nameInput,
      emailInput: emailInput,
      phoneInput: phoneInput,
      disabled: disabled
    }
  },
  methods: {
    closeEvent() {
      this.$emit('modalCreateEvent',false);
    },
    addContactEvent() {
      this.$emit('addContactEvent',{
        name: this.nameInput,
        email: this.emailInput,
        phone: this.phoneInput,
      });
      this.$emit('modalCreateEvent',false);
    },
    enableSubmit() {
      this.disabled = false;
    }
  }
}
</script>
<style scoped>
  .disabled {
    background: #ffbfbb;;
    pointer-events:none;
  }
</style>