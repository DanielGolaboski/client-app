<template>
    <div>

        <div class="header">
            <div>
                <h3>TakeLessons</h3>
            </div>
            
            
            <div>
                <select name="cars" id="cars">
                    <option value="volvo">Alphabetical</option>
                    <option value="saab">By age</option>
                    <option value="mercedes">Mercedes</option>
                    <option value="audi">Audi</option>
                </select> 
            </div>     
        </div>

        <div class="nav-bar">
            <div>
                <b-tabs content-class="mt-3" >
                    <b-tab title="DASHBOARD"><p>I'm the first tab</p></b-tab>
                    <b-tab title="CALENDAR"><p>I'm the second tab</p></b-tab>
                    <b-tab title="CLIENTS" active><p>I'm the tab with the very, very long title</p></b-tab>
                    <b-tab title="FINANCES"><p>I'm a disabled tab!</p></b-tab>
                </b-tabs>
            </div>
        </div>


        <div class="contain">
            <div class="sidebar">
                <div class="add_new">
                    <button>+ New Contact</button>
                    <form role="search" id="form">
                        <input type="search"  v-model="search"
                        placeholder="Search...">
                    </form>
                </div>
  
                <div class="sort_dropdown">
                    <label for="sort_contacts">Sort by:</label>
                    <select name="sort_contacts" id="sort_contacts" v-model="sort">
                        <option @click="sortName()" value="name">name</option>
                        <option @click="sortAge()" value="age">age</option>
                    </select>
                </div>
                <div class="contacts_list">

                    <div>
                        <ul class="list">
                            <li   v-for="client in filteredClients" :key="client"   @click="showClient(client) ">
                                <img :src="require(`../assets/${client.image}`)" width="40" height="40" alt class="icon" />                                
                                <a id="set" href="#">{{client.name}}</a>   
                            </li>
                        </ul>
                    </div>
                </div>        

            </div>
            <div class="client_info">
                <div class="client_name">
                    <p>{{selectedClient.name}}</p>
                </div>
                <div class="flex">
                    <div class="client_notes" style="width: 30%;">
                        <p>{{selectedClient.name}}</p>
                        <img :src="require(`../assets/${selectedClient.image}`)"  alt class="icon" />
                        <p>Notes</p>
                        <p>{{ selectedClient.note}}</p>
                        <p>{{ selectedClient.note}}</p>
                    </div>
                    <div class="client_info">
                        <div class="flex">
                            <div>{{ selectedClient.sex}}</div>
                            <div>{{ selectedClient.age}}</div>
                            <div>{{ selectedClient.birthday}}</div>
                        </div>
                        <div>
                            <div>{{ selectedClient.adress}}</div>
                        </div>
                        <div class="flex">
                            <div>{{ selectedClient.cell}}</div>
                            <div>{{ selectedClient.email}}</div>    
                        </div>
                        <div class="flex">
                            <div>{{ selectedClient.cell}}</div>
                            <div>{{ selectedClient.email}}</div>    
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
                sort: 'name',
                red: 'red'
                
            }
        },
        methods: {
            showClient(client) {
                this.selectedClient = client;
                console.log(this.sort)
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


.header {
    width: 100%;
    height: 80px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    background-color: #2e394b;
}

#cars {
    width: 250px;
    height: 60px;
    margin-right: 50px;
    padding: 10px;
    border: 2px solid black;
    border-radius: 5px;
    outline: none;
    background-color: #2e394b;
    color: #fff;
}

.sidebar {
    width: 20%;
    border-right: 1px solid #aaa;
}
.client_info {
    width: 60%;
}

.contain {
    display: flex;
}

.add_new {
    padding: 10px;
}

.add_new button {
    width: 100%;
    background-color: #5cb35b;
    border: 1px solid #000;
    border-radius: 2px;
    padding: 10px;
    margin-bottom: 10px;
    cursor: pointer;
    color: #fff;
    font-size: 17px;
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
</style>