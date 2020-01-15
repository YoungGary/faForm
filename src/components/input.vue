<template>
  <div>
      <input :type="type" :value="currentValue" @input="input" @blur="handleBlur">
  </div>
</template>
<script>
import Emitter from './emiter'
export default {
    name: 'faInput',
    mixins: [ Emitter ],
    props:{
        type:{
           type:String,
           default:'text' 
        },
        value:{
           type:String,
           default:'text' 
        }
    },
     data () {
        return {
            currentValue: this.value
        }
    },
    watch: {
        value (val) {
            this.currentValue = val;
        }
    },
    methods:{
        input(event){
            const value = event.target.value;
            this.currentValue = value;
            this.$emit('input', value);
            this.dispatch('faFormItem', 'on-form-change', value);
        },
        handleBlur () {
            this.dispatch('faFormItem', 'on-form-blur', this.currentValue);
        }
    }
}
</script>

<style>

</style>