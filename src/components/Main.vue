<template>
    <div>

        <div class="contain">
            <div class="sidebar">
                <div class="add_new">
                    <button >+ New Contact</button>
                    <form role="search" id="form">
                        <input type="search"  v-model="search"
                        placeholder="Search...">
                    </form>
                </div>
  
                <div class="sort_dropdown">
                    <label for="sort_contacts">Sort by:</label>
                    <select name="sort_contacts" id="sort_contacts" v-model="sort" @change="sortDropdown()">
                        <option disabled value="">Chosee option</option>
                        <option value="name">name</option>
                        <option  value="age">age</option>
                    </select>
                </div>
                <div class="contacts_list">

                    <div>
                        <ul class="list">
                            <li   v-for="client in filteredClients" :key="client"   @click="showClient(client) ">
                                <img :src="require(`../assets/${client.image}`)" width="60" height="60" alt class="icon" />                                
                                <span id="set">{{client.name}}</span>  
                            </li>
                        </ul>
                    </div>
                </div>        

            </div>
            <div class="client_container">
                <div class="client_name">
                    <p class="large_text">{{selectedClient.name}}</p>
                </div>
                <div class="flex flex_column">
                    <div class="client_notes">
                        <div class="image">
                            <img :src="require(`../assets/${selectedClient.image}`)"  alt class="icon" />
                        </div>
                        <p class="small_text">Notes</p>
                        <p class="note_text">{{ selectedClient.note}}</p>
                    </div>
                    <div class="client_info">
                        <div class="gap_small flex">
                            <div class="col_sex">
                                <p class="small_text"> Sex</p>
                                <p class="client_data_text">{{ selectedClient.sex}}</p>
                            </div>
                            <div class="col_age">
                                <p class="small_text">Age</p>
                                <p class="client_data_text">{{ selectedClient.age}}</p>
                            </div>
                            <div class="col_bday">
                                <p class="small_text">Birthday</p>
                                <p class="client_data_text">{{ selectedClient.birthday}}</p>
                            </div>
                        </div>
                        <div>
                            <div>
                                <p class="small_text">Adress</p>
                                <p class="client_data_text">{{ selectedClient.adress}}</p>
                            </div>
                        </div>
                        <div class="flex">
                            <div class=" gap_large">
                                <p class="small_text">Home</p>
                                <p class="client_data_text">{{ selectedClient.cell}}</p>
                            </div>
                            <div class=" gap_large">
                                <p class="small_text">Primary Email</p>
                                <p class="client_data_text">{{ selectedClient.email}}</p>
                            </div>    
                        </div>
                        <div class="flex">
                            <div class=" gap_large">
                                <p class="small_text">Cell</p>
                                <p class="client_data_text">{{ selectedClient.cell}}</p>
                            </div>
                            <div class=" gap_large">
                                <p class="small_text">Secondary Email</p>
                                <p class="client_data_text">{{ selectedClient.email}}</p>
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
                            <div class="lesson_date_text"><p>Tueseday 9:00am <span>60 / Weekly</span></p></div>
                            <div>
                                <select name="Action" id="" class="lesson_select">
                                    <option value="action" active>Chose an action</option>
                                    <option value="">Action</option>
                                    <option value="">Action</option>
                                </select>
                            </div>
                        </div>
                        <div class="flex gap_small padding">
                            <div>
                                <p class="small_text">Service</p>
                                <p class="client_data_text">Switch Flip 101</p>
                            </div>
                            <div>
                                <p class="small_text">Location</p>
                                <p class="client_data_text">Fantasy Fa...</p>
                            </div>
                            <div>
                                <p class="small_text">Status</p>
                                <p class="client_data_text">Paid</p>
                            </div>
                        </div>
                    </div>

                    <div class="lesson">
                        <div class="flex space_between border_bott padding">
                            <div class="lesson_date_text"><p>Tueseday 9:00am <span>60 / Weekly</span></p></div>
                            <div>
                                <select name="Action" id="" class="lesson_select">
                                    <option value="action" active>Chose an action</option>
                                    <option value="">Action</option>
                                    <option value="">Action</option>
                                </select>
                            </div>
                        </div>
                        <div class="flex gap_small padding">
                            <div>
                                <p class="small_text">Service</p>
                                <p class="client_data_text">Mega Ramp</p>
                            </div>
                            <div>
                                <p class="small_text">Location</p>
                                <p class="client_data_text">The Berricks</p>
                            </div>
                            <div>
                                <p class="small_text">Service</p>
                                <p class="client_data_text">Canceled</p>
                            </div>
                        </div>
                    </div>

                    <div class="lesson">
                        <div class="flex space_between border_bott padding">
                            <div class="lesson_date_text"><p>Tueseday 9:00am    <span>60 / Weekly</span></p></div>
                            <div>
                                <select name="Action" id="" class="lesson_select">
                                    <option value="action" active>Chose an action</option>
                                    <option value="">Action</option>
                                    <option value="">Action</option>
                                </select>
                            </div>
                        </div>
                        <div class="flex gap_small padding">
                            <div>
                                <p class="small_text">Service</p>
                                <p class="client_data_text">S.K.A.T.E Sess..</p>
                            </div>
                            <div>
                                <p class="small_text">Service</p>
                                <p class="client_data_text">The Berricks</p>
                            </div>
                            <div>
                                <p class="small_text">Service</p>
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
    import contacts from './contactsList'
    export default {
        data () {
            return {
                // showClient: false,
                clients: contacts,
                selectedClient: contacts[0],
                search: '',
                sort: '',                
            }
        },
        methods: {
            showClient(client) {
                this.selectedClient = client;
                console.log(this.sort)
            },
            sortDropdown: function() {
                if(this.sort === 'name'){
                    this.clients.sort((a,b) => {
                        if(a.name < b.name) { return -1; }
                        if(a.name > b.name) { return 1; }
                        return 0;
                    })
                }
                else {
                  return  this.clients.sort((a, b)=> a.age - b.age)
                }
            }
        },
        computed: {

            filteredClients () {
                return this.clients.filter((client) => {
                    return client.name.toLowerCase().match(this.search.toLowerCase())
                })
            },

        }
    }   
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

.col_age { width: 20%; }
.col_sex { width: 30%; }
.col_bday { width: 50%; }
.gap_large { width: 50%; }

.lesson {
    width: 90%;
    margin: 20px auto;
    border: 1px solid #aaa;
    border-radius: 5px;
    border-left: 15px solid #f27a0a;
}

.lesson_border {
    border-left: 15px solid #fec506;
}

.lesson_date_text p{
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
.client_info{
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
    max-height: 100vh;
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
  .contacts_container{
      /* background-color: red; */
      width: 100%;
  }

  .sort_dropdown {
    /* margin: 0 10px; */
    border-top: 1px solid #d8d8d8;
    border-bottom: 1px solid #d8d8d8;
    padding: 20px  10px;
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

.list li a{
    color: #000;
    text-decoration: none;
}

.list li img {
    margin-right: 20px;
}

.schedule {
    background-color: #ebebeb;
    height: 60px;
    padding: 10px;
    border-top: 1px solid #cacaca;
    border-bottom: 1px solid #cacaca;
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


.col {
    -webkit-box-flex: 0 !important;
    -ms-flex: 0 0 50% !important;
     flex: 0 0 50% !important;
}
</style>