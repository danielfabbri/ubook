<template>
  <section>
    <img class="logo" src="../assets/ic-logo.svg">
    <button class="yellow-theme" @click="this.openEvent" v-if="(total != 0)">+ Criar contato</button>
    <div>
      <input type="text" placeholder="Buscar...">
      <img class="search" src="../assets/ic-search.svg">
    </div>
  </section>
</template>
<script>
export default {
  name: 'NavBar',
  props: {
    total: Number,
  },
  methods: {
    openEvent() {
      this.$emit('modalCreateEvent',true);
    }
  }
}
</script>
<style scoped>
  section {
    height: 2rem;
    margin: 0;
    padding: 1rem;
  }
  section .logo {
    float:left;
    height:32px;
  }
  section .search {
    float:right;
    margin:9px 10px 0 0;
  }
  section button {
    float:left;
    margin:0 30px;
  }
  section div {
    background:#e4e7f4;
    float:right;
    width:calc(100% - 351px);
    border-radius: 4px;
  }
  section input {
    background:#e4e7f4;
    width:calc(100% - 50px);
  }
</style>