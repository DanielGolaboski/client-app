<template>
  <div id="app">
        <div class="header">
            <div class="main_head">
                <h3>TakeLessons</h3>
            </div>
            
            <div >
                <select name="" id="navDropdown">
                    <option value=""> Jason.H</option>
                    <option value="">Jason.S</option>
                </select> 
            </div>     
        </div>
   
        <div class="tab">
          <ul>
            <li>
              <button  @click="setActive('dashboard')" :class="{ active: isActive('dashboard') }" href="#">DASHBOARD</button>
            </li>
            <li>
              <button @click="setActive('calendar')" :class="{ active: isActive('calendar') }" href="#">CALENDAR</button>
            </li>
            <li>
              <button @click="setActive('clients')" :class="{ active: isActive('clients') }" href="#">CLIENTS</button>
            </li>
            <li>
              <button @click="setActive('finances')" :class="{ active: isActive('finances') }" href="#">FINANCES</button>
            </li>
          </ul>
        </div>

        <div id="myTabContent">
          <div class="none" :class="{ 'active': isActive('dashboard') }" id="dashboard">Dashboard component</div>
          <div class="none" :class="{ 'active': isActive('calendar') }" id="calendar">Calendar component</div>
          <div class="none" :class="{ 'active': isActive('clients') }" id="clients">    <Main/> </div>
          <div class="none" :class="{ 'active': isActive('finances') }" id="finances">Finances component</div>
        </div>

  </div>
</template>

<script>

import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Main
  },
  data () {
    return {
      activeItem: 'clients',
    }
  },
  methods: {
    isActive (menuItem) {
      return this.activeItem === menuItem
    },
    setActive (menuItem) {
      this.activeItem = menuItem
    }
  }
}
</script>
  
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* custom scrollbar */
::-webkit-scrollbar {
  width: 10px;
  height: 2vh;
}
::-webkit-scrollbar-track {
  background: #f1f1f1;
}
::-webkit-scrollbar-thumb {
  background: #888;
}
::-webkit-scrollbar-thumb:hover {
  background: #555;
}
.none {
  display: none;
}
.active {
  display: block;
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

.main_head {
  padding-left: 20px;

}

.main_head h3{
  color: #fdfdfd;
  font-weight: 900;
}

#navDropdown {
    width: 250px;
    height: 50px;
    margin-right: 50px;
    padding: 10px;
    border: 2px solid #27303f;
    border-radius: 5px;
    outline: none;
    background-color: #2e394b;
    color: #fff;
}

.tab {
  overflow: hidden;
  border-bottom: 1px solid #234063;
  background-color: #4b87d0;
}

.tab ul {
  list-style: none;
}

.tab ul li button {
  background-color: inherit;
  color: #d1d1d1;
  float: left;
  border: none;
  outline: none;
  cursor: pointer;
  padding: 14px 16px;
  font-weight: 700;
  transition: 0.3s;
}

.tab ul li button:hover {
  background-color: #2e394b;
}

.tab button.active {
  color: #ffffff;
}

.tabcontent {
  display: none;
  padding: 6px 12px;
  border: 1px solid #ccc;
  border-top: none;
}

</style>
