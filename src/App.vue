<template>
  <h3 class="mb-4">Click on the button to trigger the modal !</h3>
  <!-- Button trigger modal -->
  <button type="button" class="btn btn-primary m-auto" data-bs-toggle="modal" data-bs-target="#exampleModal">
    Add Revenue Group
  </button>
  <!-- Modal -->
  <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Add Revenue Group</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <div class="form-group revenue">
            <label for="revenue-title">Revenue Group Title</label>
            <input type="text" class="form-control" placeholder="Revenue Group Title" value="Fashion - 15%" >
          </div>
          <div class="form-group__wrapper">
            <div class="form-group__label"> If </div>
            <div class="form-group__select">
              <select name="" id="" class="form-select" aria-label="Default select example">
                <option value="selected">All</option>
              </select>
            </div>
            <div class="form-group__label">
              of the condition are met
            </div>
          </div>
          <div class="my-5">
            <template v-for="item in addList" :key="item" >
              <div class="rule__wrapper">
                <div class="rule__text">Rule {{ item }}</div>
                <NewRules @counter="checkCounter"></NewRules>
              </div>
            </template>
          </div>
          <div class="form-group__wrapper">
            <div class="form-group__label">Then Revenue is</div>
            <div class="form-group form-group__select input__group">
              <input type="number" class="form-control" placeholder="Revenue">
              <div class="form-group-text">
                <span>%</span>
              </div>
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancel</button>
          <button type="button" class="btn btn-primary">Confirm</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import NewRules from './components/NewRules.vue'
  import 'bootstrap/dist/css/bootstrap.css'

  export default {
    name: 'App',
    data(){
      return{
        addList : 1
      }
    },
    components: {
      NewRules
    },
    methods: {
      addcounter: function(){
        this.addList ++
        console.log('clicked');
      },
      minuscounter: function(){
        this.addList --
        console.log('clicked');
      },
      checkCounter(event){
        if(event == 'add'){
          this.addList ++
        } else if(event == 'minus'){
          if(this.addList > 1){
            this.addList --
          }
        }
      }   
    }
  }
</script>

<style lang="scss">
  $background-grey : #EDECE8;
  $button-background : #856D47;
  $button-blue : #9DDAC6;
  $button-red : #FF4848;
  $text-dark :#253734;
  %button{
    color: white;
    font-size: 1rem;
    background-color: $button-background;
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    margin: .5rem;
    transition: .2s all ease-in-out;
    border: 1px solid $button-background;
    &:hover{
      color: white;
      cursor: pointer;
      background-color: darken($button-background , 10%);
    }
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  p{
    margin-bottom: 0;
  }
  .c{
    &-red{
      color: black;
      background-color: $button-red;
      text-decoration: none;
      font-size: .7rem;    
      padding: .3rem .6rem;
      border-radius: 5px;
      transition: .2s all ease-in-out;
        &:hover{
          background-color: lighttem($button-red, 30%);
          color: lighten(black, 30%);
          cursor: pointer;
        }
      }
    &-blue{
      color: black;
      background-color: $button-blue;
      text-decoration: none;
      font-size: .7rem; 
      padding: .3rem .6rem;
      border-radius: 5px; 
      transition: .2s all ease-in-out;
        &:hover{
          background-color: lighttem($button-blue, 30%);
          color: lighten(black, 30%);
          cursor: pointer;
        }  
      }
  }
  .btn{
    &.btn-primary{
      @extend %button;
    }
  }
  .modal{
    &-title{
      font-weight: bold;
      color: $button-background;
    }
  }
  .rule{
    &__wrapper{
      margin: -1rem;
      padding: 1rem;
      background-color: $background-grey;
      border-top: 2px solid lighten($text-dark , 70%);
      border-bottom: 2px solid lighten($text-dark , 70%);
    }
    &__text{
      text-align: left;
      font-weight: bold;
      text-transform: uppercase;
      font-size: .8rem;
      color: $text-dark;
    }
  }
  .form-group{
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    flex: 1;
    label{
      color: $text-dark;
      font-size: .8rem;
      font-weight: bold;
    }
    &.input__group{
      .form-control{
        padding-right: 20%;
      }
    }
    &.revenue{
      flex:3;
      max-width: unset;
    }
    &__wrapper{
      display: flex;
      align-items: center;
      margin: 1rem -.5rem;
      .form-group{
        margin: 0 .5rem;
      }
    }
    &-text{
      position: absolute;
      right: 0;
      top: 0;
      transform: translate(-10px, 6px);
    }
    &__select{
      max-width: 200px;
      margin: 0 .5rem;
    }

    &__icon{
      display: flex;
      a.icon{
        @extend %button;
        width: 30px;
        height: 30px;
        border-radius: 100%;
      }
    }
    &__label{
      margin: 0 .5rem;
    }
  }
</style>