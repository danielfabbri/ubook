<template>
    <section class="overlay">
      <div class="modal">
        <p>Editar contato</p>
        <hr>
        <p class="subtitle">Nome</p>
        <input type="text" v-model="this.nameInput">
        <p class="subtitle">Email</p>
        <input type="text" v-model="this.emailInput">
        <p class="subtitle">Telefone</p>
        <input type="text" class="phone_input" v-model="this.phoneInput">
        <hr class="last-hr">
        <button class="red-theme" @click="this.editContactEvent">Salvar</button>
        <button class="white-theme" @click="this.closeEvent">Cancelar</button>
        <div class="obj"></div>
      </div>
    </section>
</template>
<script>
const localContact = [];
export default {
  name: 'ModalContactEdit',
  props: ['localContact','index'],
  data: () => {
    return {
        nameInput: localContact.name,
        emailInput: localContact.email,
        phoneInput: localContact.phone,
    }
  },
  methods: {
    closeEvent() {
      this.$emit('modalEditEvent',false);
    },
    editContactEvent() {
      this.$emit('editContactEvent',{
        name: this.nameInput,
        email: this.emailInput,
        phone: this.phoneInput,
        index: this.index,
      });
      this.closeEvent();
    }
  },
  mounted() {
    this.nameInput = this.localContact.name;
    this.emailInput = this.localContact.email;
    this.phoneInput = this.localContact.phone;
  }
}
</script>
<style scoped>
 
</style>