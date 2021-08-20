<template>
    <div class="form-group__wrapper mt-1" >
        <div class="form-group__select">
            <select name="" id="" class="form-select" aria-label="Default select example">
            <option value="selected">aff_sub</option>
            <option value="">aff_sub1</option>
            <option value="">aff_sub2</option>
            </select>
        </div>
        <div class="form-group__select">
            <select name="" id="" class="form-select" aria-label="Default select example">
            <option value="selected">is</option>
            <option value="">is</option>
            <option value="">is</option>
            </select>
        </div>
        <div class="form-group">
            <div class="form-group revenue w-100 input__group">
                <input type="text" class="form-control " placeholder="Insert parameter">
                <div class="form-group-text">
                    <a class="c-blue" @click="addRule()" >Add Rule</a>
                </div>
            </div>
            <template v-for="item in addRules" :key="item" >
                <div class="form-group revenue w-100 mt-2 input__group">
                    <input type="text" class="form-control " placeholder="Insert parameter">
                    <div class="form-group-text">
                        <a class="c-red" @click="removeRule()" >Remove Rule</a>
                    </div>
                </div>
            </template>
        </div>
        <div class="form-group__icon">
            <a class="icon" @click="counter('minus')">&minus;</a>
            <a class="icon" @click="counter('plus')">&plus;</a>
        </div>
    </div>
</template>
<script>

export default {
    name: 'App',
    data(){
        return{
            addRules : 0
        }
    },
    methods: {
        counter(event){
            if(event == 'minus'){
                this.$emit('counter', 'minus')
            } else if (event == 'plus'){
                this.$emit('counter', 'add')
            }
        },
        addRule(){
            this.addRules ++
        },
        removeRule(){
            this.addRules --
        }
    }
   
    
}
</script>