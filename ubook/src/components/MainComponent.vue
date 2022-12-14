<template>
  <NavBar 
    v-bind:total="this.contactList.length"
    @modalCreateEvent="showModalCreate = $event"
  />
  <section id="empty-box" v-show="contactList.length == 0">
    <img src="../assets/ic-book.svg">
    <p>Nenhum contato foi criado ainda.</p>
    <button class="yellow-theme" @click="this.openModalCreate">+ Criar modal</button>
  </section>
  <section id="filled-box" v-show="contactList.length > 0">
    <table>
      <thead>
        <th></th>
        <th>Contatos</th>
        <th>Email</th>
        <th>phone</th>
        <th></th>
      </thead>
      <tbody>
        <tr v-for="(contact, index) in contactList.sort((a, b) => (a.name > b.name) ? 1 : -1)" :key="index" :class="{'active':contact.justCreated}">
          <td><div class="name-initial" :style="{'background':contact.color}">{{(contact.name).substring(0, 1)}}</div></td>
          <td>{{contact.name}}</td>
          <td>{{contact.email}}</td>
          <td>{{contact.phone}}</td>
          <td>
            <div class="row-options">
              <img class="row-icon" src="../assets/ic-edit.svg" @click="this.openModalEdit(index)">
              <img class="row-icon" src="../assets/ic-delete.svg" @click="this.openModalDelete(index)">
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </section>
  <ModalContactCreate
    :index="this.currentContact"
    v-if="showModalCreate"
    @modalCreateEvent="showModalCreate = $event"
    @addContactEvent="this.addContact($event.name, $event.email, $event.phone)"
  />
  <ModalContactEdit
    v-if="showModalEdit"
    :index="this.currentContact"
    :localContact="this.contactList[this.currentContact]"
    @modalEditEvent="showModalEdit = $event"
    @editContactEvent="this.editContact($event.name, $event.email, $event.phone, $event.index)"
  />
  <ModalContactDelete
    v-if="showModalDelete"
    :index="this.currentContact"
    @modalDeleteEvent="showModalDelete = $event"
    @deleteContactEvent="removeContact($event.contactIndex)"
  />

</template>
<script>
import NavBar from './NavBar.vue';
import ModalContactCreate from './ModalContactCreate.vue';
import ModalContactEdit from './ModalContactEdit.vue';
import ModalContactDelete from './ModalContactDelete.vue';

const showModalCreate = false;
const showModalEdit = false;
const showModalDelete = false;
const currentContact = 0;
const contactList = [];

export default {
  name: 'MainComponent',
  components: {
    NavBar,
    ModalContactCreate,
    ModalContactEdit,
    ModalContactDelete,
  },
  data: () => {
    return {
      contactList: contactList,
      showModalCreate: showModalCreate,
      showModalEdit: showModalEdit,
      showModalDelete: showModalDelete,
      currentContact: currentContact,
    }
  },
  methods: {
    addContact(name,email,phone) {
      let color = "#"+Math.floor(Math.random()*16777215).toString(16);
      this.contactList.push({
        color: color,
        name: name,
        email: email,
        phone: phone,
        justCreated: true,
      });
      setTimeout(() => {
        this.contactList.sort((a, b) => (a.name > b.name) ? 1 : -1);
        let position = this.contactList.map(e => e.name).indexOf(name);
        this.contactList[position].justCreated = false;
      } , 10000);
    },
    editContact(name,email,phone,index) {
      this.contactList[index]['name'] = name;
      this.contactList[index]['email'] = email;
      this.contactList[index]['phone'] = phone;
      this.contactList[index]['index'] = index;
    },
    openModalCreate() {
      this.showModalCreate = true;
    },
    openModalEdit(contactIndex) {
      this.showModalEdit = true;
      this.currentContact = contactIndex;
    },
    openModalDelete(contactIndex) {
      this.showModalDelete = true;
      this.currentContact = contactIndex;
    },
    removeContact(index) {
      this.contactList.splice(index,1);
    }

  }
}
</script>
<style scoped>
.active {
  background: #fff3f2;
}
/* Table */
section {
  padding:15px;
}
#empty-box {
  padding-top:10rem;
  text-align:center;
}
#empty-box p {
  margin:20px 0 30px;
}
#filled-box {
  display:block;
}
table {
  width:100%;
  background:white;
  border: solid 1px #e1e1e1;
  border-radius:4px;
  border-collapse: collapse; 
}
th {
  text-align:left;
  padding:20px 10px 15px;
  color:#9198af;
  font-weight: normal;
  font-size: 0.813rem;
}
tr {
  border-top: solid 1px #e1e1e1;
  font-size: 0.875rem;
  color:#2a2d3b;
}
tr:hover {
  background: #fff3f2;
  cursor:pointer;
}
td {
  padding:8px;
  text-align:left;
}
td:nth-child(1) {  
  width:0px;
  padding-right:5px;
}
.name-initial {
  width:1.5rem;
  height:1.4rem;
  border-radius:50%;
  text-align:center;
  color:white;
  font-size:1rem;
  padding-top:.1rem;
  text-transform: uppercase;
}
.row-icon {
  cursor:pointer;
  margin:12px 20px 5px;
}
.row-options {
  text-align:right;
}
</style>