<template>
    <MainComponent/>
</template>
<script>
import MainComponent from './components/MainComponent.vue';
export default {
  name: 'App',
  components: {
    MainComponent
  }
}
</script>
<style>
/* Reset */
body {
  margin: 0;
  background:#f8f9fd;
  font-family: Roboto;
}
input {
  height:20px;
  padding:8px;
  border:none;
  border-radius: 4px;
}

/* Buttons */
button {
  padding:10px 20px;
  border-radius:25px;
  border:none;
  cursor:pointer;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16), 0 0 0 0.5px var(--black-8), inset 0 0 0 0.5px var(--black-8), 0 2px 4px 0.5px var(--black-8-16);
}
.yellow-theme {
  background:#dbff90;
  color:#fa7268;
}
.red-theme {
  color:white;
  background:#fa7268;
}
.white-theme {
  color:#fa7268;
  background:white;
}

/* Modals */
.overlay {
    position:fixed;
    top:0;
    right:0;
    bottom:0;
    left:0;
    background:rgba(0,0,0,.5);
  }
  .modal {
    background:white;
    max-width:27rem;
    margin:150px auto;
    border-radius:16px;
  }
  .modal p {
    padding:15px;
    margin:0;
    color: #2a2d3b;
  }
  .modal hr {
    display: block;
    height: 1px;
    border: 0;
    border-top: 1px solid #c0c3d2;
    margin: 0;
    padding: 0;
  }
    .modal .last-hr {  
    margin-top:30px;
  }
  .modal input {
    margin: 0 15px;
    padding:8px;
    width:calc(100% - 50px);
    background:white;
    border:1px solid #c0c3d2;
  }
  .modal button {
    float: right;
    margin:15px 15px 15px 0;
  }
  .subtitle {
    font-size: 0.875rem;
    padding-bottom:5px;
  }
  .obj {
    clear: both;
  }

  /* Forms */
  .phone_input {
    width:8rem!important;
  }
</style>
