<template>
  <div>
    <div class="contain">
      <div class="sidebar">
        <div class="add_new">
          <button>+ New Contact</button>
          <form role="search" id="form">
            <input type="search" v-model="search" placeholder="Search..." />
          </form>
        </div>

        <div class="sort_dropdown">
          <label for="sort_contacts">Sort by:</label>
          <select
            name="sort_contacts"
            id="sort_contacts"
            v-model="sort"
            @change="sortDropdown()"
          >
            <option disabled value="">Chosee option</option>
            <option value="name">name</option>
            <option value="age">age</option>
          </select>
        </div>
        <div class="contacts_list">
          <div>
            <ul class="list">
              <li
                v-for="(client, clientObject) in searchClients"
                :key="clientObject"
                @click="showClient(client)"
              >
                <img
                  :src="require(`../assets/${client.image}`)"
                  width="60"
                  height="60"
                  alt
                  class="client_image_small"
                />
                <span id="set">{{ client.name }}</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="client_container">
        <div class="client_name flex">
          <div>
            <p class="large_text">{{ selectedClient.name }}</p>
          </div>
          <div>
            <button class="edit_button">Edit</button>
          </div>
        </div>
        <div class="flex flex_column">
          <div class="client_notes">
            <div class="image">
              <img
                :src="require(`../assets/${selectedClient.image}`)"
                alt
                class=""
              />
            </div>
            <p class="small_text">Notes</p>
            <p class="note_text">{{ selectedClient.note }}</p>
          </div>
          <div class="client_info">
            <div class="gap_small flex">
              <div class="col_medium">
                <p class="small_text">Sex</p>
                <p class="client_data_text">{{ selectedClient.sex }}</p>
              </div>
              <div class="col_small">
                <p class="small_text">Age</p>
                <p class="client_data_text">{{ selectedClient.age }}</p>
              </div>
              <div class="col_large">
                <p class="small_text">Birthday</p>
                <p class="client_data_text">{{ selectedClient.birthday }}</p>
              </div>
            </div>
            <div>
              <div>
                <p class="small_text">Adress</p>
                <p class="client_data_text">{{ selectedClient.adress }}</p>
              </div>
            </div>
            <div class="flex">
              <div class="gap_large">
                <p class="small_text">Home</p>
                <p class="client_data_text">{{ selectedClient.cell }}</p>
              </div>
              <div class="gap_large">
                <p class="small_text">Primary Email</p>
                <p class="client_data_text">{{ selectedClient.email }}</p>
              </div>
            </div>
            <div class="flex">
              <div class="gap_large">
                <p class="small_text">Cell</p>
                <p class="client_data_text">{{ selectedClient.cell }}</p>
              </div>
              <div class="gap_large">
                <p class="small_text">Secondary Email</p>
                <p class="client_data_text">{{ selectedClient.email }}</p>
              </div>
            </div>
            <div>
              <div>
                <p class="small_text">Billing Contact</p>
                <div class="flex">
                  <div class="client_image_small">
                    <img src="../assets/person1.jpg" width="60" alt="" />
                  </div>
                  <div class="billing_name"><p>Eric Koston</p></div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="schedule">
          <p class="client_data_text">Schedule</p>
        </div>
        <div class="lessons_container">
          <div class="lesson lesson_border">
            <div class="flex space_between border_bott padding">
              <div class="lesson_date_text">
                <p>Tueseday 9:00am <span>60 / Weekly</span></p>
              </div>
              <div>
                <select name="Action" id="" class="lesson_select">
                  <option value="action" active>Chose an action</option>
                  <option value="">Action</option>
                  <option value="">Action</option>
                </select>
              </div>
            </div>
            <div class="flex gap_small padding">
              <div class="col_small">
                <p class="small_text">Service</p>
                <p class="client_data_text">Switch Flip 101</p>
              </div>
              <div class="col_small">
                <p class="small_text">Location</p>
                <p class="client_data_text">Fantasy Fa...</p>
              </div>
              <div class="col_small">
                <p class="small_text">Status</p>
                <p class="client_data_text">Paid</p>
              </div>
            </div>
            <div class="warning flex space_between">
              <div class="col_medium warning_text">
                <span>Lesson still needs to be marked</span>
              </div>
              <div class="col_medium space_between flex">
                <button class="btn_attended col_large">Attended</button>
                <button class="btn_missed col_large">Missed</button>
              </div>
            </div>
          </div>

          <div class="lesson">
            <div class="flex space_between border_bott padding">
              <div class="lesson_date_text">
                <p>Tueseday 9:00am <span>60 / Weekly</span></p>
              </div>
              <div>
                <select name="Action" id="" class="lesson_select">
                  <option value="action" active>Chose an action</option>
                  <option value="">Action</option>
                  <option value="">Action</option>
                </select>
              </div>
            </div>
            <div class="flex gap_small padding">
              <div class="col_small">
                <p class="small_text">Service</p>
                <p class="client_data_text">Mega Ramp</p>
              </div>
              <div class="col_small">
                <p class="small_text">Location</p>
                <p class="client_data_text">The Berricks</p>
              </div>
              <div class="col_small">
                <p class="small_text">Service</p>
                <p class="client_data_text">Canceled</p>
              </div>
            </div>
          </div>

          <div class="lesson">
            <div class="flex space_between border_bott padding">
              <div class="lesson_date_text">
                <p>Tueseday 9:00am <span>60 / Weekly</span></p>
              </div>
              <div>
                <select name="Action" id="" class="lesson_select">
                  <option value="action" active>Chose an action</option>
                  <option value="">Action</option>
                  <option value="">Action</option>
                </select>
              </div>
            </div>
            <div class="flex padding">
              <div class="col_small">
                <p class="small_text">Service</p>
                <p class="client_data_text">S.K.A.T.E Sess..</p>
              </div>
              <div class="col_small">
                <p class="small_text">Location</p>
                <p class="client_data_text">The Berricks</p>
              </div>
              <div class="col_small">
                <p class="small_text">Status</p>
                <p class="client_data_text">Paid</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import contacts from "./contactsList";
export default {
  data() {
    return {
      clients: contacts,
      selectedClient: contacts[0],
      search: "",
      sort: "",
    };
  },
  methods: {
    //   displays selected client in the details container
    showClient(client) {
      this.selectedClient = client;
      console.log(this.sort);
    },
    // sort clients by age or name
    sortDropdown: function () {
      if (this.sort === "name") {
        this.clients.sort((a, b) => {
          if (a.name < b.name) {
            return -1;
          } else if (a.name > b.name) {
            return 1;
          } else {
            return 0;
          }
        });
      } else {
        return this.clients.sort((a, b) => a.age - b.age);
      }
    },
  },
  computed: {
    // searches the client list from the form inut
    searchClients() {
      return this.clients.filter((client) => {
        return client.name.toLowerCase().match(this.search.toLowerCase());
      });
    },
  },
};
</script>

<style scoped>
.flex {
  display: flex;
}
.space_between {
  justify-content: space-between;
}

.border_bott {
  border-bottom: 1px solid #aaa;
}

.col_small {
  width: 20%;
}
.col_medium {
  width: 30%;
}
.col_large {
  width: 50%;
}
.gap_large {
  width: 50%;
}

.client_name {
  margin-top: 10px;
}
.edit_button {
  /* height: 20px; */
  padding: 5px 20px;
  margin-top: 20px;
  margin-left: 20px;
  background-color: #f3f3f3;
  border: 1px solid #aaa;
  color: #aaa;
  border-radius: 5px;
}
.billing_name {
  margin-left: 20px;
  margin-top: 20px;
}
.client_image_small {
  border: 1px solid #aaa;
  border-radius: 5px;
}
.lessons_container {
  background-color: #f6f9f8;
  padding-top: 40px;
}
.lesson {
  width: 95%;
  margin: 0 auto 20px auto;
  border: 1px solid #aaa;
  border-radius: 5px;
  border-left: 15px solid #f27a0a;
}

.lesson_border {
  border-left: 15px solid #fec506;
}

.lesson_date_text p {
  margin: 0;
  font-size: 22px;
  font-weight: 700;
  color: #535252;
}

.lesson_date_text p span {
  color: #c9cdd0;
}

.lesson_select {
  padding: 10px 10px;
  width: 250px;
  border-radius: 3px;
  background-color: #e7e7e7;
}

.padding {
  padding: 30px;
}

.image {
  width: 100%;
  margin-bottom: 10px;
  height: 400px;
  overflow: hidden;
}

.image img {
  width: 100%;
  min-height: 300px;
}

.note_text {
  font-weight: 500;
  font-size: 20px;
  text-align: left;
  color: #727272;
  word-spacing: 2px;
  width: 90%;
}

.small_text {
  color: #bbbbbb;
  margin-bottom: 10px;
  font-weight: 500;
  font-size: 18px;
}
.large_text {
  color: #929292;
  font-weight: 500;
  font-size: 50px;
  margin-left: 20px;
  letter-spacing: 2px;
  /* font-weight: bold; */
}
.client_data_text {
  font-weight: 700;
  font-size: 22px;
  margin-top: 5px;
  color: #535252;
}
.client_notes {
  width: 30%;
  margin-left: 20px;
}
.client_info {
  width: 40%;
  margin-left: 20px;
}
.client_container {
  width: 75%;
}

.sidebar {
  width: 25%;
  border-right: 1px solid #cacaca;
}

.contacts_list {
  height: 100%;
  max-height: 120vh;
  overflow: auto;
}

.contain {
  display: flex;
}

.add_new {
  padding: 30px 10px;
  background-color: #fafafa;
}

.add_new button {
  width: 100%;
  background-color: #5cb35b;
  border: 1px solid #a7a7a7;
  border-radius: 2px;
  padding: 10px;
  margin-bottom: 10px;
  cursor: pointer;
  color: #fff;
  font-size: 17px;
  transition: 0.2s ease-in;
}
.add_new button:hover {
  background-color: #fff;
  color: #5cb35b;
}
#form {
  background-color: #fff;
  border: 1px solid #aaa;
  width: 100%;
  height: 44px;
  border-radius: 5px;
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 10px;
}
#form input {
  all: unset;
  font: 16px system-ui;
  color: #000;
  height: 100%;
  width: 80%;
  padding: 6px 10px;
}

#form input::placeholder {
  color: #aaa;
  opacity: 0.7;
}

#form button {
  all: unset;
  cursor: pointer;
  width: 25px;
  height: 44px;
}

#form svg {
  color: #aaa;
  fill: currentColor;
  width: 50px;
  height: 50px;
  padding: 10px;
}
.contacts_container {
  width: 100%;
}

.sort_dropdown {
  border-top: 1px solid #d8d8d8;
  border-bottom: 1px solid #d8d8d8;
  padding: 20px 10px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  background-color: #ebebeb;
}

#sort_contacts {
  width: 70%;
  height: 30px;
  border: 1px solid #d8d8d8;
  outline: none;
  border-radius: 2px;
}

.list {
  list-style-type: none;
  margin: 0;
  padding: 0;
  background-color: #fafafa;
}

.list li {
  padding: 10px;
  background-color: #fafafa;
  border-bottom: 1px solid #d8d8d8;
  cursor: pointer;
  transition: 0.2s ease-in;
}
.list li:hover {
  background-color: #d8d8d8;
}

.list li a {
  color: #000;
  text-decoration: none;
}

.list li img {
  margin-right: 20px;
}

.schedule {
  background-color: #ebebeb;
  height: 60px;
  border-top: 1px solid #cacaca;
  border-bottom: 1px solid #cacaca;
}
.schedule p {
  padding: 10px 30px;
}

.warning {
  width: 95%;
  margin: 0 auto 10px auto;
  background-color: #eed1d3;
  padding: 10px;
  border: 1px solid #d2b0b2;
  border-radius: 5px;
}

.warning_text {
  color: #de4d48;
  padding: 10px;
}

.btn_attended {
  margin-right: 5px;
  background-color: #5cb75c;
  border: none;
  border-radius: 4px;
  color: #fff;
  font-weight: 700;
  transition: 0.2s;
}
.btn_attended:hover {
  background-color: #247724;
}

.btn_missed {
  margin-left: 5px;
  background-color: #de4d48;
  border: none;
  border-radius: 4px;
  color: #fff;
  font-weight: 700;
  transition: 0.2s;
}

.btn_missed:hover {
  background-color: #7c2421;
}
@media only screen and (max-width: 1440px) {
  .image {
    height: 250px;
  }
}
@media only screen and (max-width: 768px) {
  .flex_column {
    flex-direction: column;
  }
  .client_notes {
    width: 80%;
  }
  .client_info {
    width: 80%;
  }
}
</style>