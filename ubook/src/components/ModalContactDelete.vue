<template>
    <section class="overlay">
      <div class="modal">
        <p>Excluir contato</p>
        <hr>
        <p>Deseja realmente excluir o contato?</p>
        <hr class="last-hr">
        <button class="red-theme" @click="this.deleteContactEvent">Excluir</button>
        <button class="white-theme" @click="this.closeEvent">Cancelar</button>
        <div class="obj"></div>
      </div>
    </section>
</template>
<script>
const nameInput = '';
const emailInput = '';
const phoneInput = '';
export default {
  name: 'ModalContactCreate',
  props: ['index'],
  data: () => {
    return {
      nameInput: nameInput,
      emailInput: emailInput,
      phoneInput: phoneInput
    }
  },
  methods: {
    closeEvent() {
      this.$emit('modalDeleteEvent',false);
    },
    addContactEvent() {
      this.$emit('addContactEvent',{
        name: this.nameInput,
        email: this.emailInput,
        phone: this.phoneInput,
      });
      this.closeEvent();
    },
    deleteContactEvent() {
      this.$emit('deleteContactEvent',{ contactIndex: this.index });
      this.closeEvent();
    }
  }
}
</script>
<style scoped>
 
</style>