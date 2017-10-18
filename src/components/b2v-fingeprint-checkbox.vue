<template>
    <div class="wrapper">
        <label for="cControl" class="full-label">
            <input @change="checkMe" type="checkbox" id="cControl" class="full-label-input" :checked="checked">
            <span class="full-label-indicator"></span>
            <span class="full-label-text">TEXT</span>
        </label>
    </div>
</template>
<script>
  export default {
    name: 'FingerPrintCheckbox',
    props: {},
    data () {
      return {
        checked: false
      }
    },
    methods: {
      checkMe (event) {
        let vm = this
        console.log('checkMe', event.target.checked)
        vm.checked = event.target.checked
      }
    }
  }
</script>

<style lang="scss">
    .wrapper {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100vh;
    }
    .full-label {
        display: block;
        position: relative;
        padding: 0;
        width: 100px;
        height: 100px;
        background-color: rgba(0, 0, 0, 0.2);
        z-index: 0;
        border-radius: 5px;
        overflow: hidden;
        cursor: pointer;
        .full-label-input {
            visibility: hidden;
            position: absolute;
            &:checked ~ .full-label-indicator {
                background-color: green;
                position: absolute;
                width: 100%;
                height: 100%;
                &::after {
                    content: "\e90d";
                    line-height: 1.2em;
                }
            }
            & ~ .full-label-indicator {
                position: absolute;
                width: 100%;
                height: 100%;
                background-color: red;
                transition: all 0.3s;
                left: 0;
                &::after {
                    font-family: "Material Icons";
                    content: "A";
                    color: white;
                    font-size: 5em;
                    text-align: center;
                    line-height: 0.9em;
                }
            }
        }
    }
</style>
