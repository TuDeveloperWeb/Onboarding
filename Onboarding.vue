<!-- Onboarding.vue -->
<template>
    <div v-if="targetElement" class="onboarding">
        <div class="modal-onboarding">
            <div class="modal-onboarding__img">
                <img src="https://static.figma.com/uploads/4e36d3bbbf8633fef1b86238f66bb1bf54f54d2a"
                    width="120px" alt="Imagen" />
            </div>
            <div class="modal-onboarding__content">
                <div class="modal-onboarding__text">
                    Invite others or share this file with a link to jam
                </div>

                <div class="modal-onboarding__bottomContent">
                    <div class="">
                        <div>3 of 3</div>
                    </div>
                    
                    <button>
                        Next
                    </button>
                </div>
            </div>
            <!-- 
        <div class="actions">
          <button @click="prevStep" :disabled="currentStep === 0">Anterior</button>
          <button @click="nextStep" :disabled="currentStep === steps.length - 1">Siguiente</button>
          <button @click="closeOnboarding">Cerrar</button>
        </div> -->
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        targetElement: {
            type: HTMLElement,
            default: null,
        },
    },
    data() {
        return {
            currentStep: 0,
            steps: [
                { text: 'Paso 1: Descripción del paso 1' },
                { text: 'Paso 2: Descripción del paso 2' },
                // Agrega más pasos según sea necesario
            ],
        };
    },

    created() {
        console.log(this.targetElement);
    },

    computed: {
        currentStepText() {
            return this.steps[this.currentStep].text;
        },
    },
    methods: {
        nextStep() {
            if (this.currentStep < this.steps.length - 1) {
                this.currentStep++;
            }
        },
        prevStep() {
            if (this.currentStep > 0) {
                this.currentStep--;
            }
        },
        closeOnboarding() {
            this.$emit('closeOnboarding');
        },
    },
};
</script>
  
<style scoped>
.onboarding {
    position: fixed;
    left: 908px;
    top: 75.5px;
    width: 409px;
    height: 129px;
    background: rgba(196, 189, 189, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 10px;
    border:1px solid #44009d;
    padding: 3px;
}

.modal-onboarding{
    display: flex;  
}

.modal-onboarding__img{
    background-color: #c7baff;
    padding: 5px;
    width: 129px;
    height: 129px;
    display: flex;
    align-items: center;
    /* border-top: 1px solid #44009d;    */
    justify-content: center;
}

.modal-onboarding__content{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: rgb(44, 48, 50);
    color: #fff;
    padding: 8px;

}

.modal-onboarding__bottomContent{
 
    display: flex;
    justify-content: space-between;
}







/* Resto del código de estilos */
</style>
  